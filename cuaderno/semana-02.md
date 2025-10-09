
---
layout: default
title: "Semana 2 — HTML5 + CSS3 (básico)"
permalink: /cuaderno/semana-02/
---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)

# Semana 2 — HTML5 + CSS3 (básico)

> Objetivo: practicar **estructura semántica HTML5**, **selectores y caja (box-model)** en CSS, y una primera aproximación a **Flexbox**, **Grid** y **responsive** con **media queries**.

<style>
  .demo-s2 *{box-sizing:border-box}
  .demo-s2{font: 15px/1.5 system-ui, -apple-system, Segoe UI, Roboto, sans-serif; margin:1.5rem 0}
  .demo-s2 .card{border:1px solid #d0d7de;border-radius:10px;padding:12px;background:#fff}
  .demo-s2 .row{display:flex;gap:10px;flex-wrap:wrap;margin:1rem 0}
  .demo-s2 .col{flex:1 1 160px}
  .demo-s2 .tag{display:inline-block;padding:3px 10px;background:#eaf2ff;border:1px solid #bdd1ff;color:#1e40af;border-radius:999px;font-size:.85em;margin:0 4px}
  .demo-s2 .grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:10px;margin:1rem 0}
  .demo-s2 .box{border:1px dashed #cbd5e1;background:#f8fafc;padding:12px;text-align:center;font-weight:500}
  .demo-s2 .note{color:#64748b; font-size:.95em; margin-top:1rem; padding:0.75rem; background:#f8fafc; border-radius:6px; border-left:3px solid #94a3b8}
  .demo-s2 .header{background:#0f172a;color:#fff;padding:12px 16px;border-radius:8px;margin-bottom:10px}
  .demo-s2 .nav{background:#1e293b;padding:10px 16px;border-radius:8px;margin-bottom:10px}
  .demo-s2 .nav a{margin-right:15px;text-decoration:none;color:#60a5fa;font-weight:500;transition:color 0.2s}
  .demo-s2 .nav a:hover{color:#93c5fd}
  .demo-s2 .article{border:1px solid #e5e7eb;border-radius:8px;padding:15px;background:#fff;margin-bottom:10px}
  .demo-s2 .article h2{margin-top:0}
  .demo-s2 .aside{border-left:3px solid #3b82f6;padding:12px 15px;background:#eff6ff;color:#1e40af;border-radius:0 6px 6px 0;margin-bottom:10px}
  .demo-s2 footer{text-align:center;padding:10px;color:#64748b;font-size:.9em;border-top:1px solid #e5e7eb;margin-top:10px}
  .demo-s2 .pill{display:inline-block;margin:4px 6px 4px 0;background:#e2e8f0;border-radius:999px;padding:4px 12px;font-size:.85em;font-weight:500}
  .demo-s2 .box-model-demo{margin-top:10px; padding:20px; border:3px solid #94a3b8; background:#f1f5f9; border-radius:8px; text-align:center; font-weight:600}
  /* responsive demo */
  .demo-s2 .mq{padding:12px 16px;border-radius:8px;background:#e0f2fe;border:2px solid #7dd3fc;text-align:center;font-weight:500;transition:all 0.3s}
  @media (max-width:600px){ 
    .demo-s2 .mq{background:#fee2e2;border-color:#fca5a5}
    .demo-s2 .mq::after{content:" ✓ ¡Cambio aplicado!";color:#dc2626;font-weight:bold}
  }
  
  .code-section{background:#f8fafc;border:1px solid #e2e8f0;border-radius:8px;padding:1rem;margin:1rem 0}
  .section-title{color:#0f172a;font-weight:600;margin-top:2.5rem;margin-bottom:1rem;font-size:1.5rem;border-bottom:2px solid #e5e7eb;padding-bottom:0.5rem}
  .subsection-title{color:#1e293b;font-weight:600;margin-top:1.5rem;margin-bottom:0.75rem;font-size:1.15rem}
</style>

---

## 1) HTML5 semántico

### Vista (renderizado)
<div class="demo-s2">
  <header class="header">
    <strong>Mi Blog</strong> <span class="tag">header</span>
  </header>
  <nav class="nav" aria-label="principal">
    <a href="#">Inicio</a>
    <a href="#">Artículos</a>
    <a href="#">Contacto</a>
  </nav>
  <main>
    <article class="article">
      <h2>Título del artículo</h2>
      <p>Este es el contenido principal del sitio. Aquí usamos <code>&lt;article&gt;</code> para contenidos independientes.</p>
    </article>
    <aside class="aside">
      <strong>Aside:</strong> Datos relacionados (autor, enlaces, etc.).
    </aside>
  </main>
  <footer>© 2025 — <em>footer</em></footer>
</div>

### Código

```html
<header>Mi Blog</header>
<nav aria-label="principal">
  <a href="#">Inicio</a>
  <a href="#">Artículos</a>
  <a href="#">Contacto</a>
</nav>

<main>
  <article>
    <h2>Título del artículo</h2>
    <p>Contenido principal del sitio.</p>
  </article>

  <aside>
    Datos relacionados (autor, enlaces, etc.).
  </aside>
</main>

<footer>© 2025</footer>
```

<div class="demo-s2">
  <p class="note"><strong>💡 Nota:</strong> Las etiquetas semánticas como <code>&lt;header&gt;</code>, <code>&lt;nav&gt;</code>, <code>&lt;main&gt;</code>, <code>&lt;article&gt;</code>, <code>&lt;aside&gt;</code> y <code>&lt;footer&gt;</code> mejoran la accesibilidad y el SEO.</p>
</div>

---

## 2) CSS básico: selectores y Box Model

### Vista (renderizado)

<div class="demo-s2">
  <div class="row">
    <div class="col card" style="border-color:#60a5fa;border-width:2px">
      <strong style="color:#2563eb">#id</strong>
      <p>Selector por <code>id</code> (único).</p>
    </div>
    <div class="col card" style="border-color:#34d399;border-width:2px">
      <strong style="color:#059669">.clase</strong>
      <p>Selector por <code>class</code> (reutilizable).</p>
    </div>
    <div class="col card" style="border-color:#f59e0b;border-width:2px">
      <strong style="color:#d97706">elemento</strong>
      <p>Selector por etiqueta: <code>p</code>, <code>a</code>, etc.</p>
    </div>
  </div>
  
  <div class="card">
    <h4 style="margin-top:0">Box Model</h4>
    <div>
      <span class="pill" style="background:#fecaca">margin</span>
      <span class="pill" style="background:#fed7aa">border</span>
      <span class="pill" style="background:#fde68a">padding</span>
      <span class="pill" style="background:#d9f99d">content</span>
    </div>
    <div class="box-model-demo">
      Soy el "content"
    </div>
    <p class="note"><strong>Box Model</strong> = margin + border + padding + content. Usa <code>box-sizing: border-box</code> para incluir padding y border en el tamaño total.</p>
  </div>
</div>

### Código

```css
/* Selectores */
#principal { border:1px solid #60a5fa; }
.card { border:1px solid #34d399; border-radius:10px; }
p { font-size: 1rem; }

/* Box Model */
.caja {
  margin: 8px;           /* Espacio exterior */
  padding: 12px;         /* Espacio interior */
  border: 3px solid #94a3b8;  /* Borde */
  box-sizing: border-box; /* Incluye padding y border en el ancho total */
}
```

---

## 3) Flexbox (layout de tarjetas)

### Vista (renderizado)

<div class="demo-s2">
  <div class="row">
    <div class="col card">📦 Tarjeta A</div>
    <div class="col card">🎨 Tarjeta B</div>
    <div class="col card">⚡ Tarjeta C</div>
  </div>
  <p class="note"><strong>Flexbox:</strong> Con <code>display:flex</code>, <code>gap</code> y <code>flex-wrap</code> logramos un contenedor fluido que se adapta automáticamente.</p>
</div>

### Código

```html
<div class="row">
  <div class="col card">Tarjeta A</div>
  <div class="col card">Tarjeta B</div>
  <div class="col card">Tarjeta C</div>
</div>
```

```css
.row { 
  display: flex; 
  gap: 10px; 
  flex-wrap: wrap;  /* Permite que las tarjetas se envuelvan */
}
.col { 
  flex: 1 1 160px;  /* Crece, se encoge, base mínima 160px */
}
.card { 
  border: 1px solid #d0d7de; 
  border-radius: 10px; 
  padding: 10px; 
}
```

---

## 4) Grid (galería simple)

### Vista (renderizado)

<div class="demo-s2">
  <div class="grid">
    <div class="box">📷 1</div>
    <div class="box">🎬 2</div>
    <div class="box">🎵 3</div>
    <div class="box">📚 4</div>
    <div class="box">🎮 5</div>
    <div class="box">🎯 6</div>
  </div>
  <p class="note"><strong>CSS Grid:</strong> Ideal para layouts bidimensionales. <code>auto-fit</code> y <code>minmax()</code> crean una cuadrícula responsiva automática.</p>
</div>

### Código

```html
<div class="grid">
  <div>1</div><div>2</div><div>3</div>
  <div>4</div><div>5</div><div>6</div>
</div>
```

```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 8px;
}
.grid > div {
  border: 1px dashed #cbd5e1;
  background: #f8fafc;
  padding: 6px;
  text-align: center;
}
```

---

## 5) Responsive con Media Queries

### Vista (renderizado)

<div class="demo-s2">
  <div class="mq">📱 Reduce la ventana a menos de 600px para ver el cambio de color</div>
  <p class="note"><strong>Media Queries:</strong> Permiten aplicar estilos diferentes según el tamaño de la pantalla, orientación, o características del dispositivo.</p>
</div>

### Código

```css
.caja-resp { 
  padding: 8px; 
  background: #e0f2fe; 
}

@media (max-width: 600px) {
  .caja-resp { 
    background: #fee2e2; 
  }
}
```

---

## Resultados de laboratorio

✅ Construí una página semántica simple con **header/nav/main/footer**  
✅ Practiqué **selectores y box-model**; maqueté tarjetas con **Flexbox**  
✅ Creé una galería con **Grid** y un ejemplo de **media queries**  

---

## Reflexión

Entendí que la semántica mejora la **accesibilidad y el SEO**, y que CSS (Flexbox/Grid) permite crear **layouts fluidos y responsivos** de manera eficiente.

**Próximos pasos:**
- Seguir practicando **responsive design** con diferentes breakpoints
- Componer secciones reutilizables y crear componentes modulares
- Profundizar en técnicas avanzadas de Grid (áreas nombradas, grid-template-areas)
