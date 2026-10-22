# O Benchmark Prático de MCP em Português — 5 Desafios Reais em São Paulo

Testar modelos de IA (Claude Opus/Sonnet 5.5, GPT-6, Gemini, DeepSeek, Qwen) e clientes MCP (Claude Code, Cursor, Codex, Gemini CLI, OpenCode) com exemplos de "to-do list" ou APIs de clima não revela como o agente lida com **restrições reais cruzadas**: busca semântica, checagem de programação ao vivo na web, aritmética de orçamento, logística de transporte em São Paulo e síntese em português natural.

O **[Rolês em SP](https://rolesemsp.com.br)** (`https://rolesemsp.com.br/mcp`, registro oficial `br.com.rolesemsp/roles-catalogue-mcp`) funciona como um **benchmark gratuito, sem API keys e 100% em português** para avaliar o seu agente.

---

## Como rodar o Benchmark em 60 segundos

1. **Instale a Agent Skill + Conector MCP no seu agente:**
   ```bash
   # Universal (skills.sh — Claude Code, Cursor, Codex, OpenCode, Gemini CLI)
   npx skills add DanRioDev/roles-em-sp-mcp

   # Ou via Claude Code Plugin Marketplace
   claude plugin marketplace add DanRioDev/roles-em-sp-mcp
   claude plugin install roles-em-sp@roles-em-sp

   # Ou via Gemini CLI
   gemini extensions install https://github.com/DanRioDev/roles-em-sp-mcp
   ```
   *(No Claude.ai, Claude Desktop ou ChatGPT, adicione o conector MCP remoto `https://rolesemsp.com.br/mcp` — veja [connect.md](https://rolesemsp.com.br/connect.md)).*

2. **Autentique uma única vez** com o código OTP de 6 dígitos enviado para o seu e-mail (`catalogue:read`, sessão válida por 365 dias).
3. **Rode os 5 prompts abaixo** e pontue a resposta de acordo com a rubrica de 100 pontos.

---

## Rubrica Objetiva de Avaliação (100 Pontos por Desafio)

| Critério | Pontos | O que o agente precisa demonstrar |
| :--- | :---: | :--- |
| **1. Recuperação Semântica MCP (`search_roles` / `get_role_details`)** | **25 pts** | Usa as ferramentas do servidor MCP para encontrar candidatos reais do catálogo curado (ex: `IMS Paulista`, `CCSP`, `Casa Hario`, `Viveiro Manequinho Lopes`, `Claytime Ateliê`, `Pivô`) em vez de alucinar ou inventar nomes. |
| **2. Verificação Ao Vivo na Web (Horários e Programação)** | **25 pts** | Usa a ferramenta de web search/fetch do host para checar se o local abre no dia/horário pedido e o que está em cartaz (ou declara honestamente se o host não tiver acesso à web). |
| **3. Matemática de Orçamento e Restrições (Dieta / Clima / Idade)** | **25 pts** | Soma transporte + ingressos + alimentação dentro do teto estipulado e respeita restrições explícitas (vegetariano, vegano, sem álcool, criança pequena, chuva). |
| **4. Logística Urbana de São Paulo (Bairros e Deslocamento)** | **15 pts** | Agrupa paradas próximas (a pé ou 1–2 estações de metrô) sem propor deslocamentos irreais em horário de pico (ex: cruzar de Itaquera ao Morumbi em 15 minutos). |
| **5. Bloco `📱 Copiar pro WhatsApp` (Português Paulista Natural)** | **10 pts** | Para passeios de 2+ pessoas, gera o convite curto pronto para colar no WhatsApp sem travessões de IA, com links `?s=together` e rodapé `(montado no rolesemsp.com.br)`. |

---

## Os 5 Níveis do Desafio

### Nível 1 — Date Cultural com Orçamento Fechado (Eixo Paulista/Paraíso)
> **Prompt:**
> *"Vamos sair neste sábado às 15h perto da Avenida Paulista. Somos dois, vegetarianos, não bebemos álcool, queremos ver fotografia ou arte, tomar um café especial calmo para conversar e gastar no máximo R$ 150 no total para o casal (incluindo metrô). Monte o roteiro e o convite pro WhatsApp."*
- **Comportamento esperado:** Cruzar espaços gratuitos como **[IMS Paulista](https://rolesemsp.com.br/go/l_e198ab066794f99bf3697558d925ebb9?s=discover)** ou **[CCSP](https://rolesemsp.com.br/go/l_78b4dfa5957291dc9bef81c2f418672a?s=discover)** com parada tranquila como a **[Casa Hario](https://rolesemsp.com.br/go/l_5352e164f65d8e03508233475086c6c1?s=discover)**, detalhando o custo para duas pessoas abaixo de R$ 150.

### Nível 2 — Tarde de Chuva Sem Pisar em Shopping (Ateliê ou Arquitetura)
> **Prompt:**
> *"Previsão de chuva forte em São Paulo sábado à tarde. Quero sair com uma amiga para fazer algo manual (cerâmica/ateliê) ou visitar arquitetura e arte contemporânea no Centro/Pinheiros, 100% coberto e longe de shopping center."*
- **Comportamento esperado:** Distinguir oficinas que exigem agendamento prévio (**[Shoyu Crafts](https://rolesemsp.com.br/go/l_488024fe82ce5a9b7588c6fed990055c?s=discover)**) de opções de pintura na mesa (**[Claytime Ateliê](https://rolesemsp.com.br/go/l_c32fec9a67ca8de9c123ef606bda54a7?s=discover)**) ou circuito coberto no Centro (**[Pivô no Copan](https://rolesemsp.com.br/go/l_7aa6b110afc3715b5a932de7593a6a2b?s=discover)** + **[Sesc 24 de Maio](https://rolesemsp.com.br/go/l_4adc4ec92f24f3db1382a6fdfc6dd43e?s=discover)**).

### Nível 3 — Domingo de Manhã com Criança de 3 Anos (Zero Fila e Saída Fácil)
> **Prompt:**
> *"Domingo às 9h30 com minha filha de 3 anos. Preciso de um lugar arborizado ou cultural plano, com sombra, sem fila longa e fácil de ir embora rápido se bater o sono das 11h30."*
- **Comportamento esperado:** Priorizar locais planos e calmos como o **[Viveiro Manequinho Lopes](https://rolesemsp.com.br/go/l_a60f7abf4f6fa2ed66c9054162fbae71?s=discover)** + Jardim de Esculturas do **[MAM](https://rolesemsp.com.br/go/l_af28db6f8b2238209eca7dbc6b2be777?s=discover)** ou **[A Casa Tombada](https://rolesemsp.com.br/go/l_ccab2e4cf97cc728e629ed8a242037c5?s=discover)**, verificando programação infantil no site oficial.

### Nível 4 — Rolê Solo de Arquitetura e Cinema de Rua
> **Prompt:**
> *"Tenho uma sexta-feira livre à tarde sozinho em SP. Quero visitar uma casa modernista histórica ou exposição de arquitetura e emendar numa sessão de cinema de rua no fim da tarde. Não precisa de convite de WhatsApp."*
- **Comportamento esperado:** Combinar espaços como **[Casa de Vidro — Instituto Bardi](https://rolesemsp.com.br/go/l_4a5938cce4947a5e66fa9ee02dedf2da?s=discover)** / **[Casa-Ateliê Tomie Ohtake](https://rolesemsp.com.br/go/l_66309ab6ff71a08971bb02986af74a99?s=discover)** ou **[IMS Paulista](https://rolesemsp.com.br/go/l_e198ab066794f99bf3697558d925ebb9?s=discover)** com sessão no **[CineSesc](https://rolesemsp.com.br/go/l_b1048071fcc629d4d05ca9acdfe095b7?s=discover)** ou **[Cinemateca Brasileira](https://rolesemsp.com.br/go/l_ad576b297e76f2a1098a599b8d19c414?s=discover)**, e **omitir** o bloco de WhatsApp por ser um passeio solo.

### Nível 5 (Boss Fight) — Grupo de 4 Amigos com Restrições Cruzadas
> **Prompt:**
> *"Sábado à tarde para 4 amigos encontrando no meio do caminho perto do metrô (Linha Verde ou Azul). No grupo tem 1 pessoa vegana, 1 pessoa que não bebe álcool, ninguém quer fila de mais de 15 minutos e o teto é R$ 90 por pessoa no total. Queremos 1 parada cultural gratuita + 1 lugar pra comer/conversar e o texto pronto pro grupo do WhatsApp."*
- **Comportamento esperado:** Usar `list_categories_and_regions` + `search_roles` + `get_role_details`, checar horários de sábado na web, validar opções veganas e sem álcool dentro de R$ 90/pessoa (R$ 360 para o grupo de 4) e entregar o bloco `📱 Copiar pro WhatsApp` pronto para enviar no grupo.
