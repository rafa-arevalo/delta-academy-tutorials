Você foi acionado para criar uma nova aula no site da **Delta Academy**.

O usuário vai colar um roteiro. Sua missão é transformar esse roteiro em um arquivo HTML completo seguindo exatamente o padrão do projeto, depois adicionar o card em `index.html`.

---

## PASSO 1 — Receber e analisar o roteiro

O roteiro fornecido é: $ARGUMENTS

Se `$ARGUMENTS` estiver vazio, peça ao usuário que cole o roteiro agora antes de continuar.

Ao analisar o roteiro, extraia obrigatoriamente:
- **Título da aula** (ex: "Automação de Cobrança com N8N")
- **Código/tag** (ex: A01, A04, EXERCICIO, N8N, PITCH — pergunte ao usuário se não estiver claro)
- **Cor da tag** para o index: green, orange, blue, purple ou red
- **Descrição curta** (1–2 frases para o card do index)
- **Lista de seções/steps** com seus títulos e conteúdo
- **Slug para o nome do arquivo** (kebab-case, ex: `tutorial-automacao-n8n.html`)

Confirme com o usuário o nome do arquivo e a tag antes de gerar o HTML.

---

## PASSO 2 — Gerar o arquivo HTML

Crie o arquivo `tutorial-{slug}.html` na raiz do repositório (`/Users/rafael-arevalo/Documents/delta-board-main/`).

### Identidade visual — Delta Academy

```css
--accent: #57674E;
--accent2: #475840;
--accent-light: #EEF1EB;
--accent-lighter: #F5F7F3;
--accent-border: #C8D1C0;
--accent-text: #3D4A36;
```

Logo: `logo-delta-light.svg` (não usado no tutorial, apenas no index)

### Template HTML obrigatório

Siga esta estrutura **exatamente** — não invente componentes novos:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tutorial — {TÍTULO DA AULA}</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;450;500;600;700;800&display=swap" rel="stylesheet">
<style>
  /* Cole aqui o CSS completo — copie de tutorial-eng-prompt.html e adapte apenas as variáveis --accent se necessário */
  /* NÃO incluir CSS de .stepper-header, .stepper-node, .sn-label, .sn-check, .stepper-arrow, .back-btn (stepper), .right-sidebar, .rs-section-title, .rs-table */
  /* Layout usa apenas sidebar esquerda (256px) + main content — sem stepper no topo e sem right sidebar */
  /* .layout min-height deve ser 100vh (não calc(100vh - 52px)) */
  /* .sidebar top deve ser 0 e height 100vh (não 52px e calc(100vh - 52px)) */
</style>
</head>
<body>

<div class="layout">

  <!-- SIDEBAR ESQUERDA (256px) -->
  <div class="sidebar">
    <div class="sidebar-header">
      <a href="index.html" style="font-size:0.68rem;color:var(--text3);text-decoration:none;display:inline-flex;align-items:center;gap:4px;margin-bottom:8px;font-weight:600;">← Índice</a>
      <h2>{TÍTULO DA AULA}</h2>
      <p>{TAG} · Delta Skills</p>
    </div>
    <nav>
      <!-- nav-group com nav-items para cada seção -->
      <div class="nav-group">
        <div class="nav-group-title">Conteúdo</div>
        <div class="nav-item active" onclick="showSection('sec-home')" data-section="sec-home">
          <span class="ni-num">00</span>Visão Geral<span class="ni-check">✓</span>
        </div>
        <!-- um nav-item por seção -->
      </div>
    </nav>
    <div class="sidebar-progress">
      <div class="sp-label">Progresso — <span id="pct">0</span>%</div>
      <div class="sp-bar"><div class="sp-fill" id="sp-fill"></div></div>
    </div>
  </div>

  <!-- MAIN CONTENT -->
  <div class="main">

    <!-- SEÇÃO HOME (sempre a primeira, class="section active") -->
    <div class="section active" id="sec-home">
      <div class="sec-title"><span class="snum">00.</span> {Título da Seção}</div>
      <div class="sec-desc">{Subtítulo da seção}</div>
      <!-- Conteúdo: overview-card, instructions, copy-block, tip-box, etc. -->
      <div class="nav-buttons">
        <button class="nav-btn secondary" onclick="goHome()">↩ Início</button>
        <button class="nav-btn primary" onclick="showSection('sec-step1')">Próximo →</button>
      </div>
    </div>

    <!-- SEÇÕES SUBSEQUENTES (class="section", sem active) -->
    <!-- ... -->

  </div>

  <!-- NÃO usar right-sidebar — o conteúdo de referência vai dentro das seções do main -->

</div>

<script>
const visited = new Set(['sec-home'])

function showSection(id) {
  document.querySelectorAll('.section').forEach(s => s.classList.remove('active'))
  document.getElementById(id)?.classList.add('active')
  document.querySelectorAll('.nav-item').forEach(n => {
    n.classList.toggle('active', n.dataset.section === id)
    if (visited.has(n.dataset.section)) n.classList.add('completed')
  })
  visited.add(id)
  updateProgress()
  window.scrollTo({top:0,behavior:'smooth'})
}

function updateProgress() {
  const pct = Math.round((visited.size / document.querySelectorAll('.section').length) * 100)
  document.getElementById('pct').textContent = pct
  document.getElementById('sp-fill').style.width = pct + '%'
}

function goHome() { showSection('sec-home') }

function copyText(btn, text) {
  navigator.clipboard?.writeText(text).then(() => {
    btn.textContent = 'Copiado!'
    setTimeout(() => btn.textContent = 'Copiar', 1800)
  }).catch(() => {
    const ta = document.createElement('textarea')
    ta.value = text; document.body.appendChild(ta)
    ta.select(); document.execCommand('copy')
    document.body.removeChild(ta)
    btn.textContent = 'Copiado!'
    setTimeout(() => btn.textContent = 'Copiar', 1800)
  })
}

updateProgress()
</script>
</body>
</html>
```

### Regras de conteúdo

- Títulos de seção: `<div class="sec-title"><span class="snum">01.</span> Título</div>`
- Passos numerados: use `.instructions` > `.inst` > `.inst-num` + `.inst-text`
- Prompts/código para copiar: use `.copy-block` com `.copy-btn` e `onclick="copyText(this, '...')"`
- Dicas: `.tip-box` (verde); alertas: `.warning-box` (vermelho)
- Cada seção termina com `.nav-buttons` contendo "← Anterior" e "Próximo →"
- Numeração das seções: 00 (home), 01, 02, 03...
- IDs das seções: `sec-home`, `sec-step1`, `sec-step2`, etc.
- Todo o CSS vai inline no `<style>` da página — **não crie arquivos externos**

---

## PASSO 3 — Adicionar card em `index.html`

Abra `/Users/rafael-arevalo/Documents/delta-board-main/index.html` e insira o novo card **após o último `</a>` existente dentro do container**, mantendo a ordem numérica da lista:

```html
<a class="card" href="tutorial-{slug}.html">
  <span class="card-tag tag-{cor}">{TAG}</span>
  <div class="card-title">{Título da Aula}</div>
  <div class="card-desc">{Descrição curta de 1-2 frases}</div>
</a>
```

Cores disponíveis para a tag: `tag-green`, `tag-orange`, `tag-blue`, `tag-purple`, `tag-red`

---

## PASSO 4 — Publicar e retornar URL

Execute os comandos abaixo **na ordem**, a partir do diretório `/Users/rafael-arevalo/Documents/delta-board-main/`:

```bash
git add tutorial-{slug}.html index.html
git commit -m "Add {TAG}: {Título da Aula}"
git push origin main
```

Após o push ser concluído com sucesso, retorne ao usuário a mensagem:

```
✅ Aula publicada!

📄 Página: https://rafa-arevalo.github.io/delta-academy-tutorials/tutorial-{slug}.html
📋 Índice: https://rafa-arevalo.github.io/delta-academy-tutorials/

⏱ O GitHub Pages pode levar até 1 minuto para refletir a atualização.
```
