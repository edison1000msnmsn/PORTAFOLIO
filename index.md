---
layout: default
title: "Portafolio"
---

<!-- ===== Overrides de estilo (Cayman) ===== -->
<style>
  /* Header con imagen de fondo + overlay */
  .page-header{
    background-image:
      linear-gradient(rgba(0,0,0,.45), rgba(0,0,0,.45)),
      url("https://siemprendes.com/wp-content/uploads/2024/11/desarrollo-de-aplicaciones-web.jpg");
    background-size: cover;
    background-position: center;
  }

  /* Colores principales en azul */
  h1, h2, h3 { color:#0b5ab8 !important; }
  a { color:#0b5ab8; }

  /* Hero */
  .hero{display:grid;grid-template-columns:128px 1fr;gap:22px;align-items:center;margin:20px 0 30px}
  .hero img{width:128px;height:128px;border-radius:50%;object-fit:cover;border:3px solid #e6edf3;box-shadow:0 2px 10px rgba(0,0,0,.18)}
  .hero h1{margin:0 0 6px;font-size:2.1rem;line-height:1.2}
  .hero p{margin:.25rem 0 0;color:#57606a}

  /* Botones: todos azules */
  .cta{display:flex;flex-wrap:wrap;gap:10px;margin:18px 0 0}
  .btn{padding:10px 16px;border-radius:10px;border:1px solid #0b5ab8;text-decoration:none;
       font-weight:600;color:#fff;background:#0b5ab8;display:inline-flex;align-items:center;gap:8px;
       transition:all .2s ease}
  .btn:hover{filter:brightness(.95);transform:translateY(-1px)}
  .icon{width:18px;height:18px;display:inline-block;vertical-align:middle}

  /* Tarjetas navegación */
  .grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(270px,1fr));gap:16px;margin:22px 0}
  .card{padding:16px;border:1px solid #d0d7de;border-radius:12px;background:#fff;
        transition:transform .2s ease,box-shadow .2s ease;text-decoration:none;color:inherit}
  .card:hover{transform:translateY(-3px);box-shadow:0 4px 12px rgba(0,0,0,.07)}
  .muted{color:#57606a}

  @media (min-width:900px){
    .split{display:grid;grid-template-columns:1.1fr .9fr;gap:30px;align-items:start}
  }
</style>

<div class="hero">
  <!-- Foto por URL (LinkedIn) -->
  <img src="https://media.licdn.com/dms/image/v2/D4D03AQEJlDo21zm3-Q/profile-displayphoto-shrink_800_800/profile-displayphoto-shrink_800_800/0/1683091933866?e=1762992000&v=beta&t=RgkgznRs4TGl2uK-4HD_HxP5ZrqZ87rHKP0iYG47JGY"
       alt="Foto de Edison O. Huaire">
  <div>
    <h1>Hola, soy <strong>Edison Orlando Huaire Maravi</strong></h1>
    <p>Estudiante de <strong>Ingeniería de Sistemas – UNCP</strong>. Este es mi
      <strong>Portafolio Electrónico</strong> del curso <em>Desarrollo de Aplicaciones Web</em>.</p>

    <div class="cta">
      <a class="btn" href="{{ site.baseurl }}/cuaderno/">
        <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M6 4h11a2 2 0 0 1 2 2v12a1 1 0 0 1-1.45.89L15 17.76l-2.55 1.13A1 1 0 0 1 11 18V6a2 2 0 0 0-2-2H6z"/></svg>
        Cuaderno (S1–S7)
      </a>
      <a class="btn" href="{{ site.baseurl }}/proyectos/">
        <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M4 6h16v9H4zM2 17h20v2H2z"/></svg>
        Proyectos
      </a>
      <a class="btn" href="{{ site.baseurl }}/monografias/css-avanzado">
        <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M14 2H6a2 2 0 0 0-2 2v16l4-2 4 2 4-2 4 2V8z"/></svg>
        Monografía
      </a>
      <a class="btn" href="{{ site.baseurl }}/bibliografia">
        <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M12 6c-2-2-6-2-8 0v12c2-2 6-2 8 0 2-2 6-2 8 0V6c-2-2-6-2-8 0z"/></svg>
        Bibliografía
      </a>
      <a class="btn" href="{{ site.baseurl }}/reflexion-final">
        <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M7 9a3 3 0 0 1 6 0v6H9a2 2 0 0 1-2-2V9zm6 0a3 3 0 1 1 6 0v4a2 2 0 0 1-2 2h-4V9z"/></svg>
        Reflexión final
      </a>
    </div>
  </div>
</div>

<div class="split">
  <section>
    <h2>Sobre mí</h2>
    <p class="muted">
      Me considero una persona <strong>responsable</strong>, <strong>creativa</strong> y <strong>curiosa</strong>.
      Me gusta aprender haciendo, documentar y compartir resultados.
    </p>
    <h3>Actualmente estoy aprendiendo</h3>
    <ul>
      <li><strong>HTML, CSS y JavaScript</strong> (maquetación semántica, responsive, buenas prácticas).</li>
      <li><strong>Git y GitHub</strong> (flujo de trabajo, ramas, issues, GitHub Pages).</li>
      <li><strong>Desarrollo de aplicaciones web</strong> con enfoque en <strong>React</strong> y herramientas modernas.</li>
    </ul>

    <h2>Navegación rápida</h2>
    <div class="grid">
      <a class="card" href="{{ site.baseurl }}/cuaderno/">
        <h3>Cuaderno por semanas</h3>
        <p class="muted">Definiciones, resultados de laboratorio y reflexiones (S1–S7).</p>
      </a>
        <a class="card" href="{{ site.baseurl }}/proyectos/" aria-label="Ver proyectos concluidos y en progreso">
        <h3>Proyectos</h3>
        <p class="muted">Trabajos concluidos y proyectos en progreso disponibles en la web.</p>
        </a>

        <a class="card" href="{{ site.baseurl }}/monografias/css-avanzado" aria-label="Monografías: CSS Avanzado y trabajos de otros grupos">
        <h3>Monografías</h3>
        <p class="muted">Mi monografía grupal sobre CSS Avanzado y las de otros grupos.</p>
        </a>

      <a class="card" href="{{ site.baseurl }}/bibliografia">
        <h3>Bibliografía</h3>
        <p class="muted">Fuentes y/o bibliografia utilizadas en el curso.</p>
      </a>
    </div>
  </section>

  <aside>
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
