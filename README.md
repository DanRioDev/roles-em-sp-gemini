# Rolês em SP — Universal MCP Connector

Repositório de configuração de cliente (apenas metadados) para conectar assistentes e CLIs de IA ao servidor MCP remoto **Rolês em SP** (`https://rolesemsp.com.br/mcp`, Streamable HTTP + OAuth 2.1 com escopo `catalogue:read`).

> **Nota de arquitetura:** Este repositório contém apenas manifestos de configuração de clientes. Não contém código de servidor, catálogo privado, embeddings nem prompts internos.

- **Site:** https://rolesemsp.com.br/
- **Guia de conexão:** https://rolesemsp.com.br/connect.md
- **Endpoint MCP:** `https://rolesemsp.com.br/mcp` (Streamable HTTP)
- **Registro Oficial MCP:** `br.com.rolesemsp/roles-catalogue-mcp`

---

## Instalação Rápida por Cliente

### Claude (Claude Code / Claude Desktop)
```bash
claude plugin marketplace add DanRioDev/roles-em-sp-mcp
claude plugin install roles-em-sp@roles-em-sp
```
Ou adicione a URL `https://rolesemsp.com.br/mcp` diretamente em **Settings -> Connectors** no Claude.ai / Claude Desktop.

### Google Gemini CLI
```bash
gemini extensions install https://github.com/DanRioDev/roles-em-sp-mcp
```
Depois, autentique dentro do Gemini CLI com `/mcp auth roles-em-sp`.

### OpenAI (ChatGPT / Codex CLI)
Inclui manifesto portátil `plugin.json` + `mcp.json` (`agent-plugins.org`). No ChatGPT / Codex, conecte o servidor MCP Streamable HTTP `https://rolesemsp.com.br/mcp` via OAuth.

### xAI Grok (Grok Web & Grok Build CLI)
```bash
grok mcp add roles-em-sp --transport http https://rolesemsp.com.br/mcp
```
*(Ou auto-descoberto via `.grok/config.toml` e `.cursor/mcp.json`).*

### Alibaba Qwen Code CLI
```bash
qwen mcp add --transport http roles-em-sp https://rolesemsp.com.br/mcp
```
*(Ou auto-descoberto via `.qwen/settings.json`).*

### Moonshot Kimi CLI
```bash
kimi mcp add --transport http --auth oauth roles-em-sp https://rolesemsp.com.br/mcp
kimi mcp auth roles-em-sp
```

### Xiaomi MiMo Code
```bash
mimo mcp auth roles-em-sp
```
*(Configurado via `mimocode.json`).*

### Mistral Le Chat
Em **Connectors -> + Add Connector -> Custom MCP Connector**, informe `https://rolesemsp.com.br/mcp` e conclua o login OAuth.
