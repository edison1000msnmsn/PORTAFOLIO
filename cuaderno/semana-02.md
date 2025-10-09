¡dale! Aquí tienes la **Semana 2 — HTML5 + CSS3 (básico)** con el mismo formato que la S1 **y** con ejemplos que se **renderizan en el mismo .md** (verás el “cómo se ve” y debajo el “código fuente”).
Los estilos de las demos están **aislados** con la clase `.demo-s2` para no chocar con tu tema.

---

````md
---
layout: default
title: "Semana 2 — HTML5 + CSS3 (básico)"
permalink: /cuaderno/semana-02/
---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)

# Semana 2 — HTML5 + CSS3 (básico)

> Objetivo: practicar **estructura semántica HTML5**, **selectores y caja (box-model)** en CSS, y una primera aproximación a **Flexbox**, **Grid** y **responsive** con **media queries**.

<!-- Estilos aislados para las demos -->
<style>
  .demo-s2 *{box-sizing:border-box}
  .demo-s2{font: 15px/1.5 system-ui, -apple-system, Segoe UI, Roboto, sans-serif}
  .demo-s2 .card{border:1px solid #d0d7de;border-radius:10px;padding:10px;background:#fff}
  .demo-s2 .row{display:flex;gap:10px;flex-wrap:wrap}
  .demo-s2 .col{flex:1 1 160px}
  .demo-s2 .tag{display:inline-block;padding:2px 8px;background:#eaf2ff;border:1px solid #bdd1ff;color:#1e40af;border-radius:999px;font-size:.85em}
  .demo-s2 .grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:8px}
  .demo-s2 .box{border:1px dashed #cbd5e1;background:#f8fafc;padding:6px;text-align:center}
  .demo-s2 .note{color:#566; font-size:.95em}
  .demo-s2 .header{background:#0f172a;color:#fff;padding:8px;border-radius:8px}
  .demo-s2 .nav a{margin-right:10px;text-decoration:none;color:#2563eb}
  .demo-s2 .article{border:1px solid #e5e7eb;border-radius:8px;padding:10px;background:#fff}
  .demo-s2 .aside{border-left:3px solid #cbd5e1;padding-left:10px;color:#334155}
  .demo-s2 .pill{display:inline-block;margin:2px 6px 0 0;background:#e2e8f0;border-radius:999px;padding:2px 10px;font-size:.8em}
  /* responsive demo */
  .demo-s2 .mq{padding:8px;border-radius:8px;background:#e0f2fe;border:1px solid #7dd3fc}
  @media (max-width:600px){ .demo-s2 .mq{background:#fee2e2;border-color:#fecaca} }
</style>

---

## 1) HTML5 semántico

### Vista (renderizado)
<div class="demo-s2">
  <header class="header"><strong>Mi Blog</strong> — <span class="tag">header</span></header>
  <nav class="nav" aria-label="principal">
    <a href="#">Inicio</a><a href="#">Artículos</a><a href="#">Contacto</a>
  </nav>
  <main>
    <article class="article">
      <h2>Título del artículo</h2>
      <p>Este es el contenido principal del sitio. Aquí usamos <code>&lt;article&gt;</code> para contenidos independientes.</p>
    </article>
    <aside class="aside">Soy un <strong>aside</strong> con datos relacionados (autor, enlaces, etc.).</aside>
  </main>
  <footer class="note">© 2025 — <em>footer</em></footer>
</div>

**Código**
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
````

---

## 2) CSS básico: selectores y Box Model

### Vista (renderizado)

<div class="demo-s2">
  <div class="row">
    <div class="col card" style="border-color:#60a5fa">
      <strong>#id</strong>
      <p>Selector por <code>id</code>.</p>
    </div>
    <div class="col card" style="border-color:#34d399">
      <strong>.clase</strong>
      <p>Selector por <code>class</code>.</p>
    </div>
    <div class="col card" style="border-color:#f59e0b">
      <strong>elemento</strong>
      <p>Selector por etiqueta: <code>p</code>, <code>a</code>…</p>
    </div>
  </div>
  <div class="card" style="margin-top:8px">
    <div class="pill">margin</div><div class="pill">border</div><div class="pill">padding</div><div class="pill">content</div>
    <div class="box" style="margin-top:6px; padding:12px; border:3px solid #94a3b8">Soy el “content”</div>
    <p class="note">El <strong>Box Model</strong> = margin + border + padding + content.</p>
  </div>
</div>

**Código**

```css
/* selectores */
#principal { border:1px solid #60a5fa; }
.card { border:1px solid #34d399; border-radius:10px; }
p { font-size: 1rem; }

/* box model */
.caja {
  margin: 8px;
  padding: 12px;
  border: 3px solid #94a3b8;
}
```

---

## 3) Flexbox (layout de tarjetas)

### Vista (renderizado)

<div class="demo-s2">
  <div class="row">
    <div class="col card">Tarjeta A</div>
    <div class="col card">Tarjeta B</div>
    <div class="col card">Tarjeta C</div>
  </div>
  <p class="note">Con <code>display:flex</code>, <code>gap</code> y <code>flex-wrap</code> logramos un contenedor fluido.</p>
</div>

**Código**

```html
<div class="row">
  <div class="col card">Tarjeta A</div>
  <div class="col card">Tarjeta B</div>
  <div class="col card">Tarjeta C</div>
</div>
```

```css
.row { display:flex; gap:10px; flex-wrap:wrap; }
.col { flex:1 1 160px; }
.card { border:1px solid #d0d7de; border-radius:10px; padding:10px; }
```

---

## 4) Grid (galería simple)

### Vista (renderizado)

<div class="demo-s2">
  <div class="grid">
    <div class="box">1</div><div class="box">2</div><div class="box">3</div>
    <div class="box">4</div><div class="box">5</div><div class="box">6</div>
  </div>
</div>

**Código**

```html
<div class="grid">
  <div>1</div><div>2</div><div>3</div>
  <div>4</div><div>5</div><div>6</div>
</div>
```

```css
.grid{
  display:grid;
  grid-template-columns:repeat(auto-fit, minmax(120px, 1fr));
  gap:8px;
}
.grid > div{
  border:1px dashed #cbd5e1;
  background:#f8fafc;
  padding:6px;
  text-align:center;
}
```

---

## 5) Responsive con Media Queries

### Vista (renderizado)

<div class="demo-s2">
  <div class="mq">Reduce la ventana a &lt; 600px para ver el cambio de color.</div>
</div>

**Código**

```css
.caja-resp{ padding:8px; background:#e0f2fe; }
@media (max-width:600px){
  .caja-resp{ background:#fee2e2; }
}
```

---

## Resultados de laboratorio

* Construí una página semántica simple con **header/nav/main/footer**.
* Practiqué **selectores y box-model**; maqueté tarjetas con **Flexbox**.
* Creé una galería con **Grid** y un ejemplo de **media queries**.

## Reflexión

Entendí que la semántica mejora la **accesibilidad y el SEO**, y que CSS (Flexbox/Grid) permite **layouts fluidos**.
Seguiré practicando **responsive** y componiendo secciones reutilizables.


