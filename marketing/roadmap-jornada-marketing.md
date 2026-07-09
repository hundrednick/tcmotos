# TC-MKT-STORE — Roadmap da Jornada (Meta → Google Ads → TikTok)
**Loja:** TCmotos ABC · **Criado em:** 08/07/2026

Este documento complementa a Estrutura Organizacional Base: aqui está o passo a passo pra tirar o projeto do papel, começando por Meta Ads (onde já há campanha rodando) e preparando a entrada de Google Ads e TikTok Ads mais à frente.

---

## Etapa 0 — Pré-requisito bloqueante (fazer antes de subir qualquer criativo novo)

Nada do checklist da Seção 6 do documento base pode ser cumprido sem isso primeiro:

- [ ] **Confirmar estoque real** de cada modelo que vai virar criativo (loja/estoque fornece código TC-0xxx + foto de catálogo)
- [ ] **Confirmar com a financeira** taxa de juros e CET reais por modelo/faixa de entrada (hoje o valor de parcela usado é só uma estimativa simples, valor ÷ 48, sem juros — decisão registrada na Seção 7 do documento base, válida até essa confirmação chegar)

Enquanto isso não estiver confirmado: criativos com preço/parcela **não sobem**. Estrutura de campanha (nomes, conjuntos, segmentação) pode ser preparada em paralelo, pausada, sem problema.

---

## Fase 1 — Meta Ads (agora)

### 1.1 Diagnóstico do que já existe na conta

Auditoria feita em 08/07/2026 na conta **CA - TC MOTOS ABC** (conectada via Windsor.ai):

| Campanha | Status | Objetivo | Conjuntos |
|---|---|---|---|
| `[Engajamento - WhatsApp] [Principal - Dia]` (id ...339190673) | PAUSADA (legado) | OUTCOME_ENGAGEMENT | Publico 1/2/3 por faixa etária |
| `[Engajamento - WhatsApp] [Principal - Noturno]` (id ...230780673) | PAUSADA (legado) | OUTCOME_ENGAGEMENT | Publico Aberto |
| `[Engajamento - WhatsApp] [Principal - Dia]` (id ...682810673) | **ATIVA** | OUTCOME_ENGAGEMENT | Publico 1/2/3 por faixa etária |
| `[Engajamento - WhatsApp] [Principal - Noturno]` (id ...583710673) | **ATIVA** | OUTCOME_ENGAGEMENT | Publico Aberto |

**Achado:** há duas campanhas ativas com nomes idênticos (uma "Dia", uma "Noturno") e duas pausadas com os mesmos nomes — exatamente a mistura sem faixa etária/variante no nome descrita na Seção 2 do documento base. Os anúncios também não seguem o padrão `[MODELO-MOTO]-[VARIANTE]-[DATA-SUBIDA]` (hoje são `00 - CRIATIVO PARCELA [FOTO]`, `00 - VIDEO`, `00 - VIDEO 2`, `00 - FZ15 2024 [FOTO]`).

### 1.2 O que fazer, em ordem

1. **Não mexer nas campanhas ativas ainda** — elas têm histórico de gasto (R$ ~483 a R$ 1.585 por conjunto nos últimos 30 dias) e dados de CTR/CPC que servem de base de comparação. Pausar/duplicar sem critério perde essa referência.
2. **Resolver a Etapa 0** (estoque + financeira).
3. **Criar a nova estrutura em paralelo**, pausada, com a nomenclatura da Seção 2 (`ABC-WhatsApp-Jul26` → conjuntos `Dia-18a25`, `Dia-25a45`, `Dia-46a55`, `Noturno-Geral`) — ver Fase 1.3 abaixo. Isso não interfere com o que já roda.
4. **Rodar lado a lado por 1-2 semanas**: estrutura nova com criativos atualizados vs. estrutura antiga já validada.
5. **Migrar o orçamento** da estrutura antiga pra nova conforme a nova comprovar performance igual ou melhor (Seção 4: comparar CTR/CPC variante A vs B por faixa etária, pausar a pior).
6. **Pausar e arquivar as campanhas antigas** (as 2 pausadas legado + eventualmente as 2 ativas atuais) só depois da migração — nunca antes.
7. Daí em diante, seguir a cadência normal da Seção 4 do documento base (revisão diária/semanal/quinzenal/mensal).

### 1.3 Estrutura nova proposta (a criar)

Baseada na Seção 2 do documento base e espelhando a segmentação que já existe hoje:

- **Campanha:** `ABC-WhatsApp-Jul26` — objetivo Engajamento (Click to WhatsApp), criada pausada
- **Conjuntos:**
  - `Dia-18a25` — mesma geo dos conjuntos "Publico 2" atuais
  - `Dia-25a45` — mesma geo dos conjuntos "Publico 1" atuais
  - `Dia-46a55` — mesma geo dos conjuntos "Publico 3" atuais (hoje vai até 65+, confirmar se mantém a faixa)
  - `Noturno-Geral` — mesma geo aberta dos conjuntos noturnos atuais

**Isso ainda não foi criado na conta.** Preciso confirmar com você: orçamento (diário, por conjunto ou por campanha) e se mantém exatamente os mesmos raios/localizações dos conjuntos atuais. Assim que confirmar, crio tudo pausado (sem gasto) — anúncios com preço só entram depois da Etapa 0 resolvida.

---

## Fase 2 — Google Ads (preparação, sem execução ainda)

Conector Google Ads **ainda não está conectado** no Windsor.ai desta conta. Quando chegar a hora:

1. Conectar a conta Google Ads via Windsor.ai (fluxo OAuth)
2. Definir objetivo — provavelmente Pesquisa (captura de quem já busca "moto seminova [cidade]") complementando o Meta, que hoje é 100% prospecção fria
3. Aplicar a mesma lógica de nomenclatura da Seção 2, adaptada: campanha `ABC-Search-[Periodo]`, grupos de anúncio por modelo/intenção
4. Reaproveitar os criativos estáticos (blueprints) como base de landing/anúncio responsivo, ajustando pro formato de texto do Google
5. Definir orçamento **incremental**, não redistribuindo o que já roda no Meta até este canal provar CPL competitivo

**Não iniciar** antes da Fase 1 estabilizada (nova estrutura Meta validada) — evita otimizar dois canais novos ao mesmo tempo sem baseline.

## Fase 3 — TikTok Ads (preparação, sem execução ainda)

Conector TikTok **também ainda não está conectado**. Quando for a vez:

1. Conectar a conta TikTok Ads via Windsor.ai
2. Público de moto seminova costuma performar melhor em formato vídeo nativo — os criativos "00 - VIDEO" já testados no Meta são o ponto de partida, não os estáticos
3. Nomenclatura: mesma lógica da Seção 2, campanha `ABC-TikTok-[Periodo]`
4. Testar com verba pequena e comparar CPL contra Meta antes de escalar

**Pré-requisito:** só entra depois que Google Ads (Fase 2) estiver rodando com dado suficiente pra comparar os três canais de forma justa — evita diluir atenção do time de criativo (Seção 5) em três frentes novas de uma vez.

---

## Resumo — onde estamos agora

| Canal | Status da conexão | Etapa atual |
|---|---|---|
| Meta Ads | Conectado (conta CA - TC MOTOS ABC) | Fase 1 — aguardando Etapa 0 + sua confirmação de orçamento/segmentação pra criar estrutura nova |
| Google Ads | Não conectado | Fase 2 — não iniciar ainda |
| TikTok Ads | Não conectado | Fase 3 — não iniciar ainda |

Este roadmap deve ser revisado junto com a Seção 3 (mapa de documentos) do documento base sempre que uma fase mudar de estágio.
