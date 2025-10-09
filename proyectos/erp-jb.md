---
layout: default
title: "ERP Jorge Basadre — Ficha técnica"
permalink: /proyectos/erp-jb/
---

<!-- ===== Estilos específicos de la ficha ===== -->
<style>
  .page-header{
    background-image:
      linear-gradient(rgba(0,0,0,.55), rgba(0,0,0,.55)),
      url("https://www.udteschool.com/img/school-epr.jpg");
    background-size: cover;
    background-position: center;
    color:#fff !important;
  }
  .project-name,.project-tagline{color:#fff !important;}

  .meta{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:12px;margin:16px 0}
  .meta>div{border:1px solid #d1d5db;border-radius:10px;padding:10px 12px;background:#fff}
  .badges span{display:inline-block;background:#e2e8f0;border-radius:999px;padding:2px 10px;margin:2px 6px 0 0;font-size:.85rem}
  
  /* Botón: siempre azul, texto blanco (sin parpadeo al hover) */
  .btn{
    display:inline-block;
    padding:10px 16px;
    border-radius:10px;
    background:#2563eb;
    color:#fff !important;
    text-decoration:none;
    font-weight:600;
    border:1px solid #1e40af;
    transition:background .2s ease, transform .2s ease;
  }
  .btn:hover{
    background:#1e40af;
    color:#fff !important;
    transform:translateY(-1px);
  }

  .muted{color:#4b5563}
  pre{
    background:#0b1020;
    color:#e6edf3;
    border-radius:10px;
    padding:12px;
    overflow:auto;
    font-size:.9rem;
  }
</style>

[← Volver a proyectos]({{ site.baseurl }}/proyectos/)

# ERP Jorge Basadre — Ficha técnica

<div class="meta">
  <div><strong>Rol</strong><br/>Desarrollador Frontend (React/TypeScript) y automatización de despliegue.</div>
  <div><strong>Stack</strong><br/>React + TypeScript + Vite · TailwindCSS · React Router · Axios · API REST (Node/Express o .NET) · SQL Server.</div>
  <div><strong>Tipo</strong><br/>SPA (Single Page Application) con autenticación y dashboard por rol.</div>
</div>

<p>
  <a class="btn" href="https://github.com/edisondevin/erp-jb" target="_blank" rel="noopener">🔗 Ver repositorio en GitHub</a>
</p>

---

## 🧩 1) Contexto y objetivo
El colegio **Jorge Basadre** requería un sistema que unificara la gestión **académica** y **administrativa**, eliminando duplicidad de registros y procesos manuales.  
El ERP tiene como objetivo centralizar usuarios, roles, matrículas, notas, asistencia y reportes bajo un acceso seguro y escalable.

<div class="badges">
  <span>Académico</span><span>Administrativo</span><span>Dashboard por rol</span><span>Trazabilidad</span>
</div>

---

## ⚙️ 2) Alcance funcional

**Primera versión (MVP):**
- Autenticación (login/logout) y **autorización por rol**.  
- Dashboard por rol (**admin**, **docente**, **secretaria**).  
- **CRUD completo** de estudiantes, docentes, cursos y matrículas.  
- Registro de **asistencia** y **notas**.  
- **Reportes exportables** (CSV y PDF básico).

**Próximo sprint:**
- Importación/Exportación de datos por lotes (CSV).  
- Auditoría (*quién, qué, cuándo*) con bitácora.  
- Notificaciones por correo y panel de logs.

---

## 🧠 3) Módulos principales
- **Usuarios & Roles:** control de acceso granular y perfiles independientes.  
- **Académico:** cursos, secciones, matrículas, notas y asistencia.  
- **Comunicación:** avisos internos y notificaciones automáticas.  
- **Reportes:** métricas por período, totales y rendimiento por curso.

---

## 🖼️ 4) Evidencias
- **Repositorio:** [github.com/edisondevin/erp-jb](https://github.com/edisondevin/erp-jb)  
- **Demo:** _(pendiente de publicación)_  
- **Capturas:** `{{ site.baseurl }}/assets/erp-jb/`

---

## 🧱 5) Arquitectura (visión rápida)
Aplicación **SPA** desarrollada con React, comunicada con una **API REST** y una base de datos SQL Server:

```text
[React + TypeScript (Vite)]  —Axios→  [API REST (Node/Express o .NET)]  —ORM→  [SQL Server]
      |                                   |                                   |
   Router                           JWT / Cookies                        Índices / FKs
   Estado (hooks)                   Validación + DTOs                    Backups / Roles
   Tailwind                         Logs + CORS                          Migraciones
