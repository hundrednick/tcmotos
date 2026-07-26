# Pilares Oficiais do Google Ads e Sprint de Melhoria
**Loja:** TCmotos ABC · **Criado em:** 26/07/2026

Este documento resume o que a própria documentação oficial do Google Ads (Google Ads Help Center) recomenda como boas práticas, compara com o estado atual da conta TC Motos ABC, e propõe um sprint de 2 semanas com ações concretas. Isso serve de base para os próximos pacotes de atualização/ajuste — a ideia é repetir esse ciclo de sprints, sempre comparando com uma métrica de base (baseline), em vez de aplicar mudanças soltas.

## Fontes oficiais consultadas

- [Google Ads Best Practices](https://support.google.com/google-ads/answer/6154846) — hub oficial de boas práticas
- [Best practices for creating effective Search ads](https://support.google.com/google-ads/answer/6167122) — anúncios de pesquisa
- [Reaching the right customers on Search](https://support.google.com/google-ads/answer/6167110) — lances e segmentação com IA
- [Finding success with Smart Bidding](https://support.google.com/google-ads/answer/6167140) — lances automáticos
- [The ABCs of Account Structure](https://support.google.com/google-ads/answer/14752782) — estrutura de conta

## Pilares oficiais (resumo)

1. **Alinhar a estratégia de lances ao objetivo do negócio primeiro** — a escolha de segmentação/palavras-chave vem depois, não antes.
2. **Estrutura de conta simples e temática** — agrupar por tema, não por palavra-chave isolada; usar correspondência ampla como padrão quando já se usa lances automáticos (múltiplos tipos de correspondência do mesmo termo fragmentam o aprendizado do algoritmo).
3. **Anúncios responsivos de pesquisa (RSA) fortes** — pelo menos 2 RSAs com Índice de qualidade "Bom" ou "Excelente" por grupo de anúncios, 4+ imagens únicas, logo e nome da empresa. Quem sobe de "Ruim" para "Excelente" tem em média **15% mais cliques e conversões** (dado interno do Google).
4. **Rastreamento de conversão preciso** — pré-requisito para tudo o resto; sem isso a IA do Google não tem o que otimizar.
5. **Testar de forma incremental** — usar a aba Experimentos do Google Ads e avaliar pelo impacto incremental no grupo de anúncios/campanha, não só pela métrica isolada de um anúncio.

## Diagnóstico: onde a TC Motos ABC já está alinhada

| Prática oficial | Status na conta |
|---|---|
| Usar lances automáticos (Smart Bidding) | ✅ As 3 campanhas usam "Maximizar conversões" |
| Correspondência ampla como padrão | ✅ Maioria das 150 palavras-chave (75 manuais + 75 sugeridas pelo Google) está em Ampla |
| Rastreamento de conversão configurado | ✅ Configurado no site |
| Pontuação de otimização | ✅ 95% |

## Diagnóstico: onde está descolada (oportunidades do sprint)

| Prática oficial | Situação atual | Ação |
|---|---|---|
| RSA com qualidade "Bom"/"Excelente" | Abaixo de "Bom" nas 3 campanhas (recomendação já sinalizada no Google Ads) | Reescrever títulos/descrições na Semana 1 |
| AI Max for Search (correspondência ampla + expansão por IA) | Ainda não testado | Ativar em 1 campanha piloto na Semana 2 |
| Meta de CPA/ROAS | Não configurada | **Não ativar ainda** — volume de conversão (4/30 dias) está abaixo do necessário para o Smart Bidding otimizar com meta; ficar em "Maximizar conversões" simples é o que o próprio Google recomenda até acumular mais dado |
| Testes controlados (Experiments) | Não usado | Criar 1 experimento A/B na Semana 2 |

---

## Sprint 1 — próximas 2 semanas

### Semana 1: fundamentos (RSA e recursos)

- Reescrever os RSAs das 3 campanhas até atingir "Bom"/"Excelente": título com nome do modelo (alinhado à palavra-chave, ex. "CG 160 Usada Revisada") + benefício (ex. "Financiamento Facilitado"), seguindo a diretriz oficial de ligar título à palavra-chave.
- Adicionar CTA específico em vez de genérico (ex. "Fale agora no WhatsApp" em vez de "Saiba mais").
- Confirmar que as 3 campanhas têm 4+ imagens únicas, logo e nome da empresa aplicados (imagens já foram adicionadas numa rodada anterior — conferir se atingem o mínimo recomendado).

### Semana 2: expansão e teste controlado

- Ativar **AI Max for Search** numa campanha piloto (sugestão: Geo Sao Bernardo do Campo, que já tem a única conversão registrada) e comparar com as outras duas campanhas sem a mudança.
- Criar um **Experimento** (aba Experimentos do Google Ads) comparando o RSA antigo vs. o novo reescrito, em vez de simplesmente substituir — assim dá pra medir o efeito real.
- Revisar o relatório de estratégia de lances ao final da semana.

---

## Baseline (antes do sprint, últimos 30 dias — 26/jun a 25/jul/2026)

| Métrica | Valor |
|---|---|
| Custo total (3 campanhas de Busca) | R$ 198,03 |
| Cliques | 74 |
| Conversões | 1 |
| Custo/conversão médio da conta (4 campanhas, incl. legado) | R$ 79,13 |

## Meta de sucesso ao fim do sprint (14 dias)

- Ad Strength das 3 campanhas em "Bom" ou melhor.
- Nenhuma queda no volume de cliques em relação ao baseline.
- Registrar o novo custo/conversão e comparar com o baseline acima — só considerar "melhora" se a tendência se mantiver por mais de uma semana, não num pico isolado (ver metodologia de validação abaixo).

## Pendência para medir ROI de verdade

Custo por clique/conversão mostra eficiência do anúncio, mas não diz se o Google Ads está "se pagando". Para isso é preciso saber a margem/lucro médio por moto vendida — informação que ainda não temos aqui. Assim que esse número existir, dá pra calcular o ROAS mínimo necessário para o investimento em Ads se justificar.

## Metodologia de validação (para não confundir sorte com melhora real)

1. Definir "funcionou" como lead rastreável (WhatsApp) e, no fim da linha, venda — não like/visualização.
2. Cada campanha/conteúdo precisa ter como saber a origem do lead (link de WhatsApp diferente por campanha, ou perguntar "veio de onde?").
3. Comparar sempre com uma base antes de mudar (baseline acima).
4. Dado o volume baixo da conta, olhar tendência ao longo de várias semanas, não um pico isolado, antes de declarar uma mudança como "comprovada".

## Próximos sprints

Este é o Sprint 1. Ao final de cada sprint de 2 semanas, registrar aqui: o que foi feito, o resultado medido, e o que entra no próximo pacote de ajuste.

| Sprint | Período | Foco | Resultado |
|---|---|---|---|
| 1 | 26/07 a 09/08/2026 | RSA + AI Max + Experimento | (preencher ao final) |
| 2 | — | — | — |
