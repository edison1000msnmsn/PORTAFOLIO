
---
layout: default
title: "Semana 4 — CSS Avanzado y CSS con Bootstrap"
permalink: /cuaderno/semana-04/
---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)

# Semana 4 — CSS Avanzado y CSS con Bootstrap

> Objetivo: profundizar en **Custom Properties (variables)**, **transiciones/animaciones**, **transformaciones** y **layout avanzado**; además, introducir **Bootstrap** para prototipado rápido (grid, utilidades y componentes base).

<style>
  .demo-s4 *{ box-sizing:border-box }
  .demo-s4{ font:15px/1.5 system-ui,-apple-system,Segoe UI,Roboto,sans-serif }
  .demo-s4 .card{ border:1px solid #d0d7de; border-radius:12px; padding:12px; background:#fff }
  .demo-s4 .grid{ display:grid; gap:10px; grid-template-columns:repeat(auto-fit,minmax(160px,1fr)) }
  .demo-s4 .chip{ display:inline-block; padding:2px 10px; border-radius:999px; background:#eef2ff; border:1px solid #c7d2fe; color:#1e40af; font-size:.85em }
  .demo-s4 .btn{ display:inline-block; padding:8px 14px; border-radius:10px; background:#2563eb; color:#fff; text-decoration:none; font-weight:600; border:1px solid #1e40af }
  .demo-s4 .btn:hover{ background:#1e40af }
  .demo-s4 .k{ color:#2563eb; font-weight:700 }

  /* Variables + dark/light via data-theme */
  .demo-s4 .vars{
    --bg: #ffffff; --fg:#0f172a; --brand:#2563eb; --muted:#64748b; --panel:#f8fafc;
    background:var(--bg); color:var(--fg); border:1px solid #e2e8f0; border-radius:12px; padding:12px;
  }
  .demo-s4 .vars .panel{ background:var(--panel); padding:10px; border-radius:10px }
  .demo-s4 .vars .toggle{ cursor:pointer; padding:6px 10px; border-radius:8px; background:var(--brand); color:#fff; border:none }
  .demo-s4 .vars[data-theme="dark"]{ --bg:#0b1220; --fg:#e5e7eb; --brand:#60a5fa; --muted:#94a3b8; --panel:#0f172a; border-color:#1f2937 }

  /* Transición + transform */
  .demo-s4 .card.fx .box{
    width:110px; height:70px; border-radius:12px; background:#bfdbfe; border:1px solid #60a5fa;
    transition: transform .25s ease, box-shadow .25s ease;
  }
  .demo-s4 .card.fx .box:hover{ transform: translateY(-6px) rotate(-2deg) scale(1.03); box-shadow:0 10px 18px rgba(0,0,0,.15) }

  /* Animación keyframes */
  @keyframes pulse{
    0%{ transform:scale(1); box-shadow:0 0 0 0 rgba(37,99,235,.45) }
    70%{ transform:scale(1.03); box-shadow:0 0 0 12px rgba(37,99,235,0) }
    100%{ transform:scale(1) }
  }
  .demo-s4 .pulse{ display:inline-block; padding:10px 14px; border-radius:999px; background:#2563eb; color:#fff; animation:pulse 1.8s infinite }

  /* Grid avanzado + minmax + auto-fit */
  .demo-s4 .gallery{ display:grid; gap:8px; grid-template-columns:repeat(auto-fit,minmax(120px,1fr)) }
  .demo-s4 .gallery div{ background:#f1f5f9; border:1px dashed #cbd5e1; height:72px; display:flex; align-items:center; justify-content:center; border-radius:8px }

  /* clamp para tipografía responsiva */
  .demo-s4 .clamp{ font-size:clamp(1.1rem, 2.8vw, 1.6rem); color:#0f172a }
</style>

---

## 1) CSS Avanzado

### 1.1 Variables (Custom Properties) + tema claro/oscuro
<div class="demo-s4">
  <div class="vars" id="vars-demo" data-theme="light">
    <p class="clamp"><strong>Título adaptable</strong> con <code>clamp()</code>.</p>
    <p style="color:var(--muted)">Las variables permiten centralizar colores y escalas.</p>
    <div class="panel">Panel usando <span class="k">var(--panel)</span></div>
    <p style="margin-top:8px"><button class="toggle" onclick="
      const v=document.getElementById('vars-demo');
      v.dataset.theme = v.dataset.theme==='dark' ? 'light' : 'dark';
    ">Alternar tema</button></p>
  </div>
</div>

**Código**
```css
:root{
  --bg:#fff; --fg:#0f172a; --brand:#2563eb; --muted:#64748b; --panel:#f8fafc;
}
[data-theme="dark"]{
  --bg:#0b1220; --fg:#e5e7eb; --brand:#60a5fa; --muted:#94a3b8; --panel:#0f172a;
}
````

---

### 1.2 Transiciones, transformaciones y animaciones

<div class="demo-s4 grid">
  <div class="card fx">
    <div class="box"></div>
    <p>Hover: <span class="chip">translateY</span> <span class="chip">rotate</span> <span class="chip">scale</span> + <span class="chip">shadow</span></p>
  </div>
  <div class="card">
    <span class="pulse">Pulsar</span>
    <p class="demo-s4" style="margin-top:6px">Botón con <code>@keyframes</code>.</p>
  </div>
</div>

**Código (resumen)**

```css
.box{ transition: transform .25s ease, box-shadow .25s ease; }
.box:hover{ transform: translateY(-6px) rotate(-2deg) scale(1.03); }
@keyframes pulse{ /* ... */ }
.pulse{ animation:pulse 1.8s infinite; }
```

---

### 1.3 Layout avanzado con Grid (auto-fit + minmax)

<div class="demo-s4">
  <div class="gallery">
    <div>1</div><div>2</div><div>3</div>
    <div>4</div><div>5</div><div>6</div>
  </div>
  <p style="color:#475569">La galería se adapta automáticamente al ancho disponible.</p>
</div>

**Código**

```css
.gallery{
  display:grid;
  gap:8px;
  grid-template-columns:repeat(auto-fit, minmax(120px, 1fr));
}
```

---

## 2) Bootstrap (grid, utilidades y componentes)

> Para prototipar más rápido, Bootstrap ofrece una **red de 12 columnas**, utilidades de espaciado/colores y componentes accesibles.

### 2.1 Demo Bootstrap (se renderiza aquí)

<!-- Cargamos Bootstrap CDN SOLO para esta demo -->

<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
<div class="container my-3 p-3 border rounded">
  <h2 class="h4 mb-3">Bootstrap: grid + botones</h2>

  <div class="row g-2">
    <div class="col-12 col-md-4"><div class="p-3 border rounded-3 text-center bg-light">col-12 col-md-4</div></div>
    <div class="col-12 col-md-4"><div class="p-3 border rounded-3 text-center bg-light">col-12 col-md-4</div></div>
    <div class="col-12 col-md-4"><div class="p-3 border rounded-3 text-center bg-light">col-12 col-md-4</div></div>
  </div>

  <div class="mt-3 d-flex gap-2">
    <button class="btn btn-primary">Primary</button>
    <button class="btn btn-outline-secondary">Outline</button>
    <button class="btn btn-success">Success</button>
  </div>
</div>

**Código (grid y botones)**

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">

<div class="container my-3">
  <div class="row g-2">
    <div class="col-12 col-md-4">...</div>
    <div class="col-12 col-md-4">...</div>
    <div class="col-12 col-md-4">...</div>
  </div>

  <button class="btn btn-primary">Primary</button>
  <button class="btn btn-outline-secondary">Outline</button>
</div>
```

---

### 2.2 Navbar mínima

<div class="container p-0">
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark rounded">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">MiSitio</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navb" aria-controls="navb" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navb">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item"><a class="nav-link active" href="#">Inicio</a></li>
          <li class="nav-item"><a class="nav-link" href="#">Proyectos</a></li>
          <li class="nav-item"><a class="nav-link" href="#">Contacto</a></li>
        </ul>
      </div>
    </div>
  </nav>
</div>
<script defer src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

**Código**

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">MiSitio</a>
    <button class="navbar-toggler" data-bs-toggle="collapse" data-bs-target="#navb">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navb">
      <ul class="navbar-nav ms-auto">
        <li class="nav-item"><a class="nav-link active" href="#">Inicio</a></li>
        <li class="nav-item"><a class="nav-link" href="#">Proyectos</a></li>
        <li class="nav-item"><a class="nav-link" href="#">Contacto</a></li>
      </ul>
    </div>
  </div>
</nav>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
```

**Notas rápidas de Bootstrap**

* **Grid:** contenedor `.container` → `.row` → `.col-*` (hasta 12).
* **Breakpoints:** `-sm-`, `-md-`, `-lg-`, `-xl-`…
* **Utilidades:** `m/p` (margen/padding), `text-*`, `bg-*`, `d-*`, `gap-*`.
* **Componentes:** navbar, cards, modals, alerts, forms (con accesibilidad por defecto).

---

## Resultados de laboratorio

* Implementé variables CSS y un interruptor **light/dark** con `data-theme`.
* Practiqué **transiciones, transformaciones y animaciones** con `@keyframes`.
* Maqueté una **galería responsive** con Grid (`auto-fit` + `minmax`).
* Repliqué layout con **Bootstrap** (grid + navbar + botones).

## Reflexión

CSS avanzado me da control fino sobre **temas, movimiento y layouts**; y **Bootstrap** acelera prototipos con buenas prácticas de accesibilidad.
Seguiré combinando **CSS puro** para personalizar y **Bootstrap** cuando necesite velocidad.


