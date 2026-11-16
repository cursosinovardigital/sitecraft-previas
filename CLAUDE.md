# Arquitetura Oficial - Inovar Digital (Habblaud + OmniRoute + SiteCraft)

## 1. Visão Geral e Regras de Ouro
- Operação autônoma de prospecção B2B, auditoria de sites, criação de landing pages e disparo (E-mail + WhatsApp).
- Metas diárias: 3 leads/sites em Guarulhos-SP (Português do Brasil, UTF-8) e 2 leads/sites no Exterior/EUA (Inglês).
- PROIBIDO prospectar corretores de imóveis ou imobiliárias. Foco em empresas locais com orçamento (clínicas, estética, oficinas, advocacia, academias, roofing, HVAC).
- NUNCA reverta o `delete envClaude.ANTHROPIC_BASE_URL` na função `gerarSiteEPublicar` do `index.js`.

## 2. Divisão de Roteamento de IA (Híbrido)
- **WebDesigner (`gerarSiteEPublicar`)**: Usa diretamente a assinatura **Claude Pro (modelo Sonnet)** via CLI (`claude.cmd`), SEM passar pelo proxy do OmniRoute (`delete envClaude.ANTHROPIC_BASE_URL`), aplicando as skills de `frontend-design` / `designer-taste`.
- **Estrategista e Redator (`chamarIARoteada`)**: Passam pelo **OmniRoute** (`http://localhost:20128/v1/chat/completions`) para economia de tokens, com fallback automático para a API do Gemini 2.5 Flash.
- **Minerador, Analista, Prospectador e Disparador**: Executam via código Node.js puro (Serper.dev, fetch HTML, Supabase e Gmail SMTP), custo zero de tokens.

## 3. Portas, Pastas e Contas do Habblaud
- **Motor Principal e Painel Comercial (`http://localhost:4748`)**: `C:\Users\celso\Desktop\GERAL VICTOR TRIVINHONova pasta\HABBLAUD\index.js`
- **Escritório Visual Habblaud (`http://localhost:4747`)**: Monitora as Contas A, B, C e D.
- **Conta C (Comercial / SiteCraft - 7 Agentes)**: Lê sessões e logs em `C:\Users\celso\.claude-prospeccao\sessions` e `C:\Users\celso\.claude-prospeccao\projects\habblaud-omniroute`.
  - Os 7 agentes ativos na Conta C são: `Estrategista`, `Minerador`, `Analista`, `WebDesigner`, `Prospectador`, `Redator` e `Disparador`.
- **Contas A, B e D**: Reservadas para expansão de novos setores da empresa (ex: Conta A = E-commerce/Next Gen Store; Conta B = Atendimento/Follow-up e Financeiro; Conta D = Conteúdo/Tráfego).

## 4. Hospedagem de Prévias (GitHub Pages)
- Pasta local: `C:\Users\celso\Desktop\GERAL VICTOR TRIVINHONova pasta\HABBLAUD\sitecraft-previas`
- Repositório Git: `https://github.com/cursosinovardigital/sitecraft-previas.git` (branch `main`)
- URL Pública Base: `https://cursosinovardigital.github.io/sitecraft-previas/`