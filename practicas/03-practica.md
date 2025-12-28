## Práctica Integradora Final

- [Práctica Integradora Final](#práctica-integradora-final)
  - [Introducción](#introducción)
- [📋 ENUNCIADO DE LA PRÁCTICA](#-enunciado-de-la-práctica)
  - [Sistema de Gestión de Tareas (Task Management System)](#sistema-de-gestión-de-tareas-task-management-system)
  - [🎯 Objetivos del Proyecto](#-objetivos-del-proyecto)
  - [📊 Modelo de Datos](#-modelo-de-datos)
    - [Entidades Principales](#entidades-principales)
    - [Relaciones](#relaciones)
  - [👥 Funcionalidades por Rol](#-funcionalidades-por-rol)
    - [Usuario Regular (USER)](#usuario-regular-user)
    - [Administrador (ADMIN)](#administrador-admin)
  - [🔧 Requisitos Técnicos](#-requisitos-técnicos)
    - [Backend API REST](#backend-api-rest)
    - [Base de Datos](#base-de-datos)
    - [Frontend (Vue. js 3)](#frontend-vue-js-3)
  - [🧪 Requisitos de Testing](#-requisitos-de-testing)
    - [1. Tests Unitarios](#1-tests-unitarios)
    - [2. Tests de Integración (Testcontainers)](#2-tests-de-integración-testcontainers)
    - [3. Tests de API (Postman/Newman)](#3-tests-de-api-postmannewman)
    - [4. Tests E2E (Cypress)](#4-tests-e2e-cypress)
  - [🚀 Requisitos de CI/CD](#-requisitos-de-cicd)
    - [Pipeline de Integración Continua (CI)](#pipeline-de-integración-continua-ci)
    - [Pipeline de Despliegue Continuo (CD)](#pipeline-de-despliegue-continuo-cd)
  - [📦 Estructura de Repositorios](#-estructura-de-repositorios)
  - [🔒 Secretos y Variables de Entorno](#-secretos-y-variables-de-entorno)
  - [📝 Entregables](#-entregables)
    - [1. Código Fuente](#1-código-fuente)
  - [Frontend](#frontend)
  - [Docker Compose (stack completo)](#docker-compose-stack-completo)
- [🧪 Tests](#-tests)
  - [Tests unitarios](#tests-unitarios)
  - [Tests de integración](#tests-de-integración)
  - [Tests de API](#tests-de-api)
  - [Tests E2E](#tests-e2e)
- [🚀 Despliegue](#-despliegue)
  - [Staging](#staging)
  - [Production](#production)
- [👥 Usuarios de Prueba](#-usuarios-de-prueba)
- [📊 Pipelines CI/CD](#-pipelines-cicd)
  - [Status Badges](#status-badges)
  - [Flujo](#flujo)
- [📈 Cobertura de Código](#-cobertura-de-código)
- [📚 Documentación](#-documentación)
    - [2. Documentación Técnica](#2-documentación-técnica)
    - [3. Reportes de Tests](#3-reportes-de-tests)
    - [4. Demostración en Vivo](#4-demostración-en-vivo)
  - [🎯 Criterios de Evaluación](#-criterios-de-evaluación)
    - [Desglose Detallado de "Pipeline CI" (20%)](#desglose-detallado-de-pipeline-ci-20)
    - [Desglose de "Pipeline CD" (15%)](#desglose-de-pipeline-cd-15)
    - [Desglose de "Testing" (20%)](#desglose-de-testing-20)
  - [💡 Consejos y Recomendaciones](#-consejos-y-recomendaciones)
    - [Planificación](#planificación)
    - [Estrategia de Desarrollo](#estrategia-de-desarrollo)
    - [Errores Comunes a Evitar](#errores-comunes-a-evitar)
- [🎓 Conclusión](#-conclusión)


### Introducción

Esta práctica integradora representa la **culminación de la UD 7** y consolida todos los conocimientos adquiridos sobre CI/CD.  Los alumnos implementarán un **pipeline completo de integración y despliegue continuo** para una aplicación full-stack real, desde el código hasta producción. 

💡 **Nota del Profesor**: Esta práctica simula un proyecto profesional real.  No es un ejercicio académico simplificado:  requiere investigación, resolución de problemas y toma de decisiones técnicas. El objetivo es que experimentéis el ciclo completo de DevOps moderno que encontraréis en vuestra carrera profesional.

---

## 📋 ENUNCIADO DE LA PRÁCTICA

### Sistema de Gestión de Tareas (Task Management System)

**Contexto:**

Una startup tecnológica necesita modernizar su flujo de desarrollo e implementar prácticas DevOps para acelerar la entrega de valor a sus clientes. Tu equipo ha sido contratado para desarrollar un **Sistema de Gestión de Tareas** con un pipeline CI/CD completo que garantice calidad y despliegue automatizado.

La aplicación debe permitir a los usuarios crear, asignar, actualizar y completar tareas. El sistema debe integrarse con autenticación de usuarios y proporcionar una experiencia fluida tanto en web como en móvil.

---

### 🎯 Objetivos del Proyecto

Desarrollar e implementar un sistema completo que incluya:

1. **Backend API REST** (Spring Boot con Java **O** ASP.NET Core con C#)
2. **Base de datos relacional** (PostgreSQL)
3. **Frontend SPA** (Vue.js 3 con Composition API)
4. **Pipeline CI completo** con validación automatizada
5. **Pipeline CD** con despliegue a staging y producción
6. **Tests automatizados** en todos los niveles
7. **Monitorización** y feedback continuo

---

### 📊 Modelo de Datos

#### Entidades Principales

**1. User (Usuario)**
```
- id: Long/Guid (PK)
- email: String (único, formato email)
- username: String (único, 3-20 caracteres)
- passwordHash: String
- firstName: String
- lastName:  String
- role:  Enum (USER, ADMIN)
- isActive: Boolean
- createdAt: DateTime
- updatedAt:  DateTime
- lastLoginAt: DateTime
```

**2. Task (Tarea)**
```
- id: Long/Guid (PK)
- title: String (no vacío, max 200 caracteres)
- description: Text (opcional, max 2000 caracteres)
- status: Enum (TODO, IN_PROGRESS, REVIEW, DONE)
- priority: Enum (LOW, MEDIUM, HIGH, URGENT)
- dueDate: DateTime (opcional)
- createdById: Long/Guid (FK → User)
- assignedToId: Long/Guid (FK → User, opcional)
- projectId: Long/Guid (FK → Project, opcional)
- estimatedHours:  Decimal (opcional)
- actualHours: Decimal (opcional)
- createdAt: DateTime
- updatedAt: DateTime
- completedAt: DateTime (nullable)
```

**3. Project (Proyecto)**
```
- id: Long/Guid (PK)
- name: String (único, max 100 caracteres)
- description: Text (opcional)
- status: Enum (ACTIVE, ARCHIVED, COMPLETED)
- ownerId: Long/Guid (FK → User)
- startDate: DateTime
- endDate: DateTime (opcional)
- createdAt: DateTime
- updatedAt:  DateTime
```

**4. Comment (Comentario)**
```
- id: Long/Guid (PK)
- taskId: Long/Guid (FK → Task)
- userId: Long/Guid (FK → User)
- content: Text (max 1000 caracteres)
- createdAt: DateTime
- updatedAt: DateTime
```

**5. TaskHistory (Historial de cambios)**
```
- id: Long/Guid (PK)
- taskId: Long/Guid (FK → Task)
- userId: Long/Guid (FK → User)
- fieldChanged: String
- oldValue: String
- newValue:  String
- changedAt: DateTime
```

#### Relaciones

- Un **User** puede crear múltiples **Tasks**
- Un **User** puede tener múltiples **Tasks** asignadas
- Un **Project** contiene múltiples **Tasks**
- Una **Task** puede tener múltiples **Comments**
- Una **Task** tiene múltiples registros en **TaskHistory**

---

### 👥 Funcionalidades por Rol

#### Usuario Regular (USER)

| Funcionalidad    | Descripción                                |
| ---------------- | ------------------------------------------ |
| Registro         | Crear cuenta nueva con validación de email |
| Login/Logout     | Autenticación con JWT                      |
| Ver mis tareas   | Listar tareas asignadas a mí               |
| Crear tarea      | Crear nueva tarea y auto-asignarla         |
| Actualizar tarea | Cambiar estado, prioridad, descripción     |
| Comentar tarea   | Agregar comentarios a tareas               |
| Ver proyectos    | Ver proyectos de los que soy miembro       |
| Dashboard        | Vista general de mis tareas pendientes     |
| Filtrar tareas   | Por estado, prioridad, proyecto            |
| Buscar tareas    | Por título o descripción                   |

#### Administrador (ADMIN)

| Funcionalidad        | Descripción                        |
| -------------------- | ---------------------------------- |
| *Todo lo de USER*    | + funcionalidades administrativas  |
| Gestionar usuarios   | CRUD de usuarios                   |
| Asignar tareas       | Asignar tareas a cualquier usuario |
| Gestionar proyectos  | CRUD de proyectos                  |
| Ver todas las tareas | Acceso completo a todas las tareas |
| Reportes             | Estadísticas de productividad      |
| Auditoría            | Ver historial de cambios           |

---

### 🔧 Requisitos Técnicos

#### Backend API REST

**Tecnología:**
- **Opción A**: Spring Boot 3.2+ con Java 21
- **Opción B**: ASP.NET Core 10 con C# 14

**Endpoints Mínimos Requeridos:**

**Autenticación:**
```
POST   /api/auth/register          # Registro de usuario
POST   /api/auth/login             # Login (retorna JWT)
POST   /api/auth/logout            # Logout
GET    /api/auth/me                # Obtener usuario actual
PUT    /api/auth/password          # Cambiar contraseña
```

**Usuarios:**
```
GET    /api/users                  # Listar usuarios (admin)
GET    /api/users/{id}             # Obtener usuario específico
PUT    /api/users/{id}             # Actualizar usuario
DELETE /api/users/{id}             # Eliminar usuario (admin)
GET    /api/users/{id}/tasks       # Tareas del usuario
```

**Tareas:**
```
GET    /api/tasks                  # Listar tareas (filtros:  status, priority, assignedTo, project)
GET    /api/tasks/{id}             # Obtener tarea específica
POST   /api/tasks                  # Crear tarea
PUT    /api/tasks/{id}             # Actualizar tarea
DELETE /api/tasks/{id}             # Eliminar tarea
PATCH  /api/tasks/{id}/status      # Cambiar solo el estado
GET    /api/tasks/{id}/comments    # Comentarios de la tarea
POST   /api/tasks/{id}/comments    # Agregar comentario
GET    /api/tasks/{id}/history     # Historial de cambios
```

**Proyectos:**
```
GET    /api/projects               # Listar proyectos
GET    /api/projects/{id}          # Obtener proyecto específico
POST   /api/projects               # Crear proyecto (admin)
PUT    /api/projects/{id}          # Actualizar proyecto
DELETE /api/projects/{id}          # Eliminar proyecto (admin)
GET    /api/projects/{id}/tasks    # Tareas del proyecto
```

**Estadísticas (admin):**
```
GET    /api/statistics/dashboard   # Dashboard de métricas
GET    /api/statistics/by-user     # Tareas por usuario
GET    /api/statistics/by-project  # Tareas por proyecto
GET    /api/statistics/completion-rate  # Tasa de completitud
```

**Requisitos de la API:**

✅ **Autenticación JWT**:  Todos los endpoints protegidos requieren token válido
✅ **Validación**:  Validar todos los inputs con anotaciones/atributos
✅ **Manejo de errores**: Respuestas consistentes con códigos HTTP apropiados
✅ **Paginación**: Endpoints de listado deben soportar paginación
✅ **CORS**: Configurado para permitir frontend
✅ **Documentación**: Swagger/OpenAPI generado automáticamente
✅ **Health checks**: Endpoints `/health` y `/actuator/health`

**Estructura de respuesta de error:**
```json
{
  "timestamp": "2024-01-15T10:30:00Z",
  "status":  400,
  "error":  "Bad Request",
  "message": "El título de la tarea no puede estar vacío",
  "path": "/api/tasks",
  "errors": [
    {
      "field": "title",
      "message": "must not be blank"
    }
  ]
}
```

---

#### Base de Datos

**Requisitos:**
- PostgreSQL 16
- Migraciones versionadas (Flyway para Java / EF Migrations para .NET)
- Índices en columnas de búsqueda frecuente
- Constraints de integridad referencial
- Datos de prueba (seed)

**Script de datos iniciales (seed. sql):**
- 5 usuarios (1 admin, 4 regulares)
- 3 proyectos
- 20 tareas en diferentes estados
- 30 comentarios
- Historial de cambios

**Índices requeridos:**
```sql
CREATE INDEX idx_tasks_status ON tasks(status);
CREATE INDEX idx_tasks_assigned_to ON tasks(assigned_to_id);
CREATE INDEX idx_tasks_created_by ON tasks(created_by_id);
CREATE INDEX idx_tasks_project ON tasks(project_id);
CREATE INDEX idx_tasks_due_date ON tasks(due_date);
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_username ON users(username);
CREATE INDEX idx_comments_task ON comments(task_id);
CREATE INDEX idx_task_history_task ON task_history(task_id);
```

---

#### Frontend (Vue. js 3)

**Tecnología obligatoria:**
- Vue. js 3 con Composition API
- Vue Router
- Pinia (state management)
- Axios (HTTP client)
- Vite (build tool)
- TypeScript (opcional pero recomendado)

**Páginas Mínimas:**

**1. Login (`/login`)**
- Formulario de autenticación
- Validación de campos
- Mensajes de error claros
- Redirección a dashboard si ya está autenticado
- Link a registro

**2. Registro (`/register`)**
- Formulario de registro
- Validación de email, username, password
- Confirmación de contraseña
- Términos y condiciones
- Redirección automática después de registro

**3. Dashboard (`/dashboard`)**
- Resumen de tareas pendientes
- Tareas asignadas a mí
- Tareas por prioridad
- Gráfico de tareas por estado
- Acceso rápido a crear tarea

**4. Lista de Tareas (`/tasks`)**
- Tabla/lista de tareas con paginación
- Filtros por: 
  - Estado (TODO, IN_PROGRESS, etc.)
  - Prioridad (LOW, MEDIUM, HIGH, URGENT)
  - Proyecto
  - Usuario asignado
- Búsqueda por título/descripción
- Ordenamiento por columnas
- Indicadores visuales de prioridad
- Estado en tiempo real

**5. Detalle de Tarea (`/tasks/{id}`)**
- Información completa de la tarea
- Formulario de edición inline
- Lista de comentarios
- Formulario para agregar comentario
- Historial de cambios
- Botones de cambio de estado
- Asignación de usuario (si es admin)

**6. Crear/Editar Tarea (`/tasks/new`, `/tasks/{id}/edit`)**
- Formulario completo
- Validación en tiempo real
- Selector de proyecto
- Selector de usuario asignado
- Date picker para fecha de vencimiento
- Editor de descripción (textarea o markdown)

**7. Proyectos (`/projects`)**
- Lista de proyectos
- Filtro por estado
- Crear nuevo proyecto (admin)
- Ver tareas del proyecto

**8. Detalle de Proyecto (`/projects/{id}`)**
- Información del proyecto
- Lista de tareas del proyecto
- Estadísticas del proyecto
- Miembros del proyecto

**9. Perfil de Usuario (`/profile`)**
- Información del usuario
- Editar datos personales
- Cambiar contraseña
- Estadísticas personales

**10. Administración de Usuarios (`/admin/users`)** *(solo admin)*
- Lista de todos los usuarios
- Crear/editar/eliminar usuarios
- Activar/desactivar usuarios
- Ver tareas por usuario

**Requisitos UX/UI:**

✅ **Responsive**:  Mobile-first, funcional en smartphones, tablets y desktop
✅ **Feedback visual**: Loading states, toasts/notifications, confirmaciones
✅ **Validación**: Validación de formularios en tiempo real
✅ **Accesibilidad**: Etiquetas ARIA, navegación por teclado
✅ **Performance**: Lazy loading de rutas, optimización de imágenes
✅ **Dark mode** (opcional): Modo oscuro persistente

**Framework CSS:**
- Libre elección (Tailwind CSS, Bootstrap, Vuetify, PrimeVue, etc.)
- Debe ser consistente en toda la aplicación

---

### 🧪 Requisitos de Testing

#### 1. Tests Unitarios

**Cobertura Mínima:  80%**

**Backend - Casos requeridos (mínimo 60 tests):**

**TaskService:**
- ✅ Crear tarea con datos válidos
- ✅ Rechazar tarea sin título
- ✅ Rechazar tarea con fecha de vencimiento en el pasado
- ✅ Actualizar estado de tarea
- ✅ Asignar tarea a usuario
- ✅ Agregar comentario a tarea
- ✅ Registrar cambio en historial
- ✅ Calcular estadísticas de tareas
- ✅ Filtrar tareas por estado
- ✅ Filtrar tareas por prioridad
- ✅ Buscar tareas por título

**UserService:**
- ✅ Registrar usuario con datos válidos
- ✅ Validar formato de email
- ✅ Validar unicidad de username
- ✅ Validar fortaleza de contraseña
- ✅ Hashear password correctamente
- ✅ Autenticar con credenciales correctas
- ✅ Rechazar autenticación con password incorrecta
- ✅ Generar JWT válido
- ✅ Validar JWT expirado
- ✅ Actualizar datos de usuario

**ProjectService:**
- ✅ Crear proyecto
- ✅ Validar nombre único de proyecto
- ✅ Asignar owner al proyecto
- ✅ Listar tareas del proyecto
- ✅ Calcular progreso del proyecto

**Frontend - Casos requeridos (mínimo 40 tests con Vitest):**

**Componentes:**
- ✅ TaskCard renderiza correctamente
- ✅ TaskCard muestra prioridad correcta
- ✅ TaskForm valida campos requeridos
- ✅ TaskList renderiza lista vacía
- ✅ TaskList renderiza múltiples tareas
- ✅ UserMenu muestra información correcta
- ✅ CommentList renderiza comentarios

**Stores (Pinia):**
- ✅ authStore:  login exitoso
- ✅ authStore: logout limpia estado
- ✅ taskStore: fetchTasks carga tareas
- ✅ taskStore: createTask agrega tarea
- ✅ taskStore: updateTask actualiza tarea
- ✅ projectStore: fetchProjects

**Utils:**
- ✅ formatDate formatea correctamente
- ✅ validateEmail acepta emails válidos
- ✅ validateEmail rechaza emails inválidos
- ✅ calculateDaysUntilDue calcula correctamente

---

#### 2. Tests de Integración (Testcontainers)

**Mínimo: 30 tests**

**Casos requeridos:**

**TaskRepository:**
- ✅ CRUD básico de tareas
- ✅ Buscar tareas por estado
- ✅ Buscar tareas asignadas a usuario
- ✅ Buscar tareas por proyecto
- ✅ Buscar tareas con fecha de vencimiento próxima
- ✅ Contar tareas por estado
- ✅ Validar constraint de FK

**UserRepository:**
- ✅ CRUD básico de usuarios
- ✅ Buscar por email
- ✅ Buscar por username
- ✅ Constraint de email único
- ✅ Constraint de username único

**ProjectRepository:**
- ✅ CRUD básico de proyectos
- ✅ Buscar proyectos activos
- ✅ Contar tareas por proyecto

**Servicios con BD real:**
- ✅ Crear tarea y verificar persistencia
- ✅ Actualizar tarea actualiza timestamp
- ✅ Eliminar tarea elimina comentarios asociados
- ✅ Crear proyecto y asignar tareas
- ✅ Cambiar estado de tarea registra historial
- ✅ Transaccionalidad: rollback en error

---

#### 3. Tests de API (Postman/Newman)

**Colección Postman Requerida:  Mínimo 50 requests**

**Organización:**
```
📁 Task Management API
  📁 Authentication (8 requests)
    ├── POST Register - Valid
    ├── POST Register - Duplicate Email
    ├── POST Register - Invalid Password
    ├── POST Login - Valid
    ├── POST Login - Invalid
    ├── GET Me - Authenticated
    ├── GET Me - No Token
    └── POST Logout
  📁 Users (10 requests)
    ├── GET List Users (admin)
    ├── GET List Users (unauthorized)
    ├── GET User by ID
    ├── PUT Update User
    ├── DELETE Delete User (admin)
    └── ...
  📁 Tasks (20 requests)
    ├── GET List Tasks
    ├── GET List Tasks - Filter by Status
    ├── GET List Tasks - Filter by Priority
    ├── GET Task by ID - Exists
    ├── GET Task by ID - Not Found
    ├── POST Create Task - Valid
    ├── POST Create Task - Missing Title
    ├── POST Create Task - Invalid Due Date
    ├── PUT Update Task
    ├── PATCH Update Task Status
    ├── DELETE Delete Task
    ├── GET Task Comments
    ├── POST Add Comment
    └── GET Task History
  📁 Projects (8 requests)
  📁 Statistics (4 requests)
```

**Cada request debe incluir:**
- Tests con `pm.test()`
- Validación de status code
- Validación de estructura de respuesta
- Validación de tipos de datos
- Guardar datos en variables de entorno para requests posteriores

**Ejemplo de tests requeridos:**
```javascript
pm.test("Status code is 201 Created", function () {
    pm.response.to.have. status(201);
});

pm.test("Response has required fields", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property('id');
    pm.expect(jsonData).to.have.property('title');
    pm.expect(jsonData. status).to.equal('TODO');
});

pm.test("Response time is acceptable", function () {
    pm.expect(pm.response.responseTime).to.be.below(500);
});

// Guardar ID para tests posteriores
pm.environment.set("task_id", pm.response.json().id);
```

---

#### 4. Tests E2E (Cypress)

**Mínimo: 8 escenarios completos**

**Escenarios requeridos:**

1. **✅ Flujo completo de registro y login**
   - Registrar nuevo usuario
   - Verificar redirección a dashboard
   - Verificar persistencia después de reload
   - Logout

2. **✅ Crear tarea y verificar en lista**
   - Login
   - Crear nueva tarea
   - Verificar que aparece en lista
   - Verificar datos correctos

3. **✅ Actualizar estado de tarea**
   - Login
   - Buscar tarea
   - Cambiar estado de TODO a IN_PROGRESS
   - Verificar actualización visual
   - Verificar persistencia

4. **✅ Agregar comentario a tarea**
   - Login
   - Abrir detalle de tarea
   - Agregar comentario
   - Verificar que aparece en lista de comentarios

5. **✅ Filtrar tareas por estado**
   - Login
   - Aplicar filtro de estado
   - Verificar que solo muestra tareas del estado seleccionado

6. **✅ Buscar tareas por título**
   - Login
   - Usar barra de búsqueda
   - Verificar resultados correctos

7. **✅ Crear proyecto y asignar tarea**
   - Login como admin
   - Crear proyecto
   - Crear tarea asociada al proyecto
   - Verificar relación

8. **✅ Validación de permisos (admin vs user)**
   - Login como usuario regular
   - Intentar acceder a panel de admin
   - Verificar redirección/error

**Requisitos técnicos:**
- Uso de `data-cy` attributes para selectores
- Comandos personalizados para login
- Interceptar llamadas API con `cy.intercept()`
- Validar respuestas de API
- Screenshots automáticos en fallos
- Videos de ejecución

---

### 🚀 Requisitos de CI/CD

#### Pipeline de Integración Continua (CI)

**Triggers:**
- Push a ramas:  `main`, `develop`, `feature/**`
- Pull requests a `main`
- Manual (workflow_dispatch)

**Jobs requeridos:**

**1. Backend CI:**
```yaml
- Checkout código
- Setup Java/.  NET
- Cachear dependencias
- Compilar proyecto
- Ejecutar tests unitarios
- Ejecutar tests de integración con Testcontainers
- Generar reporte de cobertura
- Verificar cobertura > 80%
- Subir reporte a Codecov
- Análisis de código con SonarQube
- Escaneo de vulnerabilidades
- Build Docker image
- Escaneo de imagen con Trivy
- Push a Docker Hub (solo en main)
```

**2. Frontend CI:**
```yaml
- Checkout código
- Setup Node.js
- Instalar dependencias
- Linting (ESLint)
- Type checking (si usa TypeScript)
- Tests unitarios (Vitest)
- Build para producción
- Verificar tamaño de bundle
```

**3. API Tests:**
```yaml
- Descargar colección Postman
- Ejecutar Newman contra staging
- Generar reporte HTML
- Subir reporte como artifact
```

#### Pipeline de Despliegue Continuo (CD)

**Entornos:**

**Staging:**
- Frontend:  Netlify (deploy preview)
- Backend: Render (servicio staging)
- Base de datos: PostgreSQL en Render (staging)
- Deploy automático en push a `develop`

**Production:**
- Frontend: Netlify (dominio custom)
- Backend: Render (servicio production)
- Base de datos: PostgreSQL en Render (production)
- Deploy automático en push a `main`
- Requiere aprobación manual (GitHub Environment protection)

**Jobs requeridos:**

**1. Deploy Backend:**
```yaml
- Verificar que CI pasó
- Build Docker image (si no se hizo en CI)
- Tag imagen con SHA y version
- Push a Docker Hub
- Trigger Render deploy hook
- Esperar 60 segundos
- Health check del servicio
- Verificar endpoints críticos
- Smoke tests
```

**2. Deploy Frontend:**
```yaml
- Build con variables de entorno correctas
- Deploy a Netlify (automático via integración)
- Verificar deploy exitoso
- Lighthouse audit
- Verificar performance scores
```

**3. Tests E2E Post-Deploy:**
```yaml
- Esperar a que staging esté listo
- Health check de frontend y backend
- Ejecutar Cypress en modo headless
- Generar videos y screenshots
- Subir artifacts
- Generar reporte HTML
- Si fallan, notificar y NO desplegar a producción
```

**4. Notificaciones:**
```yaml
- Comentar en PR con resultados
- Notificar en Slack
- Actualizar GitHub Status Checks
```

---

### 📦 Estructura de Repositorios

**Opción A: Monorepo (recomendado)**

```
task-management/
├── backend/
│   ├── src/
│   ├── Dockerfile
│   ├── build.gradle. kts / . csproj
│   └── ... 
├── frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   ├── vite.config.js
│   └── netlify. toml
├── e2e-tests/
│   ├── cypress/
│   ├── cypress.config.js
│   └── package.json
├── postman/
│   ├── collection. json
│   └── environment. json
├── . github/
│   └── workflows/
│       ├── ci-backend.yml
│       ├── ci-frontend.yml
│       ├── deploy-staging.yml
│       ├── deploy-production.yml
│       └── e2e-tests.yml
├── docs/
│   └── architecture. md
├── docker-compose.yml (para desarrollo local)
├── README.md
└── . gitignore
```

**Opción B: Multi-repo**

```
task-management-backend/
task-management-frontend/
task-management-e2e/
```

---

### 🔒 Secretos y Variables de Entorno

**GitHub Secrets requeridos:**

```
DOCKER_USERNAME              # Docker Hub username
DOCKER_PASSWORD              # Docker Hub token
RENDER_DEPLOY_HOOK_STAGING   # Render deploy hook (staging)
RENDER_DEPLOY_HOOK_PRODUCTION # Render deploy hook (production)
NETLIFY_AUTH_TOKEN           # Netlify token (si manual)
NETLIFY_SITE_ID              # Netlify site ID
SONAR_TOKEN                  # SonarQube token
CODECOV_TOKEN                # Codecov token
SLACK_WEBHOOK                # Slack webhook URL
CYPRESS_RECORD_KEY           # Cypress Dashboard key (opcional)
```

**Variables de entorno por ambiente:**

**Staging:**
```
FRONTEND: 
  VITE_API_URL: https://task-api-staging.onrender.com

BACKEND:
  SPRING_DATASOURCE_URL / ConnectionStrings__DefaultConnection
  JWT_SECRET
  CORS_ALLOWED_ORIGINS:  https://staging--task-app.netlify.app
```

**Production:**
```
FRONTEND:
  VITE_API_URL: https://task-api.onrender.com

BACKEND:
  SPRING_DATASOURCE_URL / ConnectionStrings__DefaultConnection
  JWT_SECRET
  CORS_ALLOWED_ORIGINS: https://task-app.com
```

---

### 📝 Entregables

#### 1. Código Fuente

**Repositorio Git (GitHub) que incluya:**

✅ Todo el código fuente (backend, frontend, tests)
✅ Archivos de configuración (Dockerfile, netlify.toml, etc.)
✅ Workflows de GitHub Actions funcionales
✅ README. md completo (ver formato abajo)
✅ .gitignore apropiado (sin node_modules, build/, secrets)
✅ Commits atómicos con mensajes descriptivos (Conventional Commits recomendado)

**README.md debe incluir:**

```markdown
# Task Management System

## 📋 Descripción
[Breve descripción del proyecto]

## 🏗️ Arquitectura
[Diagrama de arquitectura con servicios y flujo CI/CD]

## 🚀 Tecnologías Utilizadas
- Backend: Spring Boot 3.2 / ASP.NET Core 10
- Frontend: Vue. js 3 + Vite
- Base de datos: PostgreSQL 16
- Despliegue: Netlify + Render
- CI/CD: GitHub Actions

## 📦 Instalación Local

### Prerrequisitos
- Java 21 / .  NET 10
- Node.js 20+
- Docker & Docker Compose
- PostgreSQL 16 (o usar Docker)

### Backend
```bash
cd backend
./gradlew bootRun  # Java
dotnet run         # .  NET
```

### Frontend
```bash
cd frontend
npm install
npm run dev
```

### Docker Compose (stack completo)
```bash
docker-compose up -d
```

## 🧪 Tests

### Tests unitarios
```bash
# Backend
./gradlew test           # Java
dotnet test              # . NET

# Frontend
cd frontend && npm run test: unit
```

### Tests de integración
```bash
./gradlew integrationTest
```

### Tests de API
```bash
cd postman
newman run collection.json -e environment.json
```

### Tests E2E
```bash
cd e2e-tests
npm run cy:run
```

## 🚀 Despliegue

### Staging
- Frontend: https://staging--task-app.netlify. app
- Backend: https://task-api-staging.onrender.com
- Auto-deploy en push a `develop`

### Production
- Frontend: https://task-app.com
- Backend: https://task-api.onrender.com
- Auto-deploy en push a `main`

## 👥 Usuarios de Prueba

| Email             | Password  | Rol   |
| ----------------- | --------- | ----- |
| admin@example.com | Admin123! | ADMIN |
| user@example.com  | User123!  | USER  |

## 📊 Pipelines CI/CD

### Status Badges
![Backend CI](https://github.com/user/repo/workflows/Backend%20CI/badge.svg)
![Frontend CI](https://github.com/user/repo/workflows/Frontend%20CI/badge.svg)
![E2E Tests](https://github.com/user/repo/workflows/E2E%20Tests/badge.svg)

### Flujo
1. Push a rama → CI ejecuta tests
2. Merge a develop → Deploy a staging
3. Tests E2E en staging
4. Merge a main → Deploy a production (requiere aprobación)

## 📈 Cobertura de Código
- Backend: 85% (ver [Codecov](https://codecov.io/gh/user/repo))
- Frontend: 80%

## 📚 Documentación
- [API Documentation (Swagger)](https://task-api.onrender.com/swagger-ui. html)
- [Architecture Decisions](docs/architecture.md)
- [API Postman Collection](postman/collection. json)

---

#### 2. Documentación Técnica

**ARCHITECTURE.md:**
- Diagrama de arquitectura del sistema
- Explicación de decisiones técnicas
- Flujo de datos entre componentes
- Estrategia de autenticación (JWT)
- Gestión de estados (Pinia)

**CI_CD.md:**
- Descripción detallada de cada workflow
- Explicación de jobs y steps
- Gestión de secretos
- Estrategia de branching (Git Flow)
- Proceso de deployment

**TESTING.md:**
- Estrategia de testing en cada nivel
- Cómo ejecutar cada tipo de test
- Interpretación de reportes
- Cobertura alcanzada y justificación

---

#### 3. Reportes de Tests

**A entregar como artifacts:**

✅ **Reporte de cobertura de código** (HTML):
   - JaCoCo para Java
   - Coverlet para .  NET
   - Vitest coverage para frontend

✅ **Reporte de tests de API** (Newman HTML)

✅ **Reporte de tests E2E** (Mochawesome HTML)

✅ **Screenshots de Cypress** (en caso de fallos durante desarrollo)

✅ **Reporte de Lighthouse** (performance audit)

---

#### 4. Demostración en Vivo

**Preparar para presentación:**

✅ **Aplicación desplegada y funcionando:**
   - URL de staging accesible
   - URL de producción accesible
   - Usuarios de prueba funcionales

✅ **Demostración de CI/CD:**
   - Mostrar workflow ejecutándose
   - Explicar cada fase
   - Mostrar artifacts generados

✅ **Demostración de funcionalidades:**
   - Registro y login
   - Crear y gestionar tareas
   - Filtros y búsqueda
   - Comentarios
   - Panel de administración

---

### 🎯 Criterios de Evaluación

| Criterio          | Peso | Descripción                                           |
| ----------------- | ---- | ----------------------------------------------------- |
| **Funcionalidad** | 20%  | La aplicación cumple todos los requisitos funcionales |
| **Pipeline CI**   | 20%  | CI completo con tests automatizados                   |
| **Pipeline CD**   | 15%  | Deploy automatizado a staging y production            |
| **Testing**       | 20%  | Cobertura > 80%, tests en todos los niveles           |
| **Código**        | 10%  | Calidad, estructura, buenas prácticas                 |
| **Documentación** | 10%  | README completo, documentación técnica clara          |
| **Despliegue**    | 5%   | Aplicación accesible y funcionando en producción      |

---

#### Desglose Detallado de "Pipeline CI" (20%)

**Tests Unitarios (6%):**
- ✅ Cobertura > 80% (3%)
- ✅ Tests bien estructurados (2%)
- ✅ Uso correcto de mocks (1%)

**Tests de Integración (6%):**
- ✅ Testcontainers funcionando (2%)
- ✅ Tests de repositorios completos (2%)
- ✅ Validación de constraints (2%)

**Análisis de Código (4%):**
- ✅ SonarQube integrado (2%)
- ✅ Sin code smells críticos (1%)
- ✅ Sin vulnerabilidades (1%)

**Build Automatizado (4%):**
- ✅ Build exitoso en CI (2%)
- ✅ Docker image generada (1%)
- ✅ Optimización de caché (1%)

---

#### Desglose de "Pipeline CD" (15%)

**Deploy Automatizado (5%):**
- ✅ Deploy a staging automático (2%)
- ✅ Deploy a production con aprobación (2%)
- ✅ Rollback funcional (1%)

**Tests E2E en Staging (5%):**
- ✅ Cypress ejecutándose en CI (2%)
- ✅ Tests de flujos críticos (2%)
- ✅ Gestión de artifacts (1%)

**Monitorización (3%):**
- ✅ Health checks (1%)
- ✅ Smoke tests (1%)
- ✅ Notificaciones (1%)

**Deploy Hooks (2%):**
- ✅ Integración con Render (1%)
- ✅ Variables de entorno correctas (1%)

---

#### Desglose de "Testing" (20%)

**Unitarios (7%):**
- Mínimo 60 tests backend (4%)
- Mínimo 40 tests frontend (3%)

**Integración (5%):**
- Mínimo 30 tests (3%)
- Testcontainers funcionando (2%)

**API (4%):**
- Colección Postman completa (2%)
- Tests con validaciones (2%)

**E2E (4%):**
- Mínimo 8 escenarios (3%)
- Selectores resilientes (1%)

---

### 💡 Consejos y Recomendaciones

#### Planificación

**Semana 1:**
- ✅ Setup del proyecto (backend + frontend + BD)
- ✅ Modelo de datos y migraciones
- ✅ Autenticación JWT
- ✅ CRUD básico de tareas

**Semana 2:**
- ✅ Frontend: Componentes principales
- ✅ Integración frontend-backend
- ✅ Tests unitarios (backend y frontend)
- ✅ Docker Compose para desarrollo local

**Semana 3:**
- ✅ Tests de integración con Testcontainers
- ✅ Colección Postman completa
- ✅ Pipeline CI en GitHub Actions
- ✅ Dockerización del backend

**Semana 4:**
- ✅ Deploy a Netlify y Render
- ✅ Pipeline CD completo
- ✅ Tests E2E con Cypress
- ✅ Documentación y refinamiento

#### Estrategia de Desarrollo

**1. Backend primero:**
Desarrolla y prueba la API antes del frontend.  Usa Postman para validar endpoints.

**2. Tests mientras desarrollas:**
No dejes los tests para el final. Escribe tests unitarios junto con el código.

**3. Commits frecuentes:**
Commits pequeños y atómicos con mensajes descriptivos. 

**4. Branching:**
```
main (production)
  ↑
develop (staging)
  ↑
feature/auth
feature/tasks
feature/frontend
```

**5. Pull Requests:**
- Crear PR de feature a develop
- CI debe pasar antes de merge
- Code review (si trabajas en equipo)

#### Errores Comunes a Evitar

❌ **CORS mal configurado**:  Frontend no puede comunicarse con backend
❌ **Secretos en el código**: Passwords, tokens en el repositorio
❌ **Tests frágiles**: Tests que fallan aleatoriamente
❌ **Build lento**: No aprovechar caché de dependencias
❌ **Sin health checks**: Render despliega pero el servicio no funciona
❌ **Variables de entorno incorrectas**: URL de API mal configurada
❌ **Cold start no anticipado**: Primera request a staging tarda 60 segundos
❌ **Sin datos de prueba**: Aplicación desplegada pero vacía

---



---

## 🎓 Conclusión

Esta práctica integradora representa el **nivel profesional** de un desarrollador full-stack moderno con conocimientos DevOps. Al completarla exitosamente, habrás demostrado capacidad para: 

✅ Desarrollar aplicaciones **full-stack complejas**
✅ Implementar **pipelines CI/CD completos**
✅ Escribir **tests en todos los niveles**
✅ **Dockerizar** aplicaciones
✅ **Desplegar** a producción con confianza
✅ **Documentar** y comunicar decisiones técnicas

Estas son las competencias que las empresas buscan en desarrolladores senior y DevOps engineers. 

💡 **Nota del Profesor Final**: Este proyecto es desafiante intencionalmente. No busquéis perfección en el primer intento. Desarrollad incrementalmente, probad constantemente y no tengáis miedo de experimentar.  Los errores son parte del aprendizaje.  El objetivo no es solo entregar código funcionando, sino **entender profundamente** cómo funciona el ciclo completo de desarrollo moderno.

¡Adelante! 🚀


¡Buena suerte con el proyecto! 🎉📚💻