# Prompt de geração da Skill `gerar-dre-lumina`

> **Para que serve este arquivo:** este é o prompt que, quando enviado ao Claude, gera a Skill `gerar-dre-lumina` em formato `.zip` pronto para upload em `Customize > Skills`.
>
> **Por que você está recebendo:** durante a aula, você usa a Skill já pronta da Lumina. Mas para o **Desafio na sua empresa**, você precisa customizar este prompt para gerar uma Skill `gerar-dre-[sua-empresa]` específica para a realidade financeira da sua operação.
>
> **Como usar:** copie o conteúdo do bloco abaixo, cole no chat do Claude, e o Claude vai entregar a Skill como artefato `.zip` para download.

---

```
Vou criar uma Skill no Claude que gera o DRE consolidado mensal de uma empresa de wellness chamada Lumina, em formato tabular executivo padrão, com comparativo automático vs mês anterior.

CONTEXTO DA EMPRESA:
- Nome: Lumina
- Setor: wellness — empresa em grande crescimento
- Produtos: 3 SKUs de balas de goma funcionais (pré-treino, creatina, whey protein)
- Canais: e-commerce (canal principal) + 2 lojas físicas próprias (São Paulo e Rio de Janeiro)
- Centros de Custo: E-commerce, Loja SP, Loja RJ, Matriz/Geral

OBJETIVO DA SKILL:
- Receber uma planilha de lançamentos já classificados no plano de contas (output da Skill organizar-lancamentos-lumina)
- Gerar o DRE consolidado do mês em formato tabular padrão CPC
- Calcular as 3 margens (Bruta, Operacional, Líquida)
- Apresentar comparativo lado a lado vs mês anterior
- NÃO fazer análise narrativa (isso é trabalho da Skill seguinte no pipeline)

ARQUIVOS DE CONTEXTO QUE A SKILL DEVE CONSULTAR (carregados no Project Financeiro Lumina):
- plano-de-contas-lumina.md (estrutura oficial de contas)
- historico-financeiro-lumina.xlsx (Aba 1 com DRE de meses anteriores para comparativo)
- dre-lumina-setembro-2025.md (DRE de referência narrativo de setembro/2025, se carregado)

OUTPUT ESPERADO DA SKILL:
1. Resumo no chat (3 elementos):
   - DRE Consolidado em tabela markdown (linha do DRE | valor R$ | % sobre Receita Líquida)
   - Comparativo lado a lado vs mês anterior (mês anterior | mês atual | variação R$ | variação %)
   - Bloco com as 3 margens em destaque

2. Artefato Markdown (.md) seguindo o formato do dre-lumina-setembro-2025.md:
   - DRE consolidado em tabela
   - Composição da receita por canal (E-commerce, Loja SP, Loja RJ)
   - Composição da receita por produto (pré-treino, creatina, whey)
   - Comparativo com mês anterior
   - SEM análise narrativa nem eventos relevantes nem olhar prospectivo (isso é da Skill de análise)
   - Nome do arquivo: dre-lumina-[mes]-[ano].md

ESTRUTURA OBRIGATÓRIA DO DRE (em ordem padrão CPC):
- Receita Bruta (subdividida por canal e por produto)
- (-) Deduções (impostos sobre vendas, devoluções, descontos)
- = Receita Líquida
- (-) CPV (matéria-prima, embalagens, terceirização)
- = Lucro Bruto
- (-) Despesas Operacionais (folha, aluguel, marketing, logística, software, contabilidade)
- = Resultado Operacional (EBITDA)
- (-) Despesas Financeiras (antecipação, taxas, IOF)
- = Resultado Líquido

REGRAS DE CÁLCULO DAS MARGENS:
- Margem Bruta = Lucro Bruto / Receita Líquida
- Margem Operacional = Resultado Operacional / Receita Líquida
- Margem Líquida = Resultado Líquido / Receita Líquida

VALIDAÇÕES OBRIGATÓRIAS ANTES DE GERAR O DRE:
- Coluna "Conta do Plano" preenchida em todas as linhas da planilha
- Período coerente em um único mês (não múltiplos meses na mesma planilha)
- Confirmar com o usuário o total de lançamentos e somatório bruto antes de prosseguir

TONS E ESTILO DA SKILL:
- Português brasileiro executivo, direto, profissional
- Formato tabular sempre — DRE não usa prosa
- Valores em padrão brasileiro: R$ 1.010.500
- Percentuais com 1 casa decimal: 60,0%
- Pontos percentuais com sufixo p.p.: +2,4 p.p.
- Tom alinhado à energia wellness premium da Lumina (sofisticado, contido)
- NÃO fazer análise interpretativa nem comentários narrativos — só números

Por favor, gere a Skill como um arquivo .zip pronto para upload em Customize > Skills no Claude. A Skill deve ter:
- Pasta "gerar-dre-lumina/" com arquivo SKILL.md dentro
- SKILL.md com frontmatter YAML (name + description) e instruções estruturadas em PASSOS (PASSO 0: carregar contexto; PASSO 1: receber planilha; PASSO 2: agrupar lançamentos no DRE padrão CPC; PASSO 3: buscar mês anterior; PASSO 4: devolver output em 2 formatos)
- Descrição (description do frontmatter) com triggers claros: "use sempre que o usuário enviar uma planilha estruturada de lançamentos da Lumina e pedir para gerar o DRE, fechar o mês, consolidar resultados ou produzir demonstrativo financeiro"
- Tratamento de erros para casos comuns (plano de contas faltando, planilha sem coluna Conta do Plano, múltiplos meses)
- Seção "Não faça" listando comportamentos a evitar (não inventar linhas, não fazer análise, não pular linhas zeradas)

Entregue como ARTEFATO .zip para download.
```

---

## Como customizar para a sua empresa

Quando você for fazer o **Desafio na sua empresa** (ao final da AP03), pegue este prompt e adapte **cada uma das seções**:

| Seção | O que trocar |
|---|---|
| **CONTEXTO DA EMPRESA** | Setor, produtos, canais, centros de custo da sua empresa |
| **ARQUIVOS DE CONTEXTO** | Nomes dos seus arquivos (`plano-de-contas-[empresa].md`, `historico-financeiro-[empresa].xlsx`, `dre-[empresa]-[mes-anterior].md`) |
| **ESTRUTURA OBRIGATÓRIA DO DRE** | Linhas que fazem sentido para o seu negócio (ex: empresa de serviços tem CPV diferente de empresa de produtos) |
| **OUTPUT ESPERADO** | Composições por canal/produto que fazem sentido para a sua operação |
| **TONS E ESTILO** | Tom alinhado à identidade da sua marca |

**Resultado:** uma Skill `gerar-dre-[empresa]` específica para a realidade financeira da sua empresa, instalada permanentemente na sua conta Claude.

---

## Importante — uso encadeado com a Skill de análise

Esta Skill **NÃO faz análise narrativa**. Ela apenas estrutura o DRE em formato tabular. A análise narrativa é feita pela Skill `analisar-dre-[empresa]` (segundo prompt de referência da AP03), que deve ser acionada **na mesma conversa** depois de gerar o DRE.

Esse design — uma Skill por responsabilidade — é proposital:

- **Skills monolíticas erram mais.** Uma Skill que faz tudo (gerar + analisar) confunde os dois passos.
- **Outputs mais consistentes.** Cada Skill faz uma coisa bem feita.
- **Mais fáceis de manter.** Se a estrutura do DRE muda, você ajusta só a Skill de geração.
