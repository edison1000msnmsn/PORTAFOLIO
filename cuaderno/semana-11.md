---

---

[← Volver al cuaderno]({{ site.baseurl }}/cuaderno/)

````md
# Semana 11 — CRUD **Docente** (Spring Boot + MySQL) + **Swagger** + **Postman**

> Curso: Desarrollo de Aplicaciones Web  
> Unidad: Backend (API REST con Java/Spring)  
> Tipo: Práctica (CRUD + endpoints extra + documentación + validaciones)

---

## 1) ¿Qué se hizo esta semana?
Se desarrolló una **API RESTful** para gestionar **Docentes** (CRUD completo) conectada a **MySQL**, y se probó con **Postman**.  
Además, se agregó:

- Endpoints extra por **ciudad**, **experiencia** y **edad promedio**
- **Swagger UI** para documentar la API
- **Validaciones** mínimas
- **Manejo global de excepciones**
- **Paginación** en el listado

---

## 2) Objetivos de la semana
- Implementar un backend con **Spring Boot + Spring Data JPA + MySQL**.
- Exponer endpoints REST para **Docente** (CRUD).
- Documentar la API con **Swagger**.
- Probar endpoints con **Postman**.
- Aplicar validaciones y respuestas de error claras.
- Implementar **paginación** en el listado.

---

## 3) Modelo de datos: Entidad `Docente`
**Campos sugeridos (tabla `docente`):**
- `idDocente` (PK)
- `nomDocente`
- `dirDocente`
- `ciuDocente`
- `emailDocente`
- `fecNacimiento` (fecha)
- `tiempoServicio` (años)

---

## 4) Endpoints requeridos (rutas)
### CRUD base
- `GET    /api/docentes/all` → lista **todos** (sin paginar)
- `GET    /api/docentes/{id}` → obtener por ID
- `POST   /api/docentes` → crear
- `PUT    /api/docentes/{id}` → actualizar
- `DELETE /api/docentes/{id}` → eliminar

### Endpoints extra
- `GET /api/docentes/ciudad/{ciudad}`  
  Ej: `/api/docentes/ciudad/Cusco`

- `GET /api/docentes/experiencia/{anios}`  
  Ej: `/api/docentes/experiencia/10`

- `GET /api/docentes/edad-promedio`  
  Devuelve la **edad promedio** de docentes registrados.

### Paginación
- `GET /api/docentes?page=0&size=10`  
  `page=0` = primera página, `size=10` = 10 docentes por página.

---

## 5) Validaciones mínimas
- `emailDocente` debe tener **formato email**
- `tiempoServicio` **no puede ser negativo**
- `fecNacimiento` debe ser **anterior** a la fecha actual

---

## 6) Estructura recomendada del proyecto (paquetes)
```txt
src/main/java/com/tu_paquete/
  controllers/
  models/
  repositories/
  services/
  dtos/
  exceptions/
````

---

## 7) Configuración del proyecto (dependencias)

### Dependencias (Maven) recomendadas

* Spring Web
* Spring Data JPA
* MySQL Driver
* Validation
* Lombok (opcional)
* Swagger (springdoc-openapi)

**Swagger (springdoc) en `pom.xml`:**

```xml
<dependency>
  <groupId>org.springdoc</groupId>
  <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
  <version>2.5.0</version>
</dependency>
```

> Nota: la versión puede variar; lo importante es `springdoc-openapi-starter-webmvc-ui`.

---

## 8) `application.properties` (MySQL)

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/academico
spring.datasource.username=root
spring.datasource.password=123456

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# Swagger (springdoc)
springdoc.swagger-ui.path=/swagger-ui.html
```

---

## 9) Implementación (código clave)

### 9.1) Entity `Docente` (models/Docente.java)

```java
package com.tu_paquete.models;

import jakarta.persistence.*;
import jakarta.validation.constraints.*;
import java.time.LocalDate;

@Entity
@Table(name = "docente")
public class Docente {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long idDocente;

    @NotBlank(message = "nomDocente es obligatorio")
    private String nomDocente;

    @NotBlank(message = "dirDocente es obligatorio")
    private String dirDocente;

    @NotBlank(message = "ciuDocente es obligatorio")
    private String ciuDocente;

    @NotBlank(message = "emailDocente es obligatorio")
    @Email(message = "emailDocente debe tener formato válido")
    private String emailDocente;

    @NotNull(message = "fecNacimiento es obligatorio")
    @Past(message = "fecNacimiento debe ser anterior a hoy")
    private LocalDate fecNacimiento;

    @NotNull(message = "tiempoServicio es obligatorio")
    @Min(value = 0, message = "tiempoServicio no puede ser negativo")
    private Integer tiempoServicio;

    // Getters & Setters
    public Long getIdDocente() { return idDocente; }
    public void setIdDocente(Long idDocente) { this.idDocente = idDocente; }

    public String getNomDocente() { return nomDocente; }
    public void setNomDocente(String nomDocente) { this.nomDocente = nomDocente; }

    public String getDirDocente() { return dirDocente; }
    public void setDirDocente(String dirDocente) { this.dirDocente = dirDocente; }

    public String getCiuDocente() { return ciuDocente; }
    public void setCiuDocente(String ciuDocente) { this.ciuDocente = ciuDocente; }

    public String getEmailDocente() { return emailDocente; }
    public void setEmailDocente(String emailDocente) { this.emailDocente = emailDocente; }

    public LocalDate getFecNacimiento() { return fecNacimiento; }
    public void setFecNacimiento(LocalDate fecNacimiento) { this.fecNacimiento = fecNacimiento; }

    public Integer getTiempoServicio() { return tiempoServicio; }
    public void setTiempoServicio(Integer tiempoServicio) { this.tiempoServicio = tiempoServicio; }
}
```

---

### 9.2) Repository (repositories/DocenteRepository.java)

```java
package com.tu_paquete.repositories;

import com.tu_paquete.models.Docente;
import org.springframework.data.jpa.repository.JpaRepository;

import java.util.List;

public interface DocenteRepository extends JpaRepository<Docente, Long> {
    List<Docente> findByCiuDocenteIgnoreCase(String ciuDocente);
    List<Docente> findByTiempoServicioGreaterThanEqual(Integer tiempoServicio);
}
```

---

### 9.3) Service (services/DocenteService.java)

```java
package com.tu_paquete.services;

import com.tu_paquete.models.Docente;
import com.tu_paquete.repositories.DocenteRepository;
import org.springframework.data.domain.*;
import org.springframework.stereotype.Service;

import java.time.LocalDate;
import java.time.Period;
import java.util.*;

@Service
public class DocenteService {

    private final DocenteRepository repo;

    public DocenteService(DocenteRepository repo) {
        this.repo = repo;
    }

    public List<Docente> listarTodos() {
        return repo.findAll();
    }

    public Page<Docente> listarPaginado(int page, int size) {
        Pageable pageable = PageRequest.of(page, size, Sort.by("idDocente").descending());
        return repo.findAll(pageable);
    }

    public Docente buscarPorId(Long id) {
        return repo.findById(id).orElseThrow(() -> new NoSuchElementException("Docente no encontrado: " + id));
    }

    public Docente crear(Docente docente) {
        docente.setIdDocente(null);
        return repo.save(docente);
    }

    public Docente actualizar(Long id, Docente datos) {
        Docente actual = buscarPorId(id);
        actual.setNomDocente(datos.getNomDocente());
        actual.setDirDocente(datos.getDirDocente());
        actual.setCiuDocente(datos.getCiuDocente());
        actual.setEmailDocente(datos.getEmailDocente());
        actual.setFecNacimiento(datos.getFecNacimiento());
        actual.setTiempoServicio(datos.getTiempoServicio());
        return repo.save(actual);
    }

    public void eliminar(Long id) {
        if (!repo.existsById(id)) throw new NoSuchElementException("Docente no encontrado: " + id);
        repo.deleteById(id);
    }

    public List<Docente> listarPorCiudad(String ciudad) {
        return repo.findByCiuDocenteIgnoreCase(ciudad);
    }

    public List<Docente> listarPorExperiencia(Integer anios) {
        return repo.findByTiempoServicioGreaterThanEqual(anios);
    }

    public double edadPromedio() {
        List<Docente> docentes = repo.findAll();
        if (docentes.isEmpty()) return 0.0;

        double suma = 0;
        for (Docente d : docentes) {
            int edad = Period.between(d.getFecNacimiento(), LocalDate.now()).getYears();
            suma += edad;
        }
        return suma / docentes.size();
    }
}
```

---

### 9.4) Controller (controllers/DocenteController.java)

```java
package com.tu_paquete.controllers;

import com.tu_paquete.models.Docente;
import com.tu_paquete.services.DocenteService;
import jakarta.validation.Valid;
import org.springframework.data.domain.Page;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.*;

@RestController
@RequestMapping("/api/docentes")
public class DocenteController {

    private final DocenteService service;

    public DocenteController(DocenteService service) {
        this.service = service;
    }

    // LISTA TODOS (sin paginar)
    @GetMapping("/all")
    public List<Docente> listarTodos() {
        return service.listarTodos();
    }

    // LISTA PAGINADA (page & size)
    @GetMapping
    public Page<Docente> listarPaginado(
            @RequestParam(defaultValue = "0") int page,
            @RequestParam(defaultValue = "10") int size
    ) {
        return service.listarPaginado(page, size);
    }

    @GetMapping("/{id}")
    public Docente buscarPorId(@PathVariable Long id) {
        return service.buscarPorId(id);
    }

    @PostMapping
    public Docente crear(@Valid @RequestBody Docente docente) {
        return service.crear(docente);
    }

    @PutMapping("/{id}")
    public Docente actualizar(@PathVariable Long id, @Valid @RequestBody Docente datos) {
        return service.actualizar(id, datos);
    }

    @DeleteMapping("/{id}")
    public ResponseEntity<Void> eliminar(@PathVariable Long id) {
        service.eliminar(id);
        return ResponseEntity.noContent().build();
    }

    // EXTRA: ciudad
    @GetMapping("/ciudad/{ciudad}")
    public List<Docente> porCiudad(@PathVariable String ciudad) {
        return service.listarPorCiudad(ciudad);
    }

    // EXTRA: experiencia mínima
    @GetMapping("/experiencia/{anios}")
    public List<Docente> porExperiencia(@PathVariable Integer anios) {
        return service.listarPorExperiencia(anios);
    }

    // EXTRA: edad promedio
    @GetMapping("/edad-promedio")
    public Map<String, Object> edadPromedio() {
        double promedio = service.edadPromedio();
        Map<String, Object> rpta = new HashMap<>();
        rpta.put("edadPromedio", promedio);
        return rpta;
    }
}
```

---

### 9.5) Manejo global de excepciones (exceptions/GlobalExceptionHandler.java)

```java
package com.tu_paquete.exceptions;

import org.springframework.http.*;
import org.springframework.web.bind.MethodArgumentNotValidException;
import org.springframework.web.bind.annotation.*;

import java.util.*;

@RestControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(NoSuchElementException.class)
    public ResponseEntity<Map<String, Object>> notFound(NoSuchElementException ex) {
        return ResponseEntity.status(HttpStatus.NOT_FOUND).body(Map.of(
                "error", "NOT_FOUND",
                "message", ex.getMessage()
        ));
    }

    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ResponseEntity<Map<String, Object>> validation(MethodArgumentNotValidException ex) {
        Map<String, String> errors = new HashMap<>();
        ex.getBindingResult().getFieldErrors()
                .forEach(e -> errors.put(e.getField(), e.getDefaultMessage()));

        return ResponseEntity.badRequest().body(Map.of(
                "error", "VALIDATION_ERROR",
                "message", "Datos inválidos",
                "fields", errors
        ));
    }

    @ExceptionHandler(Exception.class)
    public ResponseEntity<Map<String, Object>> generic(Exception ex) {
        return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).body(Map.of(
                "error", "INTERNAL_ERROR",
                "message", "Ocurrió un error inesperado"
        ));
    }
}
```

---

## 10) Swagger UI (Documentación)

Con springdoc, al ejecutar el proyecto podrás entrar a:

* **Swagger UI:** `http://localhost:8080/swagger-ui.html`
* **OpenAPI JSON:** `http://localhost:8080/v3/api-docs`

---

## 11) Pruebas en Postman (casos mínimos)

### Crear docente (POST `/api/docentes`)

```json
{
  "nomDocente": "Juan Perez",
  "dirDocente": "Av. Los Álamos 123",
  "ciuDocente": "Cusco",
  "emailDocente": "juan.perez@correo.com",
  "fecNacimiento": "1990-05-10",
  "tiempoServicio": 10
}
```

### Paginación (GET `/api/docentes?page=0&size=10`)

* Verificar que retorne `content`, `totalElements`, `totalPages`, etc.

### Validaciones rápidas

* Email inválido: `"emailDocente": "no-es-email"`
* Tiempo servicio negativo: `"tiempoServicio": -2`
* Fecha futura: `"fecNacimiento": "2099-01-01"`

---


## 12) Conclusiones

* Spring Boot + JPA acelera el desarrollo del CRUD con persistencia real en MySQL.
* Swagger mejora la comunicación: la API se entiende y prueba desde el navegador.
* Validaciones + excepciones globales hacen la API más robusta y “presentable”.

---

## 13) Preguntas de repaso

1. ¿Qué ventaja tiene usar `JpaRepository` frente a hacer SQL “a mano”?
2. ¿Cuál es la diferencia entre `@RestController` y `@Controller`?
3. ¿Qué hace `@Valid` y dónde se recomienda usarlo?
4. ¿Qué devuelve `Page<T>` y para qué sirve en paginación?
5. ¿Para qué sirve Swagger/OpenAPI en un proyecto real?

```
```
