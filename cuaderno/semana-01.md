
---

---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)

# Semana 1 — Fundamentos de la Web

## 1) Fundamentos de las tecnologías web
En esta primera semana comprendí cómo funciona la Web desde su arquitectura base:  
la comunicación entre un **cliente (navegador)** y un **servidor**, mediada por **HTTP/HTTPS** y **DNS**.

**Conceptos clave**
- **DNS:** traduce `www.ejemplo.com` a una dirección IP.
- **HTTP/HTTPS:** protocolo de solicitud (**request**) y respuesta (**response**).
- **Frontend:** HTML, CSS, JS en el navegador.
- **Backend:** lógica y datos en el servidor (Node.js, PHP, .NET, etc.).
- **Fullstack:** combina frontend y backend.

**Flujo mínimo**
```text
[Navegador]
   ↓ (HTTP Request)
Servidor Web ↔ Base de datos
   ↑ (HTTP Response)
[HTML + CSS + JS]
````

## 2) Herramientas de trabajo (VSC) y atajos

* Editor: **Visual Studio Code** con extensiones: *Live Server*, *Prettier*, *GitLens*.
* **Emmet** para acelerar la maquetación.

**Ejemplo Emmet**

```html
ul>li*3>a[href="#"]{Enlace $}
```

**Resultado**

```html
<ul>
  <li><a href="#">Enlace 1</a></li>
  <li><a href="#">Enlace 2</a></li>
  <li><a href="#">Enlace 3</a></li>
</ul>
```


## 3) Control de versiones (Git/GitHub)

Comandos básicos practicados:

```bash
git init
git add .
git commit -m "Primer commit - inicio del cuaderno web"
```


## 4) Resultados de laboratorio

* Reconocimiento de **VSC** y creación de snippets.
* Inicialización de **Git** y primer commit.
* Visualización con **Live Server**.

## 5) Reflexión

Comprendí la relación **cliente–servidor** y el papel de **HTTP/HTTPS** y **DNS**.
Mi objetivo inmediato es dominar **atajos de VSC**, usar **Emmet** con soltura y mantener repos bien organizados con **Git**.


