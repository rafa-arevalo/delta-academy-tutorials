# Design System — Tutoriais Delta Academy

> **Regra de ouro:** este arquivo é a **fonte da verdade** para o visual de qualquer tutorial da Delta Academy gerado via `/criar-nova-aula-Delta`. Se algo aqui contradiz o template, **siga este arquivo**.

**Bundle original:** `claude.ai/design` (hash `semtgnrJnvCk2-PPxWDNEg`). Para atualizar o design system, re-exporte no Claude Design e sobrescreva os arquivos deste diretório.

---

## Arquivos deste diretório

| Arquivo | Papel |
|---|---|
| `DESIGN_SYSTEM.md` | **Este arquivo.** Regras em linguagem natural. |
| `palettes.css` | 3 paletas (forest / dusk / **cream** default). Copiar inline no HTML. |
| `tokens.css` | Brand tokens (cores pine/sage/gold, type scale Aeonik, spacing, radii, shadows). Referência — **não** linkar do HTML gerado. |
| `templates/index.reference.html` | HTML completo da página-índice da aula. Usar como base. |
| `templates/tutorial.reference.html` | HTML completo de uma página de tutorial. Usar como base. |
| `assets/logo-horizontal-green.png` | Logo Delta Academy (horizontal). |
| `assets/logo-vertical-green.png` | Logo Delta Academy (vertical). |
| `fonts/Aeonik-*.otf` | Fonte oficial da marca. **Não incluir nos HTMLs** — usar Montserrat do Google Fonts como fallback. |

---

## Decisões de design (não negociáveis)

Estas decisões vieram de iterações diretas do Rafa no Claude Design. Não reinterpretar:

1. **Paleta default é `cream`** — sempre setar `data-palette="cream"` no `<html>` e `class="is-active"` no botão Cream do palette-switch.
2. **Fonte:** Montserrat (Google Fonts, pesos 400/500/600/700/800). Aeonik é a fonte da marca mas o HTML gerado usa Montserrat por portabilidade.
3. **Mono para código/prompts:** `'JetBrains Mono', 'Courier New', ui-monospace, monospace`.
4. **Card da home:** layout de 2 partes fixo:
   - **card-head** (fundo `var(--card-tag-bg)` escuro, texto `var(--card-tag-fg)` claro): `<span class="card-num">01</span>` + `<span class="card-title">Título da Aula</span>` lado a lado
   - **card-body** (fundo `#FFFFFF` puro, texto `#0E1A19`): só `<div class="card-desc">descrição</div>`
5. **Blocos de prompt:** estrutura sempre em 2 partes:
   - `<span class="copy-label">Nome do prompt</span>` **FORA** do retângulo, em verde escuro `var(--accent2)` com `border-bottom: 2px solid var(--accent2)`
   - `<div class="copy-block">` com fundo `#FFFFFF`, texto `#0E1A19`, borda esquerda 4px em `var(--accent2)`, fonte JetBrains Mono peso 500, sombra interna sutil
   - **NÃO** usar `.section-divider` acima do bloco (foi removido no design final)
6. **Sidebar (tutorial):** títulos de grupo (`Início`, `Introdução`, `Demonstração`, `Atividade Prática`) em **creme claro** `var(--sidebar-fg)`, tamanho `0.82rem`, peso `800`, uppercase — **maiores e mais fortes** que os subitens (`0.74rem`, peso `400`).
7. **Section badges (Introdução / Demonstração / Atividade Prática no main):** **todas iguais** — fundo `var(--accent2)`, texto `var(--bg)`, peso 800, `0.72rem`, letter-spacing `0.14em`. Não diferenciar por cor.
8. **Header da home:** card único com apenas o box verde escuro (`.header-bar`). H1 = título do curso em cor clara `var(--bg)`, H2 = literal **"Delta Academy"** em gold `var(--gold)`, menor, uppercase, tracking `0.1em`. **Sem** `.header-info` com metadados (professor/duração).
9. **Seção label "AULAS"** (entre header e cards): literal `<div class="section-label">AULAS</div>`, tamanho `1.15rem`, peso `800`, sage `var(--accent)`, uppercase, tracking `0.14em`. **Maior** que títulos das aulas (`0.95rem`).
10. **Palette-switch** fixo no top-right sempre presente em ambas as páginas.

---

## Estrutura esperada

### Tutorial único na raiz (uma aula avulsa)
```
tutorial-{slug}.html        ← página única
index.html                  ← card novo adicionado aqui
```

### Sub-aula (curso com múltiplas aulas) — **preferido quando há ≥ 3 módulos/atividades**
```
aula-{slug-curso}/
├── index.html              ← índice do curso (cards numerados)
├── tutorial-01-{slug}.html
├── tutorial-02-{slug}.html
└── ...
index.html                  ← card da sub-aula com href="aula-{slug-curso}/index.html"
```

**Heurística de escolha:** se o roteiro tem ≥ 3 módulos/atividades independentes → sub-aula. Caso contrário → tutorial único.

---

## Placeholders nos templates

Os arquivos em `templates/*.reference.html` são **referências funcionais** (a versão da aula "Pesquisa Profunda" 100% renderizável). Ao gerar um HTML novo, **copie o arquivo inteiro** e substitua:

### Em `index.reference.html`
- `<title>` → `{TÍTULO DO CURSO} · Delta Academy`
- `<h1>` do header-bar → título do curso
- `<h2>` do header-bar → sempre "Delta Academy" (literal, não mudar)
- `<a class="card">` — um por aula; substituir `card-num`, `card-title`, `card-desc` e `href`
- Footer: copyright e link

### Em `tutorial.reference.html`
- `<title>` → `{NN}. {TÍTULO DA AULA} · Delta Academy`
- `.sidebar-header h2` → título da aula
- `.sidebar-header p` → `Atividade NN · {NOME DO CURSO}`
- Cada `.nav-group` → um grupo (Início, Introdução, Demonstração, Atividade Prática); pode haver mais ou menos grupos
- Cada `.section` → uma seção; manter IDs `sec-home`, `sec-step1`…
- **JS:** atualizar `PKEY` (chave de localStorage) para algo único por aula, ex: `delta-tut-{slug}`; atualizar `TOTAL` para o número de seções
- Conteúdo: substituir usando os componentes abaixo

---

## Componentes disponíveis (use só estes)

### `.breadcrumb`
```html
<div class="breadcrumb">Delta Board &rsaquo; {Curso} &rsaquo; <a href="index.html">Índice</a> &rsaquo; {NN}. {Aula}</div>
```

### `.sec-title` + `.sec-desc`
```html
<div class="sec-title"><span class="snum">NN.</span> Título da seção</div>
<div class="sec-desc">Subtítulo curto</div>
```
Variantes: `.sec-title.demo` (snum azul) e `.sec-title.pratica` (snum verde).

### `.section-badge`
```html
<span class="section-badge badge-intro">Introdução</span>
<span class="section-badge badge-demo">Demonstração</span>
<span class="section-badge badge-pratica">Atividade Prática</span>
```
**Todas visualmente iguais** (verde escuro `var(--accent2)` sobre creme `var(--bg)`). Só o texto muda.

### `.lead-text`
Parágrafo de corpo. `<strong>` vira verde pinho `var(--accent2)`.

### `.overview-card` (container com H3)
```html
<div class="overview-card">
  <h3>Ficha técnica</h3>
  <p>...</p>
  <ul><li>item</li></ul>
</div>
```

### `.ficha-table` (tabela 2 colunas ou 3 colunas)
Primeira coluna em background `var(--ficha-td1-bg)`, peso 600. Headers em `var(--ficha-th-bg)` uppercase.

### `.instructions` + `.inst` (passo a passo numerado)
```html
<div class="instructions">
  <div class="inst">
    <div class="inst-num">1</div>
    <div class="inst-text"><strong>Título.</strong> <span class="time">(30 seg)</span><br>Descrição.</div>
  </div>
</div>
```

### `.copy-wrap` + `.copy-label` + `.copy-block` (blocos de prompt)
```html
<div class="copy-wrap">
  <span class="copy-label">Prompt A — busca rápida</span>
  <div class="copy-block" id="prompt-a">
    <button class="copy-btn" onclick="copyText(this, document.getElementById('prompt-a-text').textContent)">Copiar</button>
    <span id="prompt-a-text">Texto do prompt aqui.</span>
  </div>
</div>
```

### `.tip-box` (dica verde/sage)
```html
<div class="tip-box">
  <div class="tip-label">Dica</div>
  <p>Texto da dica.</p>
</div>
```

### `.warning-box` (alerta gold/warn)
```html
<div class="warning-box">
  <div class="warning-label">Importante</div>
  <p>Texto do alerta.</p>
</div>
```

### `.insight-box` (destaque escuro com acento gold)
```html
<div class="insight-box">
  <div class="insight-label">Insight</div>
  <p>Texto do insight. <strong>Palavra destacada em gold.</strong></p>
</div>
```

### `.tool-links` (grid 2 colunas de links para ferramentas)
```html
<div class="tool-links">
  <a class="tool-link" href="https://claude.ai" target="_blank">
    <div><div class="tl-name">Claude</div><div class="tl-url">claude.ai</div></div>
  </a>
</div>
```

### `.observation-list` (lista com borda esquerda azul)
```html
<ul class="observation-list">
  <li><strong>Chave.</strong> Descrição.</li>
</ul>
```

### `.nav-buttons` (rodapé da seção)
```html
<div class="nav-buttons">
  <button class="nav-btn" onclick="showSection('sec-step1')">&#8592; Anterior</button>
  <button class="nav-btn primary" onclick="showSection('sec-step3')">Próximo &#8594;</button>
</div>
```
Última seção: `<a class="nav-btn primary" href="index.html">&#8617; Voltar ao índice</a>`.

---

## Estrutura de navegação (tutorial padrão)

Padrão recomendado — **9 seções** em 4 grupos:

```
Início                       → sec-home (00. Visão Geral)
Introdução                   → sec-step1 (01. Contexto e objetivo)
Demonstração                 → sec-step2, sec-step3, sec-step4
Atividade Prática            → sec-step5, sec-step6, sec-step7, sec-step8
```

Se o roteiro pedir estrutura diferente (ex.: tutorial sem demo), adaptar o número de grupos/seções e **atualizar `TOTAL`** no JS.

---

## CSS — como embutir no HTML gerado

**Sempre inline, nunca linkar arquivos externos**, exceto:
- Google Fonts Montserrat via `<link>`
- `palettes.css` linkado **inline também** (cole o conteúdo inteiro dentro de `<style>`)

O HTML final é **auto-contido e copiável para qualquer lugar**. Nenhum `<link rel="stylesheet" href="palettes.css">` no output — sempre inline.

### Ordem obrigatória dentro do `<style>`:

1. Reset: `*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}`
2. Conteúdo completo de `palettes.css` (todas as 3 paletas + `.palette-switch`)
3. Estilos da página (copiar do template de referência)

---

## JavaScript — sempre incluir 2 blocos

### Bloco A — palette switcher (idêntico nas duas páginas)
```javascript
(function(){
  const KEY="delta-tut-palette";
  const saved=localStorage.getItem(KEY)||"cream";
  document.documentElement.setAttribute("data-palette",saved);
  const apply=(p)=>{
    document.documentElement.setAttribute("data-palette",p);
    localStorage.setItem(KEY,p);
    document.querySelectorAll(".palette-switch button").forEach(b=>b.classList.toggle("is-active",b.dataset.palette===p));
  };
  document.querySelectorAll(".palette-switch button").forEach(b=>b.addEventListener("click",()=>apply(b.dataset.palette)));
  apply(saved);
})();
```

### Bloco B — só no tutorial: navegação + progresso + copy
```javascript
const PKEY = "delta-tut-{SLUG-UNICO-DA-AULA}";
const completed = new Set(JSON.parse(localStorage.getItem(PKEY) || "[]"));
const TOTAL = 9; // ← ajustar

function renderProgress() {
  document.querySelectorAll(".nav-item").forEach(ni => {
    ni.classList.toggle("completed", completed.has(ni.dataset.section));
  });
  const pct = Math.round((completed.size / TOTAL) * 100);
  document.getElementById("pct").textContent = pct;
  document.getElementById("sp-fill").style.width = pct + "%";
}

function showSection(id) {
  document.querySelectorAll(".section").forEach(s => s.classList.remove("active"));
  document.querySelectorAll(".nav-item").forEach(n => n.classList.remove("active"));
  const sec = document.getElementById(id);
  if (sec) sec.classList.add("active");
  const nav = document.querySelector(`.nav-item[data-section="${id}"]`);
  if (nav) nav.classList.add("active");
  completed.add(id);
  localStorage.setItem(PKEY, JSON.stringify([...completed]));
  renderProgress();
  window.scrollTo({top:0, behavior:"smooth"});
}

function copyText(btn, text) {
  navigator.clipboard.writeText(text).then(() => {
    const old = btn.textContent;
    btn.textContent = "Copiado ✓";
    setTimeout(() => btn.textContent = old, 1600);
  });
}

(function init(){
  const last = localStorage.getItem(PKEY + ":last") || "sec-home";
  completed.add("sec-home");
  renderProgress();
  const origShow = showSection;
  window.showSection = function(id){ origShow(id); localStorage.setItem(PKEY + ":last", id); };
  if (last !== "sec-home") window.showSection(last);
})();
```

---

## Checklist de validação (antes de commitar qualquer HTML gerado)

- [ ] `<html lang="pt-BR" data-palette="cream">`
- [ ] Montserrat importado do Google Fonts
- [ ] Conteúdo de `palettes.css` inline dentro de `<style>`
- [ ] `.palette-switch` fixo no top-right com 3 botões (Cream `is-active`)
- [ ] Card da home: head escuro com num+title, body branco com desc
- [ ] Prompt: label verde **fora**, bloco branco com borda verde 4px **dentro**
- [ ] Section badges todas iguais (verde escuro)
- [ ] Sidebar: títulos de grupo em creme 0.82rem 800; subitens 0.74rem 400
- [ ] JS: `PKEY` único por aula, `TOTAL` reflete número real de seções
- [ ] Nenhum `<link href="palettes.css">` ou `<link href="tokens.css">` — tudo inline
- [ ] Nenhuma emoji inserida que não estivesse no roteiro
