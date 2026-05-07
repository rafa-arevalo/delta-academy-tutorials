# Prompt de geração da Skill `gerar-painel-lumina`

> **Para que serve este arquivo:** este é o prompt que, quando enviado ao Claude, gera a Skill `gerar-painel-lumina` em formato `.zip` pronto para upload em `Customize > Skills`.
>
> **Por que você está recebendo:** durante a aula, você usa a Skill já pronta da Lumina. Mas para o **Desafio na sua empresa**, você precisa customizar este prompt para gerar uma Skill `gerar-painel-[sua-empresa]` específica para a identidade visual e estrutura financeira da sua operação.
>
> **Como usar:** copie o conteúdo do bloco abaixo, cole no chat do Claude, e o Claude vai entregar a Skill como artefato `.zip` para download.

---

```
Vou criar uma Skill no Claude que produz o Painel Financeiro Mensal da Lumina como arquivo HTML autocontido. A Skill lê o DRE estruturado e a análise narrativa gerados pelas Skills anteriores na mesma conversa, e renderiza um painel visual único respeitando rigorosamente a identidade visual da marca.

CONTEXTO DA EMPRESA:
- Nome: Lumina
- Setor: wellness — empresa em grande crescimento
- Produtos: 3 SKUs de balas de goma funcionais (pré-treino, creatina, whey protein)
- Canais: e-commerce (canal principal) + 2 lojas físicas próprias (São Paulo e Rio de Janeiro)
- Identidade visual: minimalismo wellness premium — fresca, sofisticada, energética sem ser agressiva

OBJETIVO DA SKILL:
- Ler o DRE estruturado (output da Skill gerar-dre-lumina) e a análise narrativa (output da Skill analisar-dre-lumina) presentes na mesma conversa
- Produzir um arquivo HTML único e autocontido com o Painel Financeiro Mensal
- Respeitar rigorosamente a identidade visual da Lumina

ARQUIVOS DE CONTEXTO QUE A SKILL DEVE CONSULTAR (carregados no Project Financeiro Lumina):
- identidade-visual-lumina.md (paleta de cores, tipografia, princípios de design)
- historico-financeiro-lumina.xlsx (Aba 2: KPIs Operacionais; Aba 3: Eventos Relevantes)

ESTRUTURA OBRIGATÓRIA DO PAINEL EM 5 BLOCOS NA ORDEM FIXA:

BLOCO 1 — Cabeçalho institucional Lumina
- Logo SVG inline (círculo verde-musgo vazado + tipografia Fraunces "lumina" lowercase)
- Título: "Painel Financeiro Mensal"
- Subtítulo: nome do mês por extenso + ano
- Data de fechamento contábil
- Linha divisória sutil em verde-claro pálido

BLOCO 2 — Os 3 indicadores principais
Grid de 3 cards (1 coluna em mobile):
- Receita Líquida: valor monetário grande + % de variação vs mês anterior + seta colorida
- Resultado Operacional (EBITDA): mesmo padrão
- Resultado Líquido: mesmo padrão

BLOCO 3 — DRE consolidado
Tabela limpa formato CPC com colunas:
- Linha do DRE
- Valor (R$)
- % sobre Receita Líquida
- Variação vs mês anterior (R$ + %)
Princípios visuais: sem grade visível, só linhas horizontais finas entre seções, subtotais em destaque tipográfico, valores monetários alinhados à direita no padrão brasileiro.

BLOCO 4 — As 3 margens com semáforo visual
Grid de 3 cards com Margem Bruta, Operacional, Líquida.
Cada card com valor percentual grande, comparativo vs mês anterior em pontos percentuais, e semáforo discreto:
- Verde-musgo: melhorou (>= +0,5 p.p.)
- Dourado champagne: estável (entre -0,5 e +0,5 p.p.)
- Coral terroso: piorou (<= -0,5 p.p.)

BLOCO 5 — Análise narrativa
Renderizar os 5 blocos da análise narrativa (output da Skill analisar-dre-lumina) em tipografia editorial:
- Resumo Executivo (parágrafo único, em destaque)
- Análise das 3 Margens (3 blocos curtos com root causes)
- Movimentos Materiais (lista numerada)
- Olhar Prospectivo (3-4 parágrafos)
- Pontos de Atenção CFO (lista numerada com badges de prioridade)

ESPECIFICAÇÕES TÉCNICAS DO HTML:

Paleta de cores Lumina (CSS variables):
- --bg: #FBF9F5 (branco quente neutro)
- --musgo: #5C7A5A (verde-musgo, cor estrutural)
- --coral: #C97A5A (coral terroso, acentos)
- --taupe: #8A857D (cinza-taupe, texto secundário)
- --verde-claro: #D4DDC9 (verde-claro pálido, linhas/fundos sutis)
- --champagne: #D1AA53 (dourado champagne, semáforo amarelo)
- --texto: #2C2C2A (texto principal)

Tipografia:
- Títulos: Fraunces (Google Fonts CDN) — pesos 400/500/600
- Corpo: Inter (Google Fonts CDN) — pesos 400/500
- Tamanhos generosos no desktop, escalando para mobile via clamp() ou media queries

Layout:
- max-width central de ~840px no desktop
- Padding lateral generoso
- Seções separadas por espaço negativo (não bordas)
- Mobile-first: layout coluna única abaixo de 768px

Print-friendly:
- @media print com margens A4 ajustadas
- Cores preservadas (-webkit-print-color-adjust: exact)
- Quebras de página inteligentes (page-break-inside: avoid)

Sem dependências externas:
- Sem <link> para CSS externo (exceção: Google Fonts CDN)
- Sem JavaScript de servidor
- Sem imagens externas (logo é SVG inline)
- Tudo embarcado no único arquivo .html

PRINCÍPIOS DE DESIGN MINIMALISMO WELLNESS:
- Espaço negativo é protagonista — nunca preencher mais de 60% da página
- Dados acima de ornamentos — números e gráficos são o foco
- Linhas finas, nunca grossas — 1px para divisores
- Sem grade visível em tabelas — só linhas horizontais finas
- Hierarquia por espaçamento, não por cor
- Sem sombras pesadas, sem gradientes, sem ornamentos

OUTPUT ESPERADO DA SKILL:
1. Mensagem curta no chat anunciando que o painel foi gerado + dica de Ctrl+P para PDF
2. Artefato HTML único (.html) com os 5 blocos completos
   - Nome do arquivo: painel-lumina-[mes]-[ano].html

VALIDAÇÕES OBRIGATÓRIAS:
- Identidade visual carregada no Project (sem ela, painel sai genérico)
- DRE presente na conversa (gerado pela Skill gerar-dre-lumina)
- Análise narrativa presente na conversa (gerada pela Skill analisar-dre-lumina)
- DRE e análise do mesmo mês

Por favor, gere a Skill como um arquivo .zip pronto para upload em Customize > Skills no Claude. A Skill deve ter:
- Pasta "gerar-painel-lumina/" com arquivo SKILL.md dentro
- SKILL.md com frontmatter YAML (name + description) e instruções estruturadas em PASSOS (PASSO 0: carregar contexto; PASSO 1: identificar DRE e análise na conversa; PASSO 2: estruturar painel em 5 blocos; PASSO 3: renderizar como HTML autocontido; PASSO 4: devolver output)
- Descrição (description do frontmatter) com triggers claros: "use sempre que o usuário tiver gerado DRE + análise e pedir para criar o painel, gerar a peça visual, montar o relatório executivo, fechar o material do mês ou compilar o painel financeiro"
- Tratamento de erros para casos comuns (identidade visual faltando, DRE faltando, análise faltando, meses diferentes)
- Seção "Não faça" listando comportamentos a evitar (não inventar conteúdo, não usar JS externo, não usar cores fora da paleta, não usar grade visível, não preencher a página inteira)

Entregue como ARTEFATO .zip para download.
```

---

## Como customizar para a sua empresa

Quando você for fazer o **Desafio na sua empresa** (ao final da AP04), pegue este prompt e adapte **cada uma das seções**:

| Seção | O que trocar |
|---|---|
| **CONTEXTO DA EMPRESA** | Setor, produtos, canais, identidade da sua empresa |
| **ARQUIVOS DE CONTEXTO** | Nomes dos seus arquivos (`identidade-visual-[empresa].md`, `historico-financeiro-[empresa].xlsx`) |
| **ESPECIFICAÇÕES TÉCNICAS — Paleta de cores** | Substitua a paleta wellness Lumina pelas cores reais da sua marca (consulte seu manual de identidade visual) |
| **ESPECIFICAÇÕES TÉCNICAS — Tipografia** | Troque Fraunces + Inter pelas fontes oficiais da sua marca. Se não houver tipografia definida, use combinações neutras (Georgia + Inter, Playfair Display + Source Sans, Cormorant + Lato) |
| **PRINCÍPIOS DE DESIGN** | Adapte para o estilo visual da sua marca — minimalismo wellness funciona para a Lumina, mas a sua marca pode ter estilo editorial corporativo, tech minimalista, premium dourado, etc. |
| **OS 5 BLOCOS** | Mantenha a estrutura, mas ajuste informações se relevante (ex: indicadores principais podem incluir métricas específicas do seu setor — para SaaS, MRR/ARR; para varejo, GMV; para agência, billing/utilização) |

**Resultado:** uma Skill `gerar-painel-[empresa]` que produz o painel HTML autocontido específico para a sua empresa, todo mês, com a identidade visual da sua marca.

---

## Importante — encadeamento completo do pipeline

Esta Skill é a **terceira etapa do encadeamento** que você construiu nas APs anteriores:

```
[Planilha bruta]
   ↓ Skill organizar-lancamentos
[Planilha classificada]
   ↓ Skill gerar-dre
[DRE estruturado]
   ↓ Skill analisar-dre
[Análise narrativa]
   ↓ Skill gerar-painel  ← ESTA SKILL
[Painel HTML autocontido]
```

A Skill `gerar-painel-[empresa]` **só funciona se acionada APÓS** as Skills de geração de DRE e análise narrativa, na mesma conversa. Esse design é proposital — é o **encadeamento completo de Skills**:

- **Cada Skill faz uma coisa só, bem feita.** A Skill de painel não soma nem analisa — apenas traduz o conteúdo já gerado em peça visual.
- **Você pode pular etapas.** Em fechamentos rápidos, talvez só queira o DRE e a análise sem painel. Em apresentações para o conselho, vai querer o painel completo.
- **Versionamento natural.** Cada mês gera um arquivo novo `painel-[empresa]-[mes]-[ano].html`. Histórico fica organizado naturalmente em qualquer pasta ou Drive compartilhado.

Esse encadeamento é a base para a **AP05**, onde a tarefa agendada vai disparar todas as 4 Skills automaticamente uma vez por mês — sem intervenção humana.
