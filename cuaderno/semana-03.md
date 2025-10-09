
---
layout: default
title: "Semana 3 — HTML Avanzado y CSS Básico"
permalink: /cuaderno/semana-03/
---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)

# Semana 3 — HTML Avanzado y CSS Básico

> Esta semana se desarrollaron dos exposiciones clave:  
> **Grupo 1:** HTML Avanzado  
> **Grupo 2:** CSS Básico  

---

<style>
.demo-s3 *{box-sizing:border-box}
.demo-s3{font:15px/1.5 system-ui, -apple-system, Segoe UI, Roboto, sans-serif}
.demo-s3 .card{border:1px solid #d0d7de;border-radius:10px;padding:10px;background:#fff}
.demo-s3 .row{display:flex;gap:10px;flex-wrap:wrap}
.demo-s3 .grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(160px,1fr));gap:10px}
.demo-s3 .box{border:1px dashed #cbd5e1;background:#f8fafc;padding:6px;text-align:center}
.demo-s3 form{display:grid;gap:10px;max-width:300px;padding:10px;border:1px solid #d1d5db;border-radius:10px;background:#fff}
.demo-s3 input, .demo-s3 textarea, .demo-s3 select{width:100%;padding:6px;border:1px solid #cbd5e1;border-radius:6px}
.demo-s3 button{padding:8px 14px;background:#2563eb;color:white;border:none;border-radius:8px}
.demo-s3 button:hover{background:#1d4ed8}
.demo-s3 audio, .demo-s3 video{width:100%;border-radius:8px;margin-top:6px}
.demo-s3 .pill{display:inline-block;background:#e2e8f0;border-radius:999px;padding:2px 10px;font-size:.8em;margin:2px 6px 0 0}
.demo-s3 .note{color:#475569;font-size:.9em;margin-top:6px}
</style>

---

## 1) HTML Avanzado (exposición Grupo 1)

Se abordaron las etiquetas semánticas, los formularios, las tablas y los elementos multimedia que amplían las capacidades del HTML básico.

### Estructura semántica
<div class="demo-s3">
  <header class="card">
    <h2>Encabezado</h2>
    <nav><a href="#">Inicio</a> | <a href="#">Noticias</a> | <a href="#">Contacto</a></nav>
  </header>
  <article class="card">
    <h3>Artículo principal</h3>
    <p>El contenido semántico mejora la accesibilidad y SEO.</p>
  </article>
  <footer class="card">© 2025 Mi sitio</footer>
</div>

**Código**
```html
<header>
  <h2>Encabezado</h2>
  <nav>
    <a href="#">Inicio</a> | <a href="#">Noticias</a> | <a href="#">Contacto</a>
  </nav>
</header>

<article>
  <h3>Artículo principal</h3>
  <p>El contenido semántico mejora la accesibilidad y SEO.</p>
</article>

<footer>© 2025 Mi sitio</footer>
````

---

### Formularios

<div class="demo-s3">
  <form>
    <label>Nombre:<input type="text" placeholder="Ingresa tu nombre"></label>
    <label>Correo:<input type="email" placeholder="correo@ejemplo.com"></label>
    <label>Mensaje:<textarea rows="3"></textarea></label>
    <button>Enviar</button>
  </form>
</div>

**Código**

```html
<form>
  <label>Nombre:<input type="text" placeholder="Ingresa tu nombre"></label>
  <label>Correo:<input type="email" placeholder="correo@ejemplo.com"></label>
  <label>Mensaje:<textarea rows="3"></textarea></label>
  <button>Enviar</button>
</form>
```

**Puntos clave**

* Uso de atributos `placeholder`, `required`, `name`, `type`.
* Etiquetas `<label>` para accesibilidad.
* Se introdujo el atributo `action` y el método `POST/GET`.

---

### Multimedia en HTML5

<div class="demo-s3">
  <audio controls>
    <source src="{{ site.baseurl }}/assets/semana03/demo.mp3" type="audio/mp3">
    Tu navegador no soporta audio.
  </audio>

  <video controls poster="{{ site.baseurl }}/assets/semana03/poster.jpg">
    <source src="{{ site.baseurl }}/assets/semana03/demo.mp4" type="video/mp4">
    Tu navegador no soporta video.
  </video>
</div>

**Código**

```html
<audio controls>
  <source src="demo.mp3" type="audio/mp3">
</audio>

<video controls poster="poster.jpg">
  <source src="demo.mp4" type="video/mp4">
</video>
```

---

## 2) CSS Básico (exposición Grupo 2)

El segundo grupo explicó los **principios fundamentales de CSS**, sus reglas, selectores y propiedades visuales básicas.

### 🎨 Reglas CSS

<div class="demo-s3">
  <div class="card" style="background:#93c5fd;color:#0f172a;">color de fondo</div>
  <div class="card" style="border:2px solid #3b82f6;">borde</div>
  <div class="card" style="border-radius:12px;background:#bfdbfe;">bordes redondeados</div>
</div>

**Código**

```css
.caja1 { background: #93c5fd; color: #0f172a; }
.caja2 { border: 2px solid #3b82f6; }
.caja3 { border-radius: 12px; background: #bfdbfe; }
```

---

### Propiedades de texto y color

<div class="demo-s3 card">
  <h3 style="color:#2563eb;">Encabezado principal</h3>
  <p style="font-style:italic;color:#475569;">Texto con estilo itálico y color gris.</p>
  <p style="text-align:center;text-transform:uppercase;">centrado y en mayúsculas</p>
</div>

**Código**

```css
h3 { color:#2563eb; }
p { font-style: italic; color:#475569; }
p:last-child { text-align:center; text-transform:uppercase; }
```

---

### 🔳 Display y posicionamiento

<div class="demo-s3">
  <div class="grid">
    <div class="box">inline</div>
    <div class="box">block</div>
    <div class="box">inline-block</div>
  </div>
  <p class="note">Se repasó la diferencia entre <code>display: block</code>, <code>inline</code> e <code>inline-block</code>.</p>
</div>

---

### Conceptos clave repasados

* **Selectores** (elemento, clase, id).
* **Especificidad** y cascada.
* **Box Model** (margen, borde, relleno, contenido).
* **Colores:** `rgb()`, `hex`, `hsl`.
* **Fuentes:** `font-family`, `font-size`, `font-weight`.

---

## 3) Resultados de laboratorio

* Elaboré una página HTML completa con **header, main y footer**, aplicando estilos externos.
* Validé formularios y estilos básicos de texto y color.

---

## 4) Reflexión

Esta semana reforzó la **importancia de la semántica** y la **estructura visual**.
HTML organiza el contenido; CSS define su presentación.
Continuaré practicando el **modelo de caja**, **Flexbox** y **media queries** para lograr sitios más limpios y adaptativos.

