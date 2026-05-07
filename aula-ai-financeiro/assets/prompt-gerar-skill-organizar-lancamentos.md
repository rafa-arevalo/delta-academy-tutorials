# Prompt de geração da Skill `organizar-lancamentos-lumina`

> **Para que serve este arquivo:** este é o prompt que, quando enviado ao Claude, gera a Skill `organizar-lancamentos-lumina` em formato `.zip` pronto para upload em `Customize > Skills`.
>
> **Por que você está recebendo:** durante a aula, você vai usar a Skill já pronta (baixada como `.zip`). Mas para o **Desafio na sua empresa**, você vai precisar customizar este prompt — trocando referências da Lumina pelo contexto real da sua empresa — e gerar uma Skill nova, específica para a sua operação.
>
> **Como usar:** copie o conteúdo do bloco abaixo, cole no chat do Claude, e o Claude vai entregar a Skill como artefato `.zip` para download.

---

```
Vou criar uma Skill no Claude que organiza lançamentos contábeis brutos de uma empresa de wellness chamada Lumina, classificando cada lançamento dentro do plano de contas oficial da empresa.

CONTEXTO DA EMPRESA:
- Nome: Lumina
- Setor: wellness — empresa em grande crescimento
- Produtos: 3 SKUs de balas de goma funcionais (pré-treino, creatina, whey protein)
- Canais: e-commerce (canal principal) + 2 lojas físicas próprias (São Paulo e Rio de Janeiro)
- Público: pessoas que praticam exercícios e buscam suplementação prática

OBJETIVO DA SKILL:
- Receber uma planilha bruta de lançamentos financeiros (vendas online, vendas físicas, custos, despesas)
- Devolver uma planilha estruturada com cada lançamento classificado dentro do plano de contas
- Aplicar regras de política de classificação para resolver ambiguidades

ARQUIVOS DE CONTEXTO QUE A SKILL DEVE CONSULTAR (carregados no Project Financeiro Lumina):
- plano-de-contas-lumina.md (lista oficial de contas com hierarquia)
- politica-classificacao-lancamentos.md (regras para resolver ambiguidades)

OUTPUT ESPERADO DA SKILL:
1. Resumo no chat (tabela markdown) com:
   - Total de lançamentos processados
   - Distribuição por categoria (Receitas, Deduções, CPV, Despesas Op, Despesas Fin)
   - Distribuição por centro de custo (E-commerce, Loja SP, Loja RJ, Matriz/Geral)
   - Observações sobre classificações ambíguas

2. Artefato Excel (.xlsx) com:
   - Todas as colunas originais preservadas
   - Coluna "Centro de Custo" preenchida
   - Coluna "Conta do Plano" preenchida
   - Nova coluna "Justificativa" (para classificações ambíguas)
   - Aba 2: Resumo por Categoria
   - Aba 3: Resumo por Centro de Custo
   - Formatação visual minimalismo wellness premium da Lumina (verde-musgo #5C7A5A no cabeçalho, fonte Inter, linhas alternadas em branco quente #FBF9F5)

REGRAS DE CLASSIFICAÇÃO QUE A SKILL DEVE APLICAR:
- Não inventar categorias — usar estritamente o plano de contas carregado
- Frete de pedido online → Despesa Operacional · Logística · Fulfillment
- Frete de transferência entre lojas → CPV
- Influenciador via permuta → Despesa Op · Marketing (com observação se sem nota fiscal)
- Cupom promocional → Dedução · Descontos Comerciais (não é despesa de marketing)
- Devolução → Dedução · Devoluções
- Despesas que servem múltiplos canais → aplicar regra de rateio da política

TONS E ESTILO DA SKILL:
- Português brasileiro executivo, direto, profissional
- Tom alinhado com a energia wellness premium da Lumina
- Sem floreios — operação técnica
- Justificativas curtas (1-2 linhas) para classificações ambíguas

Por favor, gere a Skill como um arquivo .zip pronto para upload em Customize > Skills no Claude. A Skill deve ter:
- Pasta "organizar-lancamentos-lumina/" com arquivo SKILL.md dentro
- SKILL.md com frontmatter YAML (name + description) e instruções estruturadas em PASSOS (PASSO 0: carregar arquivos de contexto; PASSO 1: receber planilha; PASSO 2: classificar; PASSO 3: devolver output em 2 formatos)
- Descrição (description do frontmatter) com triggers claros: "use sempre que o usuário enviar uma planilha de lançamentos da Lumina e pedir para organizar/classificar/categorizar/estruturar"
- Tratamento de erros para casos comuns (arquivos faltando, planilha mal formatada, descrições vagas)
- Seção "Não faça" listando comportamentos a evitar

Entregue como ARTEFATO .zip para download.
```

---

## Como customizar para a sua empresa

Quando você for fazer o **Desafio na sua empresa** (ao final da AP02), você vai pegar este prompt e adaptar **cada uma das seções**:

| Seção | O que trocar |
|---|---|
| **CONTEXTO DA EMPRESA** | Setor, produtos, canais, público da sua empresa |
| **ARQUIVOS DE CONTEXTO** | Nomes dos seus arquivos `plano-de-contas-[empresa].md` e `politica-classificacao-[empresa].md` |
| **OUTPUT ESPERADO** | Centros de custo da sua operação (não E-commerce/SP/RJ) |
| **REGRAS DE CLASSIFICAÇÃO** | Regras que fazem sentido para o seu setor |
| **TONS E ESTILO** | Tom alinhado à identidade da sua marca |

**Resultado:** uma Skill `organizar-lancamentos-[empresa]` específica para a realidade da sua empresa, instalada permanentemente na sua conta Claude.
