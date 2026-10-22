# Rolês em SP — Universal MCP Connector & Agent Skill

[![Official MCP Registry](https://img.shields.io/badge/MCP_Registry-br.com.rolesemsp%2Froles--catalogue--mcp-0f766e)](https://registry.modelcontextprotocol.io/?q=br.com.rolesemsp)
[![Install in Cursor](https://img.shields.io/badge/Cursor-Install_MCP-000000?logo=cursor)](https://cursor.com/en/install-mcp?name=roles-em-sp&config=eyJ1cmwiOiJodHRwczovL3JvbGVzZW1zcC5jb20uYnIvbWNwIn0%3D)
[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_MCP-0098FF?logo=visualstudiocode)](https://insiders.vscode.dev/redirect/mcp/install?name=roles-em-sp&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Frolesemsp.com.br%2Fmcp%22%7D)
[![Mentioned in Awesome Gemini CLI](https://awesome.re/mentioned-badge-flat.svg)](https://github.com/Piebald-AI/awesome-gemini-cli)

Repositório universal de configuração de clientes e Agent Skill (apenas metadados públicos) para conectar assistentes, IDEs e CLIs de IA ao servidor MCP remoto **Rolês em SP** (`https://rolesemsp.com.br/mcp`, Streamable HTTP + OAuth 2.1 com escopo `catalogue:read`).

**English Summary:** Universal client configuration and Agent Skill package for **Rolês em SP**, a remote Streamable HTTP Model Context Protocol (MCP) server for discovering and planning cultural, artistic, and gastronomic outings in São Paulo, Brazil (`https://rolesemsp.com.br/mcp`). Combines semantic search over a curated 476-venue catalogue (`search_roles`, `get_role_details`, `list_categories_and_regions`) with companion web verification for live schedules, dietary needs, and budgets.

> **Nota de arquitetura / Architecture boundary:** Este repositório contém apenas manifestos de configuração de clientes e instruções públicas de uso (`skills/roles-em-sp/SKILL.md`, `GEMINI.md`). O backend e o catálogo curado permanecem privados no servidor remoto protegido por OAuth 2.1.

- **Website:** https://rolesemsp.com.br/
- **Setup Guide (`connect.md`):** https://rolesemsp.com.br/connect.md
- **Remote MCP Endpoint:** `https://rolesemsp.com.br/mcp` (Streamable HTTP)
- **SEP-1649 Server Card:** https://rolesemsp.com.br/.well-known/mcp/server-card.json
- **Official MCP Registry ID:** `br.com.rolesemsp/roles-catalogue-mcp`

---

## Instalação Rápida por Cliente / Quick Install

### 1. Universal Agent Skills (`skills.sh` — Claude Code, Cursor, Codex, OpenCode, Gemini CLI, +50 agents)
```bash
npx skills add DanRioDev/roles-em-sp-mcp
```

### 2. Claude (Claude Code CLI / Claude Desktop / Claude.ai)
```bash
claude plugin marketplace add DanRioDev/roles-em-sp-mcp
claude plugin install roles-em-sp@roles-em-sp
```
Ou via comando direto de MCP:
```bash
claude mcp add --transport http roles-em-sp https://rolesemsp.com.br/mcp
```
No **Claude.ai / Claude Desktop**, adicione `https://rolesemsp.com.br/mcp` em **Settings → Connectors**.

### 3. Cursor & VS Code (1-Click Deeplinks)
- **Cursor:** [Clique para instalar no Cursor](https://cursor.com/en/install-mcp?name=roles-em-sp&config=eyJ1cmwiOiJodHRwczovL3JvbGVzZW1zcC5jb20uYnIvbWNwIn0%3D) (ou use `.cursor/mcp.json` na raiz deste repositório)
- **VS Code (GitHub Copilot):** [Clique para instalar no VS Code](https://insiders.vscode.dev/redirect/mcp/install?name=roles-em-sp&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Frolesemsp.com.br%2Fmcp%22%7D)

### 4. Google Gemini CLI
```bash
gemini extensions install https://github.com/DanRioDev/roles-em-sp-mcp
```
Depois, autentique dentro do Gemini CLI com `/mcp auth roles-em-sp`.

### 5. OpenAI (ChatGPT / Codex CLI)
Inclui manifesto portátil `plugin.json` + `mcp.json` (`agent-plugins.org`). No ChatGPT (Developer Mode / Connectors) ou Codex CLI, conecte o servidor MCP Streamable HTTP `https://rolesemsp.com.br/mcp` via OAuth.

### 6. OpenCode / Windsurf / Cline / Continue / Zed
Adicione o endpoint Streamable HTTP `https://rolesemsp.com.br/mcp` na configuração de servidores MCP remotos (`type: "streamable-http"` ou `"http"`).

### 7. xAI Grok (Grok Web & Grok Build CLI)
```bash
grok mcp add roles-em-sp --transport http https://rolesemsp.com.br/mcp
```
*(Ou auto-descoberto via `.grok/config.toml`).*

### 8. Alibaba Qwen Code CLI
```bash
qwen mcp add --transport http roles-em-sp https://rolesemsp.com.br/mcp
```
*(Ou auto-descoberto via `.qwen/settings.json`).*

### 9. Moonshot Kimi CLI
```bash
kimi mcp add --transport http --auth oauth roles-em-sp https://rolesemsp.com.br/mcp
kimi mcp auth roles-em-sp
```

### 10. Xiaomi MiMo Code & Mistral Le Chat
- **MiMo Code:** `mimo mcp auth roles-em-sp` (via `mimocode.json`)
- **Mistral Le Chat:** Em **Connectors → + Add Connector → Custom MCP Connector**, informe `https://rolesemsp.com.br/mcp`.

---

## Ferramentas Públicas (`catalogue:read`)

Após autenticar via código OTP de 6 dígitos enviado para seu e-mail (sessão OAuth válida por 365 dias), o conector disponibiliza 3 ferramentas somente-leitura:
- `search_roles` — Busca semântica e filtrada de rolês culturais, gastronômicos e passeios em São Paulo.
- `get_role_details` — Detalhes curados do local (endereço, resumo, faixa de preço, acessibilidade, restrições alimentares e links de referência).
- `list_categories_and_regions` — Lista as categorias e regiões de São Paulo disponíveis no catálogo.
