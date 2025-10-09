---
layout: default
title: "Portafolio"
---

<!-- ===== Estilos mejorados de la portada ===== -->
<style>
  /* ==== CABECERA ==== */
  .page-header {
    background-image:
      linear-gradient(rgba(0,0,0,.55), rgba(0,0,0,.55)),
      url("https://siemprendes.com/wp-content/uploads/2024/11/desarrollo-de-aplicaciones-web.jpg");
    background-size: cover;
    background-position: center;
    color: #fff !important;
  }
  .project-name, .project-tagline { color: #fff !important; }

  /* ==== PALETA PROFESIONAL ==== */
  :root {
    --primary: #2563eb;        /* azul índigo profesional */
    --primary-dark: #1e4fd4;
    --text-muted: #4b5563;     /* gris neutro */
    --card-border: #d1d5db;
  }

  h1, h2, h3 { color: var(--primary); }
  a { color: var(--primary); }

  /* ==== HERO ==== */
  .hero {
    display: grid;
    grid-template-columns: 160px 1fr;
    gap: 24px;
    align-items: center;
    margin: 24px 0 34px;
  }
  .hero img {
    width: 160px; height: 160px;
    border-radius: 50%;
    object-fit: cover;
    border: 3px solid #fff;
    box-shadow: 0 4px 16px rgba(0,0,0,0.25);
  }
  .hero h1 { margin: 0 0 6px; font-size: 2.1rem; line-height: 1.2; }
  .hero p { margin: .3rem 0 0; color: var(--text-muted); }

  /* ==== BOTONES ==== */
  .cta {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    margin: 20px 0 0;
  }
  .btn {
    padding: 11px 18px;
    border-radius: 10px;
    border: none;
    text-decoration: none;
    font-weight: 600;
    color: #fff;
    background: var(--primary);
    display: inline-flex;
    align-items: center;
    gap: 8px;
    transition: background .2s ease, transform .2s ease, box-shadow .2s ease;
  }
  .btn:hover {
    background: var(--primary-dark);
    transform: translateY(-1px);
    box-shadow: 0 3px 8px rgba(0,0,0,0.15);
  }
  .icon { width: 18px; height: 18px; display: inline-block; vertical-align: middle; }

  /* ==== TARJETAS ==== */
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(270px, 1fr));
    gap: 16px;
    margin: 22px 0;
  }
  .card {
    padding: 16px;
    border: 1px solid var(--card-border);
    border-radius: 12px;
    background: #fff;
    transition: transform .2s ease, box-shadow .2s ease;
    text-decoration: none;
    color: inherit;
  }
  .card:hover {
    transform: translateY(-3px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.07);
  }
  .muted { color: var(--text-muted); }

  @media (min-width: 900px) {
    .split { display: grid; grid-template-columns: 1.1fr .9fr; gap: 30px; align-items: start; }
  }
</style>

<main class="content">

  <div class="hero">
    <img src="https://media.licdn.com/dms/image/v2/D4D03AQEJlDo21zm3-Q/profile-displayphoto-shrink_800_800/profile-displayphoto-shrink_800_800/0/1683091933866?e=1762992000&v=beta&t=RgkgznRs4TGl2uK-4HD_HxP5ZrqZ87rHKP0iYG47JGY"
         alt="Foto de Edison O. Huaire">
    <div>
      <h1>Edison Orlando Huaire Maravi</h1>
      <p>Estudiante de <strong>Ingeniería de Sistemas – UNCP</strong>. Este es mi
        <strong>Portafolio Electrónico</strong> del curso <em>Desarrollo de Aplicaciones Web</em>.
      </p>

      <div class="cta">
        <!-- === NUEVO BOTÓN: SOBRE MÍ === -->
        <a class="btn" href="{{ site.baseurl }}/sobre-mi/">
          <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M12 12a4 4 0 1 0-4-4 4 4 0 0 0 4 4Zm0 2c-3.31 0-6 1.34-6 3v1h12v-1c0-1.66-2.69-3-6-3Z"/></svg>
          Sobre mí
        </a>

        <a class="btn" href="{{ site.baseurl }}/cuaderno/">
          <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M6 4h11a2 2 0 0 1 2 2v12a1 1 0 0 1-1.45.89L15 17.76l-2.55 1.13A1 1 0 0 1 11 18V6a2 2 0 0 0-2-2H6z"/></svg>
          Cuaderno (S1–S7)
        </a>

        <a class="btn" href="{{ site.baseurl }}/proyectos/">
          <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M4 6h16v9H4zM2 17h20v2H2z"/></svg>
          Proyectos
        </a>

        <a class="btn" href="{{ site.baseurl }}/monografias/">
          <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M14 2H6a2 2 0 0 0-2 2v16l4-2 4 2 4-2 4 2V8z"/></svg>
          Monografía
        </a>

        <a class="btn" href="{{ site.baseurl }}/bibliografia/">
          <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M12 6c-2-2-6-2-8 0v12c2-2 6-2 8 0 2-2 6-2 8 0V6c-2-2-6-2-8 0z"/></svg>
          Bibliografía
        </a>

        <a class="btn" href="{{ site.baseurl }}/reflexion-final/">
          <svg class="icon" viewBox="0 0 24 24" fill="currentColor"><path d="M7 9a3 3 0 0 1 6 0v6H9a2 2 0 0 1-2-2V9zm6 0a3 3 0 1 1 6 0v4a2 2 0 0 1-2 2h-4V9z"/></svg>
          Reflexión final
        </a>
      </div>
    </div>
  </div>

  <div class="split">
    <section>
      <h2>Resumen</h2>
      <p class="muted">
        Portafolio académico desarrollado para el curso de <strong>Desarrollo de Aplicaciones Web</strong>.
        Aquí recopilo mis prácticas, proyectos, monografía y reflexiones del ciclo.
      </p>

      <h2>Navegación rápida</h2>
      <div class="grid">
        <a class="card" href="{{ site.baseurl }}/cuaderno/">
          <h3>Cuaderno por semanas</h3>
          <p class="muted">Definiciones, laboratorios y reflexiones (S1–S7).</p>
        </a>
        <a class="card" href="{{ site.baseurl }}/proyectos/">
          <h3>Proyectos concluidos</h3>
          <p class="muted">ERP Jorge Basadre, Turismo Chupaca, y más.</p>
        </a>
        <a class="card" href="{{ site.baseurl }}/monografias/css-avanzado">
          <h3>Monografía</h3>
          <p class="muted">Trabajo académico CSS Avanzado.</p>
        </a>
        <a class="card" href="{{ site.baseurl }}/bibliografia/">
          <h3>Bibliografía</h3>
          <p class="muted">Fuentes técnicas y académicas consultadas.</p>
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
</main>
