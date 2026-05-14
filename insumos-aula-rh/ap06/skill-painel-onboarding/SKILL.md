---
name: painel-onboarding-lumina
description: Gera um painel HTML autocontido com o status de toda a coorte de novos colaboradores em onboarding na Lumina, com semáforo de risco (verde, amarelo, vermelho), marcos atingidos por colaborador, perguntas mais frequentes do AskRH na semana e alertas para o RH agir. Use sempre que o usuário pedir o painel de onboarding, painel de acompanhamento, dashboard da coorte, status da coorte ou variações.
---

# Skill: Painel de Onboarding — Lumina

Esta Skill gera o painel HTML único de acompanhamento da coorte de onboarding da Lumina, com semáforo de risco por colaborador e alertas para o RH.

## Quando Usar

Use esta Skill sempre que o usuário fornecer (ou referenciar) os dados da coorte de onboarding em formato Markdown ou colado no chat e pedir o painel, dashboard, status ou acompanhamento da coorte.

## Input Esperado

Os dados da coorte estão no arquivo `dados-coorte-onboarding.md` carregado no Project (ou colados pelo usuário). Cada colaborador tem:
- Nome
- Cargo
- Gestor
- Data de início
- Dia de onboarding atual (Day 1, Day 7, Day 30, Day 60, Day 90)
- eNPS mais recente
- Marcos atingidos (lista)
- Marcos pendentes (lista)
- Risco percebido (definido conforme regras abaixo)

## Regras de Semáforo

| Cor | Condição |
|---|---|
| 🟢 Verde | Todos os marcos do período atingidos no prazo + eNPS ≥ meta + sem alertas |
| 🟡 Amarelo | Pelo menos 1 marco atrasado ou eNPS abaixo da meta por até 10 pontos |
| 🔴 Vermelho | 2 ou mais marcos atrasados, eNPS abaixo da meta por mais de 10 pontos, ou ausência prolongada |

Metas de eNPS por marco:
- Day 7: ≥ +70
- Day 30: ≥ +65
- Day 60: ≥ +60
- Day 90: ≥ +55

## Estrutura do Output

Gere **um único artefato HTML autocontido** com a seguinte estrutura:

### Cabeçalho
- Logo Lumina (SVG inline) + título "Painel de Onboarding — [Mês de referência]".
- Subtítulo com a data de geração e número total de colaboradores em onboarding.

### Bloco 1 — KPIs Executivos
Cards com:
- **Total em onboarding** (número de colaboradores ativos no funil)
- **Status saudável** (% em verde)
- **Em atenção** (% em amarelo)
- **Em risco** (% em vermelho)
- **eNPS médio da coorte** (média ponderada)
- **Turnover early-stage (Day 1–90) do mês** (%, se houver desligamentos)

### Bloco 2 — Tabela da Coorte
Tabela com as colunas:
- Colaborador
- Cargo
- Gestor
- Day atual
- eNPS
- Marcos atingidos (resumo: X de Y)
- Status (badge colorido com 🟢 🟡 🔴)
- Próximo marco

Ordene a tabela por **risco decrescente** (vermelhos primeiro, depois amarelos, depois verdes).

### Bloco 3 — Alertas e Recomendações para o RH
Lista priorizada com ações concretas:
- Para cada colaborador em vermelho: ação imediata recomendada.
- Para cada colaborador em amarelo: ação preventiva recomendada.
- Padrões detectados na coorte (ex: "3 dos 4 atendentes de loja SP estão com marco atrasado de degustação de produto — verificar com Coordenador da loja").

### Bloco 4 — Perguntas Mais Frequentes da Semana (AskRH)
Lista das 5 perguntas mais feitas ao AskRH na semana (se constarem nos dados de input), com:
- Tema
- Frequência
- Indicação se sugere ajuste em algum documento oficial (FAQ, política).

### Rodapé
- "Painel gerado pelo Project RH — Lumina"
- "Próxima atualização: [data]"
- Logo + branding

## Especificações Visuais

Aplique rigorosamente a identidade visual Lumina (consultar `identidade-visual-lumina.md`):

- **Background:** `#FBF9F5`.
- **Verde-musgo `#5C7A5A`:** títulos, status saudável.
- **Coral `#C97A5A`:** acentos, badges de Day atual.
- **Cinza-taupe `#8A857D`:** texto secundário.
- **Verde-claro `#D4DDC9`:** background de cards.
- **Âmbar `#D4A95C`:** status amarelo.
- **Vermelho `#B8533E`:** status vermelho.
- **Tipografia:** Fraunces (títulos) + Inter (corpo).
- **Linhas finas, muito espaço negativo, sem sombras dramáticas.**
- **Responsive:** funcional em mobile com tabela horizontal scrollável.

## Regras Importantes

1. **Um único arquivo HTML autocontido.** Tudo inline.
2. **Sem JavaScript pesado.** Pode usar JS leve para interatividade visual (filtros simples), mas não obrigatório.
3. **Personalize ao dado real do input.** Não invente colaboradores ou números.
4. **Cite as fontes** (plano de cargos para metas, política de admissão para marcos, FAQ para perguntas).
5. **Linguagem Lumina** em alertas e textos: tom direto e prático.
6. **Sem preâmbulos no chat.** Entregue o artefato HTML direto.
7. **Os dados da coorte** estão no arquivo `dados-coorte-onboarding.md` ou no input — sempre consulte antes de gerar.
