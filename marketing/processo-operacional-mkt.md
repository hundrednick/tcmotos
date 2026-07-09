# TC-MKT-STORE — Processo Operacional Padrão (SOP)
**Loja:** TCmotos ABC · **Criado em:** 08/07/2026

Este documento define como a operação de mídia paga passa a ser conduzida por mim (Claude), de forma replicável entre ambiente de teste e produção, com regras claras de autonomia e guardrails de orçamento. Ele assume o lugar operacional do "Time de criativo" e do "Responsável pela campanha" descritos na Seção 5 do documento base — mas não substitui os papéis que dependem de fato do mundo real (estoque, financiamento).

---

## 1. Matriz de responsabilidade — o que muda e o que não muda

| Papel (Seção 5 do doc base) | Antes | Agora |
|---|---|---|
| Time de criativo (montar arte, subir no Ads Manager) | Humano | **Eu assumo a operação de conta** (criar/subir campanha, conjunto, anúncio, seguindo nomenclatura). Artes finais continuam vindo do time de design a partir dos blueprints — eu não gero imagem. |
| Responsável pela campanha (acompanhar métrica, decidir corte/escala, manter documento atualizado) | Humano | **Eu assumo**: leitura diária/semanal de métrica, decisão de pausar/escalar dentro dos limites da Seção 5 abaixo, atualização mensal do plano geral. |
| Loja/estoque (confirmar moto disponível) | Humano | **Continua humano.** Eu não tenho acesso ao estoque real — sigo dependendo da confirmação (código TC-0xxx) antes de qualquer anúncio com aquele modelo ir ao ar. |
| Financeira (confirmar taxa/CET) | Humano | **Continua humano.** Mesma razão: é um dado externo que só a financeira tem. Enquanto não vier, a parcela em anúncio continua em modo estimado (Seção 7 do doc base) e eu sinalizo isso, não decido por conta própria usar uma taxa não confirmada. |
| Aprovação de criativo novo (compliance, "sujeito a análise de crédito") | Humano | **Continua humano** — é uma checagem de conformidade, não uma decisão operacional. |

Ou seja: eu assumo a **execução e as decisões de mídia** (o que pausar, o que escalar, o que subir na estrutura certa, quando). O que depende de fatos do negócio que só humanos confirmam continua sendo checkpoint humano — automatizar isso seria assumir dado que ninguém validou.

---

## 2. Ambiente de teste (fazer antes de qualquer automação em produção)

Passo que só você consegue fazer (exige seu acesso admin na Business Manager):

1. Meta Business Suite → Configurações do Negócio → Contas → Contas de anúncio → Adicionar → **Criar uma nova conta de anúncio** (ex: nome "TC Motos ABC - TESTE"). Sem cartão de pagamento vinculado — assim nada ativa de verdade por engano.
2. Me avisar o **ID dessa conta nova** (ou me dar acesso de admin nela) pra eu conectar via Windsor.ai (mesmo conector que já uso na conta real).
3. Depois de conectada, eu confirmo com `get_connectors` que ela aparece disponível antes de tocar em qualquer coisa.

A partir daí, todo o processo da Seção 3 abaixo roda **primeiro na conta de teste**, sem limite de autonomia (não tem dinheiro real em jogo).

---

## 3. Processo replicável (idêntico teste ↔ produção)

O processo é o mesmo nas duas contas — só muda o `account_id` de destino. Nada aqui é específico de teste ou de produção.

1. **Criar campanha** — nome `[LOJA]-[OBJETIVO]-[PERIODO]` (Seção 2 do doc base), objetivo, orçamento diário/mensal definido, status sempre `paused` na criação.
2. **Criar conjuntos** — um por `[HORARIO]-[FAIXA-ETARIA]`, segmentação (geo + idade) definida, status `paused`.
3. **Subir anúncios** — um por `[MODELO-MOTO]-[VARIANTE]-[DATA-SUBIDA]`, usando a arte que o time de design entrega a partir do blueprint. **Só entra anúncio com preço se a Etapa 0 (estoque + financeira) estiver confirmada** — isso vale igual em teste e produção, é checklist de conteúdo, não de ambiente.
4. **Ativar** — sair de `paused` pra `active` só depois de eu confirmar com você o orçamento final (ver Seção 5).
5. **Monitorar** — cadência da Seção 4 abaixo.
6. **Ciclo de otimização** — comparar variantes, pausar pior, trocar 1 criativo por vez a cada 2-3 semanas (regra já existente no doc base, Seção 4).

Quando o processo estiver validado na conta de teste (todas as 6 etapas rodando sem erro, resultado condizente com o esperado), replico exatamente igual na conta de produção.

---

## 4. Cadência de monitoramento (automatizável)

| Frequência | O que eu checo/faço sozinho |
|---|---|
| Diária | CPL/CPC por conjunto; tempo de resposta no WhatsApp (se houver dado); alerta se algum conjunto passar o teto de gasto diário |
| Semanal | Comparar CTR/CPC variante A vs B por faixa etária; pausar a variante pior segundo a regra da Seção 5 |
| A cada 2-3 semanas | Sinalizar qual criativo trocar (nunca os dois de uma faixa ao mesmo tempo) — troca em si depende da arte nova estar pronta |
| Mensal | Atualizar Seção 2 do plano geral (CPC, vendas fechadas, custo por venda) e comparar com histórico |

---

## 5. Regras de decisão automatizada (guardrails de orçamento)

Isso é o que define até onde a automação age sozinha **na produção**. Na conta de teste não há limite, porque não há gasto real.

- **Pausar automaticamente**, sem pedir confirmação: qualquer anúncio/conjunto com CPL acima de um limiar definido por você, ou CTR consistentemente pior que o par testado na mesma semana. Pausar nunca gera risco financeiro novo, então não precisa de aprovação.
- **Redistribuir orçamento entre conjuntos já ativos**, sem pedir confirmação, **desde que o total da campanha não mude** — só realocação interna.
- **Aumentar orçamento total da campanha**: preciso da sua confirmação antes de executar, mesmo que a tarefa agendada identifique que vale a pena escalar. Motivo: é dinheiro novo saindo, então é decisão de negócio, não só de mídia.
- **Teto de gasto mensal**: nunca ultrapasso o valor que você definir (ex: os R$4.400/mês já mencionados) sem sua aprovação explícita, mesmo que a performance justifique escalar.
- **Ativar campanha nova pausada → ativa**: sempre com sua confirmação na primeira vez que uma estrutura nova entra no ar. Depois de ativa, o dia a dia (pausar/realocar dentro do teto) já roda sozinho.

Essas regras ficam registradas aqui e você pode ajustar qualquer limiar a qualquer momento — é só pedir.

---

## 6. Automação agendada — o que fica pra depois da validação

Depois que a Seção 3 rodar sem erro na conta de teste, crio uma tarefa agendada (diária, seguindo a Seção 4) que:

1. Puxa CPL/CTR/CPC do dia/semana via Windsor.ai
2. Aplica as regras da Seção 5 (pausa automática, realocação dentro do teto)
3. Me avisa (resumo) sobre qualquer coisa que precise da sua aprovação (aumento de orçamento, ativação de estrutura nova, anúncio novo aguardando Etapa 0)
4. Atualiza o plano geral mensalmente

**Não crio essa tarefa agendada ainda** — só depois que a conta de teste confirmar que o processo end-to-end funciona como esperado (Etapa 2 do rollout abaixo).

---

## 7. Rollout — ordem de execução

1. Você cria a conta de teste (Seção 2) e me dá acesso
2. Eu conecto via Windsor.ai e valido a conexão
3. Rodamos a Seção 3 inteira na conta de teste (campanha → conjunto → anúncio fake → pausa/ativação simulada)
4. Você revisa o resultado e ajusta os guardrails da Seção 5 se quiser
5. Replico a mesma estrutura na conta de produção (`ABC-WhatsApp-Jul26`, ver roadmap), sempre pausada até sua confirmação final
6. Ativo a tarefa agendada (Seção 6) rodando sobre a conta de produção, dentro dos limites definidos

Estamos no passo 1 agora — falta você criar a conta de teste pra eu seguir.
