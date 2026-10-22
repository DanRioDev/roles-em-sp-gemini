---
name: roles-em-sp
description: Use when planning cultural outings, dates, family programs, or weekend itineraries in São Paulo using the Rolês em SP remote MCP server (https://rolesemsp.com.br/mcp). Combines semantic discovery over the curated catalogue with live web verification of opening hours, programming, dietary needs, and budget.
---

# Rolês em SP — Cultural Concierge Workflow

Use the **Rolês em SP** remote MCP server (`https://rolesemsp.com.br/mcp`, OAuth 2.1 scope `catalogue:read`) to discover and plan cultural, artistic, and gastronomic outings in São Paulo, Brazil.

> **Architecture boundary:** This skill provides client workflow instructions only. The curated catalogue and backend remain on the remote MCP server.

## 1. Authenticate First

- Ensure the `roles-em-sp` MCP server (`https://rolesemsp.com.br/mcp`) is connected and authenticated via OAuth 2.1 (6-digit email OTP via Cloudflare Access).
- Never attempt to export or dump the full catalogue; query only what the user's current request requires.

## 2. Four-Step Concierge Flow

1. **Semantic Retrieval (`search_roles` / `list_categories_and_regions`)**
   - Call `list_categories_and_regions` when you need valid category or neighborhood filters.
   - Call `search_roles` with the user's intent, neighborhood, company (solo, couple, kids/family, friends), and vibe.
   - Call `get_role_details` on the strongest candidates to inspect curated notes, address, reference links, accessibility, dietary notes, and baseline price tier.

2. **Live Schedule & Programming Check (Web Research)**
   - Curated catalogue records provide baseline context, not real-time ticket or schedule guarantees.
   - When your host environment provides web search or fetch tools, check the venue's official website or current programming for the target day/time before recommending it.
   - If web verification tools are unavailable in the host, state clearly that opening hours and live programming were not verified in real time.

3. **Dietary & Budget Validation**
   - Strictly enforce the user's stated budget cap (per person or total) and dietary constraints (vegetarian, vegan, gluten-free, kid-friendly, alcohol-free) before finalizing candidates.
   - Discard or flag any candidate whose current menu, ticket price, or schedule conflicts with the user's constraints.

4. **Final Ranking & Actionable Itinerary**
   - Present a concise, well-sequenced itinerary (e.g., exhibition -> walk -> coffee/dinner) with neighborhood logistics, realistic transit between stops, estimated spend, and official reference links.
