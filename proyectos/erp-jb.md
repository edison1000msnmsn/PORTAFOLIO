---
layout: default
title: "ERP Jorge Basadre — Ficha técnica"
permalink: /proyectos/erp-jb/
---
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
  .meta{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:12px;margin:12px 0}
  .meta>div{border:1px solid #d1d5db;border-radius:10px;padding:10px 12px;background:#fff}
  .badges span{display:inline-block;background:#e2e8f0;border-radius:999px;padding:2px 10px;margin:2px 6px 0 0;font-size:.85rem}
  .btn{display:inline-block;padding:10px 16px;border-radius:10px;background:#2563eb;color:#fff;text-decoration:none;font-weight:600}
  .btn:hover{filter:brightness(.95)}
  .muted{color:#4b5563}
  pre{background:#0b1020;color:#e6edf3;border-radius:10px;padding:12px;overflow:auto}
</style>

[← Volver a proyectos]({{ site.baseurl }}/proyectos/)

# ERP Jorge Basadre — Ficha técnica

<div class="meta">
  <div><strong>Rol</strong><br/>Frontend Developer (React/TypeScript) + scripting de despliegue</div>
  <div><strong>Stack</strong><br/>React + TypeScript + Vite · TailwindCSS · React Router · Axios · (API REST Node/Express o .NET) · SQL Server</div>
  <div><strong>Tipo</strong><br/>SPA (Single Page Application) con auth y dashboard por rol</div>
</div>

<p>
  <a class="btn" href="https://github.com/edisondevin/erp-jb" target="_blank" rel="noopener">Ver repositorio en GitHub</a>
</p>

## 1) Contexto y objetivo
El colegio **Jorge Basadre** necesita unificar procesos **académicos y administrativos**.  
El objetivo del ERP es centralizar usuarios/roles, matrícula, notas, asistencia y reportes con **acceso por perfiles** y trazabilidad básica.

<div class="badges">
  <span>Académico</span><span>Administrativo</span><span>Dashboard por rol</span><span>Trazabilidad</span>
</div>

## 2) Alcance funcional
**MVP (primera versión)**
- Autenticación (login/logout) y **autorización por rol**.
- Dashboard por rol (admin, docente, secretaria).
- **CRUD**: estudiantes, docentes, cursos, matrículas.
- Registro de **asistencia** y **notas**.
- Reportes exportables (CSV/PDF básico).

**Próximo sprint**
- Importación/Exportación de datos por lotes (CSV).
- Auditoría (quién/qué/cuándo) y bitácora mínima.
- Notificaciones por correo (plantillas simples).

## 3) Módulos principales
- **Usuarios & Roles**: Admin, Docente, Secretaria.
- **Académico**: cursos, secciones, matrículas, notas, asistencia.
- **Comunicación**: avisos internos y cola de email.
- **Reportes**: listados y métricas por período.
## 4) Evidencias
- Repositorio: https://github.com/edisondevin/erp-jb

- Demo: pendiente
## 5) Arquitectura (visión rápida)
SPA en React que consume una **API REST**:

```text
[React + TypeScript (Vite)]  —Axios→  [API REST (Node/Express o .NET)]  —ORM→  [SQL Server]
      |                                   |                                   |
   Router                           JWT / Cookies                        Índices / FKs
   Estado (hooks)                   Validación + DTOs                    Backups / Roles
   Tailwind                         Logs + CORS                          Migraciones
    
