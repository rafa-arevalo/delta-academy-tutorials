# Insumos da Aula — IA no RH (Onboarding) · Lumina

Material completo das 6 APs da aula para teste no Claude do plano gratuito.

---

## Estrutura

```
insumos-aula-rh/
├── ap01/                    # Project RH Lumina
│   ├── nome-project-rh-lumina.txt              [Copiar]
│   ├── descricao-project-rh-lumina.txt         [Copiar]
│   ├── instrucoes-project-rh-lumina.md         [Download]
│   ├── plano-de-cargos-lumina.md               [Download]
│   ├── politica-de-admissao-lumina.md          [Download]
│   ├── manual-cultural-lumina.md               [Download]
│   └── identidade-visual-lumina.md             [Download]
│
├── ap02/                    # Skill Plano 30/60/90
│   ├── skill-plano-30-60-90.zip                [Download]
│   └── exemplo-input-ana-silva.txt             [Copiar]
│
├── ap03/                    # Skill Kit de Boas-Vindas (só instalação)
│   └── skill-kit-boas-vindas.zip               [Download]
│
├── ap04/                    # Skill Manual Completo (artefato consolidado)
│   ├── skill-manual-completo.zip               [Download]
│   └── exemplo-input-manual-ana-silva.txt      [Copiar]
│
├── ap05/                    # Project AskRH (separado)
│   ├── nome-project-askrh-lumina.txt           [Copiar]
│   ├── descricao-project-askrh-lumina.txt      [Copiar]
│   ├── instrucoes-project-askrh-lumina.md      [Download]
│   ├── faq-historico-lumina.md                 [Download]
│   ├── politica-de-beneficios-lumina.md        [Download]
│   ├── cct-lumina-resumida.md                  [Download]
│   └── lista-de-perguntas-teste.txt            [Copiar]
│
└── ap06/                    # Skill Painel de Onboarding + Cowork
    ├── skill-painel-onboarding.zip             [Download]
    ├── dados-coorte-onboarding.md              [Download]
    ├── exemplo-input-painel.txt                [Copiar]
    └── passo-a-passo-cowork.md                 [Download — material de leitura]
```

---

## Roteiro de Teste no Plano Gratuito

### AP01 — Project RH Lumina (0 mensagens)

1. Em `claude.ai`, criar novo Project.
2. Colar conteúdo de `nome-project-rh-lumina.txt` no campo Nome.
3. Colar conteúdo de `descricao-project-rh-lumina.txt` no campo Descrição.
4. Colar conteúdo de `instrucoes-project-rh-lumina.md` no campo Instruções (System Prompt).
5. Fazer upload dos 4 `.md` na seção Arquivos do Project:
   - `plano-de-cargos-lumina.md`
   - `politica-de-admissao-lumina.md`
   - `manual-cultural-lumina.md`
   - `identidade-visual-lumina.md`

### AP02 — Skill Plano 30/60/90 (1 mensagem)

1. Fazer upload de `skill-plano-30-60-90.zip` na seção Skills do Project.
2. Abrir nova conversa no Project.
3. Colar conteúdo de `exemplo-input-ana-silva.txt` e enviar.
4. Validar que o Claude retorna o plano 30/60/90 personalizado da Ana Silva, com marcos semanais, indicadores e responsabilidades do gestor.

### AP03 — Skill Kit de Boas-Vindas (0 mensagens)

1. Fazer upload de `skill-kit-boas-vindas.zip` na seção Skills do Project.
2. Não invocar a Skill. Apenas abrir o conteúdo da Skill instalada e ler o `SKILL.md` para entender a estrutura dos 3 blocos (carta + checklist + briefing).

### AP04 — Skill Manual Completo (1 mensagem)

1. Fazer upload de `skill-manual-completo.zip` na seção Skills do Project.
2. Abrir nova conversa no Project (ou continuar a existente).
3. Colar conteúdo de `exemplo-input-manual-ana-silva.txt` e enviar.
4. Validar que o Claude retorna **um único artefato HTML** com 4 seções claras: carta + checklist + briefing + manual do colaborador, aplicando a identidade visual Lumina.

### AP05 — Project AskRH (1 mensagem)

1. Criar **um novo Project** no Claude chamado "AskRH — Lumina" (separado do RH — Lumina).
2. Colar nome, descrição e instruções (`nome-`, `descricao-`, `instrucoes-`).
3. Fazer upload dos 3 arquivos `.md` na seção Arquivos:
   - `faq-historico-lumina.md`
   - `politica-de-beneficios-lumina.md`
   - `cct-lumina-resumida.md`
4. Abrir nova conversa no AskRH.
5. Colar conteúdo de `lista-de-perguntas-teste.txt` (5 perguntas em uma só mensagem) e enviar.
6. Validar que o AskRH responde as 5 perguntas com a estrutura padrão (resposta direta + detalhes + fonte) e escala apropriadamente a pergunta sensível (#5 — conflito com colega).

### AP06 — Skill Painel de Onboarding (1 mensagem)

1. **Voltar ao Project RH Lumina** (o primeiro, não o AskRH).
2. Fazer upload de `skill-painel-onboarding.zip` na seção Skills.
3. Fazer upload de `dados-coorte-onboarding.md` na seção Arquivos.
4. Abrir nova conversa no Project.
5. Colar conteúdo de `exemplo-input-painel.txt` e enviar.
6. Validar que o Claude retorna um painel HTML autocontido com KPIs, tabela ordenada por risco, alertas e FAQs da semana, aplicando a identidade visual Lumina.
7. Ler `passo-a-passo-cowork.md` como material complementar.

---

## Consumo Total

| AP | Mensagens |
|---|---|
| AP01 | 0 |
| AP02 | 1 |
| AP03 | 0 |
| AP04 | 1 |
| AP05 | 1 |
| AP06 | 1 |
| **Total** | **4 mensagens** |

---

## Personagem-Âncora

**Ana Silva**, Atendente de Loja Física — Loja SP, gestor Bruno Almeida, início próxima segunda-feira.
Aparece nas APs 02 e 04 para criar continuidade narrativa.

---

## Coorte da AP06

8 colaboradores fictícios em marcos diferentes do funil de onboarding:
- 4 em status 🟢 Verde (saudável)
- 2 em status 🟡 Amarelo (atenção)
- 2 em status 🔴 Vermelho (risco crítico)

Inclui dados de eNPS, marcos atingidos/pendentes e perguntas mais frequentes do AskRH na semana.

---

## Pontos para Validar no Teste

1. **Consumo de mensagens efetivo:** confirmar se as 4 mensagens estimadas são suficientes (e não mais).
2. **Qualidade dos outputs:** validar se cada Skill entrega o output esperado com a personalização correta.
3. **Identidade visual:** confirmar se os artefatos HTML aplicam a paleta Lumina corretamente.
4. **AskRH no caso sensível:** confirmar se a Pergunta 5 (conflito) leva à escalação para humano.
5. **Painel com semáforo:** confirmar se os 8 colaboradores aparecem ordenados por risco e com badges coloridos.
