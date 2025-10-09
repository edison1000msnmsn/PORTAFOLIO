---
layout: default
title: "Turismo Chupaca — Ficha técnica"
permalink: /proyectos/turismo-chupaca/
---
<style>
  .page-header{
    background-image:
      linear-gradient(rgba(0,0,0,.55), rgba(0,0,0,.55)),
      url("https://i.pinimg.com/736x/b1/36/a3/b136a3dde4ef2a29c7cd45973b1ab2b9.jpg");
    background-size: cover;
    background-position: center;
    color:#fff !important;
  }
  .project-name,.project-tagline{color:#fff !important;}
  .meta{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:12px;margin:12px 0}
  .meta>div{border:1px solid #d1d5db;border-radius:10px;padding:10px 12px;background:#fff}
  .badges span{display:inline-block;background:#e2e8f0;border-radius:999px;padding:2px 10px;margin:2px 6px 0 0;font-size:.85rem}
  .btn{display:inline-block;padding:10px 16px;border-radius:10px;background:#2563eb;color:#fff;text-decoration:none;font-weight:600}
  .btn:hover{filter:brightness(.95)}
  .muted{color:#4b5563}
  pre{background:#0b1020;color:#e6edf3;border-radius:10px;padding:12px;overflow:auto}
</style>

[← Volver a proyectos]({{ site.baseurl }}/proyectos/)

# Turismo Chupaca — Ficha técnica

<div class="meta">
  <div><strong>Rol</strong><br/>Desarrollador web fullstack (frontend + backend)</div>
  <div><strong>Stack</strong><br/>HTML5 · CSS3 · JavaScript · PHP · MySQL · Bootstrap</div>
  <div><strong>Estado</strong><br/>Sitio web público en producción</div>
</div>

<p>
  <a class="btn" href="https://turismochupaca.com/" target="_blank" rel="noopener">Visitar sitio en producción</a>
</p>

## 1) Descripción general
**Turismo Chupaca** es una plataforma web informativa que promueve los atractivos turísticos, la cultura y la gastronomía de la provincia de **Chupaca** (Junín, Perú).  
Su objetivo es **impulsar el turismo local** y ofrecer a los visitantes una guía moderna, visual y accesible sobre lugares emblemáticos, festividades y servicios.

<div class="badges">
  <span>Turismo</span><span>Cultura</span><span>Promoción digital</span><span>Diseño responsive</span>
</div>

## 2) Objetivos principales
- Difundir los **principales destinos turísticos** de Chupaca.  
- Proporcionar información **actualizada y accesible** para visitantes.  
- Fomentar la identidad cultural y **visibilidad digital** del distrito.  
- Consolidar una base sólida para futuros módulos interactivos (mapas, comentarios, reservas).

## 3) Secciones del sitio
- 🏞️ **Inicio:** presentación visual con galería de imágenes y lema turístico.  
- 🗺️ **Atractivos turísticos:** lugares destacados con descripción, ubicación y fotografías.  
- 🎭 **Cultura y tradiciones:** festividades, danzas y costumbres locales.  
- 🍴 **Gastronomía:** platos típicos de la región (con imágenes y recetas).  
- 🏨 **Servicios:** hospedajes, restaurantes y guías locales.  
- 📩 **Contacto:** formulario y enlaces a redes sociales.

## 4) Características técnicas
- Sitio **responsive** y accesible (compatible con móviles y escritorio).  
- Menú de navegación adaptable con Bootstrap.  
- Base de datos **MySQL** con panel administrativo para registrar atractivos y eventos.  
- Integración con **Google Maps** para geolocalización de destinos.  
- SEO básico (metadatos, etiquetas alt, sitemap).  
- Hosting propio con dominio `.com` y certificado **SSL**.

## 5)  Evidencias
- Sitio oficial: https://turismochupaca.com
- Repositorio (privado/local): actualmente en desarrollo interno.

## 6) Arquitectura simplificada
```text
[Frontend: HTML, CSS, JS]  —→  [Backend: PHP]  —→  [Base de datos: MySQL]
          ↑                          ↓
   Bootstrap 5              CRUD dinámico de contenidos
   Galerías JS              Panel de administración
 