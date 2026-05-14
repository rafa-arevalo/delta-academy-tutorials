---
name: plano-30-60-90-lumina
description: Gera um plano de integração personalizado para os primeiros 90 dias de um novo colaborador da Lumina, dividido em marcos de 30, 60 e 90 dias, com objetivos semanais, responsabilidades do gestor e métricas de acompanhamento. Use sempre que o usuário enviar dados de um novo colaborador (nome e cargo) e pedir o plano 30/60/90, plano de integração, plano de onboarding, plano dos primeiros 90 dias ou similar.
---

# Skill: Plano 30/60/90 — Lumina

Esta Skill gera o plano de integração personalizado dos primeiros 90 dias de um novo colaborador da Lumina, com base no plano de cargos, política de admissão e manual cultural carregados no Project.

## Quando Usar

Use esta Skill sempre que o usuário fornecer dados de um novo colaborador (nome + cargo + gestor + data de início, no mínimo) e pedir um plano de integração, plano 30/60/90, plano dos primeiros 90 dias, plano de onboarding personalizado ou similar.

## Input Esperado

O usuário deve fornecer ao menos:
- **Nome do colaborador**
- **Cargo** (deve corresponder a um cargo descrito no plano de cargos da Lumina)
- **Gestor direto**
- **Data de início**

Quando algum desses dados estiver faltando, peça ao usuário antes de gerar o plano.

## Estrutura do Output

Gere o plano como **um único artefato Markdown** (não como HTML), estruturado nas seguintes seções na ordem exata:

### 1. Cabeçalho
- Título: "Plano 30/60/90 — [Nome do Colaborador]"
- Subtítulo com: cargo, gestor direto, data de início e data prevista de produtividade plena (com base no plano de cargos).

### 2. Visão Geral
Parágrafo curto (3 a 5 linhas) descrevendo o objetivo dos 90 dias para este colaborador específico, considerando:
- A natureza do cargo (operacional, analítico, comercial, liderança).
- O tempo até produtividade plena esperado para o cargo (consultar plano de cargos).
- Os princípios da Lumina sobre onboarding (consultar política de admissão).

### 3. Mês 1 — Dias 1 a 30 (Imersão)
- **Objetivo do mês:** uma frase clara.
- **Marcos semanais** (Semana 1, Semana 2, Semana 3, Semana 4), cada uma com:
  - 3 a 5 atividades específicas adaptadas ao cargo.
  - Responsabilidades do gestor direto na semana.
  - O que o buddy deve fazer.
- **Indicadores ao final do Mês 1:**
  - eNPS Day 7 e Day 30.
  - Conclusão de treinamentos operacionais.
  - Primeira tarefa autônoma entregue (até Day 21).
  - Marco crítico do cargo (consultar plano de cargos).

### 4. Mês 2 — Dias 31 a 60 (Ativação)
- **Objetivo do mês:** uma frase clara.
- **Marcos semanais** (Semana 5 a Semana 8), cada uma com:
  - Atividades específicas crescentemente autônomas.
  - Responsabilidades do gestor.
- **Indicadores ao final do Mês 2:**
  - eNPS Day 60.
  - Produtividade parcial (50% do esperado para o cargo).
  - Conversa de "fit cultural" realizada.
  - Para cargos de 60 dias: produtividade plena atingida.

### 5. Mês 3 — Dias 61 a 90 (Autonomia)
- **Objetivo do mês:** uma frase clara.
- **Marcos semanais** (Semana 9 a Semana 13), cada uma com:
  - Atividades de execução autônoma.
  - Responsabilidades do gestor.
- **Indicadores ao final do Mês 3:**
  - eNPS Day 90.
  - Produtividade plena (para cargos de 90 dias).
  - Check-in dos 90 dias documentado.
  - Decisão de efetivação (se contrato de experiência).

### 6. Resumo dos Indicadores

Tabela com:
| Indicador | Meta | Status |
|---|---|---|
| eNPS Day 7 | ≥ +70 | A medir |
| eNPS Day 30 | ≥ +65 | A medir |
| eNPS Day 60 | ≥ +60 | A medir |
| eNPS Day 90 | ≥ +55 | A medir |
| Tempo até produtividade plena | [conforme cargo] | A medir |
| Marco crítico do cargo | [conforme cargo] | A medir |

### 7. Próximos Passos para o Gestor

Lista curta (3 a 5 itens) do que o gestor direto deve fazer **antes do Day 1** para receber bem este colaborador.

## Regras Importantes

1. **Personalize ao cargo.** Não use texto genérico — adapte cada marco semanal ao que esse cargo específico faz na Lumina.
2. **Use a linguagem Lumina.** "Time" em vez de "colaboradores" no dia a dia; "comunidade" em vez de "clientes" no dia a dia. Tom direto, acolhedor, wellness premium.
3. **Cite o plano de cargos** para definir o tempo de produtividade, o marco crítico e o buddy recomendado.
4. **Cite a política de admissão** para os indicadores e cadência de 1:1s.
5. **Cite o manual cultural** ao referenciar rituais (Segunda Lumina, almoço, Encontrão, etc.) que devem aparecer no plano.
6. **Não invente cargos ou áreas** que não estejam no plano de cargos. Se o cargo informado não estiver listado, peça ao usuário para esclarecer.
7. **Não gere HTML.** Apenas Markdown.
8. **Sem preâmbulos.** Entregue o plano direto, sem introdução conversacional do tipo "claro, aqui está o plano...".
