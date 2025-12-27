---

---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)


# Semana 10 — Backend Java (Spring Boot + MySQL) | CRUD API (Estudiante)

> Curso: Desarrollo de Aplicaciones Web  
> Unidad: Backend (API Java)  
> Producto: API REST conectada a MySQL + pruebas en Postman

---

## 1) ¿Qué se hizo esta semana?
Se desarrolló una **API REST** con **Spring Boot** siguiendo el enfoque **MVC por capas**, creando:
- Configuración del proyecto (Spring Boot + Maven).
- Conexión a **MySQL** mediante `application.properties`.
- Paquetes: `controllers`, `models`, `repositories` (y opcional `services`).
- Entidad **Estudiante** + repositorio JPA.
- Endpoints CRUD: **POST, GET, PUT, DELETE**.
- Pruebas del CRUD con **Postman**.

---

## 2) Objetivos de aprendizaje
- Entender cómo se estructura un backend con Spring Boot.
- Conectar Spring Boot a MySQL usando JPA.
- Construir un CRUD completo para una entidad (Estudiante).
- Probar una API REST usando Postman (request/response, JSON, status codes).

---

## 3) Conceptos clave (resumen corto)
### Spring Boot
Framework que acelera el desarrollo backend (configuración automática, dependencias listas, servidor embebido, etc.).

### MVC (Modelo - Vista - Controlador)
En una API REST:
- **Model**: entidad/clase persistente (tabla en BD).
- **Controller**: expone endpoints (rutas HTTP).
- **Repository**: acceso a datos (CRUD directo con JPA).

### JPA / Hibernate
ORM que mapea clases Java ↔ tablas MySQL, evitando SQL manual para lo básico.

---

## 4) Preparación del proyecto (resumen práctico)
### 4.1 Crear proyecto
En `start.spring.io` (Maven) agrega típicamente:
- Spring Web
- Spring Data JPA
- MySQL Driver
- (Opcional) Lombok

Descarga el ZIP, descomprime y ábrelo en IntelliJ.

### 4.2 Configurar MySQL
1) Crear BD:
```sql
CREATE DATABASE academico;
````

2. Configurar `application.properties` (ejemplo):

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/academico
spring.datasource.username=root
spring.datasource.password=123456
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

> Nota: `ddl-auto=update` crea/actualiza tablas automáticamente desde las entidades.

---

## 5) Estructura recomendada del proyecto

```txt
src/main/java/com/tuempresa/apiAcademico/
  controllers/
  models/
  repositories/
  services/        (opcional)
  ApiAcademicoApplication.java
src/main/resources/
  application.properties
```

---

## 6) Código base (Estudiante CRUD)

### 6.1 Model: `Estudiante.java`

📌 Ruta sugerida: `models/Estudiante.java`

```java
package com.jsuasnabar.apiAcademico.models;

import jakarta.persistence.*;

@Entity
@Table(name = "estudiante")
public class Estudiante {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long idEstudiante;

    private String nomEstudiante;
    private String dirEstudiante;
    private String ciuEstudiante;

    public Long getIdEstudiante() {
        return idEstudiante;
    }

    public void setIdEstudiante(Long idEstudiante) {
        this.idEstudiante = idEstudiante;
    }

    public String getNomEstudiante() {
        return nomEstudiante;
    }

    public void setNomEstudiante(String nomEstudiante) {
        this.nomEstudiante = nomEstudiante;
    }

    public String getDirEstudiante() {
        return dirEstudiante;
    }

    public void setDirEstudiante(String dirEstudiante) {
        this.dirEstudiante = dirEstudiante;
    }

    public String getCiuEstudiante() {
        return ciuEstudiante;
    }

    public void setCiuEstudiante(String ciuEstudiante) {
        this.ciuEstudiante = ciuEstudiante;
    }
}
```

### 6.2 Repository: `EstudianteRepository.java`

📌 Ruta sugerida: `repositories/EstudianteRepository.java`

```java
package com.jsuasnabar.apiAcademico.repositories;

import com.jsuasnabar.apiAcademico.models.Estudiante;
import org.springframework.data.jpa.repository.JpaRepository;

public interface EstudianteRepository extends JpaRepository<Estudiante, Long> {
}
```

### 6.3 Controller: `EstudianteController.java`

📌 Ruta sugerida: `controllers/EstudianteController.java`

```java
package com.jsuasnabar.apiAcademico.controllers;

import com.jsuasnabar.apiAcademico.models.Estudiante;
import com.jsuasnabar.apiAcademico.repositories.EstudianteRepository;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/api/estudiantes")
public class EstudianteController {

    @Autowired
    private EstudianteRepository repo;

    // CREATE
    @PostMapping
    public Estudiante agregar(@RequestBody Estudiante estudiante) {
        return repo.save(estudiante);
    }

    // UPDATE
    @PutMapping("/{id}")
    public ResponseEntity<Estudiante> modificar(@PathVariable Long id, @RequestBody Estudiante datos) {
        return repo.findById(id)
                .map(est -> {
                    est.setNomEstudiante(datos.getNomEstudiante());
                    est.setDirEstudiante(datos.getDirEstudiante());
                    est.setCiuEstudiante(datos.getCiuEstudiante());
                    return ResponseEntity.ok(repo.save(est));
                })
                .orElse(ResponseEntity.notFound().build());
    }

    // DELETE
    @DeleteMapping("/{id}")
    public ResponseEntity<Void> eliminar(@PathVariable Long id) {
        if (repo.existsById(id)) {
            repo.deleteById(id);
            return ResponseEntity.noContent().build();
        }
        return ResponseEntity.notFound().build();
    }

    // READ ALL
    @GetMapping
    public List<Estudiante> listarTodos() {
        return repo.findAll();
    }

    // READ BY ID
    @GetMapping("/{id}")
    public ResponseEntity<Estudiante> buscarPorId(@PathVariable Long id) {
        return repo.findById(id)
                .map(ResponseEntity::ok)
                .orElse(ResponseEntity.notFound().build());
    }
}
```

---

## 7) Pruebas en Postman (CRUD)

> Base URL: `http://localhost:8080/api/estudiantes`

### 7.1 POST — Crear estudiante

* Method: `POST`
* URL: `http://localhost:8080/api/estudiantes`
* Body (raw / JSON):

```json
{
  "nomEstudiante": "Juan Perez",
  "dirEstudiante": "Av. Los Héroes 123",
  "ciuEstudiante": "Huancayo"
}
```

### 7.2 GET — Listar todos

* Method: `GET`
* URL: `http://localhost:8080/api/estudiantes`

### 7.3 GET — Buscar por ID

* Method: `GET`
* URL: `http://localhost:8080/api/estudiantes/1`

### 7.4 PUT — Actualizar por ID

* Method: `PUT`
* URL: `http://localhost:8080/api/estudiantes/1`
* Body (raw / JSON):

```json
{
  "nomEstudiante": "Juan P. Actualizado",
  "dirEstudiante": "Jr. Siempre Viva 742",
  "ciuEstudiante": "Chupaca"
}
```

### 7.5 DELETE — Eliminar por ID

* Method: `DELETE`
* URL: `http://localhost:8080/api/estudiantes/1`

---

## 8) Checklist de entrega (lo que debe verse)

* [ ] Proyecto Spring Boot compila y levanta.
* [ ] MySQL conectado (sin errores en consola).
* [ ] Tabla `estudiante` creada/actualizada automáticamente.
* [ ] Endpoints responden correctamente.
* [ ] Evidencias: capturas Postman (POST/GET/PUT/DELETE).

---

## 9) Errores típicos y solución rápida

* **No conecta a MySQL**: revisa puerto `3306`, credenciales, que MySQL esté corriendo.
* **Table no se crea**: confirma `spring.jpa.hibernate.ddl-auto=update`.
* **400 Bad Request en POST/PUT**: revisa JSON y nombres exactos de campos.
* **404 Not Found**: revisa `@RequestMapping("/api/estudiantes")` y el puerto donde corre Spring.
---