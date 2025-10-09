---
layout: default
title: "Proyectos concluidos"
---
 
<style>
  .page-header{
    background-image:
      linear-gradient(rgba(0,0,0,.55), rgba(0,0,0,.55)),
      url("https://ninjatalentweb.s3.eu-west-1.amazonaws.com/uploads/2023/01/12155733/python.png");
    background-size: cover; background-position: center; color:#fff !important;
  }
  .project-name,.project-tagline{color:#fff !important;}

  /* Tarjetas minimalistas, sin botones */
  .cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(270px,1fr));gap:16px;margin:18px 0}
  .card{border:1px solid #d0d7de;border-radius:12px;padding:16px;background:#fff}
  .badges{margin:.35rem 0}
  .badges .b{display:inline-block;background:#e2e8f0;border-radius:999px;padding:2px 10px;margin:2px 6px 0 0;font-size:.82rem}
  .muted{color:#4b5563}
  .card h3{margin:0 0 .25rem} .card h3 a{text-decoration:none}
</style>

[← Volver al Inicio del Portafolio]({{ site.baseurl }}/)

# Proyectos concluidos
_Agrego aquí los proyectos con los que evidencio competencias._

<div class="cards">

  <div class="card">
    <h3><a href="{{ site.baseurl }}/proyectos/erp-jb/">ERP — Jorge Basadre</a></h3>
    <div class="badges">
      <span class="b">React</span><span class="b">TypeScript</span><span class="b">SPA</span><span class="b">API REST</span>
    </div>
    <p class="muted">
      Sistema académico/administrativo con autenticación por rol, CRUD, notas, asistencia y reportes.
      Frontend en React/TS (Vite) consumiendo API REST.
    </p>
    <p><strong>Repositorio:</strong> <a href="https://github.com/edisondevin/erp-jb" target="_blank">github.com/edisondevin/erp-jb</a></p>
  </div>

  <div class="card">
    <h3><a href="{{ site.baseurl }}/proyectos/turismo-chupaca/">Turismo Chupaca</a></h3>
    <div class="badges">
      <span class="b">Producción</span><span class="b">Responsive</span><span class="b">PHP/MySQL</span>
    </div>
    <p class="muted">
      Plataforma informativa para promocionar atractivos turísticos, cultura y gastronomía de Chupaca.
      Sitio público con dominio y SSL.
    </p>
    <p><strong>Sitio:</strong> <a href="https://turismochupaca.com/" target="_blank">turismochupaca.com</a></p>
  </div>

</div>


## Notas y aprendizajes transversales 
- Documentación mínima por proyecto: objetivos, stack, scripts, capturas y roadmap.
