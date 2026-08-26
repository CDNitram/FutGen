⚽ FutGen

Plataforma de gestão de futebol amador — Estrela Mecânica FC · Foz do Iguaçu, PR
Desenvolvido por TechNigma AI Lab

O que é

FutGen é uma plataforma web para gestão de times de futebol amador, com foco em:

📋 Gestão de elenco — cadastro de jogadores, posições, grupos e status
📅 Histórico de jogos — partidas, placares, gols e artilheiros
⚽ Artilharia — ranking de gols por temporada
🧤 Árbitros & Goleiros — marketplace de agenciamento (em desenvolvimento)
💰 Financeiro — controle de pagamento por partida (em desenvolvimento)
Estrutura do projeto
FutGen/
│
├── apps/
│   ├── futgen_player_app_v1.html     # App do jogador (leitura) — público
│   └── futgen_admin_v3.html          # App do organizador (gestão)
│
├── database/
│   ├── futgen_database_v2.xlsx       # Schema + seed data local
│   └── futgen_database_schema_v2.xlsx# Documentação do schema
│
├── pitch/
│   └── futgen_arbitros_pitch.pptx    # Pitch deck — módulo árbitros & goleiros
│
└── README.md
Stack
Camada	Tecnologia
Frontend	HTML · CSS · JavaScript (vanilla)
Backend (Fase 1)	Google Apps Script (GAS)
Banco de dados (Fase 1)	Google Sheets
Hospedagem	GitHub Pages
Backend (Fase 2)	Supabase + PostgreSQL
IA	Claude API (TechNigma AI Lab)
Apps ao vivo
App	Descrição	Status
Player App V1	Tela pública do jogador — artilheiros, jogos, elenco	🟢 Live
Admin App V3	Gestão do clube — convocações, financeiro, relatórios	🟡 Beta
Árbitros & Goleiros	Marketplace de agenciamento	🔵 Em desenvolvimento
Banco de dados

O banco de dados opera em Google Sheets na Fase 1, com migração planejada para Supabase + PostgreSQL.

Sheet ID (produção): 1tQqzhs0PhI4aPgPfX2bmbTcd4-1eoxjHQRj3c9zPVes

Tabelas
Aba	Conteúdo
jogadores	Elenco completo (23 atletas)
jogos	Histórico de partidas (J1–J18)
placares_gols	Eventos de gol por partida
artilheiros	Ranking de gols da temporada
campos	Campos e quadras cadastrados
convocacoes	Presença confirmada por jogo
pagamentos	Controle financeiro por partida
log_futgen	Auditoria de ações do sistema
Piloto

Clube: Estrela Mecânica FC
Cidade: Foz do Iguaçu, PR
Temporada: 2025–2026
Jogos registrados: 18 (J1–J18)
Atletas: 23
Artilheiro: Anderson Felipe — 30 gols

Roadmap
Fase 1 — MVP Foz (agora)
 App do jogador (leitura) — elenco, jogos, artilheiros
 App do organizador — convocação, financeiro, relatórios
 Banco de dados Google Sheets
 GAS endpoint (GET/POST)
 Deploy GitHub Pages
 Módulo árbitros & goleiros
Fase 2 — Expansão (3–6 meses)
 Auth de jogadores
 Votação pós-jogo (MVP, Raça, Garra)
 Rating por IA (FutGen Score via Claude API)
 PIX integrado
 Expansão Cascavel e Toledo
Fase 3 — Plataforma (6–12 meses)
 Migração Supabase + PostgreSQL
 WebSocket ao vivo
 SaaS para times
 Multi-cidade
Convenções de código
IDs de jogadores: PLR_001, PLR_002 … PLR_1038
IDs de partidas: MTH_001 → serial J1, J2 …
IDs de eventos: EVT_001, EVT_002 …
Idioma: labels em Português (BR) · código em inglês
Versionamento de arquivos: nome_vN_YYYY-MM-DD.html
Sobre

Desenvolvido por Martin Cordoba — fundador da TechNigma AI Lab

FutGen · TechNigma AI Lab · 2026# FutGen
