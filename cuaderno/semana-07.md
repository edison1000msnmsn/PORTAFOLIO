---
layout: default
title: "Semana 7 — Componentes y Hooks"
permalink: /cuaderno/semana-07/
---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)

# Semana 7 — Componentes y Hooks

> Objetivo: practicar **composición de componentes** (props, children, lifting state up) y dominar **hooks** esenciales: `useState`, `useEffect`, `useContext`, `useRef`, `useReducer`, `useMemo` y `useCallback`.

<!-- ===== Estilos ligeros para las demos ===== -->
<style>
  .demo-s7 *{box-sizing:border-box}
  .demo-s7{font:15px/1.55 system-ui,-apple-system,Segoe UI,Roboto,sans-serif}
  .demo-s7 .card{border:1px solid #d0d7de;border-radius:12px;padding:12px;background:#fff;margin-bottom:12px}
  .demo-s7 .row{display:flex;gap:12px;flex-wrap:wrap}
  .demo-s7 .col{flex:1 1 280px}
  .demo-s7 .btn{padding:8px 14px;border-radius:10px;background:#2563eb;color:#fff;border:1px solid #1e40af}
  .demo-s7 .btn:hover{background:#1e40af}
  .demo-s7 .muted{color:#475569}
  .demo-s7 input{padding:8px;border:1px solid #cbd5e1;border-radius:8px;width:100%}
  .demo-s7 pre{background:#0b1020;color:#e6edf3;border-radius:10px;padding:12px;overflow:auto}
  .demo-s7 code{background:#eef2ff;padding:0 4px;border-radius:4px}
  .demo-s7 .pill{display:inline-block;background:#e2e8f0;border-radius:999px;padding:2px 10px;font-size:.8em;margin-right:6px}
</style>

<!-- React 18 + Babel para demos en la página -->
<script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

---

## 1) Componentes: props, children y composición

### Vista (render)
<div id="s7-props" class="demo-s7 card"></div>

<script type="text/babel">
const { createRoot } = ReactDOM;

function Tag({ kind="info", children }) {
  const palette = {
    info:  { bg:"#eef2ff", bd:"#c7d2fe", fg:"#1e40af" },
    warn:  { bg:"#fff7ed", bd:"#fed7aa", fg:"#9a3412" },
    good:  { bg:"#ecfdf5", bd:"#a7f3d0", fg:"#065f46" }
  }[kind];
  const style = { display:"inline-block", padding:"4px 10px", borderRadius:"999px",
                  background:palette.bg, border:"1px solid "+palette.bd, color:palette.fg, marginRight:"6px" };
  return <span style={style}>{children}</span>;
}

function Card({ title, children, footer }) {
  return (
    <section className="card">
      <h3>{title}</h3>
      <div className="muted">{children}</div>
      {footer && <div style={{marginTop:8}}>{footer}</div>}
    </section>
  );
}

const AppProps = () => (
  <>
    <Card title="Composición con children"
          footer={<small className="muted">* footer recibido como prop</small>}>
      Este bloque es <code>children</code> y puede contener <strong>cualquier JSX</strong>.
      <div style={{marginTop:6}}>
        <Tag>props</Tag><Tag kind="warn">children</Tag><Tag kind="good">composición</Tag>
      </div>
    </Card>
  </>
);

createRoot(document.getElementById('s7-props')).render(<AppProps />);
</script>

**Código (resumen)**
```jsx
function Card({ title, children, footer }) { /* ... */ }
function Tag({ kind="info", children }) { /* ... */ }
````

**Claves**

* `children` permite **inyectar JSX** dentro de un componente contenedor.
* Pasar JSX en props (como `footer`) habilita **slots** reutilizables.

---

## 2) `useState` + Lifting state up

### Vista (render)

<div id="s7-state" class="demo-s7 row"></div>

<script type="text/babel">
const { useState } = React;

function Input({ value, onChange, label }) {
  return (
    <label style={{display:"block"}}>
      <span className="muted">{label}</span>
      <input value={value} onChange={e => onChange(e.target.value)} />
    </label>
  );
}

function Preview({ nombre, edad }) {
  return <p className="muted">Vista previa: <strong>{nombre || "—"}</strong> ({edad || "?"} años)</p>;
}

function Perfil() {
  const [nombre, setNombre] = useState("");
  const [edad, setEdad] = useState("");
  return (
    <div className="row">
      <div className="col card">
        <h3>Formulario</h3>
        <Input label="Nombre" value={nombre} onChange={setNombre} />
        <div style={{height:8}} />
        <Input label="Edad" value={edad} onChange={setEdad} />
      </div>
      <div className="col card">
        <h3>Estado arriba (lifting)</h3>
        <Preview nombre={nombre} edad={edad} />
      </div>
    </div>
  );
}

ReactDOM.createRoot(document.getElementById('s7-state')).render(<Perfil />);
</script>

**Claves**

* `useState` **encapsula** estado en componentes funcionales.
* “Lifting state up”: el estado vive en el **padre** y se pasa por props a hijos.

---

## 3) `useEffect`: efectos y ciclo de vida

### Vista (render)

<div id="s7-effect" class="demo-s7 card"></div>

<script type="text/babel">
const { useState, useEffect } = React;

function UsersMini() {
  const [list, setList] = useState([]);
  const [loading, setLoading] = useState(false);

  useEffect(() => {
    let alive = true;
    (async () => {
      setLoading(true);
      try {
        const res = await fetch("https://jsonplaceholder.typicode.com/users?_limit=3", { cache:"no-store" });
        const data = await res.json();
        if (alive) setList(data);
      } catch (e) {
        if (alive) setList([{id:0, name:"Fallback local", email:"demo@local.dev"}]);
      } finally {
        if (alive) setLoading(false);
      }
    })();
    return () => { alive = false; }; // cleanup
  }, []);

  return (
    <>
      <h3>useEffect (fetch + cleanup)</h3>
      {loading ? <p className="muted">Cargando…</p> :
        <ul>{list.map(u => <li key={u.id}>{u.name} <small className="muted">&lt;{u.email}&gt;</small></li>)}</ul>}
    </>
  );
}

ReactDOM.createRoot(document.getElementById('s7-effect')).render(<UsersMini />);
</script>

**Claves**

* `useEffect(fn, [])` ejecuta el efecto **una sola vez** (montaje).
* La función de retorno **limpia** suscripciones/peticiones.

---

## 4) `useContext`: estado global ligero (tema)

### Vista (render)

<div id="s7-context" class="demo-s7 card"></div>

<script type="text/babel">
const { createContext, useContext, useState } = React;
const ThemeCtx = createContext();

function ThemeProvider({ children }) {
  const [theme, setTheme] = useState("light");
  const toggle = () => setTheme(t => t==="light" ? "dark" : "light");
  const value = { theme, toggle };
  return <ThemeCtx.Provider value={value}>{children}</ThemeCtx.Provider>;
}

function Panel() {
  const { theme, toggle } = useContext(ThemeCtx);
  const isDark = theme==="dark";
  const style = { padding:12, borderRadius:10, border:"1px solid #cbd5e1",
                  background:isDark?"#0f172a":"#fff", color:isDark?"#e5e7eb":"#0f172a" };
  return (
    <div style={style}>
      <p>Tema actual: <strong>{theme}</strong></p>
      <button className="btn" onClick={toggle}>Alternar</button>
    </div>
  );
}

function AppCtx(){ return <ThemeProvider><Panel/></ThemeProvider>; }
ReactDOM.createRoot(document.getElementById('s7-context')).render(<AppCtx />);
</script>

**Claves**

* `createContext` + `useContext` evita **prop drilling** para datos globales.

---

## 5) `useRef`: referencia a DOM y valores mutables

### Vista (render)

<div id="s7-ref" class="demo-s7 card"></div>

<script type="text/babel">
const { useRef } = React;

function FocusInput(){
  const inputRef = useRef(null);
  return (
    <>
      <input ref={inputRef} placeholder="Escribe aquí…" />
      <div style={{height:8}} />
      <button className="btn" onClick={() => inputRef.current?.focus()}>Foco con useRef</button>
    </>
  );
}

ReactDOM.createRoot(document.getElementById('s7-ref')).render(<FocusInput />);
</script>

**Claves**

* `useRef` guarda un **objeto mutable** (`.current`) que persiste entre renders; útil para **DOM imperativo**.

---

## 6) `useReducer`: lógica de estado más completa

### Vista (render)

<div id="s7-reducer" class="demo-s7 card"></div>

<script type="text/babel">
const { useReducer } = React;

function reducer(state, action){
  switch(action.type){
    case "inc": return {...state, count: state.count + 1};
    case "dec": return {...state, count: state.count - 1};
    case "set": return {...state, step: action.step};
    default: return state;
  }
}

function Counter(){
  const [state, dispatch] = useReducer(reducer, { count:0, step:1 });
  return (
    <>
      <p>Valor: <strong>{state.count}</strong> (paso {state.step})</p>
      <div className="row">
        <button className="btn" onClick={() => dispatch({type:"dec"})}>–</button>
        <button className="btn" onClick={() => dispatch({type:"inc"})}>+</button>
        <button className="btn" onClick={() => dispatch({type:"set", step:2})}>Paso=2</button>
      </div>
    </>
  );
}

ReactDOM.createRoot(document.getElementById('s7-reducer')).render(<Counter />);
</script>

**Claves**

* `useReducer(reducer, init)` centraliza **transiciones de estado**; útil para flujos complejos.

---

## 7) `useMemo` / `useCallback`: rendimiento

### Vista (render)

<div id="s7-memo" class="demo-s7 card"></div>

<script type="text/babel">
const { useState, useMemo, useCallback } = React;

function expensiveFilter(items, q){
  // simulamos costo
  const t = performance.now(); while(performance.now() - t < 8) {}
  return items.filter(x => x.toLowerCase().includes(q.toLowerCase()));
}

function SearchList(){
  const [q, setQ] = useState("");
  const [n, setN] = useState(0);
  const items = useMemo(() => ["React","Router","Redux","Vite","TypeScript","Axios","Tailwind","Jest"], []);

  const result = useMemo(() => expensiveFilter(items, q), [items, q]);
  const inc = useCallback(() => setN(x => x+1), []);

  return (
    <>
      <input value={q} onChange={e => setQ(e.target.value)} placeholder="Buscar..." />
      <p className="muted">Coincidencias: {result.join(", ") || "—"}</p>
      <button className="btn" onClick={inc}>Clicks (no recalcula filtro): {n}</button>
    </>
  );
}

ReactDOM.createRoot(document.getElementById('s7-memo')).render(<SearchList />);
</script>

**Claves**

* `useMemo` **memoriza** resultados costosos según dependencias.
* `useCallback` memoriza una **función estable** (evita renders/cálculos innecesarios).

---

## Resultados de laboratorio

* Practiqué **composición** (`props`, `children`, “slots” con JSX) y **lifting state up**.
* Implementé hooks clave: `useState`, `useEffect` (fetch + cleanup), `useContext`, `useRef`, `useReducer`, `useMemo` y `useCallback`.
* Observé cómo **optimizar renders** y separar la **lógica de estado**.

## Reflexión

El enfoque por **componentes** y los **hooks** vuelven a React predecible, declarativo y escalable.
Mi objetivo siguiente es profundizar en **ruteo (React Router)**, **formularios controlados** y patrones de **estado global** (Context + Reducer, o librerías).
tos de código, gif cortos) por cada hook.
