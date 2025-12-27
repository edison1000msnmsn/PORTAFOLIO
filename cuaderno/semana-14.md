---

---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)


# Semana 14 — Introducción a Python + Flask + App Inteligente (Llama 3)

## 1) ¿Qué se hizo esta semana?
Esta semana se trabajó **Python** como base para backend y sistemas inteligentes, con 3 partes:
1. **Python (POO):** clases, herencia y sobreescritura de métodos.
2. **Flask + MySQL:** una aplicación web simple para registrar estudiantes (formulario + guardar).
3. **App inteligente (LLM):** interfaz web para conversar con un modelo tipo **Llama 3** usando Flask.

---

## 2) Objetivos
- Dominar lo esencial de Python para backend (estructura, POO, módulos).
- Comprender Flask como microframework para levantar apps web ligeras.
- Conectar una app Flask con MySQL para registrar datos desde un formulario.
- Integrar un modelo LLM en una web simple (ruta `/generate`).

---

## 3) Teoría mínima (lo necesario)

### 3.1 Python en 1 idea
Python es un lenguaje interpretado, multiparadigma, con tipado dinámico. Es muy usado en backend, automatización y IA.

### 3.2 Flask (conceptos básicos)
- **Flask:** núcleo del framework.
- **Route (@app.route):** define URL → función.
- **request:** datos que envía el cliente (form o JSON).
- **render_template:** renderiza HTML usando plantillas.
- **debug=True:** reinicia y muestra errores en desarrollo.

---

## 4) Parte 1 — Ejercicio 01: POO (Persona y Estudiante)

### 4.1 Código base (POO)
```py
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad

    def presentarse(self):
        return f"Hola, soy {self.nombre} y tengo {self.edad} años."


class Estudiante(Persona):
    def __init__(self, nombre, edad, carrera):
        super().__init__(nombre, edad)
        self.carrera = carrera

    def estudiar(self):
        return f"{self.nombre} está estudiando {self.carrera}."

    def presentarse(self):
        # Sobrescritura del método
        return f"Hola, soy {self.nombre}, tengo {self.edad} años y estudio {self.carrera}."


# Ejemplo de uso
alumno = Estudiante("Laura", 20, "Ingeniería de Sistemas")
print(alumno.presentarse())
print(alumno.estudiar())
````

---

## 5) Parte 2 — Ejercicio 02: App Web en Flask + MySQL (Registro Estudiantes)

## 5.1 Requisitos

```bash
pip install flask pymysql
```

## 5.2 Base de datos y tabla

```sql
CREATE DATABASE escuela;
USE escuela;

CREATE TABLE estudiantes (
  IdEstudiante INT PRIMARY KEY AUTO_INCREMENT,
  nomEstudiante VARCHAR(100),
  dirEstudiante VARCHAR(150),
  ciuEstudiante VARCHAR(100)
);
```

## 5.3 Conexión a MySQL (conexion.py)

```py
import pymysql

def obtener_conexion():
    return pymysql.connect(
        host='localhost',
        user='root',
        password='tu_contraseña',
        db='escuela',
        cursorclass=pymysql.cursors.DictCursor
    )
```

## 5.4 Aplicación Flask (app.py)

```py
from flask import Flask, render_template, request, redirect
from conexion import obtener_conexion

app = Flask(__name__)

@app.route('/')
def formulario():
    return render_template('formulario.html')

@app.route('/guardar', methods=['POST'])
def guardar():
    nombre = request.form['nombre']
    direccion = request.form['direccion']
    ciudad = request.form['ciudad']

    conexion = obtener_conexion()
    with conexion.cursor() as cursor:
        cursor.execute(
            "INSERT INTO estudiantes(nomEstudiante, dirEstudiante, ciuEstudiante) VALUES (%s, %s, %s)",
            (nombre, direccion, ciudad)
        )
    conexion.commit()
    conexion.close()

    return redirect('/')

if __name__ == "__main__":
    app.run(debug=True)
```

## 5.5 Plantilla HTML (templates/formulario.html)

```html
<!DOCTYPE html>
<html>
<head>
  <title>Registro de Estudiantes</title>
</head>
<body>
  <h1>Agregar Estudiante</h1>

  <form action="/guardar" method="post">
    <label>Nombre:</label><br>
    <input type="text" name="nombre"><br>

    <label>Dirección:</label><br>
    <input type="text" name="direccion"><br>

    <label>Ciudad:</label><br>
    <input type="text" name="ciudad"><br><br>

    <input type="submit" value="Guardar">
  </form>
</body>
</html>
```

## 5.6 Ejecutar

```bash
python app.py
```

Abrir:

* `http://localhost:5000`

---

## 6) Parte 3 — App Inteligente: Web Chat con Llama 3 (Flask + Transformers)

> **Idea:** levantar una web con un textbox y un botón; el frontend manda un prompt y el backend devuelve la respuesta del modelo.

### 6.1 Estructura sugerida

```txt
llama_web_app/
├── app.py
├── templates/
│   └── index.html
├── static/
│   ├── style.css
│   └── script.js
└── .env
```

### 6.2 Dependencias

```bash
pip install torch transformers flask python-dotenv
```

### 6.3 Backend (app.py) — ruta `/generate`

```py
from flask import Flask, render_template, request, jsonify
from transformers import AutoTokenizer, AutoModelForCausalLM
from dotenv import load_dotenv
import torch
import os

load_dotenv()

app = Flask(__name__)

model_id = os.getenv("MODEL_ID", "meta-llama/Meta-Llama-3-8B-Instruct")

tokenizer = AutoTokenizer.from_pretrained(model_id)
model = AutoModelForCausalLM.from_pretrained(model_id, device_map="auto")

@app.route("/")
def index():
    return render_template("index.html")

@app.route("/generate", methods=["POST"])
def generate():
    prompt = request.json.get("prompt", "")
    inputs = tokenizer(prompt, return_tensors="pt").to(model.device)
    outputs = model.generate(**inputs, max_new_tokens=200)
    response = tokenizer.decode(outputs[0], skip_special_tokens=True)
    return jsonify({"response": response})

if __name__ == "__main__":
    app.run(debug=True)
```

### 6.4 Frontend (templates/index.html)

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Chat con Llama 3</title>
  <link rel="stylesheet" href="/static/style.css">
</head>
<body>
  <div id="chat-box">
    <textarea id="prompt" placeholder="Escribe tu mensaje..."></textarea>
    <button onclick="sendPrompt()">Enviar</button>
    <div id="response"></div>
  </div>

  <script src="/static/script.js"></script>
</body>
</html>
```

### 6.5 JS (static/script.js)

```js
async function sendPrompt() {
  const prompt = document.getElementById("prompt").value;
  const responseBox = document.getElementById("response");

  responseBox.innerHTML = "Generando respuesta...";

  const res = await fetch("/generate", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ prompt })
  });

  const data = await res.json();
  responseBox.innerHTML = data.response;
}
```

---

## 7) Evidencias para tu cuaderno 

* [ ] Captura de ejecución POO (Persona/Estudiante) en consola.
* [ ] Captura MySQL: tabla `estudiantes` + registros insertados.
* [ ] Captura del formulario Flask funcionando en navegador.
* [ ] Captura del chat Llama 3 generando respuesta (pantalla).
* [ ] Link de tu repo/commit donde está el código.

---

## 8) Conclusión 

En la semana 14 se consolidó Python como base para backend e IA, aplicando POO con herencia y sobreescritura de métodos. Luego se implementó una aplicación web ligera con Flask conectada a MySQL para registrar estudiantes mediante un formulario. Finalmente, se integró un modelo tipo Llama 3 en una interfaz web sencilla usando Flask y Transformers, logrando generar respuestas desde un endpoint `/generate` consumido por JavaScript.

---

