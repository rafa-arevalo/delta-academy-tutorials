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
</style>
</head>
<body>

<!-- STEPPER HEADER: uma bolinha por flow, separadas por setas -->
<div class="stepper-header">
  <div class="stepper-node active" onclick="showSection('sec-home')" id="sn-home">
    <span class="sn-check">✓</span>
    <span class="sn-label">Início</span>
  </div>
  <!-- Repita para cada flow/step: arrow + stepper-node -->
</div>

<div class="layout">

  <!-- SIDEBAR ESQUERDA (256px) -->
  <div class="sidebar">
    <div class="sidebar-header">
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

  <!-- RIGHT SIDEBAR (200px, referências contextuais) -->
  <div class="right-sidebar">
    <div class="rs-section-title">Referência Rápida</div>
    <!-- rs-table, links, etc. -->
  </div>

</div>

<script>
const stepToFlow = {
  'sec-home': 'home',
  'sec-step1': 'step1',
  // ...
}
const flowOrder = ['home','step1',/* ... */]
const visited = new Set(['sec-home'])
const completedFlows = new Set()

function showSection(id) {
  document.querySelectorAll('.section').forEach(s => s.classList.remove('active'))
  document.getElementById(id)?.classList.add('active')
  document.querySelectorAll('.nav-item').forEach(n => {
    n.classList.toggle('active', n.dataset.section === id)
    if (visited.has(n.dataset.section)) n.classList.add('completed')
  })
  visited.add(id)
  const flow = stepToFlow[id]
  if (flow) {
    const idx = flowOrder.indexOf(flow)
    if (idx > 0) completedFlows.add(flowOrder[idx-1])
  }
  updateStepper(flow)
  updateProgress()
  window.scrollTo({top:0,behavior:'smooth'})
}

function updateStepper(activeFlow) {
  document.querySelectorAll('.stepper-node').forEach(n => {
    const f = n.id.replace('sn-','')
    const idx = flowOrder.indexOf(f)
    const activeIdx = flowOrder.indexOf(activeFlow)
    n.classList.remove('active','completed','future')
    if (f === activeFlow) n.classList.add('active')
    else if (completedFlows.has(f) || idx < activeIdx) n.classList.add('completed')
    else n.classList.add('future')
  })
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

updateStepper('home')
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
