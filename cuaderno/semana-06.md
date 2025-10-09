
---

---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)

# Semana 6 — Introducción a React

> Objetivo: instalar/entender el **entorno** (Node, npm), conocer opciones de **arranque** (Create React App, **Vite**, Next.js), practicar **JSX**, **componentes** y **render** con ReactDOM. :contentReference[oaicite:0]{index=0}

---

## 1) Entorno de desarrollo

- **Node.js + npm** (descarga LTS e instalación guiada).   
- **Herramientas del ecosistema**: *bundlers* (Webpack/Turbopack), **Babel** para transpilar ES6+/JSX, **ESLint/Prettier** para calidad. :contentReference[oaicite:2]{index=2}

**Notas rápidas**
- `node_modules/` guarda todas las dependencias instaladas por `npm install`. :contentReference[oaicite:3]{index=3}
- **“Fatiga de JavaScript”**: configurar a mano Babel/Webpack/ESLint puede ser tedioso → preferir **arranques guiados**. :contentReference[oaicite:4]{index=4}

---

## 2) Opciones para crear proyectos

- **Create React App (CRA)**: config lista para dev/prod; requiere Node ≥ 14 y npm ≥ 5.6. :contentReference[oaicite:5]{index=5}  
- **Vite**: herramienta moderna, arranque muy rápido y DX simple (creada por Evan You). **Recomendada** para nuevos proyectos. :contentReference[oaicite:6]{index=6}  
- **Next.js**: framework sobre React con SSR, HMR, *code splitting*, facilita el *deploy*. :contentReference[oaicite:7]{index=7}

---

## 3) React con CDN (sin Vite): primera práctica

Esta demo usa **React 18 UMD + Babel standalone** para escribir JSX **directo en la página** (útil para entender la mecánica antes de Vite). :contentReference[oaicite:8]{index=8}

<div class="card" style="border:1px solid #d0d7de;border-radius:12px;padding:12px;background:#fff">
  <div id="hello-root"></div>
</div>

<!-- Carga de React y Babel para la demo -->
<script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

<script type="text/babel">
  const { useState } = React;

  function HolaReact({ nombre }) {
    const [clicks, setClicks] = useState(0);
    return (
      <div>
        <h3>Hola, {nombre} 👋</h3>
        <button onClick={() => setClicks(c => c + 1)}>Clicks: {clicks}</button>
      </div>
    );
  }

  const root = ReactDOM.createRoot(document.getElementById('hello-root'));
  root.render(<HolaReact nombre="Edison" />);
</script>

**Puntos clave**
- JSX necesita **transpilación** → aquí lo hace Babel en el navegador. :contentReference[oaicite:9]{index=9}
- **ReactDOM.createRoot** monta el árbol de componentes en un `div#id`. :contentReference[oaicite:10]{index=10}

---

## 4) Vite: estructura mínima y archivos clave

> Vite permite crear proyectos React con hot-reload y *build* optimizado. :contentReference[oaicite:11]{index=11}

**Comandos (referencia)**
```bash
# crear proyecto
npm create vite@latest mi-app -- --template react
cd mi-app
npm install
npm run dev   # servidor de desarrollo
npm run build # producción
````

**¿Qué contiene? (resumen)**

* `index.html`: punto de entrada real (inserta `<div id="root">`).
* `src/main.jsx`: crea el **root** y renderiza `<App />`.
* `src/App.jsx`: componente raíz.

**Ejemplo: `src/main.jsx`**

```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import './index.css'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
)
```

**Ejemplo: `src/App.jsx`**

```jsx
import { useState } from 'react'

export default function App(){
  const [count, setCount] = useState(0)
  return (
    <section>
      <h2>Hola, React + Vite</h2>
      <button onClick={() => setCount(c => c + 1)}>Clicks: {count}</button>
    </section>
  )
}
```

> Actividades sugeridas por el material: identificar archivo de inicio, roles de `main.jsx` y `App.jsx`, ubicar dónde está la librería de React y explorar React/ReactDOM (propiedades y métodos). 

---

## 5) Fundamentos de React: JSX, componentes y props/estado

### JSX

* Permite escribir **marcado** dentro de JS; requiere **transpilación** (Babel). 
* **Expresiones** dentro de `{}`: variables, atributos, evaluaciones. 

```jsx
const titulo = 'Portafolio'
const element = <h1>{titulo}</h1>
```

### Componentes (función)

* Deben iniciar con **mayúscula** y se crean en `.js/.jsx/.ts/.tsx`. 

```jsx
function Badge({ text }) {
  return <span className="badge">{text}</span>
}
```

### Props y estado (useState)

```jsx
import { useState } from 'react'

function Contador({ paso = 1 }) {
  const [n, setN] = useState(0)
  return (
    <div>
      <button onClick={() => setN(n - paso)}>-{paso}</button>
      <strong style={{margin:"0 8px"}}>{n}</strong>
      <button onClick={() => setN(n + paso)}>+{paso}</button>
    </div>
  )
}
```

> En el PDF se repasan **tipos de componentes** (clase y función) y la estructura interna (HTML/JS/CSS por componente). 

---

## 6) Resultados de laboratorio

* Ejecuté React con **CDN + Babel** y monté un componente con **estado** y **eventos**. 
* Creé un proyecto con **Vite**, identifiqué `index.html`, `main.jsx` y `App.jsx`, y probé el contador. 
* Revisé herramientas del ecosistema (**Webpack/Babel/ESLint/Prettier**) y su propósito. 

---

## 7) Reflexión

Vite simplifica el arranque y reduce la “**fatiga de JS**”, mientras que el enfoque por **componentes** (JSX + estado + props) hace a React predecible y escalable. El siguiente paso es profundizar en **componentes** (composición) y **Hooks** como `useEffect` y `useContext`.

