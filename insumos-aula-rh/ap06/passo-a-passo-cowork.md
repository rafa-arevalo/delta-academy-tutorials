# Passo a Passo — Automatizando o Painel de Onboarding via Cowork

> **Pré-requisito:** plano Claude Pro ou superior. O Cowork não está disponível no plano gratuito.
>
> Este documento é o roteiro escrito da demonstração que o professor fez em sala. Use quando você migrar para o plano pago para automatizar o painel de onboarding semanalmente — sem precisar abrir o Claude toda segunda-feira de manhã.

---

## O que o Cowork faz nesse caso

O Cowork permite agendar tarefas que rodam automaticamente no Claude em horários definidos. Aplicado ao Painel de Onboarding, o cenário é:

> **Toda segunda-feira às 7h, o Claude:**
> 1. Acessa o arquivo de dados da coorte atualizado.
> 2. Invoca a Skill `painel-onboarding-lumina`.
> 3. Gera o painel HTML.
> 4. Envia o painel pronto para o e-mail do RH (ou Slack, dependendo da integração).

O resultado é o RH chegar na segunda-feira com o painel da semana já no e-mail, sem precisar abrir o Claude.

---

## Passo 1 — Atualizar a fonte dos dados da coorte

Antes de automatizar, decida onde os dados da coorte vão viver:

**Opção A (simples):** manter o arquivo `dados-coorte-onboarding.md` no Project e atualizar manualmente toda sexta-feira ao final do expediente.

**Opção B (mais robusta):** integrar com uma planilha viva (Google Sheets, Airtable, Notion) que se conecta ao Cowork via MCP ou ferramenta de integração. Isso requer configuração técnica adicional.

A demonstração em aula usou a **Opção A** para simplicidade. Para a sua empresa, vale avaliar a complexidade do volume — se você tem mais de 30 colaboradores em onboarding ao mês, considere a Opção B.

---

## Passo 2 — Acessar o Cowork no Claude

1. No menu lateral do Claude, clique em **Cowork** (ou **Tarefas Agendadas**, dependendo da versão da interface).
2. Clique em **Nova Tarefa**.

---

## Passo 3 — Configurar a tarefa agendada

Preencha:

- **Nome da tarefa:** "Painel Semanal de Onboarding — Lumina"
- **Frequência:** Semanal
- **Dia da semana:** Segunda-feira
- **Horário:** 07:00 (fuso horário de São Paulo)
- **Project vinculado:** RH — Lumina

---

## Passo 4 — Definir o prompt da tarefa

Cole o seguinte prompt no campo "Prompt da tarefa":

```
Use a Skill painel-onboarding-lumina para gerar o painel HTML autocontido de acompanhamento da coorte de onboarding da Lumina, com base nos dados atualizados do arquivo dados-coorte-onboarding.md carregado no Project.

Aplique a identidade visual Lumina e entregue o painel pronto para apresentar à liderança.

Em seguida, envie o painel gerado em HTML para o e-mail rh@lumina.com com o assunto "Painel de Onboarding — Semana de [DATA]" e uma frase curta de abertura no corpo do e-mail destacando o número de colaboradores em risco vermelho da semana.
```

---

## Passo 5 — Configurar a integração de saída (e-mail)

Para o Cowork enviar o painel automaticamente por e-mail, você precisa conectar a integração de Gmail (ou outro provedor) ao Claude:

1. No menu de **Integrações** do seu workspace Claude, conecte sua conta de e-mail corporativo.
2. Autorize o Claude a enviar e-mails em seu nome (apenas o que for explicitamente gerado por tarefas suas).
3. Teste com uma tarefa pontual antes de ativar a tarefa agendada.

> **Alternativa para Slack:** se preferir receber o painel no canal #rh-lumina do Slack, conecte a integração Slack e ajuste o prompt para "envie a mensagem no canal #rh-lumina" em vez de e-mail.

---

## Passo 6 — Salvar e ativar a tarefa

Clique em **Salvar e Ativar**. A primeira execução acontecerá na próxima segunda-feira às 7h.

---

## Passo 7 — Validar a primeira execução

Na primeira segunda-feira após ativação:

- Verifique se o e-mail (ou mensagem Slack) chegou no horário previsto.
- Confira se o painel HTML está com os dados atualizados.
- Se algo falhar, o Cowork registra o erro no log da tarefa — acesse pelo menu de Cowork.

---

## Boas Práticas

1. **Atualize os dados da coorte semanalmente.** O painel só é útil se os dados forem reais. Defina uma sexta-feira da semana como o dia de atualização fixa do arquivo `dados-coorte-onboarding.md`.

2. **Revise o output mensalmente.** Mesmo automatizado, abra o painel uma vez por mês com calma e verifique se os semáforos e alertas estão coerentes com o que você sabe da coorte.

3. **Ajuste o prompt conforme aprende.** Se notar que o painel está pesando demais em algum aspecto, refine o prompt da tarefa Cowork.

4. **Mantenha a Skill atualizada.** Se as regras de semáforo mudarem (ex: meta de eNPS for ajustada), edite o `SKILL.md` da `painel-onboarding-lumina` — o Cowork passa a usar a versão nova automaticamente.

---

## Quando NÃO automatizar

Cowork é poderoso, mas tem custo de mensagens (mais elevado que o gratuito). Avalie:

- Se você tem menos de 5 colaboradores em onboarding ativo, o painel manual semanal (1 mensagem/semana) pode ser mais barato.
- Se a coorte muda muito pouco semana a semana, considere mensal em vez de semanal.

A automação só vale quando a frequência é suficiente para justificar o consumo recorrente.

---

## Próximos Passos

Quando você tiver o Painel rodando bem por 4 semanas, considere adicionar uma segunda tarefa Cowork:

- **Dia 1 de cada mês:** análise consolidada do mês anterior (turnover early-stage, padrões na coorte, ajustes recomendados de processo).

Mas isso é assunto da próxima aula. 🌱
