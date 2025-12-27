---

---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)


# Semana 15 — Sistemas Inteligentes en Python (Sistema Experto + Lógica Difusa + LLM con Flask)

## 1) Logro de la semana
Implementé **tres enfoques de “sistema inteligente”** en Python:
1) **Sistema experto** (reglas IF–THEN) para diagnóstico simple por síntomas.  
2) **Mini app web con Flask** que consume un **LLM (tipo Llama)** para responder prompts desde un frontend simple (HTML/CSS/JS).

---

## 2) Definiciones en mis palabras (conceptos clave)

### 2.1 ¿Qué es un sistema inteligente?
Es un sistema que **percibe información**, la **procesa**, **razona** (con reglas o modelos), **aprende** (opcional) y **actúa** para cumplir un objetivo (decidir, recomendar o automatizar algo).

### 2.2 Arquitectura típica (bloques)
- **Percepción:** entrada (sensores, formularios, texto, API).
- **Conocimiento:** datos, reglas, “hechos”, modelos.
- **Razonamiento:** decide (IF–THEN, árboles, probabilístico, difuso).
- **Aprendizaje:** mejora con datos (ML/DL) si aplica.
- **Acción:** salida (recomendación, alerta, control, respuesta).

### 2.3 Modelos discriminativos vs generativos
- **Discriminativos:** predicen una etiqueta con base en una entrada (ej. “spam/no spam”). Se enfocan en decidir/clasificar.
- **Generativos:** pueden **crear** contenido (texto, imagen, audio) aprendiendo patrones del mundo.  
- **LLM:** un tipo de modelo generativo para **lenguaje**, entrenado con Transformers para producir texto coherente dado un contexto.

### 2.4 Sistema experto (reglas IF–THEN)
Es un programa que toma decisiones con **reglas** del tipo:
- **IF** (condición) **THEN** (conclusión / acción)

Suele tener:
- **Base de conocimientos:** reglas y hechos.
- **Motor de inferencia:** evalúa reglas y concluye.
- **Interfaz:** recibe síntomas/entradas y entrega diagnóstico/decisión.

### 2.5 Lógica difusa (Fuzzy)
A diferencia de la lógica “sí/no”, la lógica difusa usa niveles (0 a 1).
Ejemplo: una temperatura puede ser **media** en un 0.6 y **alta** en un 0.3 al mismo tiempo.  
Se trabaja con:
- **Conjuntos difusos** (baja/media/alta),
- **Funciones de pertenencia** (triangular, trapezoidal, etc.),
- **Reglas difusas** (IF temperatura es alta THEN potencia es alta),
- **Defuzzificación** (convertir el resultado a un número final).

---

## 3) Laboratorio 15-1 — Sistema experto + Control difuso

### 3.1 Sistema experto: diagnóstico básico por síntomas (IF–THEN)

**Idea:** Ingresar síntomas → aplicar reglas → obtener diagnóstico probable.

**Ejemplo (Python):**
```python
# sistema_experto.py
class Persona:
    def __init__(self, nombre: str, edad: int):
        self.nombre = nombre
        self.edad = edad

class Paciente(Persona):
    def __init__(self, nombre: str, edad: int, sintomas: list[str]):
        super().__init__(nombre, edad)
        self.sintomas = [s.lower().strip() for s in sintomas]

    def mostrar_sintomas(self) -> str:
        return "Síntomas reportados: " + ", ".join(self.sintomas)

def diagnosticar(sintomas: list[str]) -> str:
    s = set([x.lower().strip() for x in sintomas])

    # Reglas IF–THEN (ejemplo educativo)
    if {"fiebre", "tos", "dolor de garganta"}.issubset(s):
        return "Diagnóstico: Posible gripe común"
    if {"fiebre", "dolor muscular", "cansancio"}.issubset(s):
        return "Diagnóstico: Posible influenza"
    if {"dolor de cabeza", "mareos", "visión borrosa"}.issubset(s):
        return "Diagnóstico: Posible migraña"
    if {"tos", "dificultad para respirar"}.issubset(s):
        return "Diagnóstico: Posible bronquitis"

    return "Diagnóstico: No se identificó una condición clara. Se recomienda consulta médica."

if __name__ == "__main__":
    paciente = Paciente("Lucía", 22, ["fiebre", "tos", "dolor de garganta"])
    print(paciente.mostrar_sintomas())
    print(diagnosticar(paciente.sintomas))
````

**Qué aprendí acá**

* Cómo convertir “conocimiento humano” en reglas.
* La lógica IF–THEN es clara y explicable, pero puede crecer mucho si el dominio es grande.

---

### 3.2 Control difuso: potencia del aire acondicionado según temperatura

**Idea:** Temperatura (°C) → Potencia sugerida (%) usando lógica difusa.

**Dependencias:**

```bash
pip install numpy scikit-fuzzy
```

**Ejemplo (Python):**

```python
# climatizador_fuzzy.py
import numpy as np
import skfuzzy as fuzz
from skfuzzy import control as ctrl

# 1) Variables difusas
temperatura = ctrl.Antecedent(np.arange(15, 41, 1), "temperatura")
potencia = ctrl.Consequent(np.arange(0, 101, 1), "potencia")

# 2) Conjuntos difusos (funciones de pertenencia)
temperatura["baja"] = fuzz.trimf(temperatura.universe, [15, 15, 25])
temperatura["media"] = fuzz.trimf(temperatura.universe, [20, 27, 34])
temperatura["alta"] = fuzz.trimf(temperatura.universe, [30, 40, 40])

potencia["baja"] = fuzz.trimf(potencia.universe, [0, 0, 50])
potencia["media"] = fuzz.trimf(potencia.universe, [30, 50, 70])
potencia["alta"] = fuzz.trimf(potencia.universe, [60, 100, 100])

# 3) Reglas difusas (IF–THEN)
r1 = ctrl.Rule(temperatura["baja"], potencia["baja"])
r2 = ctrl.Rule(temperatura["media"], potencia["media"])
r3 = ctrl.Rule(temperatura["alta"], potencia["alta"])

# 4) Sistema de control
sistema = ctrl.ControlSystem([r1, r2, r3])
sim = ctrl.ControlSystemSimulation(sistema)

def recomendar_potencia(temp_c: float) -> float:
    sim.input["temperatura"] = float(temp_c)
    sim.compute()
    return float(sim.output["potencia"])

if __name__ == "__main__":
    for t in [18, 26, 30, 37]:
        print(f"Temp={t}°C -> Potencia sugerida={recomendar_potencia(t):.2f}%")
```

**Qué hace este sistema**

* “Traduce” el clima a reglas lingüísticas (baja/media/alta).
* Da una respuesta **gradual** (más natural que umbrales duros).

---

## 4) Laboratorio 15-2 — Mini App Web con Flask + LLM (tipo Llama)

> Nota: Un LLM grande puede ser pesado. Para pruebas rápidas, uso un modelo pequeño tipo `Llama-3.2-1B-Instruct` o similar.

### 4.1 Estructura del proyecto

```txt
llama_web_app/
├── app.py
├── .env
├── templates/
│   └── index.html
└── static/
    ├── style.css
    └── script.js
```

### 4.2 Instalación

```bash
pip install flask torch transformers python-dotenv
```

### 4.3 Backend (Flask) — `app.py`

```python
from flask import Flask, render_template, request, jsonify
from dotenv import load_dotenv
from transformers import AutoTokenizer, AutoModelForCausalLM
import torch
import os
import threading

load_dotenv()

MODEL_ID = os.getenv("MODEL_ID", "meta-llama/Llama-3.2-1B-Instruct")
MAX_NEW_TOKENS = int(os.getenv("MAX_NEW_TOKENS", "120"))

app = Flask(__name__)
_lock = threading.Lock()

# Cargar una sola vez
tokenizer = AutoTokenizer.from_pretrained(MODEL_ID)
model = AutoModelForCausalLM.from_pretrained(
    MODEL_ID,
    device_map="auto",
    torch_dtype=torch.float16 if torch.cuda.is_available() else torch.float32
)

@app.get("/")
def home():
    return render_template("index.html")

@app.post("/generate")
def generate():
    data = request.get_json(silent=True) or {}
    prompt = (data.get("prompt") or "").strip()
    if not prompt:
        return jsonify({"error": "Prompt vacío"}), 400

    inputs = tokenizer(prompt, return_tensors="pt").to(model.device)

    with _lock:
        out = model.generate(
            **inputs,
            max_new_tokens=MAX_NEW_TOKENS,
            do_sample=True,
            temperature=0.7,
            top_p=0.9
        )

    text = tokenizer.decode(out[0], skip_special_tokens=True)
    return jsonify({"response": text})

if __name__ == "__main__":
    app.run(debug=True, port=5000)
```

### 4.4 Frontend — `templates/index.html`

```html
<!doctype html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Chat con LLM (Flask)</title>
  <link rel="stylesheet" href="/static/style.css" />
</head>
<body>
  <main class="wrap">
    <h1>Chat con LLM</h1>

    <textarea id="prompt" placeholder="Escribe tu mensaje..."></textarea>
    <button id="btn">Enviar</button>

    <section class="panel">
      <h2>Respuesta</h2>
      <pre id="out">Listo ✅</pre>
    </section>
  </main>

  <script src="/static/script.js"></script>
</body>
</html>
```

### 4.5 JS — `static/script.js`

```js
const btn = document.getElementById("btn");
const promptEl = document.getElementById("prompt");
const out = document.getElementById("out");

btn.addEventListener("click", async () => {
  const prompt = promptEl.value.trim();
  if (!prompt) {
    out.textContent = "Escribe algo primero.";
    return;
  }

  out.textContent = "Generando...";

  try {
    const res = await fetch("/generate", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ prompt }),
    });

    const data = await res.json();
    if (!res.ok) throw new Error(data.error || "Error");

    out.textContent = data.response;
  } catch (err) {
    out.textContent = "Error: " + err.message;
  }
});
```

### 4.6 CSS — `static/style.css`

```css
body { font-family: Arial, sans-serif; margin: 0; padding: 0; }
.wrap { max-width: 900px; margin: 24px auto; padding: 0 16px; }
textarea { width: 100%; min-height: 140px; padding: 12px; font-size: 16px; }
button { margin-top: 10px; padding: 10px 14px; cursor: pointer; }
.panel { margin-top: 18px; border: 1px solid #ddd; padding: 12px; }
pre { white-space: pre-wrap; word-wrap: break-word; }
```

### 4.7 Cómo correr

```bash
python app.py
# abrir: http://localhost:5000
```

---


## 5) Preguntas de repaso (respuestas cortas)

1. **¿Qué hace un sistema experto basado en reglas?**
   Toma decisiones aplicando reglas IF–THEN sobre hechos/entradas; es explicable porque se puede justificar con “qué regla se activó”.

2. **¿Por qué usar lógica difusa?**
   Porque el mundo real tiene “grises”: permite decisiones graduales (no solo verdadero/falso).

3. **Diferencia entre discriminativo y generativo:**
   Discriminativo = clasifica/predice etiqueta; Generativo = crea datos nuevos. LLM es generativo para lenguaje.

4. **¿Qué rol cumple Flask aquí?**
   Publicar el modelo como un **servicio web** para que un frontend le envíe prompts y reciba respuestas.

---

## 6) Reflexión personal

Esta semana entendí que “IA” no es una sola cosa: puede ser reglas (explicable), lógica difusa (natural para control) o modelos generativos (potentes pero más costosos). Lo más valioso fue integrar lo aprendido en una app funcional y probarla como producto (entrada → proceso → salida).

---
