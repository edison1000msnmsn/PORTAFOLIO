---

---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)  

````md
# Semana 09 — Backend con Java (Jakarta) + Tomcat + JSP + Maven

> **Enfoque real del profe (teórica):** introducción al backend con Java/Jakarta, servidor Tomcat, JSP y gestión de dependencias con Maven.

---

## 1) ¿Qué se vio en esta semana?

### 1.1 Arquitecturas web (cliente/servidor)
- El desarrollo web se basa en **arquitectura Cliente–Servidor**.
- Tipos comunes:
  - **MPA (Multi Page Application):** varias páginas, cada una con su HTML/CSS/JS y rutas por directorios.
  - **Multicapa (Server Side):** separación por capas (presentación, lógica, datos). Muy ligada a **MVC**.
  - **SPA (Single Page Application):** una sola página “grande”, el cliente navega con JS y al servidor le pide **datos** (JSON).
  - **Híbridas SPA/MPA:** mezcla de características.
  - **Arquitectura Hexagonal (puertos y adaptadores):** capas independientes, testeables, con entradas/salidas desacopladas.

---

## 2) Servidores web, hosting y cloud (idea base)
### 2.1 ¿Qué es un servidor web?
Un servidor web almacena y entrega recursos (HTML/CSS/JS, imágenes, etc.) por HTTP bajo cliente/servidor.

### 2.2 Software típico de servidor web
- Apache HTTP Server, Nginx, IIS, LiteSpeed, etc.
- **Apache Tomcat** (muy usado cuando el backend es Java/JSP/Servlet).

### 2.3 Hosting / Cloud Hosting
- **Hosting**: servicio para alojar tu sitio (espacio + transferencia mensual).
- **Cloud hosting**: escalable, flexible, normalmente pago por uso.
- **Cloud computing**: recursos de cómputo bajo demanda vía internet.

---

## 3) Administración básica del servidor
### 3.1 Dominio y DNS (mínimo indispensable)
- El dominio es el nombre único del sitio en internet.
- Partes:
  - **Nombre**
  - **Extensión** (.com, .org, .pe, etc.)

### 3.2 Configuración de servidor (conceptos clave)
Archivos típicos:
- Apache HTTP Server → `httpd.conf`
- Tomcat → `conf/server.xml`

Parámetros importantes:
- `DocumentRoot`: carpeta raíz del contenido.
- `Listen`: puerto (80 HTTP, 443 HTTPS; Tomcat usa 8080 por defecto).
- `ServerName`: dominio o IP.
- `DirectoryIndex`: archivo inicial (index.html, index.php, index.jsp).
- `ErrorDocument`: páginas de error (404, 500, etc.).
- `Timeout`, `MaxClients`, SSL.

---

## 4) ¿Cómo funciona el Server Side?
Flujo general:
1) El navegador envía una solicitud HTTP (con parámetros, forms, cookies, etc.).
2) El servidor interpreta la solicitud.
3) Ejecuta código backend (PHP/Node/Python/Java).
4) Consulta BD si corresponde.
5) Genera respuesta (HTML/JSON/XML).
6) Devuelve al cliente y el navegador renderiza.

---

## 5) Tomcat + JSP (Backend Java)
### 5.1 ¿Qué es Tomcat?
- Es un **contenedor de servlets y JSP**.
- Cuando se accede a una página **JSP**:
  - Tomcat **traduce JSP → Servlet Java**
  - compila
  - ejecuta
  - responde con HTML.

### 5.2 Estructura de directorios de Tomcat (para ubicarte rápido)
- `bin/` : scripts para iniciar/detener
- `conf/` : configuración (ej. `server.xml`)
- `logs/` : logs
- `webapps/` : aquí se despliegan aplicaciones
- `work/`, `temp/` : temporales
- `lib/`, `shared/`, etc. (según instalación)

### 5.3 Componentes (lo que verás en `server.xml`)
- **Server**: instancia principal
- **Service**: conjunto de conectores + engine
- **Connector**: recibe HTTP (ej. 8080). Cambias el puerto aquí.
- **Engine**: contenedor web
- **Host**: host/virtual host (con `appBase` por defecto `webapps`)
- **Context**: una aplicación web

> 💡 TIP: si te piden “cambiar el puerto”, normalmente se cambia el atributo `port` del `Connector`.

---

## 6) Gestión de dependencias con Maven
### 6.1 ¿Por qué Maven?
Porque ya no se gestionan librerías “a mano”. Maven:
- descarga dependencias
- compila, testea y empaqueta
- estandariza estructura del proyecto
- automatiza ciclo de vida (build)

### 6.2 Ciclo de vida (fases típicas)
- `compile` → compila .java → .class
- `test` → ejecuta pruebas
- `package` → genera `.jar`/`.war`
- `install` → instala en repo local
- `deploy` → despliega en repo remoto

### 6.3 Archivo `pom.xml` (idea clave)
- Es el “modelo” del proyecto (dependencias + config).

Ejemplo mínimo:
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
  <modelVersion>4.0.0</modelVersion>
  <groupId>org.example</groupId>
  <artifactId>web2</artifactId>
  <version>1.0-SNAPSHOT</version>

  <properties>
    <maven.compiler.source>20</maven.compiler.source>
    <maven.compiler.target>20</maven.compiler.target>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>
</project>
````

### 6.4 Comandos Maven útiles (cuando hay Tomcat plugin)

```bash
# desplegar
mvn clean install tomcat7:deploy

# redesplegar
mvn clean install tomcat7:redeploy

# quitar
mvn clean install tomcat7:undeploy
```

---

## 7) Laboratorio 09 (lo práctico que se dejó)

###  Objetivos del lab

* Instalar **OpenJDK**
* Instalar **IntelliJ IDEA**
* Instalar **Tomcat**

### 7.1 Instalación de OpenJDK (resumen operativo)

1. Descargar OpenJDK (según versión indicada).
2. Descomprimir (ej: `C:\java\jdk-xx`)
3. Crear variables de entorno:

   * `JAVA_HOME = C:\java\jdk-xx`
   * agregar `%JAVA_HOME%\bin` al `PATH`

Verificación:

```bash
java --version
javac --version
```

### 7.2 Instalación de Tomcat 10 (resumen operativo)

1. Descargar Tomcat 10 (Windows Service Installer).
2. Instalar tipo **Full**.
3. Revisar puertos (por defecto 8080).
4. Verificar Tomcat en el navegador:

* `http://localhost:8080/`

### 7.3 Inicio de proyecto JSP (en IntelliJ)

* Crear proyecto web
* Configurar servidor Tomcat en el IDE
* Probar despliegue con una página JSP simple.

Ejemplo de `hello.jsp` (para probar rápido):

```jsp
<%@ page contentType="text/html; charset=UTF-8" %>
<html>
  <body>
    <h2>Hello JSP ✅</h2>
    <p>Fecha servidor: <%= new java.util.Date() %></p>
  </body>
</html>
```

---

## 8) Apunte extra (seguridad / sistema web)

### Autenticación basada en tokens (idea general)

* El sistema genera un token al iniciar sesión.
* El cliente envía el token en cada request.
* El servidor valida token + expiración.
* Tipos: JWT, OAuth tokens, SAML tokens.

---

## 9) Checklist de evidencias (para tu cuaderno)

* [ ] Captura `java --version` y `javac --version`
* [ ] Captura Tomcat corriendo en `http://localhost:8080/`
* [ ] Captura de configuración de Tomcat en IntelliJ
* [ ] Captura de `hello.jsp` funcionando
* [ ] Nota breve: ¿qué hace Tomcat con un JSP?
* [ ] Nota breve: ¿para qué sirve Maven y qué es `pom.xml`?

---

## 10) Conclusión 

En la semana 09 se introdujo el desarrollo backend con Java/Jakarta, entendiendo el rol del servidor en arquitecturas cliente–servidor y multicapa. Se revisó el funcionamiento del server side y el uso de Apache Tomcat como contenedor para Servlets y JSP, donde las páginas JSP se traducen a servlets para ser compiladas y ejecutadas. Además, se estudió la gestión de dependencias con Maven mediante el archivo `pom.xml` y su ciclo de vida, y se realizó el laboratorio de instalación de OpenJDK, configuración de variables de entorno e instalación de Tomcat, verificando su ejecución y el despliegue básico de una página JSP.
---