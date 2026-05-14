---
name: kit-boas-vindas-lumina
description: Gera o conteúdo do Kit de Boas-Vindas de um novo colaborador da Lumina, com 3 partes — (1) carta de boas-vindas personalizada, (2) checklist do Day 1 e (3) briefing do gestor — em formato Markdown estruturado pronto para ser consolidado posteriormente no Manual do Colaborador HTML. Use sempre que o usuário pedir o kit de boas-vindas, kit de admissão, carta de boas-vindas, checklist Day 1 ou briefing do gestor.
---

# Skill: Kit de Boas-Vindas — Lumina

Esta Skill gera os três artefatos do Kit de Boas-Vindas (carta + checklist Day 1 + briefing do gestor) que serão consolidados, junto com o Manual do Colaborador, em um único artefato HTML pela Skill `manual-completo-lumina`.

## Quando Usar

Use esta Skill sempre que o usuário fornecer dados de um novo colaborador (nome + cargo + gestor + data de início) e pedir o kit de boas-vindas, carta de boas-vindas, checklist Day 1, briefing do gestor ou variações dessas expressões.

## Input Esperado

O usuário deve fornecer ao menos:
- **Nome do colaborador**
- **Cargo** (deve corresponder a um cargo do plano de cargos da Lumina)
- **Gestor direto**
- **Data de início**

## Estrutura do Output

Gere **três blocos Markdown claramente separados** na mesma resposta, na seguinte ordem:

---

### BLOCO 1 — Carta de Boas-Vindas

- **Destinatário:** o próprio colaborador.
- **Tom:** acolhedor, direto, sem formalidade exagerada. Linguagem Lumina ("time", "comunidade", energia wellness premium).
- **Extensão:** máximo 250 palavras.
- **Estrutura:**
  1. Saudação personalizada com o nome.
  2. Mensagem de boas-vindas conectando o cargo dele à missão da Lumina.
  3. Antecipação do que vai acontecer nos primeiros dias (Day 1, primeira semana).
  4. Quem é o buddy designado e o gestor direto.
  5. Convite para chegar com curiosidade — a Lumina aprende com quem chega.
  6. Assinatura: "Time Lumina".

### BLOCO 2 — Checklist Day 1

- **Destinatário:** o novo colaborador, mas também usado pelo RH e pelo buddy para conduzir o dia.
- **Estrutura:** tabela Markdown com colunas: **Hora**, **Atividade**, **Responsável**, **Status**.
- **Conteúdo:** itinerário completo do Day 1 do colaborador, adaptado ao cargo:
  - Para cargos de loja: chegada → uniforme → tour da loja → apresentação ao time → almoço com o gestor → degustação de produto → primeiros treinamentos → fim do dia leve.
  - Para cargos online/corporativos: recepção pelo RH → setup de equipamento → apresentação à empresa → almoço com o time → primeiras reuniões 1:1 → fim do dia leve.
- **Sempre incluir:** entrega de boas-vindas (kit físico se houver), apresentação ao buddy, primeira 1:1 com o gestor mesmo que curta.

### BLOCO 3 — Briefing do Gestor

- **Destinatário:** o gestor direto do novo colaborador.
- **Tom:** documento operacional, claro, sem rodeios.
- **Estrutura:**
  1. **Perfil do novo colaborador:** nome, cargo, breve enquadramento (cargo júnior/sênior, expectativa de tempo até produtividade plena conforme plano de cargos).
  2. **Recomendações de abordagem:** 3 a 4 dicas práticas para o gestor receber bem este colaborador específico considerando o cargo.
  3. **Plano da primeira semana do gestor:** o que o gestor precisa fazer cada dia da Semana 1 (Day 1, 2, 3, 4, 5) — pelo menos uma ação por dia.
  4. **Pontos de atenção:** o que costuma dar errado para esse cargo nos primeiros 30 dias e como prevenir.
  5. **Marcos a acompanhar:** marco crítico do cargo (consultar plano de cargos) e cadência de 1:1s (semanal nos primeiros 30 dias).

---

## Regras Importantes

1. **Os três blocos são SEPARADOS e CLARAMENTE IDENTIFICADOS** na resposta, com cabeçalhos `## BLOCO 1`, `## BLOCO 2`, `## BLOCO 3`.
2. **Use a linguagem Lumina** em todos os blocos: "time", "comunidade", tom direto e acolhedor.
3. **Personalize ao cargo** — não use textos genéricos. Cada cargo tem um Day 1 diferente, pontos de atenção diferentes, marco crítico diferente.
4. **Cite os arquivos do Project** quando relevante: plano de cargos (para tempo de produtividade e marcos), política de admissão (para cadência), manual cultural (para rituais e tom).
5. **Não gere HTML.** Apenas Markdown estruturado.
6. **Sem preâmbulos.** Entregue os 3 blocos diretamente, sem introdução conversacional.
7. **Não invente cargos ou processos** que não estejam nos arquivos do Project.
