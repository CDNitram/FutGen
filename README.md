# FutGen · Manager

> **Sistema de gestão para futebol amador** — Estrela Mecânica FC  
> Stack: HTML/CSS/JS (single file) · Google Apps Script · Google Sheets

---

## 🚀 Demo

**GitHub Pages →** [https://cdnitram.github.io/FutGen/](https://cdnitram.github.io/FutGen/)

---

## 📁 Estrutura do Repositório

```
FutGen/
├── App/
│   └── FutGen_Manager_V4.html   ← Frontend principal (versão atual)
├── GAS/
│   └── FutGen_GAS_v3.js         ← Google Apps Script (backend)
└── README.md
```

---

## 🏗️ Arquitetura

```
Browser (GitHub Pages)
    │
    │  fetch() — JSONP via GAS Web App URL
    ▼
Google Apps Script (GAS)
    │
    │  SpreadsheetApp
    ▼
Google Sheets — futgen_database_v3
    (jogadores · jogos · artilheiros · times · juizes · clube · logs)
```

> **Próximo passo (roadmap):** migrar banco para Supabase + PostgreSQL com RLS.

---

## ✨ Funcionalidades — V4

| Módulo | Status |
|---|---|
| Dashboard — KPIs ao vivo (aproveitamento, artilheiros, elenco, gols) | ✅ |
| Temporada — W/D/L dinâmico via GAS | ✅ |
| Convocação — wizard 3 passos (conv → preview → confirmação) | ✅ |
| Registro de jogo — POST via GAS (`insert_jogo`) | ✅ |
| Pagamentos — salvo junto ao jogo (`save_pagamentos`) | ✅ |
| Elenco — listagem ao vivo (`jogadores`) | ✅ |
| Artilheiros — ranking ao vivo (`artilheiros`) | ✅ |
| Times adversários — CRUD via GAS (`times` / `insert_time`) | ✅ |
| Árbitros — CRUD via GAS (`juizes` / `insert_referee`) | ✅ |
| Configurações do clube — carregado do GAS, sem dados hardcoded | ✅ |
| Modo offline — graceful fallback (sem dados mock sensíveis) | ✅ |
| Loading spinner com progress bar durante init | ✅ |

---

## 🔒 Segurança

Todo dado sensível (PIX, telefones, datas de nascimento, documentos) vive **exclusivamente no Google Sheets** e trafega via GAS em runtime.  
O HTML público (GitHub Pages) **não contém** nenhum dado pessoal ou credencial hardcoded.

- ✅ Nenhuma chave PIX no código-fonte
- ✅ Nenhum dado de jogador (nome real, telefone, doc) no HTML
- ✅ Fallback offline retorna array vazio — sem dados mock
- ✅ GAS_URL é pública por design (GAS Web Apps são stateless e controlados por permissão no Google)

---

## ⚙️ Setup

### 1. Google Sheets

Base de dados: **futgen_database_v3**  
`Spreadsheet ID: 1JqWOJUAlOhMQWXSj1ngqU0Wn9eBoXCN9kjY85V0bonM`

Abas:
| Aba | Layout | Descrição |
|---|---|---|
| `jogadores` | row 0 = título, row 1 = headers, row 2+ = dados | Elenco |
| `jogos` | row 0 = título, row 1 = headers, row 2+ = dados | Partidas |
| `artilheiros` | row 0 = título, row 1 = headers, row 2+ = dados | Ranking de gols |
| `times` | row 0 = título, row 1 = headers, row 2+ = dados | Times adversários |
| `juizes` | row 0 = título, row 1 = headers, row 2+ = dados | Árbitros |
| `clube` | row 0 = headers, row 1 = valores | Config do clube (horizontal) |
| `logs` | — | Auditoria de ações |

### 2. Google Apps Script

1. Abra o Google Sheets → **Extensões → Apps Script**
2. Cole o conteúdo de `GAS/FutGen_GAS_v3.js`
3. Salve e **Implantar → Nova implantação → Web App**
   - Executar como: **Eu**
   - Acesso: **Qualquer pessoa**
4. Copie a URL gerada

### 3. Frontend

Abra `App/FutGen_Manager_V4.html` e confirme a variável no topo do `<script>`:

```js
const GAS_URL = 'https://script.google.com/macros/s/AKfycbx.../exec';
```

Substitua pela URL da sua implantação se necessário.

### 4. Deploy

Faça push para a branch `main` — o GitHub Pages serve automaticamente.  
URL pública: `https://cdnitram.github.io/FutGen/App/FutGen_Manager_V4.html`

---

## 🔌 API GAS — Referência

### GET Actions

| `?action=` | Retorno |
|---|---|
| `all` | `{ jogadores, jogos, artilheiros, clube }` |
| `times` | Lista de times adversários |
| `juizes` | Lista de árbitros |
| `logs` | Log de ações recentes |

### POST Actions

Envio: `JSON.stringify({ action, ...payload })`

| `action` | Payload obrigatório | Retorno |
|---|---|---|
| `insert_jogo` | campos da aba `jogos` | `{ ok, match_id }` |
| `save_convocacao` | `{ match_id, jogadores[] }` | `{ ok }` |
| `save_pagamentos` | `{ match_id, pagamentos[] }` | `{ ok }` |
| `insert_time` | campos da aba `times` | `{ ok, team_id }` |
| `insert_referee` | campos da aba `juizes` | `{ ok, referee_id }` |

---

## 🎨 Design System — Premium Pitch

| Token | Valor |
|---|---|
| `--field` | `#0D2818` (verde campo) |
| `--gold` | `#C9933A` (ouro) |
| `--or` | `#E8621A` (laranja) |
| `--bg` | `#FAFAF7` (off-white) |

Fontes: **Playfair Display** (headings/italic) · **Inter** (UI) · **JetBrains Mono** (dados)

---

## 🗺️ Roadmap

- [ ] Migração do banco para **Supabase + PostgreSQL** com RLS
- [ ] Auth de usuário (admin × jogador)
- [ ] Módulo financeiro completo (receitas / despesas / saldo)
- [ ] Notificações de convocação via WhatsApp API
- [ ] Hosting: **Vercel** com domínio customizado
- [ ] PWA (service worker + manifest)

---

## 📋 Versões

| Versão | Descrição |
|---|---|
| V4 (atual) | GAS completo — dados reais, todos POSTs funcionando, sem mocks sensíveis |
| V3 | Integração parcial GAS + mocks locais |
| V2 | MVP frontend estático |
| V1 | Protótipo inicial |

---

## 👤 Autor

**Martin Cordoba** · [@CDNitram](https://github.com/CDNitram)  
Presidente — Estrela Mecânica FC · Foz do Iguaçu, PR

---

*FutGen · Manager V4 · Premium Pitch Design System*
