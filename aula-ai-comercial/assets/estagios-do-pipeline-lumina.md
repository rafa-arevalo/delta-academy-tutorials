# Estágios do Pipeline — Lumina

> **Documento de referência:** manual de regras dos 5 estágios do pipeline comercial Lumina. Define como classificar cada oportunidade, qual é o SLA esperado por estágio, e quando uma oportunidade é considerada "travada" ou "esfriando".

---

## Os 5 estágios na ordem do funil

### Estágio 1 — Lead

**Definição:** contato inicial recebido. Ainda não validado se há fit comercial.

**Como uma oportunidade entra neste estágio:**
- Formulário de contato preenchido no site
- WhatsApp recebido com pergunta sobre revenda/parceria
- Indicação de cliente atual
- Contato em feira/evento (Bio Brazil, Naturaltech, FIBO)
- Resposta a campanha de prospecção ativa (cold outreach)

**Critérios para avançar para Qualificado:**
- Empresa identificada (CNPJ ou nome/segmento confirmado)
- Decisor identificado (nome + cargo)
- Interesse real validado (não apenas curiosidade)
- Fit mínimo com ICP (porte, segmento, localização)

**SLA saudável:** 0-3 dias entre entrada e qualificação
**SLA preocupante:** 4+ dias parado neste estágio sem ação

**Ações típicas neste estágio:**
- 1ª resposta com tempo de até 24h
- Mensagem de qualificação inicial (5-7 perguntas)
- Envio de catálogo/portfólio básico

---

### Estágio 2 — Qualificado

**Definição:** validamos que há fit (porte, segmento, interesse real, decisor identificado). Pronto para abordagem comercial estruturada.

**Como uma oportunidade entra neste estágio:**
- Resposta positiva aos critérios de qualificação
- SDR aprovou avanço (no caso B2B)
- Vendedor de loja física confirmou interesse após reunião inicial

**Critérios para avançar para Proposta:**
- Necessidade clara identificada (produto, volume, prazo)
- Orçamento confirmado (faixa de investimento)
- Timeline de decisão acordada
- Reunião de aprofundamento realizada

**SLA saudável:** 3-7 dias entre qualificação e envio de proposta
**SLA preocupante:** 8+ dias parado neste estágio sem ação

**Ações típicas neste estágio:**
- Reunião de descoberta (call ou presencial)
- Apresentação institucional
- Coleta de informações para cotação
- Envio de amostras (B2B)

---

### Estágio 3 — Proposta

**Definição:** proposta comercial enviada. Aguardando resposta do cliente.

**Como uma oportunidade entra neste estágio:**
- Proposta formal enviada por email/PDF
- Cotação personalizada com produtos, volumes, preços, condições, prazo
- Inclui SLAs de entrega e suporte

**Critérios para avançar para Negociação:**
- Cliente respondeu (positiva ou negativamente, mas com sinal)
- Solicitação de ajustes (preço, prazo, condições)
- Pedido de reunião para discussão de termos

**SLA saudável:** 7-14 dias entre envio e resposta
**SLA preocupante:** 15+ dias sem resposta — proposta provavelmente esquecida ou em comparação com concorrentes

**Ações típicas neste estágio:**
- Envio da proposta com follow-up agendado em 3 dias
- 1º follow-up em 3 dias (mensagem suave)
- 2º follow-up em 7 dias (mensagem objetiva)
- 3º follow-up em 14 dias (mensagem de fechamento ou pausa)

---

### Estágio 4 — Negociação

**Definição:** cliente respondeu, está em ajustes ativos (preço, condições, prazo, volumes).

**Como uma oportunidade entra neste estágio:**
- Cliente solicitou desconto ou condição especial
- Cliente solicitou mudança de produtos/volumes
- Cliente solicitou prazo de pagamento diferente
- Reunião de negociação agendada ou realizada

**Critérios para avançar para Fechado:**
- Acordo final em todas as variáveis (produtos, preço, prazo, condições)
- Contrato/pedido enviado e aceito
- Primeira ordem de compra emitida

**SLA saudável:** 5-10 dias entre início e fechamento
**SLA preocupante:** 11+ dias parado — sinal de que negociação travou ou cliente está em standby

**Ações típicas neste estágio:**
- Reuniões de negociação (1 a 3 rodadas típicas)
- Aprovação de descontos com Coordenação
- Ajuste de contrato
- Validação de condições com financeiro/operações

---

### Estágio 5 — Fechado

**Definição:** contrato assinado e/ou primeiro pedido emitido. Oportunidade convertida.

**Como uma oportunidade entra neste estágio:**
- Pedido formal recebido
- Pagamento da 1ª parcela confirmado (B2B)
- Contrato assinado (parcerias locais e B2B grandes)

**O que acontece depois:**
- Oportunidade sai do pipeline ativo
- Vai para gestão de relacionamento (recompra, upsell, cross-sell)
- Métrica é contabilizada nas metas mensais

---

## Sinais de que uma oportunidade está esfriando

A Skill `diagnosticar-pipeline-lumina` usa estes sinais para identificar leads que precisam de atenção urgente:

### Sinal 1 — Tempo parado acima do SLA preocupante
Qualquer oportunidade no estágio há mais dias que o "SLA preocupante" definido acima.

### Sinal 2 — Estágio incompatível com perfil
Lead de e-commerce que ainda está em "Qualificado" após 7 dias (deveria ter sido transacional). Sinal de erro de classificação ou churn silencioso.

### Sinal 3 — Sem registro de interação recente
Última interação registrada (coluna "Data da última interação" na planilha) há mais de 7 dias, em qualquer estágio.

### Sinal 4 — Concentração de valor
Oportunidade com valor estimado acima de R$ 20.000 (alto valor B2B) sem ação há mais de 5 dias.

### Sinal 5 — Repique de estágio
Oportunidade que voltou de "Negociação" para "Proposta" (regrediu no funil) — sinal de re-cotação ou perda de confiança.

---

## Padrões de tendência para análise comparativa

A Skill compara o snapshot atual com o snapshot da semana anterior para identificar:

### Tendência de aceleração
- Estágio com aumento acima de 20% no número de oportunidades
- Canal com aumento acima de 15% no valor total do pipeline

### Tendência de desaceleração
- Estágio com queda acima de 15% no número de oportunidades
- Canal com queda acima de 10% no valor total do pipeline

### Estágio travado
- Estágio onde mais de 30% das oportunidades estão acima do SLA preocupante
- Estágio sem nenhuma oportunidade avançada na última semana

---

## Regras de exceção

**E-commerce e varejo loja física não usam estes 5 estágios** — são transações imediatas. As Skills devem ignorar oportunidades classificadas como "E-commerce" ou "Varejo" (sem identificação de parceria local).

**Oportunidades canceladas/perdidas** devem ser registradas em uma aba separada da planilha (não devem aparecer no pipeline ativo, mas servem como histórico para análise de root cause de perdas).

---

*Manual mantido pela Coordenação Comercial Lumina · Revisado em cada virada de trimestre.*
