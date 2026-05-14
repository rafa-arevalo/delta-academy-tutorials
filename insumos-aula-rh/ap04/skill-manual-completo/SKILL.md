---
name: manual-completo-lumina
description: Gera um único artefato HTML autocontido com 4 seções consolidadas — (1) carta de boas-vindas, (2) checklist Day 1, (3) briefing do gestor e (4) manual do colaborador completo — aplicando a identidade visual Lumina (paleta wellness premium, Fraunces + Inter). Use sempre que o usuário pedir o material completo de onboarding, o manual completo, o HTML do onboarding, o pacote final de boas-vindas ou variações.
---

# Skill: Manual Completo do Colaborador — Lumina

Esta Skill gera o artefato HTML final consolidado que reúne o Kit de Boas-Vindas (carta + checklist + briefing) e o Manual do Colaborador da Lumina em **um único arquivo HTML autocontido**, aplicando a identidade visual Lumina.

## Quando Usar

Use esta Skill sempre que o usuário fornecer dados de um novo colaborador (nome + cargo + gestor + data de início) e pedir o material completo de onboarding, manual completo, pacote final, HTML do onboarding ou expressão similar.

## Input Esperado

O usuário deve fornecer ao menos:
- **Nome do colaborador**
- **Cargo** (deve corresponder a um cargo do plano de cargos)
- **Gestor direto**
- **Data de início**

Se algum dado estiver faltando, peça antes de gerar.

## Estrutura do Output

Gere **um único artefato HTML autocontido** (CSS inline ou em `<style>` no `<head>`) com a seguinte estrutura, na ordem exata:

### Estrutura do HTML

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Onboarding [Nome] — Lumina</title>
  <link href="https://fonts.googleapis.com/css2?family=Fraunces:wght@500;600;700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
  <style>/* CSS Lumina conforme identidade visual */</style>
</head>
<body>
  <!-- Logo Lumina SVG -->
  <header>...</header>

  <!-- Hero -->
  <section class="hero">
    <h1>Bem-vinda, [Nome]</h1>
    <p>Seu onboarding na Lumina começa aqui.</p>
    <p>Cargo · Gestor · Data de início</p>
  </section>

  <!-- Navegação interna -->
  <nav>
    <a href="#carta">1. Carta de Boas-Vindas</a>
    <a href="#checklist">2. Checklist Day 1</a>
    <a href="#briefing">3. Briefing do Gestor</a>
    <a href="#manual">4. Manual do Colaborador</a>
  </nav>

  <!-- SEÇÃO 1 -->
  <section id="carta">...</section>

  <!-- SEÇÃO 2 -->
  <section id="checklist">...</section>

  <!-- SEÇÃO 3 -->
  <section id="briefing">...</section>

  <!-- SEÇÃO 4 -->
  <section id="manual">...</section>

  <footer>...</footer>
</body>
</html>
```

### Conteúdo das 4 Seções

#### Seção 1 — Carta de Boas-Vindas
- Tom acolhedor, máximo 250 palavras.
- Personalizada com nome + cargo + gestor + buddy designado.
- Linguagem Lumina ("time", "comunidade").
- Assinatura "Time Lumina".

#### Seção 2 — Checklist Day 1
- Tabela HTML com colunas: Hora · Atividade · Responsável · Status (checkbox visual).
- Itinerário completo do Day 1 adaptado ao cargo.

#### Seção 3 — Briefing do Gestor
- Caixa visualmente destacada (background pale-green) sinalizando "este conteúdo é para o gestor direto".
- 5 subseções: perfil do colaborador · recomendações de abordagem · plano da primeira semana · pontos de atenção · marcos a acompanhar.

#### Seção 4 — Manual do Colaborador (a parte mais extensa)
Esta é a seção que substitui o antigo "Manual do Colaborador" separado da AP04 anterior. Deve conter:

- **4.1 Quem é a Lumina** — resumo curto da empresa baseado no manual cultural (3 a 5 linhas).
- **4.2 O que acreditamos** — os 5 princípios da Lumina (do manual cultural), em cards visuais.
- **4.3 Como nos comportamos** — resumo das normas de reuniões, decisões, conflitos e erros (do manual cultural).
- **4.4 Rituais da Lumina** — Segunda Lumina, 1:1s, Reunião de Resultados, Aniversários, Encontrão, Retiro.
- **4.5 Benefícios** — lista resumida dos benefícios padrão da Lumina (vale-refeição, plano de saúde, day off de aniversário, parceria com academia, kit Lumina mensal).
- **4.6 Contatos essenciais** — RH (genérico), gestor direto, buddy.
- **4.7 Primeiros 90 dias** — visão geral do que esperar (resumo da política de admissão).

## Especificações Visuais

Aplique rigorosamente a identidade visual Lumina (consultar `identidade-visual-lumina.md` no Project):

- **Background:** `#FBF9F5` (branco quente).
- **Cor de marca:** `#5C7A5A` (verde-musgo) para títulos e elementos de destaque.
- **Acento:** `#C97A5A` (coral terroso) para CTAs e indicadores.
- **Texto secundário:** `#8A857D` (cinza-taupe).
- **Background de cards/blocos:** `#D4DDC9` (verde-claro pálido) com opacidade reduzida.
- **Tipografia:**
  - Títulos: Fraunces 600.
  - Corpo: Inter 400 e 500.
- **Espaçamento generoso:** padding mínimo de 24px nos cards, 64px nas seções principais.
- **Linhas finas:** bordas 0.5px ou 1px no máximo.
- **Sem sombras dramáticas.** No máximo `box-shadow: 0 1px 3px rgba(0,0,0,0.04)`.
- **Logo Lumina SVG inline** no header (círculo verde vazado + wordmark "lumina" em Fraunces lowercase).
- **Responsive básico:** funcionar em mobile com max-width 720px no conteúdo.

## Regras Importantes

1. **Um único arquivo HTML.** Tudo inline (CSS no `<head>`, fontes via Google Fonts CDN). Nada externo além das fontes.
2. **Tamanho controlado.** Não exagere — código limpo, sem comentários longos, sem CSS redundante.
3. **Personalize todas as 4 seções** ao cargo do colaborador — não use textos genéricos.
4. **Linguagem Lumina** em todas as seções: "time", "comunidade", tom direto e acolhedor.
5. **Cite os arquivos do Project** para fundamentar conteúdo (plano de cargos, política de admissão, manual cultural, identidade visual).
6. **Sem preâmbulos no chat.** Entregue o artefato HTML direto.
7. **Não invente** benefícios, cargos ou processos que não estejam nos arquivos do Project ou claramente consistentes com a Lumina.
