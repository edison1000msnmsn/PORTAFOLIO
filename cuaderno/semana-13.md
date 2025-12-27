---

---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)

````md
# Semana 13 — Backend PHP (Laravel): CRUD Estudiante + MySQL + Tailwind

## 1) Tema de la semana
Desarrollo backend con **PHP Laravel** aplicando el patrón **MVC** (Modelo–Vista–Controlador) y **Eloquent ORM** para registrar estudiantes en una BD MySQL, usando una **vista Blade** con estilos **Tailwind CSS**.

---

## 2) Objetivo
- Conocer el funcionamiento de PHP y el paso de parámetros en una aplicación web construida con Laravel.
- Implementar un registro de estudiantes (Create) usando formulario + rutas + controlador + modelo + migración.

---

## 3) Requisitos (entorno)
- PHP 8.1+
- Composer
- Node.js + npm (para Tailwind/Vite)
- MySQL (BD: `academico`)

> Nota rápida: habilitar extensiones en `php.ini` si tu Laravel/Composer lo requiere (zip, fileinfo, etc.).

---

## 4) Procedimiento (paso a paso)

### 4.1 Crear el proyecto Laravel
```bash
laravel new estudiantes-app
cd estudiantes-app
````

### 4.2 Configurar conexión a MySQL

Edita el archivo `.env` (ajusta contraseña):

```env
DB_DATABASE=academico
DB_USERNAME=root
DB_PASSWORD=tu_contraseña
```

### 4.3 Crear modelo + migración (tabla estudiantes)

```bash
php artisan make:model Estudiante -m
```

Edita `database/migrations/xxxx_create_estudiantes_table.php`:

```php
public function up()
{
    Schema::create('estudiantes', function (Blueprint $table) {
        $table->id('idEstudiante');
        $table->string('nomEstudiante');
        $table->string('dirEstudiante');
        $table->string('ciuEstudiante');
        $table->timestamps();
    });
}
```

Ejecuta migración:

```bash
php artisan migrate
```

---

## 5) Agregar Tailwind CSS

### 5.1 Instalar Tailwind (v3)

```bash
npm install -D tailwindcss@3 postcss autoprefixer
npx tailwindcss init -p
```

### 5.2 Agregar Tailwind a `resources/css/app.css`

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### 5.3 Compilar assets

```bash
npm install
npm run dev
```

---

## 6) Crear rutas + controlador + formulario (MVC)

### 6.1 Rutas — `routes/web.php`

> (En la guía aparece como `resources/routes/web.php`, pero en Laravel es `routes/web.php`)

```php
<?php

use Illuminate\Support\Facades\Route;
use App\Http\Controllers\EstudianteController;

Route::get('/', [EstudianteController::class, 'create']);
Route::post('/guardar', [EstudianteController::class, 'store']);
```

### 6.2 Controlador — `app/Http/Controllers/EstudianteController.php`

Crear controlador:

```bash
php artisan make:controller EstudianteController
```

Código base:

```php
<?php

namespace App\Http\Controllers;

use App\Models\Estudiante;
use Illuminate\Http\Request;

class EstudianteController extends Controller
{
    public function create()
    {
        return view('formulario');
    }

    public function store(Request $request)
    {
        Estudiante::create([
            'nomEstudiante' => $request->nombre,
            'dirEstudiante' => $request->direccion,
            'ciuEstudiante' => $request->ciudad
        ]);

        return redirect('/')->with('mensaje', 'Estudiante registrado');
    }
}
```

### 6.3 Modelo — `app/Models/Estudiante.php`

(Ya fue creado cuando hiciste `make:model`)

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Estudiante extends Model
{
    protected $table = 'estudiantes';
    protected $primaryKey = 'idEstudiante';
    protected $fillable = ['nomEstudiante', 'dirEstudiante', 'ciuEstudiante'];
}
```

### 6.4 Vista Blade — `resources/views/formulario.blade.php`

Crear vista:

```bash
php artisan make:view formulario
```

Contenido:

```blade
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Registro</title>
  @vite('resources/css/app.css')
</head>

<body class="bg-gray-100 flex justify-center items-center h-screen">

  <form action="/guardar" method="POST" class="bg-white p-6 rounded shadow-md w-96">
    @csrf

    <h2 class="text-xl font-bold mb-4">Nuevo Estudiante</h2>

    <input type="text" name="nombre" placeholder="Nombre" required
      class="w-full mb-3 p-2 border rounded">

    <input type="text" name="direccion" placeholder="Dirección" required
      class="w-full mb-3 p-2 border rounded">

    <input type="text" name="ciudad" placeholder="Ciudad" required
      class="w-full mb-3 p-2 border rounded">

    <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded w-full">
      Guardar
    </button>

  </form>

</body>
</html>
```

---

## 7) Ejecución y prueba

Levanta el servidor:

```bash
php artisan serve
```

* Abre: `http://localhost:8000`
* Registra un estudiante y verifica que inserte en la tabla `estudiantes`.

---


## 8) Conclusión

En esta semana se aplicó MVC en Laravel:

* **Modelo + Migración** para estructurar la tabla `estudiantes`.
* **Rutas** para mapear endpoints web.
* **Controlador** para recibir datos del formulario y registrar con **Eloquent**.
* **Vista Blade** estilizada con **Tailwind** para el registro de estudiantes.
---