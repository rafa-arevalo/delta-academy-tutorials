# Identidade Visual — Lumina

A Lumina tem uma estética **minimalismo wellness premium** — fresca, sofisticada, energética sem ser agressiva. Aplica-se a relatórios, painéis, manuais, comunicações internas e qualquer peça visual gerada pelo time.

---

## Paleta de Cores

### Cores Principais

| Cor | HEX | Uso |
|---|---|---|
| Branco quente neutro | `#FBF9F5` | Background principal |
| Verde-musgo suave | `#5C7A5A` | Cor de marca dominante; títulos, elementos de destaque |
| Coral terroso | `#C97A5A` | Acento; chamadas de ação; alertas suaves |
| Cinza-taupe quente | `#8A857D` | Texto secundário, bordas, divisores |
| Verde-claro pálido | `#D4DDC9` | Backgrounds secundários, blocos de destaque |

### Cores de Estado (para painéis e dashboards)

| Cor | HEX | Uso |
|---|---|---|
| Verde sucesso | `#5C7A5A` | Status saudável, no prazo |
| Âmbar atenção | `#D4A95C` | Atenção, próximo do limite |
| Vermelho terroso | `#B8533E` | Crítico, fora do prazo |

---

## Tipografia

| Família | Uso |
|---|---|
| **Fraunces** | Títulos — serifada moderna com toque artesanal e wellness |
| **Inter** | Corpo — sans-serif clean, neutra, alta legibilidade |

**Pesos comuns:**
- Títulos: Fraunces 600 (semibold) ou 700 (bold)
- Subtítulos: Fraunces 500 (medium)
- Corpo: Inter 400 (regular) ou 500 (medium)
- Destaque no corpo: Inter 600 (semibold)

---

## Princípios de Design

1. **Muito espaço negativo.** Respiração visual é parte da identidade. Padding generoso, margens amplas.
2. **Dados em primeiro plano.** Em painéis e relatórios, o dado é a estrela. Ornamentos servem o dado, nunca o contrário.
3. **Linhas finas.** Bordas, divisores e gráficos usam stroke fino (1px ou 0.5px). Nada de bordas grossas.
4. **Sem grade visível em gráficos.** Gridlines, quando necessárias, são quase imperceptíveis.
5. **Hierarquia por espaçamento, não por tamanho exagerado.** Diferenciar elementos pelo espaço ao redor antes de aumentar muito o tamanho de fonte.
6. **Ausência de ornamentos pesados.** Sem ícones decorativos genéricos. Sem gradientes vibrantes. Sem sombras dramáticas.
7. **Animações sutis ou ausentes.** Quando houver transição, deve ser quase imperceptível (200–300ms, easing suave).

---

## Estilo de Relatórios e Painéis

- **Background:** branco quente (#FBF9F5).
- **Cards:** sem borda visível ou borda 0.5px cinza-taupe; sombra muito sutil ou ausente.
- **Tabelas:** linhas alternadas em branco e verde-claro pálido com opacidade reduzida; sem bordas verticais.
- **Tags e badges:** retangulares com cantos suavemente arredondados (4–6px), preenchimento suave da cor de estado, texto em peso semibold.
- **Gráficos:** uma cor principal por gráfico; uso de tons da paleta principal; legendas posicionadas próximas aos elementos, não em legenda separada quando possível.

---

## Logo

O logo da Lumina é **descrito em texto** para reprodução como SVG inline quando necessário:

- **Símbolo:** pequeno círculo verde-musgo (#5C7A5A) vazado, posicionado acima da palavra "lumina".
- **Wordmark:** tipografia serifada **Fraunces** da palavra "lumina" em letras minúsculas (lowercase), peso 600.
- **Espaçamento:** o círculo tem altura equivalente a aproximadamente 60% da altura do "l" da palavra "lumina".
- **Cor padrão:** verde-musgo (#5C7A5A) em ambos os elementos sobre fundo branco quente.
- **Versão monocromática:** mesma estrutura em branco (#FBF9F5) para uso em fundos escuros.

---

## Inspirações de Estilo

Marcas que servem de referência visual para o que a Lumina busca:
- **Athletic Greens** — minimalismo wellness premium aplicado ao verde.
- **Loop** — design clean e moderno para wellness.
- **Olipop** — uso de cores terrosas com ar premium.
- **Erewhon** — estética artesanal-luxo.

---

## Aplicação em HTML

Quando gerar artefatos HTML (manuais, painéis, relatórios), usar como CSS base:

```css
:root {
  --bg: #FBF9F5;
  --green: #5C7A5A;
  --coral: #C97A5A;
  --taupe: #8A857D;
  --pale-green: #D4DDC9;
  --amber: #D4A95C;
  --red: #B8533E;
}

body {
  font-family: 'Inter', -apple-system, sans-serif;
  background: var(--bg);
  color: #2A2A2A;
  line-height: 1.6;
}

h1, h2, h3 {
  font-family: 'Fraunces', Georgia, serif;
  font-weight: 600;
  color: var(--green);
  letter-spacing: -0.02em;
}
```

Importar fontes via Google Fonts:
```html
<link href="https://fonts.googleapis.com/css2?family=Fraunces:wght@500;600;700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
```
