# Prompt de geração da Skill `analisar-dre-lumina`

> **Para que serve este arquivo:** este é o prompt que, quando enviado ao Claude, gera a Skill `analisar-dre-lumina` em formato `.zip` pronto para upload em `Customize > Skills`.
>
> **Por que você está recebendo:** durante a aula, você usa a Skill já pronta da Lumina. Mas para o **Desafio na sua empresa**, você precisa customizar este prompt para gerar uma Skill `analisar-dre-[sua-empresa]` específica para a realidade da sua operação.
>
> **Como usar:** copie o conteúdo do bloco abaixo, cole no chat do Claude, e o Claude vai entregar a Skill como artefato `.zip` para download.

---

```
Vou criar uma Skill no Claude que produz análise narrativa executiva profunda do DRE da Lumina, no padrão Executive Summary lido por CFO/liderança em 30 segundos. A Skill lê o DRE gerado pela Skill gerar-dre-lumina na mesma conversa e enriquece com root causes, materialidade e olhar prospectivo.

CONTEXTO DA EMPRESA:
- Nome: Lumina
- Setor: wellness — empresa em grande crescimento
- Produtos: 3 SKUs de balas de goma funcionais (pré-treino, creatina, whey protein)
- Canais: e-commerce (canal principal) + 2 lojas físicas próprias (São Paulo e Rio de Janeiro)
- Sazonalidade do setor: primavera/verão são mais fortes, novembro tem Black Friday

OBJETIVO DA SKILL:
- Ler o DRE gerado pela Skill gerar-dre-lumina (presente na mesma conversa)
- Aplicar threshold de materialidade para focar análise no que importa
- Produzir análise narrativa em 5 blocos estruturados (formato Executive Summary)
- Identificar root causes nos eventos relevantes do mês

ARQUIVOS DE CONTEXTO QUE A SKILL DEVE CONSULTAR (carregados no Project Financeiro Lumina):
- historico-financeiro-lumina.xlsx (Aba 2 com KPIs Operacionais e Aba 3 com Eventos Relevantes do mês)
- dre-lumina-setembro-2025.md (DRE narrativo de referência com eventos e drivers)
- identidade-visual-lumina.md (para alinhar tom da análise à energia wellness premium)

THRESHOLD DE MATERIALIDADE (regra crítica):
- Comentar APENAS variações com valor absoluto >= R$ 100.000 OU variação relativa >= 5%
- Variações em margens (Bruta/Operacional/Líquida) sempre comentadas se >= 1 ponto percentual
- Variações abaixo desse threshold são ignoradas (ruído operacional)

ESTRUTURA OBRIGATÓRIA DOS 5 BLOCOS DA ANÁLISE:

BLOCO 1 — RESUMO EXECUTIVO (15 segundos de leitura)
- Parágrafo único, denso, 3-4 frases
- Como foi o mês em uma palavra (forte/fraco/em linha/transição)
- Movimento mais relevante (1 frase)
- Resultado líquido vs mês anterior
- Sinal de alerta ou destaque positivo

BLOCO 2 — ANÁLISE DAS 3 MARGENS (com root causes)
Para cada margem (Bruta, Operacional, Líquida):
- Valor atual vs anterior em pontos percentuais
- 1-2 frases explicando o movimento e identificando root cause
- Consultar eventos relevantes do mês para identificar drivers

BLOCO 3 — MOVIMENTOS MATERIAIS (com threshold)
Lista numerada com 3-6 movimentos materiais:
- Linha do DRE | variação em R$ e % | root cause
- Cada item com 2-3 frases
- Se mais de 8 movimentos identificados, threshold pode estar muito frouxo

BLOCO 4 — OLHAR PROSPECTIVO
3-4 parágrafos curtos identificando:
- Ventos favoráveis para o próximo mês
- Ventos contrários (riscos)
- Decisões pendentes em curso

BLOCO 5 — PONTOS DE ATENÇÃO PARA O CFO
Lista numerada de 3-5 pontos:
- Cada item com 1 frase + indicação de prioridade (Alta/Média/Baixa)
- Pontos = decisões pendentes, NÃO comemorações

OUTPUT ESPERADO DA SKILL:
1. Resumo no chat: APENAS o Bloco 1 (Resumo Executivo) + linha indicando que análise completa está no artefato
2. Artefato Markdown (.md): os 5 blocos completos
   - Cabeçalho com data, threshold de materialidade aplicado
   - Nome do arquivo: analise-dre-lumina-[mes]-[ano].md

TONS E ESTILO DA SKILL:
- Português brasileiro de finanças sênior — direto, denso, sem floreios
- Tom de CFO conversando com seu controller
- Verbos no presente histórico ("a margem comprime", "o canal acelera")
- Citação de números sempre com magnitude (+R$ 95K, R$ 1,1M)
- SEM qualificadores fracos (ligeiramente, talvez, parece que)
- SEM emojis na análise (exceção: ícone de prioridade nos Pontos de Atenção, se ajudar)
- Tom alinhado à energia wellness premium da Lumina (sofisticado, contido)

VALIDAÇÕES OBRIGATÓRIAS:
- DRE presente na conversa (gerado pela Skill gerar-dre-lumina)
- Histórico Lumina disponível para identificar root causes
- Threshold calibrado (3 a 8 movimentos materiais; fora dessa faixa, sinalizar)

Por favor, gere a Skill como um arquivo .zip pronto para upload em Customize > Skills no Claude. A Skill deve ter:
- Pasta "analisar-dre-lumina/" com arquivo SKILL.md dentro
- SKILL.md com frontmatter YAML (name + description) e instruções estruturadas em PASSOS (PASSO 0: carregar contexto; PASSO 1: identificar DRE alvo; PASSO 2: aplicar threshold de materialidade; PASSO 3: gerar análise nos 5 blocos; PASSO 4: devolver output em 2 formatos)
- Descrição (description do frontmatter) com triggers claros: "use sempre que o usuário tiver gerado um DRE com a Skill gerar-dre-lumina e pedir análise, comentário, narrativa, comparação detalhada com mês anterior, variance analysis, ou material para apresentar à liderança"
- Tratamento de erros para casos comuns (sem DRE na conversa, histórico faltando, threshold descalibrado)
- Seção "Não faça" listando comportamentos a evitar (não usar Bloco 5 para parabenizar, não inventar root causes, não comentar abaixo do threshold)

Entregue como ARTEFATO .zip para download.
```

---

## Como customizar para a sua empresa

Quando você for fazer o **Desafio na sua empresa** (ao final da AP03), pegue este prompt e adapte **cada uma das seções**:

| Seção | O que trocar |
|---|---|
| **CONTEXTO DA EMPRESA** | Setor, produtos, canais, sazonalidade da sua empresa |
| **ARQUIVOS DE CONTEXTO** | Nomes dos seus arquivos (`historico-financeiro-[empresa].xlsx`, `dre-[empresa]-[mes-anterior].md`, `identidade-visual-[empresa].md`) |
| **THRESHOLD DE MATERIALIDADE** | Calibre R$ e % de acordo com o porte da sua empresa (uma empresa menor pode usar R$ 20K e 3%; uma maior pode usar R$ 500K e 5%) |
| **OS 5 BLOCOS** | Mantenha a estrutura, mas ajuste o tipo de análise se relevante (ex: empresa B2B pode ter "Análise de pipeline de vendas" no Bloco 4) |
| **TONS E ESTILO** | Tom alinhado à identidade da sua marca |

**Resultado:** uma Skill `analisar-dre-[empresa]` que produz análise narrativa executiva específica para a realidade da sua empresa.

---

## Importante — uso encadeado com a Skill de geração

Esta Skill **só funciona se acionada APÓS** a Skill `gerar-dre-[empresa]` na mesma conversa. Esse design é proposital — é o **encadeamento de Skills**:

```
[Anexo: planilha estruturada] → Skill gerar-dre → DRE em tela → Skill analisar-dre → Análise narrativa
```

Por que separar geração e análise em 2 Skills:

- **Geração é técnica** (somar e estruturar). Análise é interpretativa (narrar e recomendar).
- **Skills monolíticas erram mais.** Misturar os dois passos compromete o rigor estrutural do DRE e a profundidade da análise.
- **Você pode usar uma sem a outra.** Em fechamentos rápidos, talvez você só queira o DRE estruturado. Em apresentações para o conselho, vai querer também a análise.

Esse encadeamento é a base para a **AP04**, onde a Skill `gerar-painel-lumina` vai ler tanto o DRE quanto a análise narrativa para produzir o painel HTML executivo final.
