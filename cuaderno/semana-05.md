
---
layout: default
title: "Semana 5 — JavaScript Básico y Avanzado"
permalink: /cuaderno/semana-05/
---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)

# Semana 5 — JavaScript Básico y Avanzado

> Objetivo: consolidar fundamentos (variables, tipos, funciones, DOM y eventos) y avanzar con **arrays funcionales**, **clases**, **closures** y **asincronía** (promesas y `async/await`).

<!-- ===== Estilos y utilidades aislados para las demos ===== -->
<style>
  .demo-s5 *{box-sizing:border-box}
  .demo-s5{font:15px/1.55 system-ui, -apple-system, Segoe UI, Roboto, sans-serif}
  .demo-s5 .card{border:1px solid #d0d7de;border-radius:12px;padding:12px;background:#fff}
  .demo-s5 .row{display:flex;gap:12px;flex-wrap:wrap}
  .demo-s5 .col{flex:1 1 260px}
  .demo-s5 .btn{padding:8px 14px;border-radius:10px;background:#2563eb;color:#fff;border:1px solid #1e40af}
  .demo-s5 .btn:hover{background:#1e40af}
  .demo-s5 pre{background:#0b1020;color:#e6edf3;border-radius:10px;padding:12px;overflow:auto}
  .demo-s5 .out{background:#f8fafc;border:1px dashed #cbd5e1;border-radius:8px;padding:8px;margin-top:8px;min-height:36px}
  .demo-s5 code{background:#f1f5f9;padding:0 4px;border-radius:4px}
  .demo-s5 .badge{display:inline-block;background:#e2e8f0;border-radius:999px;padding:2px 10px;font-size:.8em;margin-right:6px}
</style>

---

## 1) Básico: variables, tipos y funciones

### Vista (render)
<div class="demo-s5">
  <div class="row">
    <div class="col card">
      <h3>Calculadora simple</h3>
      <input id="s5-a" type="number" value="2" style="width:48%">
      <input id="s5-b" type="number" value="3" style="width:48%;float:right">
      <button id="s5-sum" class="btn" style="margin-top:8px">Sumar</button>
      <div id="s5-res1" class="out"></div>
      <p class="badge">let/const</p><p class="badge">función</p>
    </div>

    <div class="col card">
      <h3>Template strings</h3>
      <input id="s5-nombre" placeholder="Tu nombre" style="width:100%">
      <button id="s5-saludar" class="btn" style="margin-top:8px">Saludar</button>
      <div id="s5-res2" class="out"></div>
      <p class="badge">string interpolation</p>
    </div>
  </div>
</div>

<script>
// IIFE para aislar demo
(() => {
  const $ = sel => document.querySelector(sel);
  $('#s5-sum')?.addEventListener('click', () => {
    const a = Number($('#s5-a').value);
    const b = Number($('#s5-b').value);
    const sumar = (x, y) => x + y;
    $('#s5-res1').textContent = `Resultado: ${sumar(a, b)}`;
  });

  $('#s5-saludar')?.addEventListener('click', () => {
    const nombre = $('#s5-nombre').value || 'mundo';
    $('#s5-res2').textContent = `Hola, ${nombre}! Bienvenido/a a JS 🎯`;
  });
})();
</script>

**Código**
```js
const sumar = (x, y) => x + y;
const mensaje = nombre => `Hola, ${nombre}!`;
````

---

## 2) DOM + eventos

### Vista (render)

<div class="demo-s5">
  <div class="card">
    <h3>Contador</h3>
    <button id="s5-dec" class="btn">–</button>
    <button id="s5-inc" class="btn">+</button>
    <span id="s5-count" style="margin-left:10px;font-weight:700">0</span>
    <div class="out" id="s5-log"></div>
  </div>
</div>

<script>
(() => {
  let count = 0;
  const out = document.getElementById('s5-count');
  const log = document.getElementById('s5-log');
  const render = () => { out.textContent = count; log.textContent = `Estado: ${count}`; };
  document.getElementById('s5-inc')?.addEventListener('click', () => { count++; render(); });
  document.getElementById('s5-dec')?.addEventListener('click', () => { count--; render(); });
  render();
})();
</script>

**Código**

```js
let count = 0;
const render = () => { out.textContent = count; };
btnInc.addEventListener('click', () => { count++; render(); });
btnDec.addEventListener('click', () => { count--; render(); });
```

---

## 3) Arrays y objetos (map, filter, reduce)

### Vista (render)

<div class="demo-s5">
  <div class="card">
    <h3>Operaciones funcionales</h3>
    <div class="out" id="s5-arr-out"></div>
  </div>
</div>

<script>
(() => {
  const productos = [
    { id:1, nombre:'Teclado', precio:80 },
    { id:2, nombre:'Mouse',   precio:50 },
    { id:3, nombre:'Monitor', precio:550 },
    { id:4, nombre:'Cable',   precio:20 }
  ];

  const nombres = productos.map(p => p.nombre);
  const caros   = productos.filter(p => p.precio >= 100);
  const total   = productos.reduce((acc, p) => acc + p.precio, 0);

  const html = `
    <p><strong>Nombres:</strong> ${nombres.join(', ')}</p>
    <p><strong>Caros (≥ 100):</strong> ${caros.map(p=>p.nombre).join(', ') || '—'}</p>
    <p><strong>Total:</strong> S/ ${total}</p>
  `;
  document.getElementById('s5-arr-out').innerHTML = html;
})();
</script>

**Código**

```js
const nombres = productos.map(p => p.nombre);
const caros   = productos.filter(p => p.precio >= 100);
const total   = productos.reduce((acc, p) => acc + p.precio, 0);
```

---

## 4) Asincronía: Promesas y `async/await`

### Vista (render)

<div class="demo-s5">
  <div class="card">
    <h3>Fetch (con fallback)</h3>
    <button id="s5-fetch" class="btn">Cargar usuarios</button>
    <div id="s5-users" class="out"></div>
    <p class="badge">promise</p><p class="badge">async/await</p>
  </div>
</div>

<script>
(() => {
  const $ = s => document.querySelector(s);
  const fallback = [
    {name:'Usuario Local 1', email:'u1@demo.dev'},
    {name:'Usuario Local 2', email:'u2@demo.dev'},
    {name:'Usuario Local 3', email:'u3@demo.dev'},
  ];

  async function cargarUsuarios() {
    const target = $('#s5-users');
    target.textContent = 'Cargando...';
    try {
      const res = await fetch('https://jsonplaceholder.typicode.com/users?_limit=3', {cache:'no-store'});
      if (!res.ok) throw new Error('HTTP ' + res.status);
      const data = await res.json();
      target.innerHTML = data.map(u => `• ${u.name} <${u.email}>`).join('<br>');
    } catch (err) {
      target.innerHTML = `⚠️ Sin Internet / CORS. Fallback:<br>${fallback.map(u=>`• ${u.name} <${u.email}>`).join('<br>')}`;
    }
  }

  $('#s5-fetch')?.addEventListener('click', cargarUsuarios);
})();
</script>

**Código**

```js
async function cargarUsuarios() {
  try {
    const res = await fetch('https://jsonplaceholder.typicode.com/users?_limit=3');
    const data = await res.json();
    // usar data...
  } catch (e) {
    // fallback
  }
}
```

---

## 5) JS Avanzado: closures, `this`, clases y módulos

### 5.1 Closure (privacidad de estado)

```js
function contador() {
  let valor = 0;
  return {
    inc: () => ++valor,
    get: () => valor
  };
}
const c = contador();
c.inc(); // 1
c.get(); // 1
```

### 5.2 `this` y `bind`

```js
const mod = {
  x: 10,
  show(){ return this.x; }
};
const fn = mod.show;
fn();            // undefined (o window.x)
fn.bind(mod)();  // 10
```

### 5.3 Clases

<div class="demo-s5">
  <div class="card">
    <button id="s5-clase" class="btn">Crear usuario</button>
    <div id="s5-clase-out" class="out"></div>
  </div>
</div>

<script>
(() => {
  class Usuario {
    constructor(nombre){ this.nombre = nombre; }
    saludar(){ return `Hola, soy ${this.nombre}`; }
    static from(obj){ return new Usuario(obj.nombre); }
  }
  document.getElementById('s5-clase')?.addEventListener('click', () => {
    const u = Usuario.from({nombre:'Edison'});
    document.getElementById('s5-clase-out').textContent = u.saludar();
  });
})();
</script>

**Código**

```js
class Usuario {
  constructor(nombre){ this.nombre = nombre; }
  saludar(){ return `Hola, soy ${this.nombre}`; }
  static from(obj){ return new Usuario(obj.nombre); }
}
```

### 5.4 Módulos (ESM) — ejemplo conceptual

> En proyectos reales se usa bundler (Vite) o rutas de archivos. Aquí solo mostramos **cómo se importaría**:

```html
<script type="module">
  // archivo suma.js: export const suma = (a,b)=>a+b
  import { suma } from './suma.js';
  console.log(suma(2,3));
</script>
```

---

## Resultados de laboratorio

* Construí **interacciones DOM** (contador y formularios).
* Practiqué **map/filter/reduce** con datos estructurados.
* Implementé un `fetch` con **manejo de errores** y **fallback** local.
* Apliqué **closures**, **clases** y entendí el contexto de `this`.

## Reflexión

JavaScript permite pasar de páginas estáticas a **interfaces dinámicas**.
Con los fundamentos claros (funciones puras, arrays, DOM, asincronía), estoy listo para **React** y para escribir código más **modular y mantenible**.

