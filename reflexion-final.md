---
layout: default
title: "Reflexión final"
permalink: /reflexion-final/
---

<!-- Header: imagen específica para esta página -->
<style>
  .page-header{
    background-image:
      linear-gradient(rgba(0,0,0,.55), rgba(0,0,0,.55)),
      url("https://0701.static.prezi.com/preview/v2/mbfep2veof36phuudtonwd5fqh6jc3sachvcdoaizecfr3dnitcq_3_0.png");
    background-size: cover;
    background-position: center;
    color:#fff !important;
  }
  .project-name,.project-tagline{color:#fff !important;}
  .muted{color:#4b5563}
  .kpi{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:12px;margin:12px 0}
  .kpi>div{border:1px solid #d1d5db;border-radius:10px;padding:10px 12px;background:#fff}
</style>

[← Volver al Inicio del Portafolio]({{ site.baseurl }}/)

# Reflexión final (actualizada hasta Semana 15)

**¿Qué aprendí?**  
A lo largo del curso consolidé un recorrido completo de desarrollo web: **fundamentos web** y maquetación, **CSS avanzado** (Flexbox, Grid, responsive, cascada y especificidad), **JavaScript** para interacción y consumo de servicios, y el uso de **React** (componentes, props, estado y hooks).  
En el segundo tramo del curso reforcé el **backend** con prácticas reales: **Java/Spring Boot** (CRUD con MySQL, pruebas con **Postman** y documentación con **Swagger**), **PHP/Laravel** (MVC + migraciones + Eloquent + Blade/Tailwind), y **Python/Flask** (formularios, rutas y conexión a MySQL). Finalmente, integré contenido de **sistemas inteligentes**, trabajando con un **LLM tipo Llama** en una app web y prácticas de enfoque inteligente.

**¿Cómo aprendí?**  
Alternando teoría puntual con **laboratorios**, prácticas guiadas y ejercicios aplicados. La clave fue repetir el ciclo: **configurar → implementar → probar → documentar**.  
Todo quedó registrado en el portafolio: definiciones en mis palabras, pasos, errores comunes, endpoints y evidencias (capturas/commits).

**¿Qué desafíos enfrenté?**  
- **CSS (cascada y especificidad)** → lo resolví ordenando estilos, usando clases consistentes y evitando reglas innecesarias.  
- **Responsive real** → probé en varios anchos (mobile/desktop) y ajusté con Grid/Flex + breakpoints.  
- **APIs (errores 400/404/500 y CORS/CSRF)** → aprendí a depurar con Postman/Swagger, revisar rutas y estructurar mejor las respuestas.  
- **Entorno y dependencias** (JDK/Tomcat, MySQL, Composer, pip, npm) → mejoré mi forma de instalar, verificar versiones y documentar configuración.  
- **IA en local (LLM)** → entendí limitaciones de recursos y cómo exponer el modelo vía endpoint (`/generate`) desde Flask.

**¿Qué logros obtuve?**  
- **Cuaderno completo hasta Semana 15** (teoría + práctica + reflexión).  
- **CRUD Estudiante** (Spring Boot + MySQL) con pruebas en Postman.  
- **CRUD Docente** con endpoints extra + **Swagger UI** + manejo de validaciones/errores.  
- **Backend PHP/Laravel** con migraciones, controlador, rutas y vista Blade con Tailwind.  
- **Backend Python/Flask** + MySQL y una **app inteligente** integrando un LLM tipo Llama.  
- Portafolio ordenado para presentar (navegación clara y evidencias).

**¿Cómo aplicaré lo aprendido?**  
- Publicar proyectos en GitHub con estándar mínimo: **README + capturas + instrucciones + deploy**.  
- Usar **Issues y ramas** para planificar y dejar trazabilidad real.  
- Mantener el enfoque “producto”: **que funcione**, que esté probado y documentado.  
- Profundizar en backend: validaciones, seguridad, pruebas y despliegue.  
- Integrar IA de forma responsable: endpoints claros, límites de recursos y buenas prácticas.

---

## Evidencias breves (hasta S15)
<div class="kpi">
  <div><strong>Cuaderno (S1–S15):</strong> definiciones propias, pasos de laboratorio y evidencias.</div>
  <div><strong>Java/Spring:</strong> CRUDs + Swagger/Postman + MySQL.</div>
  <div><strong>PHP/Laravel:</strong> MVC + migraciones + Eloquent + Blade/Tailwind.</div>
  <div><strong>Python/Flask + IA:</strong> CRUD + app inteligente con LLM.</div>
</div>
