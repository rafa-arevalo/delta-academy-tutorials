---
description: Cria uma nova aula (tutorial único ou sub-aula com múltiplos módulos) no padrão do Design System Delta Academy
---

Você foi acionado para criar uma nova aula no site da **Delta Academy** seguindo **estritamente** o Design System Delta Academy.

---

## PASSO 0 — Carregar o Design System (OBRIGATÓRIO, antes de qualquer coisa)

Leia **na íntegra e na ordem** os arquivos abaixo. Não prossiga sem fazer isso. O design system é a fonte da verdade — contradições entre o que você lembra e o que está nesses arquivos, **ganha o arquivo**:

1. `/Users/rafael-arevalo/Documents/delta-board-main/design-system/DESIGN_SYSTEM.md` — regras em linguagem natural
2. `/Users/rafael-arevalo/Documents/delta-board-main/design-system/palettes.css` — tokens das 3 paletas (cream é padrão)
3. `/Users/rafael-arevalo/Documents/delta-board-main/design-system/templates/index.reference.html` — template da página-índice
4. `/Users/rafael-arevalo/Documents/delta-board-main/design-system/templates/tutorial.reference.html` — template da página de tutorial

> Se qualquer um desses arquivos não existir, **pare e avise o usuário** — o design system está quebrado e não dá para gerar aula sem ele.

Depois de ler, **confirme em uma linha** que carregou o design system antes de seguir. Exemplo: "✅ Design System Delta Academy carregado (paleta default: cream)."

---

## PASSO 1 — Receber e analisar o roteiro

O roteiro fornecido é: $ARGUMENTS

Se `$ARGUMENTS` estiver vazio, peça ao usuário que cole o roteiro agora antes de continuar.

Ao analisar o roteiro, extraia obrigatoriamente:

- **Tipo de entrega** (decidir com heurística abaixo):
  - **Tutorial único** — uma aula avulsa em arquivo único na raiz (`tutorial-{slug}.html`)
  - **Sub-aula** — curso com ≥ 3 módulos/atividades independentes, com diretório próprio e índice (`aula-{slug}/`)
- **Título da aula/curso**
- **Slug** (kebab-case, sem acentos)
- **Descrição curta** (1-2 frases para o card do index raiz)
- **Estrutura de seções/módulos** com títulos e conteúdo

**Confirme com o usuário** o tipo de entrega (tutorial único vs sub-aula), o slug e o título antes de gerar o HTML. Uma pergunta só, objetiva.

---

## PASSO 2 — Gerar os HTMLs

### Regras absolutas (valem para qualquer HTML gerado)

1. **Paleta default:** sempre `<html lang="pt-BR" data-palette="cream">` e `class="is-active"` no botão Cream do palette-switch.
2. **Fontes:** Montserrat via Google Fonts (`https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800&display=swap`). Mono para prompts: `'JetBrains Mono','Courier New',ui-monospace,monospace`.
3. **CSS inline:** todo o CSS dentro de `<style>` no próprio HTML, incluindo o conteúdo integral de `palettes.css`. **Nunca** `<link rel="stylesheet" href="palettes.css">`.
4. **JS inline:** os dois blocos de JS do `DESIGN_SYSTEM.md` — palette switcher (idêntico) + (só no tutorial) navegação/progresso/copy com `PKEY` único.
5. **Palette-switch** fixo no top-right sempre presente, nas duas páginas.
6. **Card da home** — **sempre** estrutura `card-head` (verde escuro com num+title) + `card-body` (branco com desc). Não inverter.
7. **Bloco de prompt** — **sempre** `.copy-wrap` > `.copy-label` (fora, verde com underline) + `.copy-block` (dentro, branco puro com borda verde 4px).
8. **Section badges** — **todas iguais** (verde escuro sobre creme). Não diferenciar por cor.
9. **Sidebar** — títulos de grupo em creme claro, 0.82rem, peso 800, **maiores** que subitens (0.74rem, 400).
10. **Header da home** — card único só com box escuro: H1 título do curso em claro, H2 literal "Delta Academy" em gold.
11. **Section-label "AULAS"** entre header e cards: 1.15rem, 800, sage, uppercase, tracking 0.14em.

### 2A. Se for TUTORIAL ÚNICO

Gere **um arquivo** em `/Users/rafael-arevalo/Documents/delta-board-main/tutorial-{slug}.html` usando `tutorial.reference.html` como base. Substitua apenas o conteúdo (título, sidebar, seções, prompts, PKEY, TOTAL).

### 2B. Se for SUB-AULA

Crie o diretório `/Users/rafael-arevalo/Documents/delta-board-main/aula-{slug-curso}/` e gere:

1. **`aula-{slug-curso}/index.html`** — usando `index.reference.html` como base. Substitua header, cards das aulas e footer.
2. **`aula-{slug-curso}/tutorial-NN-{slug-aula}.html`** — um por módulo/atividade, usando `tutorial.reference.html` como base.

Todos os links internos (breadcrumbs, sidebar back-link, nav-buttons) devem apontar para `index.html` local do diretório da sub-aula, **não** para a raiz.

### Conteúdo — não inventar

- Siga **exatamente** os componentes listados no `DESIGN_SYSTEM.md`. Não invente novos callouts, não mude cores de badges, não altere hierarquia.
- **Não inserir emojis** que não estivessem no roteiro original.
- Se o roteiro pedir algo que não existe no design system (ex.: um tipo de caixa que não está lá), pergunte ao usuário antes de improvisar.

---

## PASSO 3 — Adicionar card em `index.html` da raiz

Abra `/Users/rafael-arevalo/Documents/delta-board-main/index.html`. Insira um novo `<a class="card">` **após o último `</a>` existente** dentro do `<div class="container">`, seguindo o mesmo padrão visual dos cards existentes no index raiz (esse index é diferente do template da sub-aula — é o catálogo geral do site e usa paleta mais simples).

### Para TUTORIAL ÚNICO
```html
<a class="card" href="tutorial-{slug}.html">
  <span class="card-tag tag-{cor}">{TAG}</span>
  <div class="card-title">{Título da Aula}</div>
  <div class="card-desc">{Descrição curta}</div>
</a>
```
Cores de tag: `tag-green`, `tag-orange`, `tag-blue`, `tag-purple`, `tag-red`.

### Para SUB-AULA
```html
<a class="card" href="aula-{slug-curso}/index.html" style="border-left:3px solid {COR-HEX}">
  <span class="card-tag tag-{cor}">{TAG-CURSO}</span>
  <div class="card-title">{Nome do Curso}</div>
  <div class="card-desc">{Descrição: N módulos práticos: ...}</div>
</a>
```
Sugestão de cor da border-left para Delta Academy: `#1F3331` (pine) ou `#B8933E` (gold).

---

## PASSO 4 — Publicar

A partir de `/Users/rafael-arevalo/Documents/delta-board-main/`:

```bash
# Tutorial único
git add tutorial-{slug}.html index.html
git commit -m "Add {TAG}: {Título da Aula}"

# Sub-aula
git add aula-{slug-curso}/ index.html
git commit -m "Add {TAG}: {Nome do Curso} (sub-aula com N módulos)"

git push origin main
```

**Só entregue a URL depois do `git push` retornar sucesso.** Se der erro (rejected, autenticação, hook), reporte o erro e **não** entregue a URL.

Use HEREDOC para a mensagem de commit se ela tiver múltiplas linhas. Inclua `Co-Authored-By: Claude <noreply@anthropic.com>` se for prática do projeto.

---

## PASSO 5 — Entregar ao usuário

Após push bem-sucedido, retorne a mensagem abaixo com os placeholders **já substituídos** pelos valores reais:

### Tutorial único
```
✅ Aula publicada no GitHub Pages!

🔗 URL para testar:
   https://rafa-arevalo.github.io/delta-academy-tutorials/tutorial-{slug}.html

📋 Índice atualizado:
   https://rafa-arevalo.github.io/delta-academy-tutorials/

⏱ Aguarde 30–60 segundos antes de abrir (GitHub Pages demora alguns segundos para publicar). Cmd+Shift+R se não carregar.

🎨 Paleta default: Cream. Use o switch no canto superior direito para testar Forest e Dusk.
```

### Sub-aula
```
✅ Sub-aula publicada no GitHub Pages!

🔗 Índice da sub-aula:
   https://rafa-arevalo.github.io/delta-academy-tutorials/aula-{slug-curso}/

🔗 Tutoriais:
   https://rafa-arevalo.github.io/delta-academy-tutorials/aula-{slug-curso}/tutorial-01-{slug}.html
   https://rafa-arevalo.github.io/delta-academy-tutorials/aula-{slug-curso}/tutorial-02-{slug}.html
   ...

📋 Índice raiz atualizado:
   https://rafa-arevalo.github.io/delta-academy-tutorials/

⏱ Aguarde 30–60 segundos. Cmd+Shift+R se não carregar.

🎨 Paleta default: Cream. Switch de paleta no canto superior direito (persistido em localStorage).
```

---

## Regras operacionais

- **Sempre entregue URLs completas clicáveis** (com `https://` e slugs substituídos).
- **Não abra a URL** — quem testa é o usuário.
- **Se o design system for atualizado** (arquivos em `design-system/` mudarem), as próximas aulas geradas já refletem — o comando relê tudo a cada execução.
- **Se surgir dúvida** entre roteiro vs design system, **peça confirmação** antes de decidir por conta.
