````md
# Portafolio Electrónico — Desarrollo de Aplicaciones Web

**Autor:** Edison Orlando Huaire Maravi  
**Universidad:** UNCP • **Curso:** Desarrollo de Aplicaciones Web  
**Sitio público (GitHub Pages):** `https://edison1000msnmsn.github.io/PORTAFOLIO/`

## 1) ¿Qué es este portafolio?

Repositorio que documenta mi avance en el curso **Desarrollo de Aplicaciones Web**. Incluye:

- **Cuaderno semanal (S1–S15):** definiciones en mis palabras, resultados de laboratorio, prácticas y reflexiones.
- **Back-end (prácticas):** CRUD con **Java/Spring Boot** + **MySQL**, pruebas con **Postman** y documentación con **Swagger**.
- **Back-end (PHP/Laravel):** MVC, migraciones, Eloquent, Blade + Tailwind.
- **Back-end (Python/Flask):** formularios, rutas, conexión a MySQL.
- **IA / Sistemas inteligentes:** mini app web integrando un **LLM tipo Llama** (Flask + endpoint `/generate`) y prácticas relacionadas.
- **Monografías / Tarea académica:** CSS avanzado.
- **Bibliografía (formato IEEE)** y **reflexión final (actualizada hasta Semana 15)**.

El sitio está construido con **Jekyll** (tema *Cayman*) y publicado con **GitHub Pages**.

---

## 2) Estructura del repositorio

```text
PORTAFOLIO/
├─ _config.yml                 # Configuración Jekyll (title, baseurl, tema)
├─ index.md                    # Portada del portafolio (foto, CTA y tarjetas)
├─ sobre-mi.md                 # Perfil y contacto (o /sobre-mi/index.md)
├─ bibliografia.md             # Fuentes (IEEE)
├─ reflexion-final.md          # Cierre del curso (actualizado hasta S15)
│
├─ cuaderno/                   # Bitácora por semanas
│  ├─ index.md                 # Índice del cuaderno
│  ├─ semana-01.md             # Fundamentos de la Web
│  ├─ semana-02.md             # HTML5 + CSS básico (demos embebidas)
│  ├─ semana-03.md             # HTML avanzado + CSS básico (exposiciones)
│  ├─ semana-04.md             # CSS avanzado + Bootstrap
│  ├─ semana-05.md             # JavaScript básico y avanzado (demos)
│  ├─ semana-06.md             # Introducción a React (CDN + Vite)
│  ├─ semana-07.md             # Componentes y Hooks (demos React)
│  ├─ semana-09.md             # Teoría Backend Java/JSP/Tomcat/Maven
│  ├─ semana-10.md             # Práctica: CRUD Estudiante (Spring Boot + MySQL + Postman)
│  ├─ semana-11.md             # Práctica: CRUD Docente (Swagger + Postman + endpoints extra)
│  ├─ semana-12.md             # Teoría Backend PHP (Apache + PHP + Composer)
│  ├─ semana-13.md             # Práctica: CRUD Laravel (MySQL + Blade/Tailwind)
│  ├─ semana-14.md             # Python + Flask (CRUD) + app inteligente (LLM tipo Llama)
│  └─ semana-15.md             # Evaluación/Proyecto inteligente (enfoque del curso)
│
├─ monografias/
│  ├─ index.md                 # Índice de monografías
│  └─ css-avanzado.md          # Trabajo académico principal
│
├─ proyectos/
│  ├─ index.md                 # Tarjetas de proyectos
│  ├─ erp-jb.md                # “ERP Jorge Basadre” (ficha técnica)
│  └─ turismo_chupaca.md       # “Turismo Chupaca” (ficha técnica)
│
└─ assets/                     # Evidencias (imágenes, capturas)
   ├─ semana01/ ...            # Carpeta por semana (si aplica)
   ├─ semana09/ ...            # Evidencias Tomcat/JDK/Maven (si aplica)
   ├─ semana10/ ...            # Evidencias Postman/CRUD Estudiante
   ├─ semana11/ ...            # Evidencias Swagger/CRUD Docente
   ├─ semana12/ ...            # Evidencias Apache/PHP/Composer
   ├─ semana13/ ...            # Evidencias Laravel (migrate/form)
   ├─ semana14/ ...            # Evidencias Flask + LLM
   ├─ semana15/ ...            # Evidencias del parcial/proyecto inteligente
   ├─ erp-jb/ ...              # Capturas del ERP
   └─ proyectos/ ...           # Otras imágenes
````

> **Nota:** En páginas que usan bloques HTML con Markdown dentro, se puede usar `markdown="1"` para que Jekyll procese el Markdown correctamente dentro de un `<div>`.

---

## 3) Navegación del sitio

* **Portada:** `index.md`
  Enlaces rápidos a **Sobre mí**, **Proyectos**, **Cuaderno**, **Monografías**, **Bibliografía**, **Reflexión final**.

* **Cuaderno:** `cuaderno/index.md`
  Enlaces a **S1–S15** con teoría, prácticas (CRUDs) y evidencias.

* **Proyectos:** `proyectos/index.md`
  Tarjetas que llevan a fichas técnicas:

  * `/proyectos/erp-jb/`
  * `/proyectos/turismo-chupaca/`

* **Monografías:** `monografias/index.md` → `css-avanzado.md`

* **Bibliografía:** `bibliografia.md`

* **Reflexión final:** `reflexion-final.md`

---

## 4) Publicación con GitHub Pages

* **Rama:** `main`

* **Ruta pública:** `https://edison1000msnmsn.github.io/PORTAFOLIO/`

* En `_config.yml`:

  ```yml
  title: "Portafolio – Edison H."
  theme: jekyll-theme-cayman
  baseurl: "/PORTAFOLIO"   # importante para que los enlaces funcionen
  url: "https://edison1000msnmsn.github.io"
  ```

* Usar `{{ site.baseurl }}` en enlaces internos, por ejemplo:

  * `{{ site.baseurl }}/cuaderno/`
  * `{{ site.baseurl }}/proyectos/erp-jb/`

> Sugerencia: tras cada cambio, `git add . && git commit -m "..." && git push`. Pages se reconstruye automáticamente.

---

## 5) Estándares y convenciones

* **Front matter** en cada `.md`:

  ```md
  ---
  layout: default
  title: "Título de la página"
  permalink: /ruta-deseada/     # opcional, útil para rutas limpias
  ---
  ```

* **Rutas limpias** en proyectos:

  * `erp-jb.md` → `permalink: /proyectos/erp-jb/`
  * `turismo_chupaca.md` → `permalink: /proyectos/turismo-chupaca/`

* **Estilos locales:** páginas como portada y fichas usan `<style>...</style>` con clases específicas para no chocar con el tema.

* **Accesibilidad y SEO:** uso de etiquetas semánticas, `alt` en imágenes y títulos claros por sección.

---

## 6) Cómo agregar una nueva semana

1. Crear archivo en `cuaderno/semana-XX.md` con:

   ```md
   ---
   layout: default
   title: "Semana XX — Tema"
   permalink: /cuaderno/semana-XX/
   ---
   [← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)
   # Semana XX — Tema
   ## Definiciones
   ...
   ```

2. Añadir la tarjeta/enlace en `cuaderno/index.md`.

3. Subir evidencias (imágenes) a `assets/semanaXX/` y referenciar con:

   * `{{ site.baseurl }}/assets/semanaXX/mi-captura.png`

---

## 7) Cómo agregar un nuevo proyecto

1. Crear `proyectos/mi-proyecto.md` con:

   ```md
   ---
   layout: default
   title: "Mi Proyecto — Ficha técnica"
   permalink: /proyectos/mi-proyecto/
   ---
   ```

2. Añadir tarjeta en `proyectos/index.md` enlazando a:

   * `{{ site.baseurl }}/proyectos/mi-proyecto/`

3. Guardar capturas en `assets/proyectos/mi-proyecto/` y referenciarlas desde la ficha.

---

## 8) Material didáctico incluido

* **Semana 1–5:** demos HTML/CSS/JS embebidas (render y código fuente).
* **Semana 6–7:** demos **React 18** con **Babel** (CDN) para JSX en la página, además de ejemplos de estructura **Vite**.
* **Semana 9–15:** backend y prácticas aplicadas:

  * Java/Spring + MySQL + Swagger/Postman
  * PHP/Laravel + MySQL + Blade/Tailwind
  * Python/Flask + MySQL + LLM tipo Llama
* **Monografía CSS Avanzado:** capítulos con referencias en formato **IEEE**.

---

## 9) Contacto

* **Nombre completo:** Edison Orlando Huaire Maravi
* **Email académico:** [e_2021200783B@uncp.edu.pe](mailto:e_2021200783B@uncp.edu.pe)
* **Email personal:** [edison10huaire@gmail.com](mailto:edison10huaire@gmail.com)
* **GitHub:** [https://github.com/edison1000msnmsn](https://github.com/edison1000msnmsn)
* **LinkedIn:** [https://pe.linkedin.com/in/edison-huaire-maravi-a39019275](https://pe.linkedin.com/in/edison-huaire-maravi-a39019275)

```
::contentReference[oaicite:0]{index=0}
```
