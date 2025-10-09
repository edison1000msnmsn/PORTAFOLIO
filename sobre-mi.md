---
layout: default
title: "Sobre mí"
permalink: /sobre-mi/
---

<style>
  .page-header{
    background-image:
      linear-gradient(rgba(0,0,0,.55), rgba(0,0,0,.55)),
      url("https://img.lovepik.com/photo/50770/0641.jpg_wh860.jpg");
    background-size: cover;
    background-position: center;
    color:#fff !important;
  }
  .project-name,.project-tagline{color:#fff !important;}

  .about-container{
    display:grid;
    grid-template-columns:1fr;
    gap:2rem;
    margin-top:2rem;
  }
  
  .cards-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
    gap:1.5rem;
    margin-top:1.5rem;
  }
  
  .info-card{
    border:1px solid #e5e7eb;
    border-radius:12px;
    padding:1.5rem;
    background:#fff;
    box-shadow:0 1px 3px rgba(0,0,0,0.1);
    transition:transform 0.2s, box-shadow 0.2s;
  }
  
  .info-card:hover{
    transform:translateY(-2px);
    box-shadow:0 4px 12px rgba(0,0,0,0.15);
  }
  
  .info-card h3{
    margin-top:0;
    margin-bottom:1rem;
    color:#1a202c;
    font-size:1.25rem;
    font-weight:600;
  }
  
  .contact-links{
    line-height:1.8;
    color:#4b5563;
  }
  
  .contact-links a{
    color:#2563eb;
    text-decoration:none;
    transition:color 0.2s;
  }
  
  .contact-links a:hover{
    color:#1d4ed8;
    text-decoration:underline;
  }
  
  .tools-list, .steps-list{
    list-style:none;
    padding-left:0;
    margin:0;
  }
  
  .tools-list li, .steps-list li{
    padding:0.5rem 0;
    color:#4b5563;
    border-bottom:1px solid #f3f4f6;
  }
  
  .tools-list li:last-child, .steps-list li:last-child{
    border-bottom:none;
  }
  
  .tools-list li:before{
    content:"✓ ";
    color:#10b981;
    font-weight:bold;
    margin-right:0.5rem;
  }
  
  .steps-list li:before{
    content:"→ ";
    color:#3b82f6;
    font-weight:bold;
    margin-right:0.5rem;
  }
  
  .intro-section{
    background:#f9fafb;
    padding:1.5rem;
    border-radius:12px;
    border-left:4px solid #3b82f6;
    margin-bottom:1.5rem;
  }
  
  .objective-box{
    background:#eff6ff;
    padding:1.25rem;
    border-radius:8px;
    border-left:3px solid #3b82f6;
    margin:1.5rem 0;
  }
  
  .section-title{
    color:#1a202c;
    font-weight:600;
    margin-top:2rem;
    margin-bottom:1rem;
    font-size:1.35rem;
  }
  
  .skill-badge{
    display:inline-block;
    background:#dbeafe;
    color:#1e40af;
    padding:0.25rem 0.75rem;
    border-radius:6px;
    font-size:0.9rem;
    font-weight:500;
    margin:0.25rem;
  }
  
  @media (min-width:900px){
    .about-container{
      grid-template-columns:1.2fr 0.8fr;
    }
  }
</style>

[← Volver al Inicio del Portafolio]({{ site.baseurl }}/)

# Sobre mí

<div class="about-container">

<div class="main-content">

<div class="intro-section">
  <p>Soy <strong>Edison Orlando Huaire Maravi</strong>. Me considero una persona <strong>responsable</strong>, <strong>curiosa</strong> y constante.</p>
  <p>Me interesa el <strong>desarrollo web moderno</strong> y la calidad del código estructurado.</p>
</div>

<div class="objective-box">
  <strong>Objetivo a corto plazo:</strong> consolidar bases sólidas en <span class="skill-badge">HTML/CSS/JS</span> y <span class="skill-badge">React</span>, y publicar proyectos pequeños pero bien construidos (documentados y versionados).
</div>

<h2 class="section-title">Lo que sé hacer</h2>
<ul>
  <li>Maquetación con <strong>HTML5</strong> y <strong>CSS3</strong></li>
  <li><strong>JavaScript</strong> (bases)</li>
</ul>

<h2 class="section-title">Actualmente practicando</h2>
<ul>
  <li><strong>Frontend:</strong> HTML5, CSS (Flexbox, Grid, <em>container queries</em>), <span class="skill-badge">Tailwind CSS</span>, JS/TS, <span class="skill-badge">React</span> (componentes, estado, hooks)</li>
  <li><strong>Herramientas:</strong> <span class="skill-badge">Vite</span>, configuración mínima de proyectos</li>
  <li><strong>Diseño:</strong> criterios <strong>UI/UX</strong> básicos y prototipado en Figma</li>
</ul>

<h2 class="section-title">Valores de trabajo</h2>
<ul>
  <li>Código claro y legible (nombres consistentes, formateo automático y documentación clara)</li>
  <li><strong>Commits</strong> pequeños con mensajes descriptivos</li>
  <li>Aprendizaje continuo y respeto por los estándares web</li>
</ul>

</div>

<aside class="sidebar-content">

<div class="cards-grid">

<div class="info-card">
  <h3>📬 Contacto</h3>
  <div class="contact-links">
    <strong>Email académico:</strong><br>
    <a href="mailto:e_2021200783B@uncp.edu.pe">e_2021200783B@uncp.edu.pe</a>
    <br><br>
    <strong>Email personal:</strong><br>
    <a href="mailto:edison10huaire@gmail.com">edison10huaire@gmail.com</a>
    <br><br>
    <strong>GitHub:</strong><br>
    <a href="https://github.com/edison1000msnmsn" target="_blank">edison1000msnmsn</a>
    <br><br>
    <strong>LinkedIn:</strong><br>
    <a href="https://pe.linkedin.com/in/edison-huaire-maravi-a39019275" target="_blank">Edison Huaire Maravi</a>
  </div>
</div>

<div class="info-card">
  <h3>🛠️ Herramientas cotidianas</h3>
  <ul class="tools-list">
    <li>VS Code (atajos, extensiones)</li>
    <li>Git CLI y GitHub Desktop</li>
    <li>NPM, Vite, configuraciones</li>
  </ul>
</div>

<div class="info-card">
  <h3>🎯 Próximos pasos</h3>
  <ul class="steps-list">
    <li>Routing y consumo de APIs en React</li>
    <li>Buenas prácticas de accesibilidad</li>
  </ul>
</div>

</div>

</aside>

</div>