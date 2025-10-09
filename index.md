---
layout: default
title: "Portafolio"
---

<!-- ===== Overrides de estilo para Cayman (portada profesional) ===== -->
<style>
  /* Reemplaza el gradiente del header por una imagen con overlay */
  .page-header {
    background-image:
      linear-gradient(rgba(0,0,0,.45), rgba(0,0,0,.45)),
      url("https://siemprendes.com/wp-content/uploads/2024/11/desarrollo-de-aplicaciones-web.jpg");
    background-size: cover;
    background-position: center;
  }

  /* Contenido de la portada */
  .hero{display:grid;grid-template-columns:128px 1fr;gap:22px;align-items:center;margin:20px 0 36px}
  .hero img{width:128px;height:128px;border-radius:50%;object-fit:cover;border:3px solid #e6edf3;box-shadow:0 2px 10px rgba(0,0,0,.18)}
  .hero h1{margin:0 0 6px;font-size:2.1rem;line-height:1.2}
  .hero p{margin:.2rem 0 0;color:#57606a;font-size:1rem}

  .cta{display:flex;flex-wrap:wrap;gap:10px;margin:18px 0 8px}
  .btn{padding:10px 16px;border-radius:10px;border:1px solid #d0d7de;text-decoration:none;font-weight:600;color:#0f172a;background:#ffffff;display:inline-flex;align-items:center;gap:8px;transition:all .2s ease}
  .btn:hover{background:#f6f8fa;transform:translateY(-1px)}
  .btn.primary{background:#0b5ab8;color:#fff;border-color:#0b5ab8}
  .btn.primary:hover{background:#0a4ea1}

  .icon{width:18px;height:18px;display:inline-block;vertical-align:middle}

  .kpi{display:flex;gap:12px;flex-wrap:wrap;margin-top:10px}
  .kpi div{background:#f6f8fa;border:1px solid #d0d7de;border-radius:10px;padding:8px 12px;font-size:.95rem}

  .grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(270px,1fr));gap:16px;margin:22px 0}
  .card{padding:16px;border:1px solid #d0d7de;border-radius:12px;background:#fff;transition:transform .2s ease,box-shadow .2s ease;text-decoration:none;color:inherit}
  .card:hover{transform:translateY(-3px);box-shadow:0 4px 12px rgba(0,0,0,.07)}
  .muted{color:#57606a}
  .timeline li{margin:.4rem 0}
  @media (min-width:900px){.split{display:grid;grid-template-columns:1.3fr .7fr;gap:30px;align-items:start}}
</style>

<div class="hero">
  <!-- Foto por URL (nota: LinkedIn puede rotar la URL en el futuro) -->
  <img src="https://media.licdn.com/dms/image/v2/D4D03AQEJlDo21zm3-Q/profile-displayphoto-shrink_800_800/profile-displayphoto-shrink_800_800/0/1683091933866?e=1762992000&v=beta&t=RgkgznRs4TGl2uK-4HD_HxP5ZrqZ87rHKP0iYG47JGY"
       alt="Foto de Edison O. Huaire">
  <div>
    <h1>Hola, soy <strong>Edison Orlando Huaire Maravi</strong></h1>
    <p>Estudiante de <strong>Ingeniería de Sistemas – UNCP</strong>. Este es mi
      <strong>Portafolio Electrónico</strong> del curso <em>Desarrollo de Aplicaciones Web</em>.</p>

    <div class="cta">
      <a class="btn primary" href="{{ site.baseurl }}/cuaderno/">
        <!-- libro -->
        <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M6 4h11a2 2 0 0 1 2 2v12a1 1 0 0 1-1.45.89L15 17.76l-2.55 1.13A1 1 0 0 1 11 18V6a2 2 0 0 0-2-2H6z"/></svg>
        Cuaderno (S1–S7)
      </a>
      <a class="btn" href="{{ site.baseurl }}/proyectos/">
        <!-- laptop -->
        <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M4 6h16v9H4zM2 17h20v2H2z"/></svg>
        Proyectos
      </a>
      <a class="btn" href="{{ site.baseurl }}/monografias/css-avanzado">
        <!-- documento -->
        <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M14 2H6a2 2 0 0 0-2 2v16l4-2 4 2 4-2 4 2V8z"/></svg>
        Monografía
      </a>
      <a class="btn" href="{{ site.baseurl }}/bibliografia">
        <!-- libro abierto -->
        <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M12 6c-2-2-6-2-8 0v12c2-2 6-2 8 0 2-2 6-2 8 0V6c-2-2-6-2-8 0z"/></svg>
        Bibliografía
      </a>
      <a class="btn" href="{{ site.baseurl }}/reflexion-final">
        <!-- cerebro simple -->
        <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M7 9a3 3 0 0 1 6 0v6H9a2 2 0 0 1-2-2V9zm6 0a3 3 0 1 1 6 0v4a2 2 0 0 1-2 2h-4V9z"/></svg>
        Reflexión final
      </a>
    </div>

    <div class="kpi">
      <div>Semanas publicadas: <strong>7 / 16</strong></div>
      <div>Monografía: <strong>CSS Avanzado</strong></div>
      <div>Próximo entregable: <strong>Consolidado 1 (Semana 8)</strong></div>
    </div>
  </div>
</div>

<hr/>

<div class="split">
  <section>
    <h2>Objetivos del portafolio</h2>
    <ul>
      <li>Evidenciar mis <strong>aprendizajes semanales</strong> (definiciones, prácticas, reflexiones).</li>
      <li>Documentar <strong>proyectos desarrollados</strong> (repos, capturas, código y aprendizajes).</li>
      <li>Integrar la <strong>Tarea Académica</strong> (Monografía: <em>CSS Avanzado</em>).</li>
      <li>Planificar los entregables <strong>Consolidado 1 (S8)</strong> y <strong>Consolidado 2 (S16)</strong>.</li>
    </ul>

    <h2>Navegación rápida</h2>
    <div class="grid">
      <a class="card" href="{{ site.baseurl }}/cuaderno/">
        <h3>Cuaderno por semanas</h3>
        <p class="muted">Fundamentos de la Web, HTML+CSS, CSS Avanzado, React y Hooks con evidencias.</p>
      </a>
      <a class="card" href="{{ site.baseurl }}/proyectos/">
        <h3>Proyectos concluidos</h3>
        <p class="muted">ERP Jorge Basadre (SPA React/TS), despliegues y documentación.</p>
      </a>
      <a class="card" href="https://turismochupaca.com/" target="_blank" rel="noopener">
        <h3>Proyecto personal: turismochupaca.com</h3>
        <p class="muted">Sitio público en producción. Enlace externo.</p>
      </a>
      <a class="card" href="{{ site.baseurl }}/monografias/css-avanzado">
        <h3>Monografía académica</h3>
        <p class="muted">10 secciones formales con formato IEEE y bibliografía.</p>
      </a>
    </div>
  </section>

  <aside>
    <h2>Línea de tiempo (Semanas 1–7)</h2>
    <ul class="timeline">
      <li><strong>S1:</strong> Fundamentos Web, DNS/HTTP, roles, VSC.</li>
      <li><strong>S2:</strong> HTML5 + CSS3, Flexbox, Grid, responsive.</li>
      <li><strong>S3–S5 (+S6):</strong> Exposiciones — CSS Avanzado.</li>
      <li><strong>S6:</strong> React: entorno (Node, npm), Vite/CRA, JSX.</li>
      <li><strong>S7:</strong> Componentes + Hooks (useState, useEffect, etc.).</li>
    </ul>

    <h2>Contacto</h2>
    <p class="muted">
      <strong>Nombre completo:</strong> Edison Orlando Huaire Maravi<br/>
      <strong>Email académico:</strong> <a href="mailto:e_2021200783B@uncp.edu.pe">e_2021200783B@uncp.edu.pe</a><br/>
      <strong>Email personal:</strong> <a href="mailto:edison10huaire@gmail.com">edison10huaire@gmail.com</a><br/>
      <strong>GitHub:</strong> <a href="https://github.com/edison1000msnmsn" target="_blank">edison1000msnmsn</a><br/>
      <strong>LinkedIn:</strong> <a href="https://pe.linkedin.com/in/edison-huaire-maravi-a39019275" target="_blank">Edison Huaire Maravi</a>
    </p>
  </aside>
</div>

<hr/>

<p class="muted">
  Sitio publicado con <strong>GitHub Pages</strong> (tema Cayman).  
  Última actualización automática tras cada <code>git push</code>.
</p>
