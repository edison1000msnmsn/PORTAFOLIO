---
layout: default
title: "Proyectos concluidos"
---

<style>
  .page-header{
    background-image:
      linear-gradient(rgba(0,0,0,.55), rgba(0,0,0,.55)),
      url("https://ninjatalentweb.s3.eu-west-1.amazonaws.com/uploads/2023/01/12155733/python.png");
    background-size: cover;
    background-position: center;
    color:#fff !important;
  }
  .project-name,.project-tagline{color:#fff !important;}

  /* Tarjetas */
  .cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(270px,1fr));gap:16px;margin:18px 0}
  .card{border:1px solid #d1d5db;border-radius:12px;padding:16px;background:#fff;text-decoration:none;color:inherit;transition:transform .2s,box-shadow .2s}
  .card:hover{transform:translateY(-3px);box-shadow:0 4px 14px rgba(0,0,0,.08)}
  .badges{margin:.35rem 0}
  .badges .b{display:inline-block;background:#e2e8f0;border-radius:999px;padding:2px 10px;margin:2px 6px 0 0;font-size:.82rem}
  .muted{color:#4b5563}
  .btn{display:inline-block;margin-top:8px;padding:9px 14px;border-radius:10px;background:#2563eb;color:#fff;text-decoration:none;font-weight:600}
  .btn:hover{filter:brightness(.95)}
</style>

[← Volver al Inicio del Portafolio]({{ site.baseurl }}/)

# Proyectos concluidos

_Agrego aquí los proyectos con los que evidencio competencias._

<div class="cards">

  <!-- ERP -->
  <a class="card" href="{{ site.baseurl }}/proyectos/erp-jb">
    <h3>ERP — Jorge Basadre</h3>
    <div class="badges">
      <span class="b">React</span>
      <span class="b">TypeScript</span>
      <span class="b">SPA</span>
      <span class="b">API REST</span>
    </div>
    <p class="muted">
      Sistema académico/administrativo con autenticación por rol, CRUD de entidades,
      notas, asistencia y reportes. Frontend en React/TS (Vite) consumiendo API REST.
    </p>
    <p><strong>Repo:</strong> <a href="https://github.com/edisondevin/erp-jb" target="_blank">github.com/edisondevin/erp-jb</a></p>
    <span class="btn">Ver ficha</span>
  </a>

  <!-- Turismo Chupaca -->
  <a class="card" href="{{ site.baseurl }}/proyectos/turismo_chupaca">
    <h3>Turismo Chupaca</h3>
    <div class="badges">
      <span class="b">Producción</span>
      <span class="b">Responsive</span>
    </div>
    <p class="muted">
      Plataforma informativa para promocionar atractivos turísticos, cultura y gastronomía
      de Chupaca. Sitio público con dominio y SSL.
    </p>
    <p><strong>Live:</strong> <a href="https://turismochupaca.com/" target="_blank">turismochupaca.com</a></p>
    <span class="btn">Ver ficha</span>
  </a>

</div>

## Notas y aprendizajes transversales
- Planificación con **GitHub Issues**, ramas `feat/*` y `fix/*`.  
- Estándares de **accesibilidad** (semántica, labels, contraste) y **rendimiento** (imágenes y carga).  
- Documentación mínima por proyecto: objetivos, stack, scripts, capturas y roadmap.
