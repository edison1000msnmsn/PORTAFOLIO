---
layout: default
title: "Portada"
---

<!-- ===== Estilos específicos de la portada (ligeros, inline) ===== -->
<style>
  .hero{display:grid;grid-template-columns:120px 1fr;gap:20px;align-items:center;margin:20px 0 36px}
  .hero img{width:120px;height:120px;border-radius:50%;object-fit:cover;border:3px solid #e6edf3;box-shadow:0 2px 8px rgba(0,0,0,.15)}
  .hero h1{margin:0;font-size:2.2rem;line-height:1.2}
  .hero p{margin:.3rem 0 0;color:#57606a;font-size:1rem}
  .cta{display:flex;flex-wrap:wrap;gap:10px;margin:18px 0 10px}
  .btn{padding:8px 14px;border-radius:10px;border:1px solid #d0d7de;text-decoration:none;transition:all .2s ease}
  .btn:hover{background:#f6f8fa;transform:translateY(-1px)}
  .btn.primary{background:#0969da;color:#fff;border-color:#0969da}
  .grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:16px;margin:20px 0}
  .card{padding:16px;border:1px solid #d0d7de;border-radius:12px;background:#fff;transition:transform .2s ease,box-shadow .2s ease}
  .card:hover{transform:translateY(-3px);box-shadow:0 4px 12px rgba(0,0,0,.06)}
  .muted{color:#57606a}
  .kpi{display:flex;gap:16px;flex-wrap:wrap;margin-top:10px}
  .kpi div{background:#f6f8fa;border:1px solid #d0d7de;border-radius:10px;padding:10px 12px;font-size:.95rem}
  .timeline li{margin:.35rem 0}
  @media (min-width:900px){
    .split{display:grid;grid-template-columns:1.2fr .8fr;gap:30px;align-items:start}
  }
</style>

<div class="hero">
  <img src="{{ site.baseurl }}/PORTAFOLIO/profile.jpg" alt="Foto de Edison O. Huaire">
  <div>
    <h1>👋 Hola, soy <strong>Edison Orlando Huairé Maraví</strong></h1>
    <p>Estudiante de <strong>Ingeniería de Sistemas – UNCP</strong>.  
      Este es mi <strong>Portafolio Electrónico</strong> del curso <em>Desarrollo de Aplicaciones Web</em>.</p>

    <div class="cta">
      <a class="btn primary" href="{{ site.baseurl }}/cuaderno/">📘 Cuaderno (S1–S7)</a>
      <a class="btn" href="{{ site.baseurl }}/proyectos/">💻 Proyectos</a>
      <a class="btn" href="{{ site.baseurl }}/monografias/css-avanzado">📑 Monografía</a>
      <a class="btn" href="{{ site.baseurl }}/bibliografia">📚 Bibliografía</a>
      <a class="btn" href="{{ site.baseurl }}/reflexion-final">🧠 Reflexión final</a>
    </div>

    <div class="kpi">
      <div>✅ Semanas publicadas: <strong>7 / 16</strong></div>
      <div>📖 Monografía: <strong>CSS Avanzado</strong></div>
      <div>🗓 Próximo entregable: <strong>Consolidado 1 (Semana 8)</strong></div>
    </div>
  </div>
</div>

<hr/>

<div class="split">
  <section>
    <h2>🎯 Objetivos del portafolio</h2>
    <ul>
      <li>Registrar y evidenciar mis <strong>aprendizajes semanales</strong> (definiciones, prácticas, reflexiones).</li>
      <li>Documentar los <strong>proyectos desarrollados</strong> (repositorio, capturas, código fuente, aprendizajes).</li>
      <li>Integrar la <strong>Tarea Académica</strong>: Monografía <em>CSS Avanzado</em>.</li>
      <li>Preparar los entregables <strong>Consolidado 1 (S8)</strong> y <strong>Consolidado 2 (S16)</strong>.</li>
    </ul>

    <h2>🧭 Navegación rápida</h2>
    <div class="grid">
      <a class="card" href="{{ site.baseurl }}/cuaderno/">
        <h3>📘 Cuaderno por semanas</h3>
        <p class="muted">Fundamentos de la Web, HTML+CSS, CSS Avanzado, React y Hooks. Incluye evidencias y reflexiones.</p>
      </a>
      <a class="card" href="{{ site.baseurl }}/proyectos/">
        <h3>💻 Proyectos concluidos</h3>
        <p class="muted">ERP Jorge Basadre (SPA React/TS), dashboards y despliegues. Incluye repositorios y capturas.</p>
      </a>
      <a class="card" href="{{ site.baseurl }}/monografias/css-avanzado">
        <h3>📑 Monografía académica</h3>
        <p class="muted">“CSS Avanzado”: 10 secciones formales con formato IEEE y referencias académicas.</p>
      </a>
      <a class="card" href="{{ site.baseurl }}/bibliografia">
        <h3>📚 Bibliografía (IEEE)</h3>
        <p class="muted">Fuentes técnicas (libros y documentación oficial) utilizadas durante el curso.</p>
      </a>
    </div>
  </section>

  <aside>
    <h2>🗓 Línea de tiempo (Semanas 1–7)</h2>
    <ul class="timeline">
      <li><strong>S1:</strong> Fundamentos Web, DNS/HTTP, roles, VSC.</li>
      <li><strong>S2:</strong> HTML5 + CSS3, Flexbox, Grid, responsive.</li>
      <li><strong>S3–S5 (+S6):</strong> Exposiciones — <em>CSS Avanzado</em>.</li>
      <li><strong>S6:</strong> React: entorno (Node, npm), Vite/CRA, JSX.</li>
      <li><strong>S7:</strong> Componentes + Hooks (useState, useEffect, etc.).</li>
    </ul>

    <h2>📩 Contacto</h2>
    <p class="muted">
      <strong>GitHub:</strong>
      <a href="https://github.com/edison1000msnmsn" target="_blank">edison1000msnmsn</a><br/>

      <strong>Email académico:</strong> <em>e_2021200783B@uncp.edu.pe</em><br/>
      <strong>Nombre completo:</strong> Edison Orlando Huairé Maraví<br/>

      <strong>LinkedIn:</strong>
      <a href="https://pe.linkedin.com/in/edison-huaire-maravi-a39019275" target="_blank">Edison Huairé Maraví</a>
    </p>
  </aside>
</div>

<hr/>

<p class="muted">
  Sitio publicado con <strong>GitHub Pages</strong> (tema Cayman).  
  Última actualización automática tras cada <code>git push</code>.
</p>
