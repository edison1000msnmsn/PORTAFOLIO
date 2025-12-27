---

---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)



````md
# Semana 12 — Backend con PHP (Teoría)
> Curso: Desarrollo de Aplicaciones Web  
> Unidad: Desarrollo PHP  
> Modalidad: Teórica (preparación para la práctica de la semana 13)

---

## 1) Logro / Propósito de la semana
Comprender **cómo funciona un backend con PHP**, cómo se despliega en un **servidor web Apache**, y dejar listo el entorno de trabajo con **PHP + Apache (portable) + Composer** para empezar proyectos y luego pasar a frameworks como **Laravel**.

---

## 2) Conceptos clave (Backend)
### ¿Qué es Apache?
Apache (Apache HTTP Server) es un **servidor web** que:
1. **Recibe** solicitudes HTTP/HTTPS del navegador.
2. **Busca** el contenido solicitado (HTML, imágenes, etc.) en el servidor.
3. **Responde** devolviendo ese contenido al cliente.

✅ En pocas palabras: Apache atiende requests y entrega responses.

---

## 3) Servidor portable (Apache Lounge)
Apache Lounge es una comunidad/sitio que ofrece **binarios compilados de Apache para Windows** y permite usarlo incluso como **servidor portable (ZIP)**.

### Instalación portable (idea general)
1. **Descargar** el ZIP (Apache Lounge).
2. **Extraer** en una carpeta tipo: `D:\server\Apache24`
3. Verificar dependencias: **Visual C++ Redistributable**
4. Configurar `httpd.conf` (archivo principal de Apache)

### Parámetros importantes en `httpd.conf`
Ejemplo típico de configuración básica:
- `Listen 8080`
- `ServerName localhost:8080`
- `Define SRVROOT "D:\server\Apache24"`

> Con esto puedes levantar Apache en el puerto 8080 y probar en el navegador: `http://localhost:8080`

---

## 4) PHP — Hypertext Preprocessor (Backend)
### ¿Qué es PHP?
PHP es un lenguaje de programación **del lado del servidor**, usado para construir **sitios y aplicaciones web dinámicas**.

### ¿Cómo funciona PHP (flujo mental)?
Cuando un usuario solicita una página `.php`:
1. Apache recibe el request.
2. Apache envía el script al **intérprete PHP**.
3. PHP ejecuta lógica (variables, DB, formularios, etc.).
4. PHP genera **HTML/CSS/JS final**.
5. El navegador recibe **solo** el resultado (no ve el PHP).

---

## 5) Instalación de PHP en Windows (ZIP)
### Pasos (idea general)
1. Descargar el **ZIP** de PHP (según arquitectura x64/x86).
2. Extraer en una ruta tipo: `D:\server\php`
3. Configurar `php.ini`
   - Copiar `php.ini-development` → renombrar a `php.ini`
   - Habilitar extensiones (quitando `;`):
     - `extension_dir = "ext"`
     - `extension=mysqli`
     - `extension=curl`
4. Agregar PHP al **PATH** del sistema (Variables de entorno).
5. Verificar en consola:
   - `php -v`

---

## 6) Archivo clave: `httpd.conf` (Apache)
`httpd.conf` es el corazón de Apache: define puertos, rutas, módulos y comportamiento.

### Directivas más comunes (para entender qué estás tocando)
- **ServerRoot**: ruta base donde está Apache.
- **Listen**: puerto/IP donde escucha.
- **ServerName**: nombre/host del servidor (ej: localhost:8080).
- **DocumentRoot**: carpeta desde donde se sirven archivos web.
- **DirectoryIndex**: archivo por defecto al entrar a una carpeta (ej: index.html / index.php).
- **ErrorLog**: archivo donde se registran errores.
- **LogLevel**: nivel de detalle del log.
- **LoadModule**: cargar módulos extra (para extender funcionalidad).

---

## 7) Composer (gestor de dependencias en PHP)
Composer es el gestor de dependencias de facto para PHP (similar a `npm` o `pip`), y trabaja por proyecto (crea carpeta `vendor/`).

### Requisitos y verificación
- Tener PHP instalado y en PATH.
- Verificar:
  - `php -v`
- Verificar Composer:
  - `composer -V`

---

## 8) Sintaxis esencial de PHP (lo mínimo que debes dominar)
### Estructura básica
Todo PHP va entre etiquetas:
```php
<?php
  // tu código
?>
````

### Comentarios

```php
// una línea
# una línea
/* varias líneas */
```

### Variables

```php
$nombre = "Ana";
$edad = 25;
```

> PHP diferencia mayúsculas/minúsculas en variables: `$Color` ≠ `$color`

### Salida de datos

```php
echo "Hola";
print "PHP es genial";
```

### Condicionales

```php
if ($edad >= 18) {
  echo "Mayor de edad";
} elseif ($edad == 17) {
  echo "Casi llegas";
} else {
  echo "Menor de edad";
}
```

### switch

```php
switch ($color) {
  case "rojo": echo "Rojo"; break;
  case "azul": echo "Azul"; break;
  default: echo "No reconocido";
}
```

### Bucles

**for**

```php
for ($i = 0; $i < 5; $i++) {
  echo "Número: $i<br>";
}
```

**while / do...while**

```php
$x = 0;
while ($x < 5) {
  echo "Valor: $x<br>";
  $x++;
}

$y = 0;
do {
  echo "Valor: $y<br>";
  $y++;
} while ($y < 5);
```

**foreach**

```php
$frutas = ["Manzana", "Banana", "Cereza"];
foreach ($frutas as $fruta) {
  echo "Fruta: $fruta<br>";
}
```

### include / require (inclusión de archivos)

* `include`: warning y continúa si no existe
* `require`: fatal error y se detiene si no existe

```php
include 'funciones.php';
require 'config.php';
```

### Funciones

```php
function saludar($nombre) {
  return "¡Hola, $nombre!";
}
echo saludar("Carlos");
```

### exit / die

```php
if (!file_exists("importante.txt")) {
  exit("No se encontró el archivo importante.");
}
```

---


## 9) Conclusión 
Esta semana dejé listo el entorno backend con **Apache + PHP + Composer**, entendí el flujo request/response y repasé la sintaxis mínima de PHP (variables, condicionales, bucles, funciones, includes). Con esto ya estoy preparado para implementar la **práctica CRUD en Laravel** de la semana 13.

```
::contentReference[oaicite:1]{index=1}
```
