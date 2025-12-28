# Despliegue de Aplicaciones Web - 07 - Integración y Despliegue Continuo (CI/CD)

Tema 07. Integración y Despliegue Continuo (CI/CD). 2DAW. Curso 2025-2026.

![imagen](https://github.com/joseluisgs/DespliegueAplicacionesWeb-00-2024-2025/raw/master/images/despliegue.png)

- [Despliegue de Aplicaciones Web - 07 - Integración y Despliegue Continuo (CI/CD)](#despliegue-de-aplicaciones-web---07---integración-y-despliegue-continuo-cicd)
- [Contenido en Youtube](#contenido-en-youtube)
  - [1. Fundamentos de la Automatización en el Ciclo de Vida](#1-fundamentos-de-la-automatización-en-el-ciclo-de-vida)
    - [Introducción:  El Problema que Resuelve CI/CD](#introducción--el-problema-que-resuelve-cicd)
    - [1.1. Filosofía DevOps: El Flujo de Entrega Continua](#11-filosofía-devops-el-flujo-de-entrega-continua)
      - [El Problema de los Silos Tradicionales](#el-problema-de-los-silos-tradicionales)
      - [La Filosofía DevOps](#la-filosofía-devops)
      - [Principios Fundamentales de DevOps](#principios-fundamentales-de-devops)
    - [1.2. Conceptos Clave](#12-conceptos-clave)
      - [Integración Continua (Continuous Integration - CI)](#integración-continua-continuous-integration---ci)
      - [Entrega Continua (Continuous Delivery - CD)](#entrega-continua-continuous-delivery---cd)
      - [Despliegue Continuo (Continuous Deployment - CD)](#despliegue-continuo-continuous-deployment---cd)
    - [Comparación Visual de los Tres Conceptos](#comparación-visual-de-los-tres-conceptos)
    - [1.3. Evolución de Herramientas:  GitHub Actions vs Jenkins](#13-evolución-de-herramientas--github-actions-vs-jenkins)
      - [Contexto Histórico](#contexto-histórico)
      - [Comparativa Técnica Detallada](#comparativa-técnica-detallada)
      - [Análisis en Profundidad](#análisis-en-profundidad)
      - [¿Por Qué Enseñar GitHub Actions en Este Curso?](#por-qué-enseñar-github-actions-en-este-curso)
  - [2. GitHub Actions como Motor de CI/CD](#2-github-actions-como-motor-de-cicd)
    - [Introducción:  La Arquitectura de GitHub Actions](#introducción--la-arquitectura-de-github-actions)
    - [2.1. Componentes del Ecosistema](#21-componentes-del-ecosistema)
      - [Anatomía de un Workflow](#anatomía-de-un-workflow)
      - [Workflows:  Definición en YAML](#workflows--definición-en-yaml)
      - [Events: Disparadores de Workflows](#events-disparadores-de-workflows)
      - [Combinación de Eventos](#combinación-de-eventos)
      - [Jobs: Unidades de Ejecución](#jobs-unidades-de-ejecución)
      - [Steps: Tareas Individuales](#steps-tareas-individuales)
      - [Runners: Entornos de Ejecución](#runners-entornos-de-ejecución)
      - [Contexts y Expresiones](#contexts-y-expresiones)
    - [Ejemplo Completo: Workflow CI/CD Avanzado](#ejemplo-completo-workflow-cicd-avanzado)
    - [2. 2. Seguridad y Secretos](#2-2-seguridad-y-secretos)
      - [GitHub Secrets:  Gestión Segura de Credenciales](#github-secrets--gestión-segura-de-credenciales)
      - [Variables de Entorno](#variables-de-entorno)
      - [Contextos Dinámicos y Outputs](#contextos-dinámicos-y-outputs)
  - [3. Pipeline de Integración Continua (CI)](#3-pipeline-de-integración-continua-ci)
    - [Introducción:  Anatomía de un Pipeline CI Profesional](#introducción--anatomía-de-un-pipeline-ci-profesional)
    - [3.1. Automatización del Build](#31-automatización-del-build)
      - [Java con Gradle (Kotlin DSL)](#java-con-gradle-kotlin-dsl)
      - [GitHub Actions Workflow para Java](#github-actions-workflow-para-java)
      - [Optimizaciones del Pipeline Java](#optimizaciones-del-pipeline-java)
    - [. NET 10 \& C# 14](#-net-10--c-14)
      - [GitHub Actions Workflow para . NET](#github-actions-workflow-para--net)
      - [Dockerfile para .NET (Multi-stage)](#dockerfile-para-net-multi-stage)
    - [3.2. Ejecución de la Suite de Tests](#32-ejecución-de-la-suite-de-tests)
      - [Testcontainers en el Pipeline](#testcontainers-en-el-pipeline)
    - [3.3. Control de Calidad y Cobertura](#33-control-de-calidad-y-cobertura)
      - [Configuración de JaCoCo (Java)](#configuración-de-jacoco-java)
      - [Configuración de Coverlet (. NET)](#configuración-de-coverlet--net)
  - [4. Automatización del Frontend en Netlify](#4-automatización-del-frontend-en-netlify)
    - [Introducción:  Por Qué Netlify para Frontends](#introducción--por-qué-netlify-para-frontends)
    - [4.1. Flujo de Trabajo Netlify-GitHub](#41-flujo-de-trabajo-netlify-github)
      - [Arquitectura de Integración](#arquitectura-de-integración)
      - [🛠️ Paso a Paso: Configuración Inicial](#️-paso-a-paso-configuración-inicial)
      - [Configuración Avanzada: netlify.toml](#configuración-avanzada-netlifytoml)
      - [Configuración de Redirects para SPAs](#configuración-de-redirects-para-spas)
    - [4.2. Preview Deployments:  Entornos Temporales por PR](#42-preview-deployments--entornos-temporales-por-pr)
      - [Flujo de Trabajo](#flujo-de-trabajo)
      - [Configuración de Deploy Previews](#configuración-de-deploy-previews)
      - [Integración con GitHub Checks](#integración-con-github-checks)
    - [4.3. Variables de Entorno por Contexto](#43-variables-de-entorno-por-contexto)
      - [Configuración en Netlify UI](#configuración-en-netlify-ui)
      - [Configuración en netlify.toml](#configuración-en-netlifytoml)
      - [Uso en Vue. js](#uso-en-vue-js)
    - [Configuración de Dominios Personalizados](#configuración-de-dominios-personalizados)
      - [Agregar Dominio Custom](#agregar-dominio-custom)
      - [Configuración de Apex Domain (sin www)](#configuración-de-apex-domain-sin-www)
      - [Configuración de Subdominios Múltiples](#configuración-de-subdominios-múltiples)
    - [Optimizaciones y Best Practices](#optimizaciones-y-best-practices)
      - [1. Build Plugins](#1-build-plugins)
      - [2. Asset Optimization](#2-asset-optimization)
      - [3. Caché Estratégico](#3-caché-estratégico)
      - [4. Prerendering para SEO](#4-prerendering-para-seo)
      - [5. Split Testing (A/B Testing)](#5-split-testing-ab-testing)
    - [Integración con GitHub Actions](#integración-con-github-actions)
    - [Monitorización y Debugging](#monitorización-y-debugging)
      - [Logs de Build](#logs-de-build)
      - [Analytics](#analytics)
      - [Deploy Notifications](#deploy-notifications)
    - [Ejemplo Completo: Proyecto Vue + Netlify](#ejemplo-completo-proyecto-vue--netlify)
- [UD 7: Integración y Despliegue Continuo (CI/CD) - Continuación](#ud-7-integración-y-despliegue-continuo-cicd---continuación)
  - [5. Contenerización y Despliegue del Backend en Render](#5-contenerización-y-despliegue-del-backend-en-render)
    - [Introducción:  Por Qué Render para Backends](#introducción--por-qué-render-para-backends)
    - [5.1. Ciclo de Vida de la Imagen Docker](#51-ciclo-de-vida-de-la-imagen-docker)
      - [Flujo Completo:  Código → Contenedor → Producción](#flujo-completo--código--contenedor--producción)
      - [🛠️ Paso a Paso: Dockerfile Multi-Stage Optimizado](#️-paso-a-paso-dockerfile-multi-stage-optimizado)
      - [Optimizaciones Avanzadas del Dockerfile](#optimizaciones-avanzadas-del-dockerfile)
    - [5.2. Orquestación en Render](#52-orquestación-en-render)
      - [🛠️ Paso a Paso: Configuración de Servicio en Render](#️-paso-a-paso-configuración-de-servicio-en-render)
      - [Deploy Hooks:  Automatización desde CI/CD](#deploy-hooks--automatización-desde-cicd)
      - [Estrategias de Tagging](#estrategias-de-tagging)
    - [5.3. El Concepto de Cold Start](#53-el-concepto-de-cold-start)
      - [¿Qué es un Cold Start?](#qué-es-un-cold-start)
      - [Estrategias para Mitigar Cold Starts](#estrategias-para-mitigar-cold-starts)
      - [Configuración de render.yaml (Infrastructure as Code)](#configuración-de-renderyaml-infrastructure-as-code)
      - [Monitorización en Render](#monitorización-en-render)
      - [Ejemplo de Configuración Completa](#ejemplo-de-configuración-completa)
    - [Resumen del Punto 5](#resumen-del-punto-5)
- [UD 7: Integración y Despliegue Continuo (CI/CD) - Continuación](#ud-7-integración-y-despliegue-continuo-cicd---continuación-1)
  - [6. Validación Final E2E y Documentación](#6-validación-final-e2e-y-documentación)
    - [Introducción:  La Última Línea de Defensa](#introducción--la-última-línea-de-defensa)
    - [6.1. Cypress en el Pipeline](#61-cypress-en-el-pipeline)
      - [Arquitectura de Tests E2E en CI/CD](#arquitectura-de-tests-e2e-en-cicd)
      - [🛠️ Paso a Paso: Configuración de Cypress para CI](#️-paso-a-paso-configuración-de-cypress-para-ci)
      - [GitHub Actions Workflow para Cypress](#github-actions-workflow-para-cypress)
      - [Gestión de Artefactos](#gestión-de-artefactos)
    - [6. 2. Generación de Documentación Técnica](#6-2-generación-de-documentación-técnica)
      - [Importancia de la Documentación Automatizada](#importancia-de-la-documentación-automatizada)
      - [Javadoc para Java](#javadoc-para-java)
      - [DocFX para . NET](#docfx-para--net)
      - [Publicación en GitHub Pages](#publicación-en-github-pages)
- [Autor](#autor)
  - [Contacto](#contacto)
  - [Licencia de uso](#licencia-de-uso)


# Contenido en Youtube

- [Podcast](https://youtu.be/IrFU6U_d7YI)
- [Resumen](https://youtu.be/TbotPkOe2hk)
- [Lista de Reproducción](https://www.youtube.com/watch?v=HX2gSuX0oow&list=PLGIH-7eZDbVxu55hmqqdQE-Ba6FdPoO-Z)


---

## 1. Fundamentos de la Automatización en el Ciclo de Vida

### Introducción:  El Problema que Resuelve CI/CD

Imagina este escenario común en desarrollo de software: 

> **Viernes, 17:00h**:  El equipo de desarrollo termina una nueva funcionalidad. Todo funciona en sus máquinas. 
> 
> **Viernes, 17:30h**: Se sube el código al repositorio y se notifica al equipo de sistemas.
> 
> **Lunes, 9:00h**:  Sistemas intenta desplegar en staging.  El proceso de build falla porque falta una dependencia.
> 
> **Lunes, 11:00h**: Se corrige la dependencia, pero los tests fallan en el servidor (aunque funcionaban localmente).
> 
> **Lunes, 15:00h**: Se descubre que la base de datos de staging tiene un esquema desactualizado.
> 
> **Martes, 10:00h**:  Finalmente se despliega en staging. QA empieza a probar. 
> 
> **Miércoles, 16:00h**: Se aprueba para producción. 
> 
> **Jueves, 9:00h**: El despliegue a producción falla porque las credenciales están desactualizadas. 

**Resultado**: Una funcionalidad que tardó 3 días en desarrollarse tardó **6 días más** en llegar a producción, con múltiples intervenciones manuales, errores y frustración del equipo.

**CI/CD resuelve este problema** automatizando cada paso del proceso:  construcción, testing, empaquetado y despliegue. 

💡 **Nota del Profesor**: CI/CD no es una herramienta, es una **cultura y una práctica**. Las herramientas (GitHub Actions, Jenkins, GitLab CI) son solo medios para implementar esta filosofía.

---

### 1.1. Filosofía DevOps: El Flujo de Entrega Continua

#### El Problema de los Silos Tradicionales

En modelos tradicionales de desarrollo de software, existen **barreras organizativas** que ralentizan la entrega:

```
┌──────────────┐      ┌──────────────┐      ┌──────────────┐
│ Desarrollo   │      │    QA        │      │  Operaciones │
│              │      │              │      │   (Ops)      │
│ "Funciona en │ -->  │ "Encuentra   │ -->  │ "No sabemos  │
│  mi máquina" │      │  bugs"       │      │  desplegarlo"│
└──────────────┘      └──────────────┘      └──────────────┘
       ↓                      ↓                      ↓
   Código listo        Tests manuales        Deploy manual
   (días)              (días/semanas)        (días/semanas)
                                                     ↓
                                            "Funciona diferente
                                             en producción"
```

**Problemas de este modelo:**

- ❌ **Comunicación lenta**: Cada equipo tiene sus propias prioridades y herramientas
- ❌ **Procesos manuales**: Propensos a errores humanos
- ❌ **Feedback tardío**: Los bugs se descubren semanas después de escribir el código
- ❌ **"Funciona en mi máquina"**:  Diferencias entre entornos de desarrollo y producción
- ❌ **Miedo al despliegue**: Los deploys son eventos traumáticos que requieren horas extra
- ❌ **Rollbacks complejos**: Volver atrás es difícil y arriesgado

#### La Filosofía DevOps

**DevOps** fusiona **Development** (Desarrollo) y **Operations** (Operaciones) en un único flujo de trabajo colaborativo:

```
┌─────────────────────────────────────────────────────────────┐
│                    Equipo DevOps Unificado                  │
│                                                             │
│  Desarrolladores + QA + Ops trabajando juntos              │
│                                                             │
│  Principios:                                                │
│  • Automatización de todo lo automatizable                 │
│  • Infraestructura como código (IaC)                       │
│  • Monitorización y feedback continuo                      │
│  • Despliegues frecuentes y pequeños                       │
│  • Cultura de responsabilidad compartida                   │
└─────────────────────────────────────────────────────────────┘
         ↓                    ↓                    ↓
    Código nuevo      Tests automáticos      Deploy automático
    (minutos)          (minutos)              (minutos)
                            ↓
                  Feedback inmediato
                  en cada commit
```

**Beneficios del modelo DevOps:**

- ✅ **Entregas rápidas**: De semanas a minutos
- ✅ **Mayor calidad**: Tests automáticos en cada cambio
- ✅ **Menos errores**: Automatización elimina errores humanos
- ✅ **Feedback inmediato**: Los desarrolladores saben en minutos si algo falló
- ✅ **Deploys frecuentes**: Cambios pequeños = menor riesgo
- ✅ **Rollbacks simples**: Volver a la versión anterior es trivial

#### Principios Fundamentales de DevOps

**1. Automatización Total**

Todo proceso repetible debe automatizarse: 
- Construcción de código
- Ejecución de tests
- Análisis de calidad
- Generación de artefactos
- Despliegue a entornos
- Configuración de infraestructura
- Monitorización y alertas

**2. Infraestructura como Código (IaC)**

Los servidores, redes y configuraciones se definen en archivos de código: 

```yaml
# Ejemplo:  docker-compose.yml
version: '3.8'
services:
  backend:
    image: myapp:latest
    environment: 
      - DATABASE_URL=${DB_URL}
    deploy:
      replicas: 3
      restart_policy:
        condition: on-failure
```

**Ventajas:**
- Reproducibilidad: El mismo archivo genera el mismo entorno
- Versionado: Los cambios de infraestructura están en Git
- Revisión: Se pueden hacer pull requests de cambios de infraestructura

**3. Cultura de "You Build It, You Run It"**

Los desarrolladores son responsables de: 
- Escribir el código
- Escribir los tests
- Configurar el pipeline
- Monitorizar en producción
- Responder a incidentes

Esto genera: 
- Mayor empatía con los usuarios
- Código más robusto (quien lo escribe lo mantiene)
- Feedback directo sobre la calidad

**4. Medición y Monitorización Continua**

Se miden métricas clave: 
- **DORA Metrics** (DevOps Research and Assessment):
  - **Deployment Frequency**: Frecuencia de despliegue
  - **Lead Time for Changes**: Tiempo desde commit hasta producción
  - **Change Failure Rate**: % de deploys que causan problemas
  - **Time to Restore Service**: Tiempo para recuperarse de un fallo

**Ejemplo de métricas de un equipo maduro:**

| Métrica         | Equipo Tradicional | Equipo DevOps Elite |
| --------------- | ------------------ | ------------------- |
| Deploys por día | < 1 por mes        | Múltiples por día   |
| Lead time       | Semanas/meses      | < 1 hora            |
| Failure rate    | 30-45%             | < 5%                |
| Recovery time   | Días               | < 1 hora            |

**5. Shift Left:  Detectar Problemas Temprano**

El concepto de **"Shift Left"** significa mover la detección de problemas lo más a la izquierda posible en el ciclo de vida: 

```
Desarrollo → Build → Test → Deploy → Producción
     ↑          ↑      ↑       ↑          ↑
   Aquí       Aquí   Aquí    Aquí       AQUÍ
  (barato)   (barato)        (caro)   (MUY CARO)
```

**Cuanto antes se detecta un bug, menos cuesta corregirlo.**

---

### 1.2. Conceptos Clave

#### Integración Continua (Continuous Integration - CI)

**Definición:**

La práctica de **fusionar** los cambios de código de todos los desarrolladores en un repositorio compartido **varias veces al día**, con validación automatizada en cada fusión.

**El Problema que Resuelve:**

Antes de CI, los equipos trabajaban en ramas aisladas durante semanas. Cuando intentaban fusionar al final, surgían **"integration hells"** (infiernos de integración):

```
Developer A:    ━━━━━━━━━━━━━━━━━━━━━━━━ (3 semanas en rama)
Developer B:   ━━━━━━━━━━━━━━━━━━━━━━━━ (3 semanas en rama)
Developer C:   ━━━━━━━━━━━━━━━━━━━━━━━━ (3 semanas en rama)
                                    ↓
                         Intentar fusionar todo
                                    ↓
                    🔥 CONFLICTOS MASIVOS 🔥
                    (días/semanas resolviendo)
```

**Con CI:**

```
Developer A:   ━━━ ━━━ ━━━ ━━━ ━━━ ━━━ (fusiones diarias)
                 ↓   ↓   ↓   ↓   ↓   ↓
Main:         ━━━━━━━━━━━━━━━━━━━━━━━━━━ (siempre actualizado)
                 ↑   ↑   ↑   ↑   ↑   ↑
Developer B:    ━━━ ━━━ ━━━ ━━━ ━━━ ━━━
Developer C:   ━━━ ━━━ ━━━ ━━━ ━━━ ━━━

Conflictos pequeños y frecuentes = Fáciles de resolver
```

**Flujo de CI:**

```mermaid
graph LR
    A[Developer:  git push] --> B[CI Server detecta cambio]
    B --> C[Checkout código]
    C --> D[Instalar dependencias]
    D --> E[Compilar/Build]
    E --> F[Ejecutar tests unitarios]
    F --> G[Ejecutar tests de integración]
    G --> H[Análisis de código]
    H --> I{¿Todo OK?}
    I -->|Sí| J[✅ Build exitoso]
    I -->|No| K[❌ Build fallido]
    J --> L[Notificar éxito]
    K --> M[Notificar fallo + logs]
```

**Prácticas Esenciales de CI:**

1. **Repositorio único** (monorepo o múltiples repos bien organizados)
2. **Builds automatizados** (un solo comando para compilar todo)
3. **Tests automáticos** (ejecutados en cada commit)
4. **Builds rápidos** (idealmente < 10 minutos)
5. **Ambiente de staging** idéntico a producción
6. **Visibilidad**:  Todos ven el estado del build (dashboards, notificaciones)

**Ejemplo de GitHub Actions para CI (Java):**

```yaml
name:  Continuous Integration

on:
  push:
    branches: [ main, develop ]
  pull_request: 
    branches: [ main ]

jobs:
  build-and-test:
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout código
        uses: actions/checkout@v4
      
      - name:  Configurar JDK 21
        uses: actions/setup-java@v4
        with:
          java-version: '21'
          distribution: 'temurin'
      
      - name: Caché de Gradle
        uses: actions/cache@v3
        with:
          path:  |
            ~/.gradle/caches
            ~/.gradle/wrapper
          key: ${{ runner.os }}-gradle-${{ hashFiles('**/*.gradle*', '**/gradle-wrapper.properties') }}
      
      - name: Compilar proyecto
        run: ./gradlew build
      
      - name:  Ejecutar tests unitarios
        run: ./gradlew test
      
      - name: Ejecutar tests de integración
        run: ./gradlew integrationTest
      
      - name: Generar reporte de cobertura
        run: ./gradlew jacocoTestReport
      
      - name: Verificar cobertura mínima
        run: ./gradlew jacocoTestCoverageVerification
      
      - name:  Subir reporte de cobertura
        uses: actions/upload-artifact@v3
        if: always()
        with:
          name: coverage-report
          path: build/reports/jacoco/test/html/
```

---

#### Entrega Continua (Continuous Delivery - CD)

**Definición:**

Extensión de CI donde **cada cambio que pasa las validaciones automáticas** está listo para ser desplegado a producción, pero el despliegue final requiere **aprobación manual**.

**El Pipeline Completo:**

```
Código → Build → Test → Package → Deploy Staging → Tests E2E
                                          ↓
                                  👤 Aprobación Manual
                                          ↓
                                   Deploy Producción
```

**Características:**

- ✅ Todo el proceso hasta staging es automático
- ✅ Los artefactos (JARs, contenedores Docker) se generan automáticamente
- ✅ Los despliegues a staging ocurren en cada commit exitoso
- ⚠️ El paso a producción requiere un "botón" humano
- ✅ En teoría, se puede desplegar a producción en cualquier momento

**¿Por qué mantener aprobación manual?**

- Coordinación con marketing para lanzamientos
- Despliegues en ventanas de mantenimiento específicas
- Validación final de negocio
- Cumplimiento normativo (sectores regulados)

**Ejemplo de Workflow con Entrega Continua:**

```yaml
name: Continuous Delivery

on:
  push:
    branches: [ main ]

jobs:
  # ... jobs de CI (build, test) ...
  
  deploy-staging:
    needs: build-and-test
    runs-on: ubuntu-latest
    environment: staging
    
    steps: 
      - name: Desplegar a Staging
        run: |
          echo "Desplegando a staging..."
          # Comandos de despliegue automático
  
  # Este job requiere aprobación manual
  deploy-production:
    needs:  deploy-staging
    runs-on: ubuntu-latest
    environment:  production  # Environment con protección
    
    steps: 
      - name: Desplegar a Producción
        run:  |
          echo "Desplegando a producción..."
          # Comandos de despliegue
```

**Configuración de Environment con Aprobación Manual en GitHub:**

En GitHub: 
1. Settings → Environments → New environment
2. Nombre: `production`
3. Habilitar "Required reviewers"
4. Agregar usuarios que deben aprobar

**Flujo con aprobación:**

```
1. Developer hace push a main
2. CI:  Build + Tests (automático) ✅
3. CD: Deploy a staging (automático) ✅
4. CD: Tests E2E en staging (automático) ✅
5. GitHub envía notificación:  "Waiting for approval"
6. 👤 Tech Lead revisa staging y aprueba
7. CD: Deploy a producción (automático) ✅
```

---

#### Despliegue Continuo (Continuous Deployment - CD)

**Definición:**

Todo cambio que pasa las validaciones automáticas es **desplegado automáticamente a producción** sin intervención humana.

**Diferencia clave con Continuous Delivery:**

| Continuous Delivery          | Continuous Deployment       |
| ---------------------------- | --------------------------- |
| Listo para producción        | En producción               |
| Requiere aprobación manual   | 100% automático             |
| Deploy = decisión de negocio | Deploy = resultado de tests |

**El Pipeline Sin Intervención Humana:**

```
Código → Build → Test → Package → Deploy Staging → Tests E2E
                                          ↓
                                    ✅ Tests OK? 
                                          ↓
                                   Deploy Producción
                                          ↓
                                  Monitorización Activa
                                          ↓
                            Rollback automático si falla
```

**Requisitos para Despliegue Continuo:**

Para que esto sea seguro, se necesita:

1. **Confianza extrema en los tests**:
   - Cobertura > 80%
   - Tests E2E robustos
   - Tests de regresión completos

2. **Monitorización avanzada**:
   - Métricas en tiempo real
   - Alertas automáticas
   - Trazabilidad completa

3. **Feature Flags**:
   - Activar/desactivar funcionalidades sin redesplegar
   - Rollout progresivo (10% → 50% → 100% usuarios)

4. **Rollback automático**:
   - Capacidad de volver a la versión anterior en segundos
   - Blue-Green deployments o Canary releases

5. **Cultura de calidad**:
   - Todo el equipo comprometido con la calidad
   - Revisiones de código estrictas
   - Tests escritos antes/junto con el código

**Ejemplo de Despliegue Continuo con Feature Flags:**

```java
@Service
public class PaymentService {
    
    @Autowired
    private FeatureFlagService featureFlags;
    
    public void processPayment(Payment payment) {
        if (featureFlags.isEnabled("new-payment-gateway")) {
            // Nueva implementación (en producción pero desactivada)
            newPaymentGateway.process(payment);
        } else {
            // Implementación antigua (activa)
            oldPaymentGateway.process(payment);
        }
    }
}
```

**Rollout progresivo:**

```
Día 1: new-payment-gateway habilitado para 1% usuarios
       ↓ (Monitorizar errores, latencia, tasas de éxito)
Día 2: Si OK → 10% usuarios
       ↓
Día 3: Si OK → 25% usuarios
       ↓
Día 4: Si OK → 50% usuarios
       ↓
Día 5: Si OK → 100% usuarios
       ↓
Día 6: Eliminar código antiguo en próximo release
```

**Ejemplo de GitHub Actions con Despliegue Continuo:**

```yaml
name: Continuous Deployment

on:
  push:
    branches: [ main ]

jobs:
  deploy: 
    runs-on: ubuntu-latest
    
    steps: 
      - uses: actions/checkout@v4
      
      - name: Build & Test
        run: |
          ./gradlew build test
      
      - name: Build Docker Image
        run: |
          docker build -t myapp:${{ github.sha }} .
      
      - name: Push to Registry
        run: |
          echo "${{ secrets.DOCKER_PASSWORD }}" | docker login -u "${{ secrets.DOCKER_USERNAME }}" --password-stdin
          docker push myapp:${{ github. sha }}
      
      - name: Deploy to Production
        run: |
          kubectl set image deployment/myapp myapp=myapp:${{ github.sha }}
          kubectl rollout status deployment/myapp
      
      - name: Verificar Salud del Servicio
        run: |
          sleep 30
          response=$(curl -s -o /dev/null -w "%{http_code}" https://api.myapp.com/health)
          if [ $response -ne 200 ]; then
            echo "Health check failed!"
            kubectl rollout undo deployment/myapp
            exit 1
          fi
      
      - name: Notificar en Slack
        if: always()
        uses: slackapi/slack-github-action@v1
        with:
          payload: |
            {
              "text": "Deploy ${{ job.status }}: ${{ github. sha }}"
            }
```

---

### Comparación Visual de los Tres Conceptos

```
┌─────────────────────────────────────────────────────────────┐
│                   CONTINUOUS INTEGRATION                    │
├─────────────────────────────────────────────────────────────┤
│  Código → Build → Test ✅                                   │
│  Objetivo: Detectar problemas de integración rápido        │
│  Frecuencia: Cada commit                                    │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                   CONTINUOUS DELIVERY                       │
├─────────────────────────────────────────────────────────────┤
│  Código → Build → Test → Package → Staging ✅              │
│                                       ↓                      │
│                                  👤 Aprobación              │
│                                       ↓                      │
│                                  Producción                 │
│  Objetivo: Tener artefactos siempre listos para producción │
│  Frecuencia:  Cada commit exitoso                            │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                  CONTINUOUS DEPLOYMENT                      │
├─────────────────────────────────────────────────────────────┤
│  Código → Build → Test → Package → Staging → Producción ✅ │
│  (TODO automático, sin intervención humana)                 │
│  Objetivo: Entregar valor al usuario en minutos            │
│  Frecuencia: Cada commit exitoso llega a producción        │
└─────────────────────────────────────────────────────────────┘
```

**¿Cuál implementar?**

| Madurez del Equipo | Recomendación                                              |
| ------------------ | ---------------------------------------------------------- |
| **Principiante**   | CI solamente → Automatizar build y tests                   |
| **Intermedio**     | Continuous Delivery → Añadir deploys a staging automáticos |
| **Avanzado**       | Continuous Deployment → Confianza total en automatización  |

💡 **Nota del Profesor**:  No hay que llegar a Continuous Deployment el primer día. Es un viaje evolutivo.  Lo importante es empezar con CI y mejorar incrementalmente.  Muchas empresas exitosas usan Continuous Delivery y están perfectamente bien.

---

### 1.3. Evolución de Herramientas:  GitHub Actions vs Jenkins

#### Contexto Histórico

**Jenkins (2011 - presente):**
- Primera herramienta CI/CD ampliamente adoptada
- Open source, auto-hospedado
- Altamente extensible (miles de plugins)
- Dominó la industria durante una década

**GitHub Actions (2019 - presente):**
- Nativo de GitHub (integración perfecta)
- Infraestructura administrada por GitHub
- Modelo declarativo (YAML)
- Marketplace de acciones reutilizables

#### Comparativa Técnica Detallada

| Aspecto                  | Jenkins                                       | GitHub Actions                        |
| ------------------------ | --------------------------------------------- | ------------------------------------- |
| **Hospedaje**            | Auto-hospedado (tu servidor)                  | Administrado por GitHub               |
| **Configuración**        | Interfaz web + Jenkinsfile                    | Archivos YAML en `.github/workflows/` |
| **Mantenimiento**        | Requiere actualizar Jenkins, plugins, agentes | Cero mantenimiento de infraestructura |
| **Escalabilidad**        | Manual (agregar más agentes)                  | Automática (GitHub gestiona runners)  |
| **Coste inicial**        | Alto (servidores, configuración)              | Bajo (2000 minutos gratis/mes)        |
| **Integración Git**      | Mediante plugins (menos fluida)               | Nativa y perfecta                     |
| **Seguridad**            | Responsabilidad del equipo                    | Gestionada por GitHub                 |
| **Curva de aprendizaje** | Empinada (UI compleja)                        | Suave (YAML declarativo)              |
| **Reutilización**        | Shared Libraries (complejo)                   | Actions Marketplace (simple)          |
| **Velocidad de setup**   | Horas/días                                    | Minutos                               |

#### Análisis en Profundidad

**1. Modelo de Configuración**

**Jenkins (Jenkinsfile - Groovy DSL):**
```groovy
pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }
        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                sh './deploy.sh'
            }
        }
    }
    
    post {
        always {
            junit 'build/test-results/**/*.xml'
        }
        success {
            slackSend channel: '#deploys', message: 'Build exitoso'
        }
    }
}
```

**GitHub Actions (YAML declarativo):**
```yaml
name: CI/CD Pipeline

on: 
  push:
    branches:  [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build: 
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v4
      
      - name:  Setup Java
        uses: actions/setup-java@v4
        with: 
          java-version: '21'
          distribution: 'temurin'
      
      - name: Build
        run: ./gradlew build
      
      - name: Test
        run: ./gradlew test
      
      - name:  Upload test results
        if: always()
        uses: actions/upload-artifact@v3
        with:
          name: test-results
          path: build/test-results/
  
  deploy:
    needs:  build
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    
    steps:
      - name:  Deploy
        run: ./deploy.sh
      
      - name: Notify Slack
        uses: slackapi/slack-github-action@v1
        with: 
          channel-id: 'C1234567890'
          slack-message: 'Build exitoso'
```

**Ventaja de GitHub Actions**:  YAML es más legible y estándar que Groovy.  Menos "magia", más declarativo.

---

**2. Gestión de Infraestructura**

**Jenkins:**
- Necesitas un servidor Linux/Windows para el Master
- Configurar agentes (slaves) para distribución de carga
- Gestionar plugins (actualizaciones, compatibilidad)
- Configurar seguridad (autenticación, autorización)
- Backups de configuración
- Monitorización de salud del servidor

**Coste oculto**:  Un DevOps dedicando 20% de su tiempo a mantener Jenkins.

**GitHub Actions:**
- GitHub proporciona runners (Ubuntu, Windows, macOS)
- Escalado automático según demanda
- Sin mantenimiento de infraestructura
- Actualizaciones automáticas
- Seguridad gestionada

**Coste**:  Solo pagas por minutos de ejecución (2000 gratis/mes para repositorios públicos).

---

**3. Integración con el Ecosistema**

**Jenkins:**
- Requiere plugins para integración con GitHub
- Webhooks configurados manualmente
- Gestión de credenciales en Jenkins
- Notificaciones mediante plugins adicionales

**GitHub Actions:**
- Integración nativa total con GitHub
- Acceso directo al código, issues, PRs
- Secrets gestionados en GitHub
- Anotaciones directas en PRs
- Marketplace con 10,000+ actions

**Ejemplo de anotación automática en PR:**

```yaml
- name: Run linter
  run: npm run lint -- --format=json > lint-results.json
  continue-on-error: true

- name:  Annotate PR with linting errors
  uses: ataylorme/eslint-annotate-action@v2
  with: 
    repo-token: ${{ secrets. GITHUB_TOKEN }}
    report-json: lint-results.json
```

Resultado: Comentarios automáticos en el PR indicando exactamente qué líneas tienen problemas.

---

**4. Velocidad de Adopción**

**Tiempo hasta el primer pipeline funcional:**

**Jenkins:**
1. Aprovisionar servidor (1-2 horas)
2. Instalar Jenkins (30 min)
3. Configurar seguridad (1 hora)
4. Instalar plugins necesarios (1 hora)
5. Configurar agentes (2 horas)
6. Crear primer job (1 hora)
7. Integrar con GitHub (1 hora)
8. Configurar webhooks (30 min)

**Total: ~9 horas** (y eso sin contar problemas)

**GitHub Actions:**
1. Crear archivo `.github/workflows/ci.yml` (10 min)
2. Push al repositorio
3. Ver el workflow ejecutándose

**Total: ~15 minutos**

---

**5. Reutilización y Comunidad**

**Jenkins:**
- Shared Libraries: Complejas de configurar
- Requieren repositorio Git separado
- Código Groovy (curva de aprendizaje)

**GitHub Actions:**
- Actions Marketplace: Buscar, usar, listo
- Versionadas (v1, v2, etc.)
- Escritas en JavaScript, Docker o Composite

**Ejemplo de uso de action del marketplace:**

```yaml
- name: Deploy to Netlify
  uses: netlify/actions/cli@master
  with:
    args: deploy --prod
  env:
    NETLIFY_SITE_ID: ${{ secrets. NETLIFY_SITE_ID }}
    NETLIFY_AUTH_TOKEN: ${{ secrets. NETLIFY_AUTH_TOKEN }}
```

Esa action encapsula toda la complejidad de autenticación y despliegue en Netlify.  En Jenkins, tendrías que escribir scripts bash y gestionar credenciales manualmente.

---

**6. Costes Reales**

**Jenkins (infraestructura propia):**
```
Servidor (AWS t3.medium):     $30/mes
Storage (100GB):               $10/mes
Agentes adicionales (3x):     $90/mes
Tiempo DevOps (20% FTE):    $1000/mes
---------------------------------------------
Total:                       ~$1130/mes
```

**GitHub Actions (cloud):**
```
Plan Team (si es privado):    $4/usuario/mes
2000 minutos gratis
Minutos adicionales:           $0.008/min

Uso típico:
  - 50 builds/día × 5 min = 250 min/día
  - 250 × 30 = 7500 min/mes
  - 7500 - 2000 = 5500 min adicionales
  - 5500 × $0.008 = $44/mes

---------------------------------------------
Total (equipo de 5):        ~$64/mes
```

**Ahorro:  94%** (sin contar tiempo de DevOps)

---

**7. Casos de Uso Donde Jenkins Sigue Siendo Mejor**

A pesar de las ventajas de GitHub Actions, Jenkins tiene sentido en: 

✅ **Entornos on-premise estrictos**: Cuando los datos no pueden salir de la red corporativa
✅ **Pipelines extremadamente complejos**: Con cientos de jobs interconectados
✅ **Integración con herramientas legacy**: Cuando ya tienes 100+ plugins configurados
✅ **Necesidades de hardware específico**: Builds que requieren GPUs, hardware especial
✅ **Compliance extremo**: Sectores regulados con auditorías estrictas

---

#### ¿Por Qué Enseñar GitHub Actions en Este Curso?

1. **Facilidad de aprendizaje**: Los alumnos pueden empezar en minutos
2. **Coste cero para aprender**:  Repositorios públicos = CI/CD gratis
3. **Relevancia industrial**: Cada vez más empresas migran a soluciones cloud-native
4. **Integración perfecta**: GitHub es la plataforma de código más usada
5. **Habilidades transferibles**: El conocimiento de YAML y CI/CD se aplica a GitLab CI, Azure Pipelines, etc. 

💡 **Nota del Profesor**: Aprender GitHub Actions no significa ignorar Jenkins. Los conceptos fundamentales (pipelines, stages, artifacts, secrets) son idénticos. Si dominas uno, entender el otro es trivial.  Elegimos GitHub Actions porque permite enfocarse en **qué hacer** (CI/CD) en lugar de **cómo configurar infraestructura**.

---

## 2. GitHub Actions como Motor de CI/CD

### Introducción:  La Arquitectura de GitHub Actions

GitHub Actions es un motor de automatización nativo de GitHub que permite ejecutar **workflows** (flujos de trabajo) en respuesta a eventos que ocurren en tu repositorio. 

A diferencia de herramientas tradicionales donde la configuración está en una base de datos o interfaz web, en GitHub Actions **todo está versionado como código** en tu repositorio.

```
tu-proyecto/
├── .github/
│   └── workflows/
│       ├── ci.yml           ← Pipeline de integración continua
│       ├── deploy.yml       ← Pipeline de despliegue
│       └── release.yml      ← Automatización de releases
├── src/
├── tests/
└── README.md
```

💡 **Nota del Profesor**: El directorio `.github/workflows/` es **mágico**. GitHub detecta automáticamente cualquier archivo `.yml` o `.yaml` en esta carpeta y lo registra como un workflow.  No hay configuración adicional necesaria.

---

### 2.1. Componentes del Ecosistema

#### Anatomía de un Workflow

Un workflow de GitHub Actions tiene una **estructura jerárquica** clara:

```
Workflow (Archivo . yml)
  ├── Metadata (name, on)
  ├── Environment Variables
  ├── Defaults
  └── Jobs
        ├── Job 1
        │   ├── Runs-on (runner)
        │   ├── Environment
        │   ├── Strategy (matrix)
        │   └── Steps
        │       ├── Step 1 (uses: action)
        │       ├── Step 2 (run: command)
        │       └── Step 3 (uses: action)
        ├── Job 2 (needs: job1)
        └── Job 3 (needs: [job1, job2])
```

---

#### Workflows:  Definición en YAML

**Ejemplo básico comentado:**

```yaml
# Nombre del workflow (aparece en la UI de GitHub)
name: Continuous Integration

# Eventos que disparan este workflow
on:
  push: 
    branches: [ main, develop ]
  pull_request: 
    branches: [ main ]
  # Trigger manual desde la UI
  workflow_dispatch: 

# Variables de entorno globales para todos los jobs
env:
  JAVA_VERSION: '21'
  NODE_VERSION: '20'

# Configuración por defecto para todos los jobs
defaults:
  run:
    shell: bash

# Definición de jobs (se ejecutan en paralelo por defecto)
jobs:
  build:
    name: Build and Test
    runs-on: ubuntu-latest
    
    steps:
      - name:  Checkout code
        uses: actions/checkout@v4
      
      - name: Setup Java
        uses: actions/setup-java@v4
        with: 
          java-version: ${{ env.JAVA_VERSION }}
          distribution: 'temurin'
      
      - name:  Build with Gradle
        run:  ./gradlew build
      
      - name: Run tests
        run: ./gradlew test
```

**Características clave:**

- ✅ **Formato YAML**: Estructura legible y estándar
- ✅ **Versionado con el código**: Cambios en el pipeline se revisan como código
- ✅ **Declarativo**: Describes QUÉ quieres, no CÓMO hacerlo
- ✅ **Reutilizable**: Puedes llamar workflows desde otros workflows

---

#### Events: Disparadores de Workflows

Los **events** determinan **cuándo** se ejecuta un workflow.  GitHub ofrece más de 40 tipos de eventos. 

**Eventos más comunes:**

**1. Push Event**

```yaml
on:
  push:
    branches: 
      - main
      - develop
      - 'release/**'  # Cualquier rama que empiece con release/
    paths: 
      - 'src/**'      # Solo si cambian archivos en src/
      - 'pom.xml'
    tags: 
      - 'v*'          # Cualquier tag que empiece con v
```

**Casos de uso:**
- CI en ramas principales
- Despliegue automático al hacer push a main
- Build de releases al crear tags

**2. Pull Request Event**

```yaml
on:
  pull_request:
    types: 
      - opened        # Cuando se abre el PR
      - synchronize   # Cuando se hace push al PR
      - reopened      # Cuando se reabre un PR cerrado
    branches:
      - main
    paths-ignore:
      - 'docs/**'     # Ignorar cambios en documentación
      - '**. md'
```

**Casos de uso:**
- Validación de código antes de merge
- Preview deployments
- Análisis de calidad de código

**3. Schedule Event (Cron)**

```yaml
on:
  schedule:
    # Ejecutar cada día a las 2 AM UTC
    - cron: '0 2 * * *'
    # Ejecutar cada lunes a las 9 AM
    - cron: '0 9 * * 1'
```

**Casos de uso:**
- Backups diarios
- Limpieza de datos antiguos
- Reportes semanales
- Tests de smoke en producción

**Formato cron:**
```
┌───────────── minuto (0 - 59)
│ ┌───────────── hora (0 - 23)
│ │ ┌───────────── día del mes (1 - 31)
│ │ │ ┌───────────── mes (1 - 12)
│ │ │ │ ┌───────────── día de la semana (0 - 6, domingo = 0)
│ │ │ │ │
* * * * *
```

**4. Workflow Dispatch (Manual)**

```yaml
on:
  workflow_dispatch:
    inputs:
      environment:
        description: 'Environment to deploy'
        required: true
        type: choice
        options:
          - staging
          - production
      version:
        description: 'Version to deploy'
        required:  true
        type: string
      debug:
        description: 'Enable debug mode'
        required: false
        type: boolean
        default: false
```

**Uso en el workflow:**

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Deploy
        run: |
          echo "Deploying version ${{ inputs.version }} to ${{ inputs. environment }}"
          if [ "${{ inputs.debug }}" == "true" ]; then
            echo "Debug mode enabled"
          fi
```

**Casos de uso:**
- Despliegues manuales controlados
- Operaciones de mantenimiento
- Tests bajo demanda con parámetros específicos

**5. Repository Dispatch (Trigger externo)**

```yaml
on:
  repository_dispatch:
    types:
      - webhook-received
      - external-trigger
```

**Disparar desde API:**

```bash
curl -X POST \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer ${GITHUB_TOKEN}" \
  https://api.github.com/repos/OWNER/REPO/dispatches \
  -d '{"event_type":"webhook-received","client_payload":{"data":"custom"}}'
```

**Casos de uso:**
- Integración con sistemas externos
- Triggers desde otros servicios (Netlify, Vercel, etc.)
- Orquestación compleja entre múltiples repositorios

**6. Release Event**

```yaml
on:
  release:
    types: 
      - published
      - created
```

**Casos de uso:**
- Publicación de artefactos (JARs, binarios)
- Actualización de documentación
- Notificaciones a usuarios

**7. Issues y Comments**

```yaml
on:
  issues:
    types: 
      - opened
      - labeled
  issue_comment:
    types: 
      - created
```

**Casos de uso:**
- Bots que responden a issues
- Automatización de triaging
- Integración con sistemas de tickets

---

#### Combinación de Eventos

Puedes combinar múltiples eventos en un workflow:

```yaml
on:
  # CI en push a ramas principales
  push:
    branches: [ main, develop ]
  
  # Validación en PRs
  pull_request: 
    branches: [ main ]
  
  # Despliegue manual
  workflow_dispatch:
    inputs:
      environment:
        type: choice
        options:  [staging, production]
  
  # Build nocturno
  schedule:
    - cron: '0 2 * * *'
```

---

#### Jobs: Unidades de Ejecución

Un **job** es un conjunto de **steps** que se ejecutan en el mismo **runner**.

**Configuración de un Job:**

```yaml
jobs:
  build-backend:
    name: Build Java Backend            # Nombre descriptivo
    runs-on: ubuntu-latest              # Runner a usar
    timeout-minutes: 30                 # Timeout del job
    
    # Estrategia de matriz (explicada después)
    strategy:
      matrix:
        java:  [17, 21]
      fail-fast: false
    
    # Variables de entorno del job
    env:
      JAVA_VERSION: ${{ matrix. java }}
    
    # Condición para ejecutar el job
    if: github.event_name == 'push'
    
    # Environment con protecciones
    environment:
      name: production
      url: https://app.example.com
    
    # Outputs del job (disponibles para otros jobs)
    outputs:
      artifact-url: ${{ steps.upload. outputs.artifact-url }}
    
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name:  Setup Java ${{ matrix.java }}
        uses: actions/setup-java@v4
        with:
          java-version: ${{ matrix.java }}
          distribution: 'temurin'
      
      - name: Build
        run: ./gradlew build
      
      - name: Upload artifact
        id: upload
        uses: actions/upload-artifact@v3
        with:
          name:  app-jar
          path: build/libs/*. jar
```

**Características importantes:**

**1. Paralelismo por defecto:**

```yaml
jobs:
  frontend:    # Se ejecuta en paralelo
    runs-on: ubuntu-latest
    steps:
      - run: npm run build
  
  backend:     # Se ejecuta en paralelo
    runs-on: ubuntu-latest
    steps:
      - run: ./gradlew build
  
  tests:       # Se ejecuta en paralelo
    runs-on: ubuntu-latest
    steps:
      - run: pytest
```

Los tres jobs empiezan **simultáneamente** (si hay runners disponibles).

**2. Dependencias entre jobs:**

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: ./gradlew build
  
  test:
    needs: build           # Espera a que build termine
    runs-on: ubuntu-latest
    steps:
      - run: ./gradlew test
  
  deploy:
    needs: [build, test]   # Espera a que ambos terminen
    runs-on:  ubuntu-latest
    steps: 
      - run: ./deploy.sh
```

**Flujo:**
```
build (1 min)
  ↓
test (2 min)
  ↓
deploy (30 seg)

Tiempo total: 3. 5 minutos
```

**3. Condicionales:**

```yaml
jobs:
  deploy-staging:
    if: github.ref == 'refs/heads/develop'
    runs-on: ubuntu-latest
    steps:
      - run: ./deploy-staging.sh
  
  deploy-production:
    if: github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest
    steps: 
      - run: ./deploy-production.sh
```

---

#### Steps: Tareas Individuales

Los **steps** son las tareas individuales que componen un job.

**Tipos de steps:**

**1. Actions (uses):**

```yaml
steps:
  # Action del marketplace de GitHub
  - name: Checkout code
    uses: actions/checkout@v4
    with:
      fetch-depth: 0  # Parámetros del action
  
  # Action de terceros
  - name: Setup Node.js
    uses: actions/setup-node@v4
    with:
      node-version:  '20'
      cache: 'npm'
  
  # Action local del repositorio
  - name: Custom action
    uses: ./.github/actions/my-custom-action
    with:
      param1: value1
```

**2. Comandos (run):**

```yaml
steps:
  # Comando simple
  - name: Build project
    run: npm run build
  
  # Script multi-línea
  - name: Deploy
    run: |
      echo "Starting deployment..."
      ./scripts/pre-deploy.sh
      ./scripts/deploy.sh
      ./scripts/post-deploy.sh
      echo "Deployment complete"
  
  # Con shell específico
  - name: PowerShell script
    run: |
      Write-Host "Running on Windows"
      Get-ChildItem
    shell: pwsh
  
  # Con directorio de trabajo específico
  - name: Build frontend
    working-directory: ./frontend
    run: npm ci && npm run build
```

**3. Condicionales en steps:**

```yaml
steps:
  - name: Run tests
    run: npm test
  
  # Solo se ejecuta si el step anterior tuvo éxito
  - name: Deploy
    if: success()
    run: ./deploy.sh
  
  # Solo se ejecuta si algo falló
  - name: Send failure notification
    if: failure()
    run: |
      curl -X POST $SLACK_WEBHOOK \
        -d '{"text":"Build failed!"}'
  
  # Siempre se ejecuta (incluso si algo falló)
  - name: Cleanup
    if: always()
    run: rm -rf temp/
  
  # Solo en rama main
  - name: Deploy to production
    if: github.ref == 'refs/heads/main'
    run: ./deploy-prod.sh
```

**Funciones de condición:**

| Función       | Descripción                               |
| ------------- | ----------------------------------------- |
| `success()`   | Todos los steps anteriores tuvieron éxito |
| `failure()`   | Algún step anterior falló                 |
| `cancelled()` | El workflow fue cancelado                 |
| `always()`    | Se ejecuta siempre                        |

**4. Continue on error:**

```yaml
steps:
  - name: Run linter (no-blocking)
    run: npm run lint
    continue-on-error:  true  # No falla el workflow si esto falla
  
  - name: Run tests (blocking)
    run: npm test
    # Si esto falla, el workflow falla
```

**5. Timeout de steps:**

```yaml
steps:
  - name: Long running task
    run: ./long-task.sh
    timeout-minutes: 10  # Falla si tarda más de 10 minutos
```

---

#### Runners: Entornos de Ejecución

Los **runners** son las máquinas virtuales donde se ejecutan tus workflows.

**Tipos de Runners:**

**1. GitHub-hosted runners (administrados por GitHub):**

```yaml
jobs:
  ubuntu-job:
    runs-on: ubuntu-latest    # Ubuntu 22.04
  
  windows-job:
    runs-on: windows-latest   # Windows Server 2022
  
  macos-job:
    runs-on: macos-latest     # macOS 13 (Ventura)
  
  specific-version:
    runs-on: ubuntu-20.04     # Versión específica
```

**Especificaciones de los runners:**

| Runner           | vCPUs | RAM   | Storage | Sistema Operativo   |
| ---------------- | ----- | ----- | ------- | ------------------- |
| `ubuntu-latest`  | 2     | 7 GB  | 14 GB   | Ubuntu 22.04        |
| `ubuntu-20.04`   | 2     | 7 GB  | 14 GB   | Ubuntu 20.04        |
| `windows-latest` | 2     | 7 GB  | 14 GB   | Windows Server 2022 |
| `macos-latest`   | 3     | 14 GB | 14 GB   | macOS 13            |

**Software preinstalado:**

Cada runner viene con herramientas comunes preinstaladas:

**Ubuntu:**
- Docker
- Git
- Node.js (múltiples versiones)
- Python
- Java (JDK 8, 11, 17, 21)
- . NET SDK
- Ruby
- Go
- Rust
- AWS CLI, Azure CLI, gcloud
- kubectl, Helm
- Navegadores (Chrome, Firefox)

**Lista completa:** https://github.com/actions/runner-images

**2. Self-hosted runners (auto-hospedados):**

```yaml
jobs:
  custom-hardware:
    runs-on: self-hosted
```

**Casos de uso para self-hosted:**
- Hardware específico (GPUs, mucha RAM)
- Acceso a red privada
- Software/licencias específicas
- Reducción de costes en uso intensivo
- Requisitos de compliance

**Configurar self-hosted runner:**

1. Ir a Settings → Actions → Runners → New self-hosted runner
2. Seguir instrucciones según OS
3. Ejecutar: 

```bash
# Descargar
mkdir actions-runner && cd actions-runner
curl -o actions-runner-linux-x64-2.311.0.tar.gz -L \
  https://github.com/actions/runner/releases/download/v2.311.0/actions-runner-linux-x64-2.311.0.tar.gz
tar xzf ./actions-runner-linux-x64-2.311.0.tar.gz

# Configurar
./config.sh --url https://github.com/OWNER/REPO --token TOKEN

# Ejecutar como servicio
sudo ./svc.sh install
sudo ./svc.sh start
```

**3. Matrix Strategy (ejecución en múltiples runners):**

```yaml
jobs:
  test:
    runs-on: ${{ matrix.os }}
    
    strategy:
      matrix: 
        os: [ubuntu-latest, windows-latest, macos-latest]
        node:  [18, 20]
        # Esto crea 6 jobs (3 OS × 2 versiones de Node)
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Node.js ${{ matrix.node }}
        uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node }}
      
      - name: Run tests
        run: npm test
```

**Resultado:**
- ✅ ubuntu-latest + Node 18
- ✅ ubuntu-latest + Node 20
- ✅ windows-latest + Node 18
- ✅ windows-latest + Node 20
- ✅ macos-latest + Node 18
- ✅ macos-latest + Node 20

Todos se ejecutan **en paralelo**. 

**Matrix con exclusiones:**

```yaml
strategy:
  matrix:
    os: [ubuntu-latest, windows-latest]
    java: [17, 21]
    exclude: 
      # No ejecutar Java 17 en Windows
      - os: windows-latest
        java:  17
    include:
      # Agregar combinación adicional
      - os: macos-latest
        java: 21
```

**Matrix con fail-fast:**

```yaml
strategy:
  fail-fast: false  # No cancela otros jobs si uno falla
  matrix:
    os: [ubuntu-latest, windows-latest, macos-latest]
```

Por defecto, `fail-fast: true` cancela todos los jobs restantes si uno falla.

---

#### Contexts y Expresiones

GitHub Actions proporciona **contexts** que contienen información sobre el workflow, job, runner, etc.

**Contexts disponibles:**

```yaml
steps:
  - name: Print contexts
    run: |
      echo "Repository: ${{ github.repository }}"
      echo "Actor: ${{ github.actor }}"
      echo "Event: ${{ github.event_name }}"
      echo "Ref: ${{ github.ref }}"
      echo "SHA: ${{ github.sha }}"
      echo "Run ID: ${{ github.run_id }}"
      echo "Runner OS: ${{ runner.os }}"
      echo "Job status: ${{ job.status }}"
```

**Context `github`:**

| Propiedad                 | Descripción                     | Ejemplo                                    |
| ------------------------- | ------------------------------- | ------------------------------------------ |
| `github.repository`       | Nombre del repositorio          | `owner/repo`                               |
| `github.repository_owner` | Dueño del repositorio           | `owner`                                    |
| `github.actor`            | Usuario que disparó el workflow | `username`                                 |
| `github.event_name`       | Nombre del evento               | `push`, `pull_request`                     |
| `github.ref`              | Ref completo                    | `refs/heads/main`                          |
| `github.ref_name`         | Nombre de la rama/tag           | `main`                                     |
| `github.sha`              | SHA del commit                  | `ffac537e6cbbf934b08745a378932722df287a53` |
| `github.run_id`           | ID único del run                | `1234567890`                               |
| `github.run_number`       | Número incremental              | `42`                                       |

**Context `env`:**

```yaml
env:
  GLOBAL_VAR: 'global'

jobs:
  example:
    env:
      JOB_VAR: 'job-level'
    
    steps:
      - name:  Print variables
        env: 
          STEP_VAR: 'step-level'
        run: |
          echo "Global: ${{ env.GLOBAL_VAR }}"
          echo "Job: ${{ env.JOB_VAR }}"
          echo "Step: ${{ env.STEP_VAR }}"
```

**Context `secrets`:**

```yaml
steps:
  - name: Deploy
    run: ./deploy.sh
    env:
      API_KEY: ${{ secrets.API_KEY }}
      DB_PASSWORD: ${{ secrets.DB_PASSWORD }}
```

💡 **Nota del Profesor**:  Los secrets NUNCA se imprimen en logs.   GitHub los enmascara automáticamente.

**Context `steps`:**

```yaml
steps:
  - name: Build
    id: build-step
    run: |
      echo "artifact-path=./dist/app.jar" >> $GITHUB_OUTPUT
      echo "version=1.2.3" >> $GITHUB_OUTPUT
  
  - name: Use outputs
    run: |
      echo "Artifact:  ${{ steps.build-step. outputs.artifact-path }}"
      echo "Version: ${{ steps.build-step.outputs.version }}"
```

**Expresiones:**

```yaml
steps:
  # Operadores lógicos
  - name: Deploy to prod
    if: github.ref == 'refs/heads/main' && github.event_name == 'push'
    run: ./deploy. sh
  
  # Funciones
  - name: Check if PR
    if: startsWith(github.ref, 'refs/pull/')
    run: echo "This is a PR"
  
  - name: Check commit message
    if: contains(github.event. head_commit.message, '[skip ci]')
    run: exit 0
  
  # Operador ternario
  - name: Set environment
    run: |
      ENVIRONMENT=${{ github.ref == 'refs/heads/main' && 'production' || 'staging' }}
      echo "Deploying to $ENVIRONMENT"
```

**Funciones útiles:**

| Función                      | Descripción                    | Ejemplo                                |
| ---------------------------- | ------------------------------ | -------------------------------------- |
| `contains(string, search)`   | Verifica si contiene substring | `contains(github.ref, 'release')`      |
| `startsWith(string, search)` | Verifica si empieza con        | `startsWith(github.ref, 'refs/tags/')` |
| `endsWith(string, search)`   | Verifica si termina con        | `endsWith(github.ref, '-beta')`        |
| `format(string, args...)`    | Formatea string                | `format('Hello {0}', github.actor)`    |
| `join(array, separator)`     | Une array                      | `join(matrix. os, ', ')`               |
| `toJSON(value)`              | Convierte a JSON               | `toJSON(github)`                       |
| `fromJSON(string)`           | Parsea JSON                    | `fromJSON('{"key": "value"}')`         |

---

### Ejemplo Completo: Workflow CI/CD Avanzado

```yaml
name: Complete CI/CD Pipeline

on: 
  push:
    branches: [ main, develop ]
    paths-ignore:
      - 'docs/**'
      - '**. md'
  pull_request:
    branches:  [ main ]
  workflow_dispatch: 
    inputs:
      deploy-environment:
        description: 'Target environment'
        required: true
        type: choice
        options:
          - staging
          - production

env:
  JAVA_VERSION: '21'
  GRADLE_OPTS: '-Dorg.gradle.daemon=false -Dorg.gradle.parallel=true'

jobs:
  # Job 1: Compilación y tests
  build-and-test:
    name: Build & Test (Java ${{ matrix.java }})
    runs-on: ${{ matrix.os }}
    timeout-minutes: 20
    
    strategy:
      fail-fast: false
      matrix: 
        os: [ubuntu-latest, windows-latest]
        java: [17, 21]
    
    steps:
      - name:  Checkout code
        uses: actions/checkout@v4
        with:
          fetch-depth: 0  # Para SonarQube
      
      - name:  Setup JDK ${{ matrix.java }}
        uses: actions/setup-java@v4
        with: 
          java-version: ${{ matrix.java }}
          distribution: 'temurin'
          cache: 'gradle'
      
      - name: Validate Gradle Wrapper
        uses: gradle/wrapper-validation-action@v1
      
      - name:  Build project
        run: ./gradlew build -x test
      
      - name: Run unit tests
        run: ./gradlew test
      
      - name: Run integration tests
        run: ./gradlew integrationTest
      
      - name: Generate test report
        if: always()
        uses: dorny/test-reporter@v1
        with:
          name: Test Results (${{ matrix.os }} - Java ${{ matrix.java }})
          path: build/test-results/**/*.xml
          reporter: java-junit
      
      - name: Upload build artifacts
        if: matrix.os == 'ubuntu-latest' && matrix.java == '21'
        uses: actions/upload-artifact@v3
        with:
          name:  application-jar
          path: build/libs/*. jar
          retention-days: 7
  
  # Job 2: Análisis de calidad
  code-quality:
    name: Code Quality Analysis
    runs-on:  ubuntu-latest
    needs: build-and-test
    
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth:  0
      
      - name: Setup JDK
        uses: actions/setup-java@v4
        with:
          java-version: ${{ env.JAVA_VERSION }}
          distribution: 'temurin'
          cache: 'gradle'
      
      - name: Run SonarQube analysis
        env:
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
        run: |
          ./gradlew sonarqube \
            -Dsonar. projectKey=my-project \
            -Dsonar.host.url=https://sonarcloud.io \
            -Dsonar.organization=my-org
      
      - name: Generate coverage report
        run: ./gradlew jacocoTestReport
      
      - name: Upload coverage to Codecov
        uses: codecov/codecov-action@v3
        with:
          files: build/reports/jacoco/test/jacocoTestReport.xml
          flags: unittests
          name:  codecov-umbrella
  
  # Job 3: Build Docker image
  build-docker:
    name: Build Docker Image
    runs-on: ubuntu-latest
    needs: [build-and-test, code-quality]
    if: github.event_name == 'push' || github.event_name == 'workflow_dispatch'
    
    outputs:
      image-tag: ${{ steps.meta.outputs.tags }}
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Download JAR artifact
        uses: actions/download-artifact@v3
        with: 
          name: application-jar
          path: build/libs/
      
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3
      
      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with: 
          username: ${{ secrets. DOCKER_USERNAME }}
          password:  ${{ secrets.DOCKER_PASSWORD }}
      
      - name:  Docker metadata
        id: meta
        uses: docker/metadata-action@v5
        with:
          images: myorg/myapp
          tags: |
            type=ref,event=branch
            type=sha,prefix={{branch}}-
            type=semver,pattern={{version}}
      
      - name: Build and push
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
  
  # Job 4: Deploy to staging
  deploy-staging:
    name: Deploy to Staging
    runs-on: ubuntu-latest
    needs: build-docker
    if: github. ref == 'refs/heads/develop'
    environment: 
      name: staging
      url: https://staging.example.com
    
    steps:
      - name: Deploy to Render
        run: |
          curl -X POST "${{ secrets.RENDER_DEPLOY_HOOK_STAGING }}"
      
      - name: Wait for deployment
        run: sleep 60
      
      - name: Health check
        run: |
          response=$(curl -s -o /dev/null -w "%{http_code}" https://staging.example.com/health)
          if [ $response -ne 200 ]; then
            echo "Health check failed!"
            exit 1
          fi
  
  # Job 5: Deploy to production
  deploy-production: 
    name: Deploy to Production
    runs-on: ubuntu-latest
    needs: build-docker
    if: |
      github.ref == 'refs/heads/main' || 
      (github.event_name == 'workflow_dispatch' && inputs.deploy-environment == 'production')
    environment:
      name: production
      url: https://example.com
    
    steps:
      - name: Deploy to Render
        run: |
          curl -X POST "${{ secrets.RENDER_DEPLOY_HOOK_PRODUCTION }}"
      
      - name:  Wait for deployment
        run: sleep 90
      
      - name: Run smoke tests
        run: |
          curl -f https://example.com/health
          curl -f https://example.com/api/v1/status
      
      - name:  Notify team
        if: always()
        uses: slackapi/slack-github-action@v1
        with: 
          payload: |
            {
              "text": "Production deployment ${{ job.status }}:  ${{ github.sha }}",
              "blocks": [
                {
                  "type": "section",
                  "text": {
                    "type": "mrkdwn",
                    "text":  "*Production Deployment*\nStatus: ${{ job.status }}\nCommit: ${{ github.sha }}\nActor: ${{ github.actor }}"
                  }
                }
              ]
            }
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK }}
```

---

### 2. 2. Seguridad y Secretos

#### GitHub Secrets:  Gestión Segura de Credenciales

Los **secrets** son variables cifradas que almacenan información sensible. 

**Tipos de secrets:**

1. **Repository secrets**:  Disponibles solo para un repositorio
2. **Organization secrets**: Disponibles para múltiples repositorios
3. **Environment secrets**: Específicos de un environment (staging, production)

**Configurar secrets:**

**A nivel de repositorio:**
1. Ir a Settings → Secrets and variables → Actions
2. Click "New repository secret"
3. Nombre:  `DOCKER_PASSWORD`
4. Valor: `tu-password-seguro`
5. Add secret

**A nivel de organization:**
1. Ir a Organization settings → Secrets and variables → Actions
2. New organization secret
3. Seleccionar repositorios que pueden usarlo

**Uso en workflows:**

```yaml
steps:
  - name: Login to Docker Hub
    run: |
      echo "${{ secrets.DOCKER_PASSWORD }}" | docker login -u "${{ secrets.DOCKER_USERNAME }}" --password-stdin
  
  - name: Deploy to server
    run: |
      ssh -i <(echo "${{ secrets.SSH_PRIVATE_KEY }}") user@server "deploy. sh"
    env:
      API_KEY: ${{ secrets.API_KEY }}
      DATABASE_URL: ${{ secrets.DATABASE_URL }}
```

**Buenas prácticas:**

✅ **Nunca hagas echo de secrets:**
```yaml
# ❌ MAL - El secret se verá en logs
- run: echo "Password is ${{ secrets.PASSWORD }}"

# ✅ BIEN - GitHub enmascara automáticamente
- run: curl -u "user:${{ secrets.PASSWORD }}" https://api.example.com
```

✅ **Usa secrets para:**
- Contraseñas
- Tokens de API
- Claves SSH
- Certificados
- URLs con credenciales embebidas

✅ **No uses secrets para:**
- Información pública
- Configuración no sensible
- Datos que varían frecuentemente

---

#### Variables de Entorno

Para datos no sensibles, usa **variables**:

```yaml
env:
  # Variables globales
  NODE_VERSION: '20'
  JAVA_VERSION: '21'

jobs:
  build:
    env:
      # Variables del job
      BUILD_ENV: 'production'
    
    steps:
      - name: Build
        env:
          # Variables del step
          CUSTOM_FLAG: 'enabled'
        run: |
          echo "Node version: $NODE_VERSION"
          echo "Build environment: $BUILD_ENV"
          echo "Custom flag: $CUSTOM_FLAG"
```

**Variables configurables en GitHub:**

Settings → Secrets and variables → Actions → Variables

```yaml
steps:
  - name: Use variable
    run: echo "API URL: ${{ vars.API_URL }}"
```

Diferencia con secrets:
- **Variables**: Visibles en logs, para configuración
- **Secrets**:  Enmascaradas, para información sensible

---

#### Contextos Dinámicos y Outputs

**Pasar datos entre steps:**

```yaml
steps:
  - name: Generate version
    id: version
    run: |
      VERSION=$(date +%Y%m%d)-$(git rev-parse --short HEAD)
      echo "version=$VERSION" >> $GITHUB_OUTPUT
      echo "Generated version: $VERSION"
  
  - name: Use version
    run: |
      echo "Version from previous step: ${{ steps.version. outputs.version }}"
      docker build -t myapp:${{ steps.version.outputs.version }} .
```

**Pasar datos entre jobs:**

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    outputs:
      artifact-url: ${{ steps.upload. outputs.artifact-url }}
      version: ${{ steps.version. outputs.version }}
    
    steps:
      - name: Generate version
        id: version
        run: echo "version=1.2.3" >> $GITHUB_OUTPUT
      
      - name: Upload artifact
        id: upload
        uses: actions/upload-artifact@v3
        with:
          name: app
          path: dist/
  
  deploy:
    needs:  build
    runs-on: ubuntu-latest
    steps:
      - name: Deploy version
        run: |
          echo "Deploying version:  ${{ needs.build.outputs. version }}"
          echo "Artifact URL: ${{ needs.build.outputs.artifact-url }}"
```

---

## 3. Pipeline de Integración Continua (CI)

### Introducción:  Anatomía de un Pipeline CI Profesional

Un pipeline de **Integración Continua** moderno no solo compila código.  Debe validar **calidad, seguridad y funcionalidad** antes de permitir que los cambios lleguen a la rama principal.

**Fases típicas de un pipeline CI:**

```
┌─────────────────────────────────────────────────────────────┐
│                    PIPELINE CI COMPLETO                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1. Checkout      → Obtener código del repositorio         │
│  2. Setup         → Configurar entorno (JDK, Node, etc.)   │
│  3. Dependencies  → Instalar/cachear dependencias          │
│  4. Lint/Format   → Validar estilo de código              │
│  5. Build         → Compilar código                        │
│  6. Unit Tests    → Tests rápidos y aislados              │
│  7. Integration   → Tests con BD/servicios reales         │
│  8. Coverage      → Medir cobertura de código             │
│  9. Quality Gate  → Verificar umbrales de calidad         │
│  10. Security     → Escaneo de vulnerabilidades           │
│  11. Artifacts    → Empaquetar resultado (JAR, Docker)    │
│  12. Notify       → Informar resultado al equipo          │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

💡 **Nota del Profesor**: Un buen pipeline CI falla **rápido y ruidosamente**. Si algo está mal, debe detectarse en minutos, no en días.  La velocidad de feedback es crítica.

---

### 3.1. Automatización del Build

#### Java con Gradle (Kotlin DSL)

**Configuración del Proyecto:**

**build.gradle.kts:**

```kotlin
plugins {
    java
    jacoco
    id("org.springframework.boot") version "3.2.0"
    id("io.spring.dependency-management") version "1.1.4"
    id("org.sonarqube") version "4.4.1.3373"
}

group = "com.example"
version = System.getenv("VERSION") ?: "1.0.0-SNAPSHOT"

java {
    toolchain {
        languageVersion. set(JavaLanguageVersion.of(21))
    }
}

repositories {
    mavenCentral()
}

dependencies {
    // Spring Boot
    implementation("org.springframework.boot:spring-boot-starter-web")
    implementation("org.springframework.boot:spring-boot-starter-data-jpa")
    implementation("org.springframework.boot:spring-boot-starter-validation")
    
    // Database
    runtimeOnly("org.postgresql:postgresql")
    
    // Testing
    testImplementation("org. springframework.boot:spring-boot-starter-test")
    testImplementation("org.testcontainers:testcontainers:1.19.3")
    testImplementation("org.testcontainers:postgresql:1.19.3")
    testImplementation("org.testcontainers:junit-jupiter:1.19.3")
}

tasks.test {
    useJUnitPlatform()
    
    // Configuración para CI
    maxParallelForks = Runtime.getRuntime().availableProcessors()
    
    testLogging {
        events("passed", "skipped", "failed")
        exceptionFormat = org.gradle.api.tasks. testing.logging.TestExceptionFormat.FULL
        showStandardStreams = false
    }
    
    // Finalizar con reporte de cobertura
    finalizedBy(tasks.jacocoTestReport)
}

jacoco {
    toolVersion = "0.8.11"
}

tasks.jacocoTestReport {
    dependsOn(tasks.test)
    
    reports {
        xml.required.set(true)  // Para SonarQube/Codecov
        html.required.set(true)  // Para revisión local
        csv.required.set(false)
    }
    
    // Excluir clases de la cobertura
    classDirectories.setFrom(
        files(classDirectories.files.map {
            fileTree(it) {
                exclude(
                    "**/config/**",
                    "**/dto/**",
                    "**/entity/**",
                    "**/*Application. class"
                )
            }
        })
    )
}

tasks.jacocoTestCoverageVerification {
    violationRules {
        rule {
            limit {
                minimum = "0.80". toBigDecimal()
            }
        }
        
        rule {
            element = "CLASS"
            limit {
                counter = "LINE"
                value = "COVEREDRATIO"
                minimum = "0.75".toBigDecimal()
            }
        }
    }
}

// Task para CI:  build + tests + coverage verification
tasks.register("ciCheck") {
    dependsOn("build", "test", "jacocoTestCoverageVerification")
}

// Configuración de SonarQube
sonarqube {
    properties {
        property("sonar.projectKey", "my-project")
        property("sonar.organization", "my-org")
        property("sonar.host.url", "https://sonarcloud.io")
        property("sonar.coverage.jacoco.xmlReportPaths", 
            "${buildDir}/reports/jacoco/test/jacocoTestReport.xml")
    }
}
```

---

#### GitHub Actions Workflow para Java

**. github/workflows/ci-java. yml:**

```yaml
name: Java CI Pipeline

on:
  push: 
    branches: [ main, develop, 'feature/**' ]
    paths: 
      - 'src/**'
      - 'build.gradle. kts'
      - 'gradle/**'
      - '.github/workflows/ci-java.yml'
  pull_request:
    branches: [ main, develop ]

env:
  JAVA_VERSION:  '21'
  GRADLE_OPTS: >-
    -Dorg. gradle.daemon=false
    -Dorg.gradle.parallel=true
    -Dorg. gradle.caching=true
    -Dorg.gradle.configuration-cache=true

jobs:
  # ==========================================
  # Job 1: Validación y Build
  # ==========================================
  build: 
    name: Build & Unit Tests
    runs-on: ubuntu-latest
    timeout-minutes: 15
    
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
        with:
          fetch-depth: 0  # Necesario para SonarQube
      
      - name: Setup JDK ${{ env.JAVA_VERSION }}
        uses: actions/setup-java@v4
        with:
          java-version: ${{ env. JAVA_VERSION }}
          distribution:  'temurin'
          cache: 'gradle'
      
      # Validar integridad del Gradle Wrapper
      - name: Validate Gradle Wrapper
        uses: gradle/wrapper-validation-action@v1
      
      # Verificar formato de código
      - name: Check code formatting
        run: ./gradlew spotlessCheck
        continue-on-error: true  # No bloquear por formato
      
      # Compilar sin ejecutar tests
      - name: Build project
        run: ./gradlew build -x test --no-daemon
      
      # Ejecutar tests unitarios
      - name: Run unit tests
        run: ./gradlew test --no-daemon
      
      # Generar reporte de tests
      - name:  Publish test report
        uses: dorny/test-reporter@v1
        if: always()
        with:
          name:  JUnit Test Results
          path: build/test-results/test/*. xml
          reporter: java-junit
          fail-on-error:  true
      
      # Generar reporte de cobertura
      - name: Generate coverage report
        run: ./gradlew jacocoTestReport --no-daemon
      
      # Verificar umbrales de cobertura
      - name:  Verify coverage thresholds
        run: ./gradlew jacocoTestCoverageVerification --no-daemon
      
      # Subir reporte de cobertura a Codecov
      - name: Upload coverage to Codecov
        uses: codecov/codecov-action@v3
        with:
          files: build/reports/jacoco/test/jacocoTestReport.xml
          flags: unittests
          name: codecov-umbrella
          fail_ci_if_error: false
      
      # Cachear dependencias para siguientes jobs
      - name: Cache build artifacts
        uses: actions/cache@v3
        with:
          path:  |
            ~/.gradle/caches
            ~/.gradle/wrapper
            build/
          key: ${{ runner.os }}-gradle-${{ hashFiles('**/*.gradle*', '**/gradle-wrapper.properties') }}
          restore-keys: |
            ${{ runner.os }}-gradle-
      
      # Subir JAR como artifact
      - name: Upload JAR artifact
        uses: actions/upload-artifact@v3
        with: 
          name: application-jar
          path: build/libs/*.jar
          retention-days: 7
  
  # ==========================================
  # Job 2: Tests de Integración
  # ==========================================
  integration-tests:
    name: Integration Tests (Testcontainers)
    runs-on: ubuntu-latest
    needs: build
    timeout-minutes: 20
    
    services:
      # PostgreSQL para tests que no usan Testcontainers
      postgres: 
        image: postgres:16-alpine
        env:
          POSTGRES_DB: testdb
          POSTGRES_USER: testuser
          POSTGRES_PASSWORD: testpass
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
        ports:
          - 5432:5432
    
    steps:
      - name:  Checkout code
        uses: actions/checkout@v4
      
      - name: Setup JDK ${{ env.JAVA_VERSION }}
        uses: actions/setup-java@v4
        with:
          java-version:  ${{ env.JAVA_VERSION }}
          distribution: 'temurin'
          cache: 'gradle'
      
      # Restaurar caché de build
      - name: Restore Gradle cache
        uses: actions/cache@v3
        with:
          path: |
            ~/.gradle/caches
            ~/.gradle/wrapper
            build/
          key: ${{ runner.os }}-gradle-${{ hashFiles('**/*.gradle*', '**/gradle-wrapper.properties') }}
      
      # Ejecutar tests de integración
      - name: Run integration tests
        run: ./gradlew integrationTest --no-daemon
        env:
          SPRING_DATASOURCE_URL: jdbc:postgresql://localhost:5432/testdb
          SPRING_DATASOURCE_USERNAME: testuser
          SPRING_DATASOURCE_PASSWORD: testpass
      
      - name: Publish integration test report
        uses: dorny/test-reporter@v1
        if:  always()
        with:
          name: Integration Test Results
          path: build/test-results/integrationTest/*.xml
          reporter: java-junit
  
  # ==========================================
  # Job 3: Análisis de Calidad de Código
  # ==========================================
  code-quality:
    name: Code Quality Analysis
    runs-on:  ubuntu-latest
    needs: build
    timeout-minutes: 15
    
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
        with:
          fetch-depth: 0
      
      - name: Setup JDK ${{ env.JAVA_VERSION }}
        uses: actions/setup-java@v4
        with: 
          java-version: ${{ env.JAVA_VERSION }}
          distribution: 'temurin'
          cache: 'gradle'
      
      - name: Cache SonarQube packages
        uses: actions/cache@v3
        with:
          path: ~/.sonar/cache
          key: ${{ runner.os }}-sonar
          restore-keys: ${{ runner.os }}-sonar
      
      # Análisis con SonarQube
      - name: Run SonarQube analysis
        env:
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
          GITHUB_TOKEN: ${{ secrets. GITHUB_TOKEN }}
        run:  |
          ./gradlew sonarqube \
            -Dsonar.projectKey=my-project \
            -Dsonar.organization=my-org \
            -Dsonar.host.url=https://sonarcloud.io \
            -Dsonar. token=$SONAR_TOKEN \
            --no-daemon
      
      # Esperar resultado del Quality Gate
      - name: Wait for SonarQube Quality Gate
        uses: sonarsource/sonarqube-quality-gate-action@master
        timeout-minutes: 5
        env:
          SONAR_TOKEN: ${{ secrets. SONAR_TOKEN }}
  
  # ==========================================
  # Job 4: Seguridad - Escaneo de Dependencias
  # ==========================================
  security-scan:
    name: Security Vulnerability Scan
    runs-on:  ubuntu-latest
    needs: build
    
    steps:
      - name:  Checkout code
        uses: actions/checkout@v4
      
      - name: Setup JDK ${{ env.JAVA_VERSION }}
        uses: actions/setup-java@v4
        with:
          java-version:  ${{ env.JAVA_VERSION }}
          distribution: 'temurin'
          cache: 'gradle'
      
      # Escaneo de dependencias con OWASP Dependency-Check
      - name: Run OWASP Dependency Check
        run: ./gradlew dependencyCheckAnalyze --no-daemon
      
      - name: Upload dependency check report
        uses: actions/upload-artifact@v3
        if:  always()
        with:
          name: dependency-check-report
          path:  build/reports/dependency-check-report.html
      
      # Escaneo de código con Trivy
      - name: Run Trivy security scanner
        uses: aquasecurity/trivy-action@master
        with:
          scan-type: 'fs'
          scan-ref: '.'
          format: 'sarif'
          output: 'trivy-results.sarif'
      
      - name: Upload Trivy results to GitHub Security
        uses: github/codeql-action/upload-sarif@v2
        if: always()
        with:
          sarif_file: 'trivy-results.sarif'
  
  # ==========================================
  # Job 5: Verificación Multi-OS (Matrix)
  # ==========================================
  multi-platform-test:
    name: Test on ${{ matrix.os }}
    runs-on: ${{ matrix.os }}
    needs: build
    
    strategy:
      fail-fast: false
      matrix: 
        os: [ubuntu-latest, windows-latest, macos-latest]
    
    steps: 
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name:  Setup JDK ${{ env. JAVA_VERSION }}
        uses: actions/setup-java@v4
        with:
          java-version: ${{ env. JAVA_VERSION }}
          distribution:  'temurin'
          cache: 'gradle'
      
      - name: Run tests on ${{ matrix.os }}
        run: ./gradlew test --no-daemon
      
      - name: Upload test results
        uses: actions/upload-artifact@v3
        if: always()
        with:
          name: test-results-${{ matrix.os }}
          path: build/test-results/test/*. xml
  
  # ==========================================
  # Job 6: Resumen Final
  # ==========================================
  ci-summary:
    name: CI Summary
    runs-on: ubuntu-latest
    needs: [build, integration-tests, code-quality, security-scan]
    if: always()
    
    steps:
      - name: Check job results
        run: |
          echo "Build: ${{ needs.build.result }}"
          echo "Integration Tests: ${{ needs.integration-tests.result }}"
          echo "Code Quality: ${{ needs.code-quality.result }}"
          echo "Security Scan: ${{ needs.security-scan.result }}"
          
          if [[ "${{ needs.build.result }}" != "success" ]] || \
             [[ "${{ needs.integration-tests.result }}" != "success" ]] || \
             [[ "${{ needs.code-quality.result }}" != "success" ]]; then
            echo "❌ CI Pipeline failed"
            exit 1
          fi
          
          echo "✅ CI Pipeline passed"
      
      - name: Create summary
        run: |
          echo "# CI Pipeline Summary" >> $GITHUB_STEP_SUMMARY
          echo "" >> $GITHUB_STEP_SUMMARY
          echo "| Job | Status |" >> $GITHUB_STEP_SUMMARY
          echo "|-----|--------|" >> $GITHUB_STEP_SUMMARY
          echo "| Build | ${{ needs.build.result }} |" >> $GITHUB_STEP_SUMMARY
          echo "| Integration Tests | ${{ needs.integration-tests.result }} |" >> $GITHUB_STEP_SUMMARY
          echo "| Code Quality | ${{ needs.code-quality.result }} |" >> $GITHUB_STEP_SUMMARY
          echo "| Security Scan | ${{ needs.security-scan. result }} |" >> $GITHUB_STEP_SUMMARY
```

---

#### Optimizaciones del Pipeline Java

**1. Caché de Gradle:**

El caché puede reducir el tiempo de build de 5 minutos a 30 segundos. 

```yaml
- name: Setup JDK
  uses: actions/setup-java@v4
  with:
    java-version: '21'
    distribution: 'temurin'
    cache: 'gradle'  # ← Esto cachea ~/. gradle automáticamente
```

**Caché manual más agresivo:**

```yaml
- name: Cache Gradle packages
  uses: actions/cache@v3
  with:
    path: |
      ~/.gradle/caches
      ~/.gradle/wrapper
      ~/. m2/repository
    key:  ${{ runner.os }}-gradle-${{ hashFiles('**/*. gradle*', '**/gradle-wrapper.properties') }}
    restore-keys: |
      ${{ runner.os }}-gradle-
```

**2. Build Scan de Gradle:**

Agregar al `build.gradle. kts`:

```kotlin
plugins {
    id("com.gradle.enterprise") version "3.16"
}

gradleEnterprise {
    buildScan {
        termsOfServiceUrl = "https://gradle.com/terms-of-service"
        termsOfServiceAgree = "yes"
        publishAlways()
    }
}
```

Esto genera un enlace público con análisis detallado del build.

**3. Paralelización de tests:**

```kotlin
tasks.test {
    maxParallelForks = Runtime.getRuntime().availableProcessors()
}
```

**4. Gradle Configuration Cache:**

```yaml
env:
  GRADLE_OPTS: -Dorg.gradle.configuration-cache=true
```

Acelera builds subsecuentes en un 20-50%.

---

### . NET 10 & C# 14

**Configuración del Proyecto:**

**Directory.Build.props (en la raíz de la solución):**

```xml
<Project>
  <PropertyGroup>
    <TargetFramework>net10.0</TargetFramework>
    <LangVersion>14. 0</LangVersion>
    <Nullable>enable</Nullable>
    <ImplicitUsings>enable</ImplicitUsings>
    <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
    <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
  </PropertyGroup>

  <ItemGroup>
    <!-- Análisis de código -->
    <PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="8.0.0">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
    </PackageReference>
  </ItemGroup>
</Project>
```

**MyApp.csproj:**

```xml
<Project Sdk="Microsoft.NET.Sdk. Web">

  <PropertyGroup>
    <TargetFramework>net10.0</TargetFramework>
    <LangVersion>14.0</LangVersion>
    <Nullable>enable</Nullable>
    <ImplicitUsings>enable</ImplicitUsings>
    <Version>1.0.0</Version>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="10.0.0" />
    <PackageReference Include="Npgsql.EntityFrameworkCore. PostgreSQL" Version="10.0.0" />
    <PackageReference Include="Swashbuckle.AspNetCore" Version="6.5.0" />
  </ItemGroup>

</Project>
```

**MyApp.Tests.csproj:**

```xml
<Project Sdk="Microsoft. NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net10.0</TargetFramework>
    <LangVersion>14.0</LangVersion>
    <IsPackable>false</IsPackable>
    <IsTestProject>true</IsTestProject>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="coverlet.collector" Version="6.0.0" />
    <PackageReference Include="FluentAssertions" Version="6.12.0" />
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="17.9.0" />
    <PackageReference Include="Moq" Version="4.20.70" />
    <PackageReference Include="NUnit" Version="4.0.1" />
    <PackageReference Include="NUnit. Analyzers" Version="4.0.1" />
    <PackageReference Include="NUnit3TestAdapter" Version="4.5.0" />
    <PackageReference Include="Testcontainers.PostgreSql" Version="3.7.0" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\MyApp\MyApp.csproj" />
  </ItemGroup>

</Project>
```

---

#### GitHub Actions Workflow para . NET

**. github/workflows/ci-dotnet.yml:**

```yaml
name: .NET CI Pipeline

on:
  push: 
    branches: [ main, develop ]
    paths: 
      - 'src/**'
      - 'tests/**'
      - '**. csproj'
      - '**.sln'
      - '. github/workflows/ci-dotnet.yml'
  pull_request:
    branches: [ main ]

env:
  DOTNET_VERSION: '10.0.x'
  DOTNET_SKIP_FIRST_TIME_EXPERIENCE: true
  DOTNET_CLI_TELEMETRY_OPTOUT: true

jobs:
  # ==========================================
  # Job 1: Build y Tests Unitarios
  # ==========================================
  build-and-test: 
    name: Build & Unit Tests
    runs-on: ${{ matrix.os }}
    timeout-minutes: 15
    
    strategy:
      fail-fast: false
      matrix: 
        os: [ubuntu-latest, windows-latest, macos-latest]
    
    steps: 
      - name: Checkout code
        uses: actions/checkout@v4
        with:
          fetch-depth:  0  # Para versionado
      
      - name: Setup . NET ${{ env.DOTNET_VERSION }}
        uses: actions/setup-dotnet@v4
        with:
          dotnet-version: ${{ env. DOTNET_VERSION }}
      
      # Restaurar dependencias
      - name: Restore dependencies
        run: dotnet restore
      
      # Validar formato de código
      - name: Check code formatting
        run: dotnet format --verify-no-changes --verbosity diagnostic
        continue-on-error: true
      
      # Compilar en Release
      - name: Build solution
        run: dotnet build --configuration Release --no-restore
      
      # Ejecutar tests unitarios con cobertura
      - name: Run unit tests
        run: |
          dotnet test \
            --configuration Release \
            --no-build \
            --verbosity normal \
            --logger "trx;LogFileName=test-results.trx" \
            --collect:"XPlat Code Coverage" \
            --results-directory ./TestResults \
            -- DataCollectionRunSettings.DataCollectors.DataCollector.Configuration.Format=opencover
      
      # Publicar resultados de tests
      - name:  Publish test results
        uses: dorny/test-reporter@v1
        if: always() && matrix.os == 'ubuntu-latest'
        with:
          name: Test Results (. NET)
          path: TestResults/**/*.trx
          reporter: dotnet-trx
      
      # Generar reporte HTML de cobertura
      - name: Generate coverage report
        if: matrix.os == 'ubuntu-latest'
        run: |
          dotnet tool install -g dotnet-reportgenerator-globaltool
          reportgenerator \
            -reports:"TestResults/**/coverage.opencover.xml" \
            -targetdir:"CoverageReport" \
            -reporttypes:"Html;Cobertura"
      
      # Subir reporte de cobertura
      - name: Upload coverage to Codecov
        if: matrix.os == 'ubuntu-latest'
        uses: codecov/codecov-action@v3
        with:
          files: CoverageReport/Cobertura.xml
          flags: unittests
          name: codecov-dotnet
      
      # Verificar umbral de cobertura
      - name:  Verify coverage threshold
        if: matrix.os == 'ubuntu-latest'
        run: |
          COVERAGE=$(grep -oP 'line-rate="\K[0-9.]+' CoverageReport/Cobertura.xml | head -1)
          COVERAGE_PERCENT=$(echo "$COVERAGE * 100" | bc)
          echo "Coverage: $COVERAGE_PERCENT%"
          
          if (( $(echo "$COVERAGE < 0.80" | bc -l) )); then
            echo "❌ Coverage is below 80%"
            exit 1
          fi
          
          echo "✅ Coverage meets threshold"
      
      # Empaquetar artefactos
      - name:  Publish artifacts
        if: matrix.os == 'ubuntu-latest'
        run: |
          dotnet publish src/MyApp/MyApp.csproj \
            --configuration Release \
            --output ./publish \
            --no-build
      
      - name: Upload publish artifacts
        if: matrix.os == 'ubuntu-latest'
        uses: actions/upload-artifact@v3
        with:
          name: dotnet-app
          path: ./publish
          retention-days: 7
  
  # ==========================================
  # Job 2: Tests de Integración
  # ==========================================
  integration-tests: 
    name: Integration Tests (Testcontainers)
    runs-on: ubuntu-latest
    needs: build-and-test
    timeout-minutes: 20
    
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Setup .NET ${{ env.DOTNET_VERSION }}
        uses: actions/setup-dotnet@v4
        with:
          dotnet-version: ${{ env.DOTNET_VERSION }}
      
      - name: Restore dependencies
        run: dotnet restore
      
      - name: Build solution
        run: dotnet build --configuration Release --no-restore
      
      # Ejecutar tests de integración
      - name: Run integration tests
        run: |
          dotnet test tests/MyApp.IntegrationTests/MyApp.IntegrationTests.csproj \
            --configuration Release \
            --no-build \
            --verbosity normal \
            --logger "trx;LogFileName=integration-test-results.trx" \
            --results-directory ./IntegrationTestResults
      
      - name:  Publish integration test results
        uses:  dorny/test-reporter@v1
        if: always()
        with:
          name:  Integration Test Results
          path: IntegrationTestResults/**/*.trx
          reporter: dotnet-trx
  
  # ==========================================
  # Job 3: Análisis de Código con SonarQube
  # ==========================================
  code-analysis:
    name: SonarQube Analysis
    runs-on: windows-latest  # SonarScanner funciona mejor en Windows para . NET
    needs: build-and-test
    
    steps:
      - name:  Checkout code
        uses: actions/checkout@v4
        with:
          fetch-depth: 0
      
      - name: Setup . NET ${{ env.DOTNET_VERSION }}
        uses: actions/setup-dotnet@v4
        with:
          dotnet-version: ${{ env.DOTNET_VERSION }}
      
      - name: Setup Java (required for SonarScanner)
        uses: actions/setup-java@v4
        with:
          java-version: '17'
          distribution: 'temurin'
      
      - name: Install SonarScanner
        run: dotnet tool install --global dotnet-sonarscanner
      
      - name: Begin SonarQube analysis
        env:
          SONAR_TOKEN: ${{ secrets. SONAR_TOKEN }}
        run: |
          dotnet sonarscanner begin `
            /k:"my-dotnet-project" `
            /o:"my-org" `
            /d:sonar.host.url="https://sonarcloud.io" `
            /d:sonar.token="${env:SONAR_TOKEN}" `
            /d:sonar. cs.opencover.reportsPaths="**/TestResults/**/coverage.opencover.xml"
      
      - name: Build and test
        run: |
          dotnet build --configuration Release
          dotnet test --configuration Release --collect:"XPlat Code Coverage" -- DataCollectionRunSettings.DataCollectors.DataCollector.Configuration. Format=opencover
      
      - name: End SonarQube analysis
        env:
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
        run: dotnet sonarscanner end /d: sonar.token="${env:SONAR_TOKEN}"
  
  # ==========================================
  # Job 4: Seguridad - Escaneo de Vulnerabilidades
  # ==========================================
  security-audit:
    name: Security Audit
    runs-on: ubuntu-latest
    needs: build-and-test
    
    steps: 
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Setup .NET ${{ env.DOTNET_VERSION }}
        uses: actions/setup-dotnet@v4
        with:
          dotnet-version: ${{ env.DOTNET_VERSION }}
      
      # Escanear dependencias vulnerables
      - name: Run dotnet list package --vulnerable
        run: |
          dotnet list package --vulnerable --include-transitive > vulnerabilities.txt
          cat vulnerabilities.txt
          
          if grep -q "has the following vulnerable packages" vulnerabilities.txt; then
            echo "⚠️ Vulnerable packages found"
            exit 1
          fi
      
      # Análisis con Trivy
      - name: Run Trivy scanner
        uses: aquasecurity/trivy-action@master
        with:
          scan-type: 'fs'
          scan-ref: '.'
          format: 'sarif'
          output: 'trivy-results.sarif'
      
      - name: Upload Trivy results
        uses: github/codeql-action/upload-sarif@v2
        if: always()
        with:
          sarif_file: 'trivy-results.sarif'
  
  # ==========================================
  # Job 5: Build Docker Image
  # ==========================================
  docker-build:
    name:  Build Docker Image
    runs-on: ubuntu-latest
    needs:  [build-and-test, integration-tests]
    if: github.event_name == 'push' && github.ref == 'refs/heads/main'
    
    steps:
      - name:  Checkout code
        uses: actions/checkout@v4
      
      - name: Download publish artifacts
        uses: actions/download-artifact@v3
        with:
          name: dotnet-app
          path: ./publish
      
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3
      
      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKER_USERNAME }}
          password: ${{ secrets. DOCKER_PASSWORD }}
      
      - name: Docker metadata
        id: meta
        uses: docker/metadata-action@v5
        with:
          images: myorg/myapp-dotnet
          tags: |
            type=ref,event=branch
            type=sha,prefix={{branch}}-
            type=semver,pattern={{version}}
      
      - name: Build and push
        uses: docker/build-push-action@v5
        with:
          context: . 
          push: true
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
```

---

#### Dockerfile para .NET (Multi-stage)

**Dockerfile:**

```dockerfile
# ============================================
# Stage 1: Build
# ============================================
FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /src

# Copiar archivos de proyecto y restaurar dependencias
COPY ["src/MyApp/MyApp. csproj", "src/MyApp/"]
COPY ["src/MyApp.Core/MyApp.Core.csproj", "src/MyApp. Core/"]
RUN dotnet restore "src/MyApp/MyApp.csproj"

# Copiar el resto del código
COPY . . 

# Compilar y publicar
WORKDIR "/src/src/MyApp"
RUN dotnet build "MyApp.csproj" -c Release -o /app/build
RUN dotnet publish "MyApp.csproj" -c Release -o /app/publish

# ============================================
# Stage 2: Runtime
# ============================================
FROM mcr.microsoft.com/dotnet/aspnet:10.0 AS final
WORKDIR /app

# Instalar herramientas de diagnóstico (opcional)
RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*

# Copiar artefactos publicados
COPY --from=build /app/publish .

# Usuario no-root
RUN useradd -m -u 1000 appuser && chown -R appuser:appuser /app
USER appuser

# Configuración
ENV ASPNETCORE_URLS=http://+:8080
ENV ASPNETCORE_ENVIRONMENT=Production
EXPOSE 8080

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD curl -f http://localhost:8080/health || exit 1

ENTRYPOINT ["dotnet", "MyApp.dll"]
```

---

### 3.2. Ejecución de la Suite de Tests

#### Testcontainers en el Pipeline

**Problema**:  Los tests de integración necesitan servicios reales (PostgreSQL, Redis, etc.).

**Solución**: Testcontainers levanta contenedores Docker durante los tests.

**Configuración en el runner:**

GitHub Actions runners ya tienen Docker instalado y corriendo.  No necesitas configuración adicional.

**Ejemplo de test con Testcontainers (Java):**

```java
@SpringBootTest
@Testcontainers
public class UserRepositoryIntegrationTest {
    
    @Container
    @ServiceConnection  // Spring Boot 3.1+
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16-alpine")
        .withDatabaseName("testdb")
        .withUsername("testuser")
        .withPassword("testpass");
    
    @Autowired
    private UserRepository userRepository;
    
    @Test
    void shouldSaveAndRetrieveUser() {
        User user = new User("john", "john@example.com");
        userRepository.save(user);
        
        Optional<User> found = userRepository.findByUsername("john");
        
        assertThat(found).isPresent();
        assertThat(found.get().getEmail()).isEqualTo("john@example.com");
    }
}
```

**Ejemplo de test con Testcontainers (. NET):**

```csharp
[TestFixture]
public class UserRepositoryIntegrationTests
{
    private PostgreSqlContainer _postgresContainer = null! ;
    private UserDbContext _dbContext = null!;

    [OneTimeSetUp]
    public async Task OneTimeSetup()
    {
        _postgresContainer = new PostgreSqlBuilder()
            .WithImage("postgres:16-alpine")
            .WithDatabase("testdb")
            .WithUsername("testuser")
            .WithPassword("testpass")
            .Build();

        await _postgresContainer.StartAsync();

        var options = new DbContextOptionsBuilder<UserDbContext>()
            .UseNpgsql(_postgresContainer.GetConnectionString())
            .Options;

        _dbContext = new UserDbContext(options);
        await _dbContext.Database. EnsureCreatedAsync();
    }

    [Test]
    public async Task ShouldSaveAndRetrieveUser()
    {
        // Arrange
        var user = new User { Username = "john", Email = "john@example.com" };
        _dbContext.Users.Add(user);
        await _dbContext.SaveChangesAsync();

        // Act
        var found = await _dbContext.Users.FirstOrDefaultAsync(u => u.Username == "john");

        // Assert
        found.Should().NotBeNull();
        found! .Email.Should().Be("john@example.com");
    }

    [OneTimeTearDown]
    public async Task OneTimeTearDown()
    {
        await _dbContext. DisposeAsync();
        await _postgresContainer.DisposeAsync();
    }
}
```

**Optimización:   Reutilización de contenedores:**

Por defecto, Testcontainers crea un contenedor nuevo para cada clase de test. Para acelerar, reutiliza contenedores: 

**Singleton pattern (Java):**

```java
public abstract class AbstractIntegrationTest {
    
    private static final PostgreSQLContainer<?> POSTGRES;
    
    static {
        POSTGRES = new PostgreSQLContainer<>("postgres:16-alpine")
            .withReuse(true);  // Reutilizar entre ejecuciones
        POSTGRES.start();
    }
    
    @DynamicPropertySource
    static void properties(DynamicPropertyRegistry registry) {
        registry.add("spring.datasource.url", POSTGRES::getJdbcUrl);
        registry.add("spring. datasource.username", POSTGRES:: getUsername);
        registry.add("spring.datasource.password", POSTGRES::getPassword);
    }
}
```

**Compartir contenedor (. NET):**

```csharp
public class SharedPostgresFixture : IAsyncLifetime
{
    public PostgreSqlContainer PostgresContainer { get; private set; } = null!;

    public async Task InitializeAsync()
    {
        PostgresContainer = new PostgreSqlBuilder()
            .WithImage("postgres:16-alpine")
            .Build();

        await PostgresContainer.StartAsync();
    }

    public async Task DisposeAsync()
    {
        await PostgresContainer. DisposeAsync();
    }
}

[TestFixture]
public class UserRepositoryTests :  IClassFixture<SharedPostgresFixture>
{
    private readonly SharedPostgresFixture _fixture;

    public UserRepositoryTests(SharedPostgresFixture fixture)
    {
        _fixture = fixture;
    }

    // Tests usan _fixture.PostgresContainer. GetConnectionString()
}
```

---

### 3.3. Control de Calidad y Cobertura

#### Configuración de JaCoCo (Java)

Ya configuramos JaCoCo en el `build.gradle. kts`. Ahora integrémoslo con el workflow:

**Verificar cobertura en el pipeline:**

```yaml
- name: Verify coverage threshold
  run: ./gradlew jacocoTestCoverageVerification
```

Este comando falla si la cobertura está por debajo del umbral configurado (80% en nuestro caso).

**Generar reporte HTML:**

```yaml
- name: Generate coverage report
  run: ./gradlew jacocoTestReport

- name: Upload coverage report
  uses: actions/upload-artifact@v3
  with:
    name: coverage-report
    path: build/reports/jacoco/test/html/
```

**Integración con Codecov:**

```yaml
- name: Upload to Codecov
  uses: codecov/codecov-action@v3
  with:
    files: build/reports/jacoco/test/jacocoTestReport.xml
    flags: unittests
    fail_ci_if_error: false
```

**Codecov mostrará:**
- Badge de cobertura en el README
- Reporte detallado por archivo
- Comparación entre commits
- Comentarios automáticos en PRs

---

#### Configuración de Coverlet (. NET)

**Generar reporte XML:**

```bash
dotnet test \
  --collect:"XPlat Code Coverage" \
  -- DataCollectionRunSettings.DataCollectors.DataCollector.Configuration. Format=opencover
```

**Generar reporte HTML con ReportGenerator:**

```yaml
- name: Install ReportGenerator
  run: dotnet tool install -g dotnet-reportgenerator-globaltool

- name: Generate HTML report
  run: |
    reportgenerator \
      -reports:"TestResults/**/coverage.opencover.xml" \
      -targetdir:"CoverageReport" \
      -reporttypes:"Html;Cobertura"

- name: Upload coverage report
  uses: actions/upload-artifact@v3
  with:
    name: coverage-report-dotnet
    path: CoverageReport/
```

**Verificar umbral:**

```yaml
- name: Check coverage threshold
  run: |
    COVERAGE=$(grep -oP 'line-rate="\K[0-9.]+' CoverageReport/Cobertura.xml | head -1)
    COVERAGE_PERCENT=$(echo "$COVERAGE * 100" | bc)
    
    if (( $(echo "$COVERAGE < 0.80" | bc -l) )); then
      echo "❌ Coverage $COVERAGE_PERCENT% is below 80%"
      exit 1
    fi
    
    echo "✅ Coverage $COVERAGE_PERCENT% meets threshold"
```

---

## 4. Automatización del Frontend en Netlify

### Introducción:  Por Qué Netlify para Frontends

**Netlify** es una plataforma especializada en el despliegue de aplicaciones **JAMstack** (JavaScript, APIs, Markup). A diferencia de plataformas generales como AWS o Azure, Netlify está optimizado específicamente para: 

- ✅ **Single Page Applications (SPAs)**: React, Vue, Angular, Svelte
- ✅ **Static Site Generators**:  Next.js, Gatsby, Hugo, Eleventy
- ✅ **Progressive Web Apps (PWAs)**
- ✅ **Sites estáticos** con contenido dinámico via APIs

**Ventajas sobre hosting tradicional:**

| Característica      | Hosting Tradicional            | Netlify                      |
| ------------------- | ------------------------------ | ---------------------------- |
| **Deploy**          | FTP manual, scripts SSH        | Git push automático          |
| **HTTPS**           | Configuración manual           | Automático con Let's Encrypt |
| **CDN Global**      | Configuración compleja/costosa | Incluido (100+ PoPs)         |
| **Rollback**        | Restore manual de archivos     | Un click                     |
| **Preview Deploys** | Ambiente staging separado      | Automático por PR            |
| **Forms**           | Backend necesario              | Serverless incluido          |
| **Redirects**       | Configurar Nginx/Apache        | Archivo `_redirects`         |

💡 **Nota del Profesor**: Netlify democratizó el despliegue de frontends.  Lo que antes requería un DevOps senior configurando CDNs, certificados SSL y sistemas de deploy, ahora se hace automáticamente conectando tu repositorio de GitHub. 

---

### 4.1. Flujo de Trabajo Netlify-GitHub

#### Arquitectura de Integración

```
┌─────────────────────────────────────────────────────────────┐
│                    GitHub Repository                        │
│                                                             │
│  main branch     →  Production (app.example.com)            │
│  develop branch  →  Staging (staging--app.netlify.app)      │
│  PR #123        →  Preview (deploy-preview-123--app....)  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
                            ↓
                   Netlify Build System
                            ↓
        ┌────────────────────────────────────┐
        │  1. npm install                    │
        │  2. npm run build                  │
        │  3. Deploy to CDN                  │
        │  4. Update DNS                     │
        │  5. Comment on PR with URL         │
        └────────────────────────────────────┘
                            ↓
            Global CDN (150+ ubicaciones)
                            ↓
                    👥 Usuarios Finales
```

---

#### 🛠️ Paso a Paso: Configuración Inicial

**1. Crear cuenta en Netlify:**

- Ir a https://www.netlify.com
- Sign up with GitHub (recomendado para mejor integración)
- Autorizar acceso a repositorios

**2. Conectar Repositorio:**

1. Dashboard → **Add new site** → **Import an existing project**
2. Seleccionar **GitHub**
3. Buscar y seleccionar tu repositorio
4. Configurar build settings: 

```yaml
Build command: npm run build
Publish directory: dist
```

(Netlify detecta automáticamente Vue, React, etc.  y sugiere configuraciones)

**3. Variables de Entorno:**

Site settings → Environment variables → Add a variable

```
Key: VITE_API_URL
Value: https://api.example.com
```

**4. Deploy! **

Click en **Deploy site** y Netlify: 
- Clona el repo
- Ejecuta `npm install`
- Ejecuta `npm run build`
- Despliega a CDN
- Asigna URL temporal:  `https://random-name-12345.netlify.app`

---

#### Configuración Avanzada: netlify.toml

Para configuraciones complejas, crea un archivo `netlify.toml` en la raíz del proyecto:

**netlify.toml:**

```toml
# ============================================
# Configuración de Build
# ============================================
[build]
  # Comando de build
  command = "npm run build"
  
  # Directorio a publicar
  publish = "dist"
  
  # Directorio base (si el frontend está en subdirectorio)
  base = "frontend/"
  
  # Variables de entorno del build
  environment = { NODE_VERSION = "20", VITE_API_URL = "https://api.example.com" }

# ============================================
# Configuración de Contexto (por rama)
# ============================================

# Producción (main branch)
[context.production]
  command = "npm run build: prod"
  environment = { VITE_API_URL = "https://api.example.com", VITE_ENV = "production" }

# Staging (develop branch)
[context.develop]
  command = "npm run build:staging"
  environment = { VITE_API_URL = "https://api-staging.example.com", VITE_ENV = "staging" }

# Deploy previews (PRs)
[context.deploy-preview]
  command = "npm run build:preview"
  environment = { VITE_API_URL = "https://api-staging.example.com", VITE_ENV = "preview" }

# Branch deploys (otras ramas)
[context.branch-deploy]
  command = "npm run build"

# ============================================
# Headers HTTP Personalizados
# ============================================
[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-Content-Type-Options = "nosniff"
    X-XSS-Protection = "1; mode=block"
    Referrer-Policy = "strict-origin-when-cross-origin"
    Permissions-Policy = "geolocation=(), microphone=(), camera=()"
    
    # Cache de assets
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "*. html"
  [headers.values]
    Cache-Control = "public, max-age=0, must-revalidate"

[[headers]]
  for = "/api/*"
  [headers.values]
    Access-Control-Allow-Origin = "*"
    Access-Control-Allow-Methods = "GET, POST, PUT, DELETE, OPTIONS"

# ============================================
# Redirects y Rewrites
# ============================================

# SPA routing:  Todas las rutas no encontradas van a index.html
[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200

# Redirect de www a apex domain
[[redirects]]
  from = "https://www.example.com/*"
  to = "https://example.com/: splat"
  status = 301
  force = true

# API proxy (evitar CORS en desarrollo)
[[redirects]]
  from = "/api/*"
  to = "https://api.example.com/:splat"
  status = 200
  force = false
  headers = {X-From = "Netlify"}

# Redirect de rutas legacy
[[redirects]]
  from = "/old-page"
  to = "/new-page"
  status = 301

# Redirect condicional por país
[[redirects]]
  from = "/store"
  to = "/store/us"
  status = 302
  conditions = {Country = ["US"]}

[[redirects]]
  from = "/store"
  to = "/store/eu"
  status = 302
  conditions = {Country = ["GB", "FR", "DE", "ES"]}

# ============================================
# Funciones Serverless (opcional)
# ============================================
[functions]
  directory = "netlify/functions"
  node_bundler = "esbuild"

# ============================================
# Plugins de Netlify
# ============================================
[[plugins]]
  package = "@netlify/plugin-lighthouse"
  
  [plugins.inputs]
    output_path = "reports/lighthouse. html"

[[plugins]]
  package = "netlify-plugin-submit-sitemap"
  
  [plugins.inputs]
    baseUrl = "https://example.com"
    sitemapPath = "/sitemap.xml"
    providers = ["google", "bing"]

# ============================================
# Optimizaciones
# ============================================
[build.processing]
  skip_processing = false

[build.processing.css]
  bundle = true
  minify = true

[build.processing.js]
  bundle = true
  minify = true

[build.processing. html]
  pretty_urls = true

[build.processing.images]
  compress = true
```

---

#### Configuración de Redirects para SPAs

**Problema**: En una SPA, todas las rutas son manejadas por JavaScript.  Si un usuario navega directamente a `https://app.com/dashboard`, el servidor no encuentra ese archivo y devuelve 404.

**Solución**:  Redirigir todas las peticiones a `index.html`.

**Opción 1: Archivo `_redirects`**

Crear archivo `public/_redirects`:

```
# Redirigir todo a index.html para SPA routing
/*    /index.html   200

# Excepto archivos reales
/images/*  /images/: splat  200
/assets/*  /assets/:splat  200
```

**Opción 2: En `netlify.toml`** (ya mostrado arriba)

**Opción 3: Vue Router con historyFallback**

Para Vue Router con modo `history`:

```javascript
// vue.config.js
module.exports = {
  publicPath: '/',
  devServer: {
    historyApiFallback: true
  }
}
```

Y en Netlify:

```toml
[[redirects]]
  from = "/*"
  to = "/index. html"
  status = 200
```

---

### 4.2. Preview Deployments:  Entornos Temporales por PR

**Preview Deployments** son una de las features más poderosas de Netlify.  Cada Pull Request obtiene su propia URL temporal con el código del PR desplegado.

#### Flujo de Trabajo

```
Developer: 
  1. git checkout -b feature/new-button
  2. git commit -am "Add awesome button"
  3. git push origin feature/new-button
  4.  Crear PR en GitHub

GitHub Actions (opcional):
  5. Ejecutar tests
  6. Build success ✅

Netlify:
  7. Detectar nuevo commit en PR
  8. Clonar código del PR
  9. npm install
  10. npm run build
  11. Desplegar en URL temporal
  12. Comentar en PR con URL: 
      "✅ Deploy preview ready! 
       🔗 https://deploy-preview-42--myapp.netlify.app"

Team:
  13. QA revisa en la URL temporal
  14. Product Owner aprueba
  15. Merge PR → Deploy automático a producción
```

#### Configuración de Deploy Previews

**En Netlify Dashboard:**

Site settings → Build & deploy → Deploy contexts

```
✅ Production deploys:  Deploy only the production branch
   Production branch: main

✅ Deploy previews: Any pull request against your production branch
   ☐ Branch deploys: Deploy only specific branches
```

**Personalizar comando de build para previews:**

```toml
[context.deploy-preview]
  command = "npm run build:preview"
  environment = { 
    VITE_API_URL = "https://api-staging.example.com",
    VITE_FEATURE_FLAGS = "all"
  }
```

#### Integración con GitHub Checks

Netlify se integra con GitHub Status Checks: 

```
GitHub PR → Checks: 
  ✅ Netlify deploy:  Deploy preview ready
     Details: https://deploy-preview-42--myapp.netlify.app
  ✅ Lighthouse scores: All checks passed
  ✅ Build time: 1m 23s
```

**Configurar protección de rama con Netlify:**

GitHub repo → Settings → Branches → Branch protection rules (main):

```
☑ Require status checks to pass before merging
  ☑ netlify/myapp/deploy-preview
```

Ahora no se puede hacer merge si el deploy preview falla.

---

### 4.3. Variables de Entorno por Contexto

**Problema**: El frontend necesita diferentes configuraciones según el entorno (dev, staging, prod).

**Solución**: Variables de entorno específicas por contexto.

#### Configuración en Netlify UI

Site settings → Environment variables: 

```
Variable: VITE_API_URL

Contexts:
  Production:         https://api.example.com
  Deploy previews:   https://api-staging.example.com
  Branch deploys:    https://api-dev.example.com

Scopes:
  ☑ Builds
  ☑ Functions
  ☐ Post processing
```

#### Configuración en netlify.toml

```toml
[context.production. environment]
  VITE_API_URL = "https://api.example.com"
  VITE_ANALYTICS_ID = "UA-PRODUCTION-ID"
  VITE_SENTRY_DSN = "https://xxx@sentry.io/production"

[context.deploy-preview.environment]
  VITE_API_URL = "https://api-staging.example.com"
  VITE_ANALYTICS_ID = ""  # Deshabilitar analytics en previews
  VITE_SENTRY_DSN = "https://xxx@sentry.io/staging"
```

#### Uso en Vue. js

**vite.config.js:**

```javascript
import { defineConfig, loadEnv } from 'vite'
import vue from '@vitejs/plugin-vue'

export default defineConfig(({ mode }) => {
  const env = loadEnv(mode, process.cwd(), '')
  
  return {
    plugins: [vue()],
    
    define: {
      __APP_VERSION__: JSON.stringify(process.env.npm_package_version),
      __BUILD_TIME__: JSON.stringify(new Date().toISOString()),
    },
    
    server: {
      proxy: {
        '/api': {
          target: env.VITE_API_URL || 'http://localhost:8080',
          changeOrigin: true,
          rewrite: (path) => path.replace(/^\/api/, '')
        }
      }
    }
  }
})
```

**En componentes Vue:**

```vue
<script setup>
const apiUrl = import.meta.env. VITE_API_URL
const isDev = import.meta.env. DEV
const isProd = import.meta.env. PROD

console.log('API URL:', apiUrl)
console.log('Environment:', isDev ? 'development' : 'production')

async function fetchData() {
  const response = await fetch(`${apiUrl}/users`)
  return response.json()
}
</script>
```

**Tipos TypeScript para variables de entorno:**

**env.d.ts:**

```typescript
/// <reference types="vite/client" />

interface ImportMetaEnv {
  readonly VITE_API_URL: string
  readonly VITE_ANALYTICS_ID: string
  readonly VITE_SENTRY_DSN: string
  readonly VITE_FEATURE_FLAGS: string
}

interface ImportMeta {
  readonly env:  ImportMetaEnv
}
```

---

### Configuración de Dominios Personalizados

#### Agregar Dominio Custom

**En Netlify:**

1. Site settings → Domain management → Domains
2. Add custom domain
3. Ingresar:  `app.example.com`
4. Netlify proporciona registros DNS: 

```
Type: CNAME
Name: app
Value: myapp.netlify.app
```

5. Configurar en tu proveedor DNS (Cloudflare, Route53, etc.)
6. Netlify verifica automáticamente
7. HTTPS se habilita automáticamente con Let's Encrypt

#### Configuración de Apex Domain (sin www)

Para `example.com` (sin subdominio):

```
Type: A
Name: @
Value: 75.2.60.5

Type: A
Name: @
Value: 99.83.190.102

Type: A
Name: @
Value: 145.40.104.81

Type: A
Name: @
Value: 174.138.53.76
```

(IPs oficiales de Netlify Load Balancer)

#### Configuración de Subdominios Múltiples

```
app.example.com      → Aplicación principal
staging.example.com  → Rama develop
docs.example.com     → Documentación (otro site)
```

Cada uno configurado como sitio separado en Netlify.

---

### Optimizaciones y Best Practices

#### 1. Build Plugins

**Plugin de Lighthouse (análisis de performance):**

```toml
[[plugins]]
  package = "@netlify/plugin-lighthouse"
  
  [plugins.inputs]
    output_path = "reports/lighthouse"
    
    [[plugins.inputs.audits]]
      path = "/"
      thresholds = { performance = 0.9, accessibility = 0.9, seo = 0.9 }
    
    [[plugins.inputs.audits]]
      path = "/dashboard"
      thresholds = { performance = 0.85 }
```

**Plugin de optimización de imágenes:**

```toml
[[plugins]]
  package = "netlify-plugin-image-optim"
```

#### 2. Asset Optimization

**Configuración en netlify.toml:**

```toml
[build.processing]
  skip_processing = false

[build.processing.css]
  bundle = true
  minify = true

[build.processing. js]
  bundle = true
  minify = true

[build.processing.images]
  compress = true
```

#### 3. Caché Estratégico

```toml
# Assets con hash (inmutables)
[[headers]]
  for = "/assets/*"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

# HTML (nunca cachear)
[[headers]]
  for = "/*.html"
  [headers.values]
    Cache-Control = "public, max-age=0, must-revalidate"

# Service Worker
[[headers]]
  for = "/service-worker.js"
  [headers.values]
    Cache-Control = "public, max-age=0, must-revalidate"
```

#### 4. Prerendering para SEO

Para mejorar SEO en SPAs:

```toml
[[plugins]]
  package = "@netlify/plugin-nextjs"

# O para Vue/React
[[plugins]]
  package = "netlify-plugin-prerender-spa"
  
  [plugins.inputs]
    publicPath = "/dist"
    prerenderRoutes = [
      "/",
      "/about",
      "/contact",
      "/products/*"
    ]
```

#### 5. Split Testing (A/B Testing)

```toml
[[redirects]]
  from = "/*"
  to = "/experiment-a/: splat"
  status = 200
  conditions = {Cookie = ["experiment=a"]}
  force = true

[[redirects]]
  from = "/*"
  to = "/experiment-b/:splat"
  status = 200
  conditions = {Cookie = ["experiment=b"]}
  force = true

# 50% a cada variante
[[redirects]]
  from = "/*"
  to = "/experiment-a/:splat"
  status = 200
  force = false
  
[[redirects]]
  from = "/*"
  to = "/experiment-b/:splat"
  status = 200
  force = false
```

---

### Integración con GitHub Actions

Aunque Netlify maneja deploys automáticamente, puedes integrar checks adicionales con GitHub Actions:

**. github/workflows/frontend-checks.yml:**

```yaml
name: Frontend Checks

on: 
  pull_request:
    branches: [ main ]
    paths:
      - 'frontend/**'

jobs:
  lint-and-test:
    runs-on: ubuntu-latest
    
    steps:
      - uses:  actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
          cache-dependency-path: frontend/package-lock.json
      
      - name: Install dependencies
        working-directory: frontend
        run:  npm ci
      
      - name: Run ESLint
        working-directory:  frontend
        run: npm run lint
      
      - name: Run unit tests
        working-directory: frontend
        run: npm run test: unit
      
      - name:  Type check
        working-directory: frontend
        run: npm run type-check
      
      - name: Build (verify no errors)
        working-directory:  frontend
        run: npm run build
        env:
          VITE_API_URL: https://api-staging.example.com
      
      - name: Comment PR with bundle size
        uses: andresz1/size-limit-action@v1
        with: 
          github_token: ${{ secrets. GITHUB_TOKEN }}
          directory: frontend
```

**Flujo combinado:**

```
1. Developer crea PR
2. GitHub Actions ejecuta: 
   ✅ Linting
   ✅ Unit tests
   ✅ Type checking
   ✅ Build verification
3. Netlify ejecuta:
   ✅ Deploy preview
   ✅ Lighthouse audit
4. Ambos comentan en el PR
5. Solo se puede merge si todo pasa
```

---

### Monitorización y Debugging

#### Logs de Build

Netlify proporciona logs detallados de cada deploy:

```
9:23:14 AM: Build ready to start
9:23:16 AM: build-image version: 8a2f7780a0e0edd5ddb5e6b38be9eca5
9:23:16 AM: buildbot version: 7dfae24c1b6b5d37fc90df60ecca0fba
9:23:16 AM:  Fetching cached dependencies
9:23:16 AM: Starting to download cache of 234. 5MB
9:23:18 AM: Finished downloading cache in 1.856s
9:23:20 AM: Starting to extract cache
9:23:24 AM: Finished extracting cache in 3.987s
9:23:24 AM: Installing NPM modules using NPM version 10.2.3
9:23:35 AM: npm install completed
9:23:35 AM:  Started restoring cached build plugins
9:23:35 AM: Finished restoring cached build plugins
9:23:35 AM:  Different publish path detected, going to use the one specified in toml file:  'dist' versus 'build' in the Netlify UI
9:23:35 AM: Starting build script
9:23:36 AM: > frontend@1.0.0 build
9:23:36 AM: > vite build
9:23:38 AM: vite v5.0.8 building for production...
9:23:42 AM: ✓ 1247 modules transformed.
9:23:44 AM: dist/index.html                   0.46 kB │ gzip:  0.30 kB
9:23:44 AM: dist/assets/index-B7xGJ9Km.css   45.32 kB │ gzip:  10.21 kB
9:23:44 AM: dist/assets/index-DQwF8k3s.js   234.12 kB │ gzip:  75.43 kB
9:23:44 AM: ✓ built in 6.21s
9:23:44 AM: Build script success
9:23:45 AM: Uploading Cache of size 234.7MB
9:23:47 AM: Finished processing build request in 31.2s
```

#### Analytics

Netlify proporciona analytics integrados:

```
Site overview → Analytics: 
  - Page views
  - Unique visitors
  - Top pages
  - Traffic sources
  - Bandwidth usage
  - Build minutes used
```

#### Deploy Notifications

Configurar notificaciones en Slack/Discord:

Site settings → Build & deploy → Deploy notifications

```
Types: 
  ☑ Deploy started
  ☑ Deploy succeeded
  ☑ Deploy failed
  ☑ Deploy locked
  ☑ Deploy unlocked

Webhook URL: https://hooks.slack.com/services/T00/B00/xxx
```

---

### Ejemplo Completo: Proyecto Vue + Netlify

**Estructura del proyecto:**

```
frontend/
├── public/
│   ├── _redirects
│   └── robots.txt
├── src/
│   ├── components/
│   ├── views/
│   ├── router/
│   ├── stores/
│   └── main.js
├── .env. production
├── .env.staging
├── netlify.toml
├── package.json
└── vite.config.js
```

**package.json:**

```json
{
  "name": "frontend",
  "version": "1.0.0",
  "scripts": {
    "dev": "vite",
    "build":  "vite build",
    "build:staging": "vite build --mode staging",
    "build:production":  "vite build --mode production",
    "preview": "vite preview",
    "lint": "eslint . --ext .vue,.js,. jsx,.cjs,.mjs --fix",
    "type-check": "vue-tsc --noEmit",
    "test:unit": "vitest run"
  },
  "dependencies":  {
    "vue": "^3.4.0",
    "vue-router": "^4.2.0",
    "pinia": "^2.1.0",
    "axios": "^1.6.0"
  },
  "devDependencies": {
    "@vitejs/plugin-vue": "^5.0.0",
    "vite": "^5.0.0",
    "eslint": "^8.55.0",
    "typescript": "^5.3.0",
    "vue-tsc": "^1.8.0",
    "vitest": "^1.0.0"
  }
}
```

**.env.production:**

```env
VITE_API_URL=https://api.example.com
VITE_ANALYTICS_ID=UA-PRODUCTION-ID
VITE_SENTRY_DSN=https://xxx@sentry.io/1
```

**.env.staging:**

```env
VITE_API_URL=https://api-staging.example.com
VITE_ANALYTICS_ID=
VITE_SENTRY_DSN=https://xxx@sentry.io/2
```

**public/_redirects:**

```
# SPA fallback
/*    /index.html   200
```

**netlify.toml:**

```toml
[build]
  command = "npm run build"
  publish = "dist"

[context.production]
  command = "npm run build:production"

[context.deploy-preview]
  command = "npm run build:staging"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200

[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"

[[headers]]
  for = "/assets/*"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"
```

**Despliegue:**

```bash
# Desarrollo local
npm run dev

# Build local
npm run build: staging

# Commit y push
git add . 
git commit -m "feat: add new feature"
git push origin feature/new-feature

# Crear PR → Netlify automáticamente crea deploy preview
# Merge PR → Netlify automáticamente despliega a producción
```

---

# UD 7: Integración y Despliegue Continuo (CI/CD) - Continuación

## 5. Contenerización y Despliegue del Backend en Render

### Introducción:  Por Qué Render para Backends

**Render** es una plataforma moderna de cloud computing que simplifica el despliegue de aplicaciones backend, bases de datos y servicios web. Es la evolución natural de Heroku pero con mejor pricing y características más modernas.

**Comparativa con otras plataformas:**

| Característica    | Heroku         | Render                  | AWS/Azure  | Railway   |
| ----------------- | -------------- | ----------------------- | ---------- | --------- |
| **Configuración** | Buildpacks     | Dockerfile nativo       | Compleja   | Simple    |
| **Free tier**     | Eliminado 2022 | Limitado pero existente | Complejo   | Limitado  |
| **Auto-deploy**   | ✅              | ✅                       | Manual     | ✅         |
| **PostgreSQL**    | ✅ Addon        | ✅ Incluido              | Manual RDS | ✅         |
| **HTTPS**         | ✅ Automático   | ✅ Automático            | Manual     | ✅         |
| **Pricing**       | $7/mes         | $7/mes                  | Variable   | $5/mes    |
| **DX**            | Excelente      | Excelente               | Compleja   | Muy buena |

💡 **Nota del Profesor**: Render es ideal para equipos pequeños y medianos que necesitan la simplicidad de Heroku pero con control total sobre contenedores Docker.  A diferencia de AWS que requiere configurar VPCs, Load Balancers, Auto Scaling Groups, etc., Render abstrae toda esa complejidad.

---

### 5.1. Ciclo de Vida de la Imagen Docker

#### Flujo Completo:  Código → Contenedor → Producción

```
┌─────────────────────────────────────────────────────────────┐
│                    FASE 1: BUILD                            │
├─────────────────────────────────────────────────────────────┤
│  Developer:   git push                                       │
│       ↓                                                     │
│  GitHub Actions:                                            │
│    1. Checkout código                                       │
│    2. Setup Docker Buildx                                   │
│    3. Build imagen multi-stage                              │
│    4. Run tests en contenedor                               │
│    5. Scan vulnerabilidades                                 │
└─────────────────────────────────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────────┐
│                    FASE 2: REGISTRY                         │
├─────────────────────────────────────────────────────────────┤
│  GitHub Actions:                                            │
│    6. Login a Docker Hub                                    │
│    7. Tag imagen (sha, version, latest)                     │
│    8. Push a Docker Hub                                     │
│    9. Verificar push exitoso                                │
└─────────────────────────────────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────────┐
│                    FASE 3: DEPLOY                           │
├─────────────────────────────────────────────────────────────┤
│  GitHub Actions:                                            │
│    10. Trigger Render Deploy Hook                           │
│  Render:                                                     │
│    11. Pull imagen desde Docker Hub                         │
│    12. Stop contenedor anterior                             │
│    13. Start nuevo contenedor                               │
│    14. Health check                                         │
│    15. Route traffic al nuevo contenedor                    │
└─────────────────────────────────────────────────────────────┘
                         ↓
                  🎉 Producción
```

---

#### 🛠️ Paso a Paso: Dockerfile Multi-Stage Optimizado

**Para Java/Spring Boot:**

**Dockerfile:**

```dockerfile
# ============================================
# Stage 1: Build con Gradle
# ============================================
FROM gradle:8.5-jdk21-alpine AS builder

WORKDIR /app

# Copiar archivos de configuración de Gradle
COPY gradle/ gradle/
COPY gradlew . 
COPY build.gradle. kts .
COPY settings. gradle.kts .

# Descargar dependencias (cacheado separado)
RUN ./gradlew dependencies --no-daemon

# Copiar código fuente
COPY src/ src/

# Compilar aplicación
RUN ./gradlew bootJar --no-daemon -x test

# ============================================
# Stage 2: Runtime ligero
# ============================================
FROM eclipse-temurin:21-jre-alpine

# Metadata
LABEL maintainer="tu-email@example.com"
LABEL version="1.0.0"
LABEL description="User Management API"

# Variables de entorno por defecto
ENV JAVA_OPTS="-XX:+UseContainerSupport -XX:MaxRAMPercentage=75.0 -XX:InitialRAMPercentage=50.0"
ENV SERVER_PORT=8080
ENV SPRING_PROFILES_ACTIVE=production

# Instalar utilidades
RUN apk add --no-cache \
    curl \
    bash \
    tzdata && \
    cp /usr/share/zoneinfo/Europe/Madrid /etc/localtime && \
    echo "Europe/Madrid" > /etc/timezone && \
    apk del tzdata

# Crear usuario no-root
RUN addgroup -g 1000 appgroup && \
    adduser -D -u 1000 -G appgroup appuser

# Directorio de trabajo
WORKDIR /app

# Copiar JAR desde stage de build
COPY --from=builder /app/build/libs/*.jar app.jar

# Cambiar ownership
RUN chown -R appuser:appgroup /app

# Cambiar a usuario no-root
USER appuser

# Puerto expuesto
EXPOSE 8080

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=40s --retries=3 \
    CMD curl -f http://localhost:8080/actuator/health || exit 1

# Comando de inicio
ENTRYPOINT ["sh", "-c", "java $JAVA_OPTS -jar app.jar"]
```

**Características clave:**

✅ **Multi-stage**:  Imagen final solo contiene JRE + JAR (no Gradle ni código fuente)
✅ **Alpine**:  Imagen base ligera (~50MB vs ~200MB con Ubuntu)
✅ **Cache de dependencias**: Gradle dependencies se cachean en capa separada
✅ **Usuario no-root**: Seguridad (no ejecuta como root)
✅ **Health check**: Kubernetes/Render pueden verificar salud del contenedor
✅ **Variables configurables**:  JAVA_OPTS, puertos, perfiles

**Tamaño resultante:**

```
REPOSITORY          TAG         SIZE
myapp-java          full        450 MB  (sin multi-stage)
myapp-java          optimized   180 MB  (con multi-stage + Alpine)
```

---

**Para . NET 10:**

**Dockerfile:**

```dockerfile
# ============================================
# Stage 1: Build
# ============================================
FROM mcr.microsoft.com/dotnet/sdk:10.0-alpine AS build

WORKDIR /src

# Copiar archivos de proyecto
COPY ["src/MyApp/MyApp.csproj", "src/MyApp/"]
COPY ["src/MyApp. Core/MyApp.Core.csproj", "src/MyApp. Core/"]
COPY ["src/MyApp.Infrastructure/MyApp.Infrastructure.csproj", "src/MyApp.Infrastructure/"]

# Restaurar dependencias (cacheado)
RUN dotnet restore "src/MyApp/MyApp. csproj" --runtime linux-musl-x64

# Copiar todo el código
COPY .  .

# Build y publish
WORKDIR "/src/src/MyApp"
RUN dotnet publish "MyApp.csproj" \
    -c Release \
    -o /app/publish \
    --no-restore \
    --runtime linux-musl-x64 \
    --self-contained false

# ============================================
# Stage 2: Runtime
# ============================================
FROM mcr.microsoft. com/dotnet/aspnet: 10.0-alpine AS final

# Metadata
LABEL maintainer="tu-email@example.com"
LABEL version="1.0.0"

# Variables de entorno
ENV ASPNETCORE_URLS=http://+:8080
ENV ASPNETCORE_ENVIRONMENT=Production
ENV DOTNET_SYSTEM_GLOBALIZATION_INVARIANT=false

# Instalar dependencias necesarias
RUN apk add --no-cache \
    curl \
    icu-libs \
    tzdata && \
    cp /usr/share/zoneinfo/Europe/Madrid /etc/localtime && \
    echo "Europe/Madrid" > /etc/timezone && \
    apk del tzdata

# Crear usuario no-root
RUN addgroup -g 1000 appgroup && \
    adduser -D -u 1000 -G appgroup appuser

WORKDIR /app

# Copiar artefactos publicados
COPY --from=build /app/publish .

# Cambiar ownership
RUN chown -R appuser:appgroup /app

# Cambiar a usuario no-root
USER appuser

EXPOSE 8080

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=40s --retries=3 \
    CMD curl -f http://localhost:8080/health || exit 1

ENTRYPOINT ["dotnet", "MyApp.dll"]
```

**Tamaños comparativos:**

```
REPOSITORY          TAG         SIZE
myapp-dotnet        full        320 MB  (Ubuntu base)
myapp-dotnet        alpine      125 MB  (Alpine base)
myapp-dotnet        aot         45 MB   (Native AOT - C# 12+)
```

---

#### Optimizaciones Avanzadas del Dockerfile

**1. . dockerignore (Reducir contexto de build):**

```
# . dockerignore
**/.git
**/.github
**/node_modules
**/dist
**/build
**/target
**/.gradle
**/.idea
**/.vscode
**/coverage
**/test-results
**/*. md
**/Dockerfile
**/docker-compose. yml
**/. env
**/.env.local
**/secrets
**/temp
**/logs
```

**2. Build Arguments para configuración dinámica:**

```dockerfile
# Variables de build
ARG APP_VERSION=1.0.0
ARG BUILD_DATE
ARG VCS_REF

# Metadata dinámica
LABEL org.opencontainers.image.version="$APP_VERSION"
LABEL org.opencontainers.image.created="$BUILD_DATE"
LABEL org.opencontainers.image.revision="$VCS_REF"

# Usar en build
ENV APP_VERSION=$APP_VERSION
```

**Construir con argumentos:**

```bash
docker build \
  --build-arg APP_VERSION=1.2.3 \
  --build-arg BUILD_DATE=$(date -u +"%Y-%m-%dT%H:%M:%SZ") \
  --build-arg VCS_REF=$(git rev-parse --short HEAD) \
  -t myapp: 1.2.3 .
```

**3. Cache de BuildKit:**

```dockerfile
# Habilitar BuildKit cache mount (más rápido)
# syntax=docker/dockerfile:1.4

FROM gradle:8.5-jdk21-alpine AS builder

WORKDIR /app

COPY build.gradle.kts . 
COPY settings.gradle.kts . 

# Cache mount para Gradle
RUN --mount=type=cache,target=/root/.gradle \
    ./gradlew dependencies --no-daemon
```

**Build con BuildKit:**

```bash
DOCKER_BUILDKIT=1 docker build -t myapp:latest .
```

---

### 5.2. Orquestación en Render

#### 🛠️ Paso a Paso: Configuración de Servicio en Render

**1. Crear cuenta en Render:**

- Ir a https://render.com
- Sign up with GitHub
- Autorizar acceso

**2. Crear PostgreSQL Database:**

Dashboard → New → PostgreSQL

```
Name: myapp-db
Database:  myapp_production
User: myapp_user
Region: Frankfurt (EU Central)
PostgreSQL Version: 16
Plan: Free (shared CPU, 256MB RAM, 1GB storage)
```

Render proporciona:
```
Internal Database URL: postgres://user:pass@dpg-xxx-a: 5432/myapp_production
External Database URL: postgres://user:pass@dpg-xxx-a. frankfurt-postgres.render.com:5432/myapp_production
```

**3. Configurar Web Service:**

Dashboard → New → Web Service

**Opción A: Deploy desde GitHub (sin Docker Hub):**

```
Name: myapp-backend
Region: Frankfurt
Branch: main
Root Directory: backend/
Environment: Docker
Docker Command: (Render lo detecta automáticamente)
Plan:  Starter ($7/month)
```

**Opción B: Deploy desde Docker Hub (recomendado):**

```
Name: myapp-backend
Region: Frankfurt
Image URL: docker.io/tu-usuario/myapp: latest
Plan: Starter ($7/month)
```

**4. Configurar Variables de Entorno:**

En Render Dashboard → myapp-backend → Environment: 

```
Key: SPRING_DATASOURCE_URL
Value: [copiar Internal Database URL de la BD creada]

Key: SPRING_DATASOURCE_USERNAME
Value: myapp_user

Key: SPRING_DATASOURCE_PASSWORD
Value: [Auto-generado por Render]

Key: SPRING_PROFILES_ACTIVE
Value: production

Key: JWT_SECRET
Value: [Generar con:  openssl rand -base64 32]

Key: SERVER_PORT
Value: 8080

Key: JAVA_OPTS
Value: -Xmx512m -Xms256m
```

**Para . NET:**

```
Key: ConnectionStrings__DefaultConnection
Value:  [Internal Database URL]

Key:  ASPNETCORE_ENVIRONMENT
Value: Production

Key: JwtSettings__Secret
Value: [Secret generado]
```

**5. Configurar Health Check:**

```
Health Check Path: /actuator/health
```

Render llamará a esta ruta cada 30 segundos.  Si falla 3 veces consecutivas, reinicia el contenedor.

**6. Configurar Auto-Deploy:**

```
☑ Auto-Deploy:  Yes
Branch: main
```

Ahora cada push a `main` despliega automáticamente. 

---

#### Deploy Hooks:  Automatización desde CI/CD

**Obtener Deploy Hook URL:**

Render Dashboard → myapp-backend → Settings → Deploy Hook

Copiar URL:  `https://api.render.com/deploy/srv-xxx? key=yyy`

**Guardar en GitHub Secrets:**

GitHub repo → Settings → Secrets and variables → Actions → New repository secret

```
Name: RENDER_DEPLOY_HOOK
Value: https://api.render.com/deploy/srv-xxx? key=yyy
```

**Integrar en GitHub Actions Workflow:**

**. github/workflows/deploy-backend.yml:**

```yaml
name: Deploy Backend to Render

on:
  push:
    branches: [ main ]
    paths: 
      - 'backend/**'
      - '. github/workflows/deploy-backend. yml'
  workflow_dispatch:

env:
  DOCKER_IMAGE: tu-usuario/myapp
  JAVA_VERSION: '21'

jobs:
  # ==========================================
  # Job 1: Build y Push a Docker Hub
  # ==========================================
  build-and-push:
    name: Build Docker Image
    runs-on: ubuntu-latest
    timeout-minutes: 20
    
    outputs:
      image-tag: ${{ steps.meta.outputs.tags }}
      image-digest: ${{ steps.build. outputs.digest }}
    
    steps:
      - name: Checkout code
        uses:  actions/checkout@v4
      
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3
      
      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with: 
          username: ${{ secrets. DOCKER_USERNAME }}
          password:  ${{ secrets.DOCKER_PASSWORD }}
      
      - name:  Docker metadata
        id: meta
        uses: docker/metadata-action@v5
        with:
          images: ${{ env.DOCKER_IMAGE }}
          tags: |
            type=ref,event=branch
            type=sha,prefix={{branch}}-
            type=raw,value=latest,enable={{is_default_branch}}
          labels: |
            org.opencontainers.image. title=MyApp Backend
            org.opencontainers.image.description=User Management API
            org.opencontainers.image.vendor=MyCompany
      
      - name: Build and push
        id: build
        uses:  docker/build-push-action@v5
        with:
          context: ./backend
          file: ./backend/Dockerfile
          push: true
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
          build-args: |
            APP_VERSION=${{ github.ref_name }}
            BUILD_DATE=${{ github.event.head_commit.timestamp }}
            VCS_REF=${{ github.sha }}
      
      - name: Image digest
        run: echo "Image digest: ${{ steps.build.outputs.digest }}"
  
  # ==========================================
  # Job 2: Scan de Seguridad
  # ==========================================
  security-scan:
    name: Security Scan
    runs-on:  ubuntu-latest
    needs: build-and-push
    
    steps:
      - name: Run Trivy vulnerability scanner
        uses:  aquasecurity/trivy-action@master
        with:
          image-ref: ${{ needs. build-and-push.outputs. image-tag }}
          format: 'sarif'
          output:  'trivy-results.sarif'
          severity: 'CRITICAL,HIGH'
      
      - name: Upload Trivy results to GitHub Security
        uses: github/codeql-action/upload-sarif@v2
        if: always()
        with:
          sarif_file: 'trivy-results.sarif'
      
      - name: Fail on critical vulnerabilities
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: ${{ needs.build-and-push.outputs.image-tag }}
          exit-code: '1'
          severity: 'CRITICAL'
  
  # ==========================================
  # Job 3: Deploy a Render
  # ==========================================
  deploy-render:
    name:  Deploy to Render
    runs-on: ubuntu-latest
    needs: [build-and-push, security-scan]
    environment: 
      name: production
      url: https://myapp-backend.onrender.com
    
    steps:
      - name:  Trigger Render deploy
        run: |
          response=$(curl -X POST "${{ secrets.RENDER_DEPLOY_HOOK }}" \
            -H "Content-Type: application/json" \
            -w "\n%{http_code}" -s)
          
          http_code=$(echo "$response" | tail -n 1)
          body=$(echo "$response" | head -n -1)
          
          echo "HTTP Status: $http_code"
          echo "Response: $body"
          
          if [ "$http_code" -ne 200 ] && [ "$http_code" -ne 201 ]; then
            echo "❌ Deploy hook failed"
            exit 1
          fi
          
          echo "✅ Deploy triggered successfully"
      
      - name: Wait for deployment
        run: |
          echo "Waiting 90 seconds for Render to pull and deploy..."
          sleep 90
      
      - name: Health check
        run: |
          max_attempts=10
          attempt=0
          
          while [ $attempt -lt $max_attempts ]; do
            echo "Health check attempt $((attempt + 1))/$max_attempts"
            
            response=$(curl -s -o /dev/null -w "%{http_code}" \
              https://myapp-backend.onrender.com/actuator/health || echo "000")
            
            if [ "$response" = "200" ]; then
              echo "✅ Service is healthy!"
              exit 0
            fi
            
            echo "Service not ready yet (HTTP $response), waiting..."
            sleep 15
            attempt=$((attempt + 1))
          done
          
          echo "❌ Service failed health check after $max_attempts attempts"
          exit 1
      
      - name:  Smoke tests
        run: |
          # Test endpoint público
          curl -f https://myapp-backend.onrender.com/api/health || exit 1
          
          # Test endpoint de info
          curl -f https://myapp-backend.onrender.com/actuator/info || exit 1
          
          echo "✅ Smoke tests passed"
  
  # ==========================================
  # Job 4: Notificaciones
  # ==========================================
  notify:
    name:  Notify Team
    runs-on: ubuntu-latest
    needs: [deploy-render]
    if: always()
    
    steps:
      - name:  Notify Slack
        uses: slackapi/slack-github-action@v1
        with:
          payload: |
            {
              "text": "Backend Deployment ${{ needs.deploy-render.result }}",
              "blocks": [
                {
                  "type": "header",
                  "text": {
                    "type": "plain_text",
                    "text": "🚀 Backend Deployment"
                  }
                },
                {
                  "type": "section",
                  "fields": [
                    {
                      "type": "mrkdwn",
                      "text": "*Status:*\n${{ needs.deploy-render.result }}"
                    },
                    {
                      "type":  "mrkdwn",
                      "text": "*Environment:*\nProduction"
                    },
                    {
                      "type":  "mrkdwn",
                      "text": "*Commit:*\n${{ github. sha }}"
                    },
                    {
                      "type": "mrkdwn",
                      "text": "*Author:*\n${{ github.actor }}"
                    }
                  ]
                },
                {
                  "type": "section",
                  "text": {
                    "type":  "mrkdwn",
                    "text": "<https://myapp-backend.onrender.com|View Service> | <${{ github.event.head_commit.url }}|View Commit>"
                  }
                }
              ]
            }
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK }}
          SLACK_WEBHOOK_TYPE:  INCOMING_WEBHOOK
```

---

#### Estrategias de Tagging

**Convención de tags recomendada:**

```yaml
tags:  |
  type=ref,event=branch                    # main, develop, feature/xyz
  type=sha,prefix={{branch}}-              # main-abc1234
  type=semver,pattern={{version}}          # 1.2.3 (si es tag Git)
  type=semver,pattern={{major}}.{{minor}}  # 1.2
  type=raw,value=latest,enable={{is_default_branch}}  # latest solo en main
```

**Resultado:**

```
Push a main con commit abc1234:
  - tu-usuario/myapp:main
  - tu-usuario/myapp:main-abc1234
  - tu-usuario/myapp:latest

Push a develop con commit def5678:
  - tu-usuario/myapp:develop
  - tu-usuario/myapp: develop-def5678

Tag Git v1.2.3:
  - tu-usuario/myapp:1.2.3
  - tu-usuario/myapp:1.2
  - tu-usuario/myapp:latest
```

**Ventajas:**
- `latest`: Siempre apunta a la última versión de main
- `main-abc1234`: Permite rollback exacto a un commit
- `1.2.3`: Versionado semántico para releases

---

### 5.3. El Concepto de Cold Start

#### ¿Qué es un Cold Start?

En el **plan gratuito de Render**, los servicios inactivos se ponen en "sleep" después de **15 minutos sin recibir tráfico**. La próxima petición debe: 

1. "Despertar" el contenedor
2. Iniciar la aplicación
3. Conectar a la base de datos
4. Procesar la petición

**Tiempos típicos:**

| Framework       | Cold Start | Warm Request |
| --------------- | ---------- | ------------ |
| Spring Boot     | 30-60s     | 100-300ms    |
| . NET Core      | 20-40s     | 50-200ms     |
| Node.js/Express | 5-15s      | 50-150ms     |
| Go/Fiber        | 3-8s       | 10-50ms      |

💡 **Nota del Profesor**:  Cold starts son **aceptables para desarrollo y staging**, pero **inaceptables para producción**. En producción usa el plan de pago ($7/mes) que mantiene tu servicio siempre activo.

---

#### Estrategias para Mitigar Cold Starts

**1. Upgrade al plan de pago (recomendado para producción):**

```
Starter Plan:  $7/mes
  - Always on (sin cold starts)
  - 512 MB RAM
  - 0.5 CPU
  - Deploy automático
```

**2. Mantener el servicio "caliente" con pings (plan gratuito):**

**UptimeRobot (gratis):**

- Crear cuenta en https://uptimerobot.com
- Add New Monitor: 
  ```
  Monitor Type: HTTP(s)
  Friendly Name: MyApp Backend Health
  URL: https://myapp-backend.onrender.com/actuator/health
  Monitoring Interval: 5 minutes
  ```

Esto hace ping cada 5 minutos, manteniendo el servicio activo.

**GitHub Actions cron (alternativa):**

```yaml
name: Keep Warm

on:
  schedule:
    # Cada 10 minutos
    - cron: '*/10 * * * *'

jobs:
  ping:
    runs-on: ubuntu-latest
    steps:
      - name: Ping service
        run: curl -f https://myapp-backend.onrender.com/actuator/health
```

**3. Optimizar tiempo de startup:**

**Spring Boot:**

```properties
# application.properties
# Lazy initialization (más rápido startup, pero primer request más lento)
spring.main.lazy-initialization=true

# Reducir logs de startup
logging.level.root=WARN
```

**Java JVM:**

```dockerfile
ENV JAVA_OPTS="-XX:+TieredCompilation -XX:TieredStopAtLevel=1"
```

**.NET:**

```xml
<!-- . csproj -->
<PropertyGroup>
  <ServerGarbageCollection>false</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
</PropertyGroup>
```

**4. Health check endpoint optimizado:**

```java
@RestController
public class HealthController {
    
    @GetMapping("/health")
    public ResponseEntity<Map<String, String>> health() {
        // Ultra ligero, sin queries a BD
        return ResponseEntity.ok(Map.of(
            "status", "UP",
            "timestamp", Instant.now().toString()
        ));
    }
}
```

**5. Precalentar en el workflow:**

```yaml
- name: Wait and warm up
  run: |
    echo "Waiting for deploy to complete..."
    sleep 60
    
    echo "Warming up service..."
    for i in {1..3}; do
      curl -f https://myapp-backend.onrender.com/health
      sleep 5
    done
```

---

#### Configuración de render.yaml (Infrastructure as Code)

Render permite definir toda la infraestructura en código: 

**render.yaml:**

```yaml
services:
  # ==========================================
  # Web Service (Backend API)
  # ==========================================
  - type: web
    name: myapp-backend
    runtime: docker
    dockerfilePath: ./backend/Dockerfile
    dockerContext: ./backend
    region: frankfurt
    plan: starter
    branch: main
    
    # Health check
    healthCheckPath: /actuator/health
    
    # Variables de entorno
    envVars:
      - key:  SPRING_PROFILES_ACTIVE
        value: production
      
      - key: SERVER_PORT
        value: 8080
      
      - key: SPRING_DATASOURCE_URL
        fromDatabase:
          name: myapp-db
          property:  connectionString
      
      - key:  JWT_SECRET
        generateValue: true
        sync: false
    
    # Auto-deploy
    autoDeploy: true
    
    # Notificaciones
    buildCommand: echo "Building..."
    
  # ==========================================
  # PostgreSQL Database
  # ==========================================
databases:
  - name: myapp-db
    databaseName: myapp_production
    user: myapp_user
    region: frankfurt
    plan: free
    postgresMajorVersion: 16
    
    # Backups automáticos (solo planes de pago)
    # ipAllowList: []
```

**Deploy con render.yaml:**

```bash
# Instalar Render CLI
npm install -g @render-cli/cli

# Login
render login

# Deploy desde archivo
render blueprint launch
```

---

#### Monitorización en Render

**Logs en tiempo real:**

```bash
# Desde dashboard
Render Dashboard → myapp-backend → Logs → (stream en vivo)

# Desde CLI
render logs myapp-backend --tail
```

**Métricas:**

Render Dashboard → myapp-backend → Metrics: 

```
- CPU Usage
- Memory Usage
- Request Count
- Response Time (p50, p95, p99)
- Error Rate
- Bandwidth
```

**Alertas (solo planes de pago):**

```
Configurar en:  Settings → Notifications
  - Deploy success/failure
  - Service down
  - High CPU/Memory
  - High error rate
```

---

#### Ejemplo de Configuración Completa

**Repositorio estructura:**

```
myapp/
├── backend/
│   ├── Dockerfile
│   ├── src/
│   ├── build.gradle. kts
│   └── ... 
├── frontend/
│   ├── src/
│   ├── package.json
│   ├── netlify.toml
│   └── ...
├── . github/
│   └── workflows/
│       ├── ci-backend.yml
│       ├── deploy-backend.yml
│       └── ci-frontend.yml
├── render.yaml
└── README.md
```

**Variables en Render:**

```
SPRING_DATASOURCE_URL:  [Auto desde BD]
SPRING_DATASOURCE_USERNAME: myapp_user
SPRING_DATASOURCE_PASSWORD: [Auto generado]
SPRING_PROFILES_ACTIVE: production
JWT_SECRET: [Generado seguro]
CORS_ALLOWED_ORIGINS: https://myapp.netlify.app,https://app.example.com
LOG_LEVEL: INFO
```

**Frontend (Netlify) apunta a Backend (Render):**

```javascript
// frontend/src/config. js
export const API_URL = import.meta.env.VITE_API_URL || 'https://myapp-backend.onrender.com'
```

**Netlify environment:**

```
VITE_API_URL: https://myapp-backend.onrender. com
```

---

### Resumen del Punto 5

**Hemos aprendido:**

✅ **Dockerfile multi-stage**:  Optimización de tamaño y seguridad
✅ **Docker Hub**: Registry para almacenar imágenes
✅ **Render**:  Plataforma simplificada para deploy de backends
✅ **Deploy Hooks**: Automatización desde GitHub Actions
✅ **Tagging estratégico**: Versionado y rollback
✅ **Cold starts**:  Qué son y cómo mitigarlos
✅ **render.yaml**: Infrastructure as Code
✅ **Monitorización**: Logs, métricas y alertas

**Flujo completo CI/CD:**

```
1. Developer:  git push
2. GitHub Actions: 
   - Build y tests
   - Build Docker image
   - Push a Docker Hub
   - Scan de seguridad
   - Trigger Render deploy hook
3. Render:
   - Pull imagen
   - Deploy nuevo contenedor
   - Health check
   - Route traffic
4.  Notificación a equipo
```

**Costes mensuales típicos:**

```
Netlify (Frontend): $0 (plan gratis)
Render Backend: $7/mes (Starter)
Render PostgreSQL: $7/mes (Starter con backups)
Docker Hub: $0 (plan gratis, 1 repo privado)
GitHub Actions: $0 (2000 minutos gratis)
--------------------------------
Total: ~$14/mes para stack completo
```

# UD 7: Integración y Despliegue Continuo (CI/CD) - Continuación

## 6. Validación Final E2E y Documentación

### Introducción:  La Última Línea de Defensa

Después de que el código pasa tests unitarios, tests de integración, análisis de calidad y se despliega exitosamente, todavía queda una pregunta crítica: 

> **¿Funciona realmente la aplicación completa desde la perspectiva del usuario?**

Los **tests End-to-End (E2E)** son la verificación final que simula **comportamiento real de usuarios** interactuando con la aplicación desplegada. Son la última barrera antes de considerar un despliegue completamente exitoso.

**Pipeline completo con validación E2E:**

```
┌─────────────────────────────────────────────────────────────┐
│                    CI/CD PIPELINE COMPLETO                  │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1. Build & Unit Tests          ← Valida lógica aislada    │
│  2. Integration Tests            ← Valida componentes juntos│
│  3. Code Quality & Security      ← Valida estándares       │
│  4. Build Docker Image           ← Empaqueta aplicación    │
│  5. Deploy to Staging            ← Despliegue temporal     │
│  6. E2E Tests en Staging    ← VALIDACIÓN FINAL ✅          │
│  7. Deploy to Production         ← Solo si E2E pasa        │
│  8. Smoke Tests en Producción    ← Verificación rápida    │
│  9. Generate Documentation       ← Para equipo/usuarios    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

💡 **Nota del Profesor**: Los tests E2E son **lentos y caros** de mantener, pero **invaluables**. No testees cada botón y formulario.  Enfócate en **user journeys críticos**:  registro, login, flujo de compra, operaciones principales.  Un usuario real no hace click en cada botón; sigue flujos específicos.  Tus E2E tests deben hacer lo mismo. 

---

### 6.1. Cypress en el Pipeline

#### Arquitectura de Tests E2E en CI/CD

```
┌─────────────────────────────────────────────────────────────┐
│                    GitHub Actions Runner                    │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐  │
│  │         Cypress Container (Headless)                 │  │
│  │                                                       │  │
│  │  Electron Browser                                     │  │
│  │    ↓                                                  │  │
│  │  Tests E2E (JavaScript)                              │  │
│  │    ↓                                                  │  │
│  │  Hace requests a → https://staging.myapp.com         │  │
│  │                                                       │  │
│  │  Captura:                                              │  │
│  │  - Screenshots de fallos                             │  │
│  │  - Videos de ejecución                               │  │
│  │  - Logs de consola                                   │  │
│  │  - Network requests                                  │  │
│  └─────────────────────────────────────────────────────┘  │
│                          ↓                                  │
│              Subir artifacts a GitHub                       │
│                                                             │
└─────────────────────────────────────────────────────────────┘
                            ↓
                 https://staging.myapp.com
                  (Frontend en Netlify +
                   Backend en Render)
```

---

#### 🛠️ Paso a Paso: Configuración de Cypress para CI

**1. Estructura del Proyecto:**

```
e2e-tests/
├── cypress/
│   ├── e2e/
│   │   ├── auth/
│   │   │   ├── login.cy. js
│   │   │   └── registration.cy.js
│   │   ├── user/
│   │   │   ├── profile.cy.js
│   │   │   └── dashboard.cy.js
│   │   └── critical-flows. cy.js
│   ├── fixtures/
│   │   ├── users.json
│   │   └── test-data.json
│   ├── support/
│   │   ├── commands.js
│   │   ├── e2e. js
│   │   └── index. d.ts
│   └── videos/           (generado)
│   └── screenshots/      (generado)
├── cypress.config.js
├── package.json
├── Dockerfile
└── README.md
```

**2. cypress.config.js (Configuración para CI):**

```javascript
const { defineConfig } = require('cypress')

module.exports = defineConfig({
  e2e: {
    // URL base (override con env var)
    baseUrl: process.env.CYPRESS_BASE_URL || 'http://localhost:3000',
    
    // API URL
    env: {
      apiUrl: process.env.CYPRESS_API_URL || 'http://localhost:8080/api',
      adminEmail: 'admin@example.com',
      adminPassword: 'admin123',
    },
    
    // Configuración de viewport
    viewportWidth: 1280,
    viewportHeight: 720,
    
    // Timeouts
    defaultCommandTimeout:  10000,
    requestTimeout: 10000,
    responseTimeout: 30000,
    pageLoadTimeout: 60000,
    
    // Video y screenshots
    video: true,
    videoCompression: 32,
    videosFolder: 'cypress/videos',
    screenshotOnRunFailure: true,
    screenshotsFolder: 'cypress/screenshots',
    
    // Retry en CI
    retries: {
      runMode: 2,      // Reintentar 2 veces en CI
      openMode: 0      // No reintentar en desarrollo local
    },
    
    // Configuración de Chrome para CI
    chromeWebSecurity: false,
    
    // Reportes
    reporter: 'cypress-multi-reporters',
    reporterOptions: {
      reporterEnabled: 'mochawesome, mocha-junit-reporter',
      mochawesomeReporterOptions: {
        reportDir: 'cypress/results/mochawesome',
        overwrite: false,
        html: true,
        json: true,
        timestamp: 'mmddyyyy_HHMMss'
      },
      mochaJunitReporterReporterOptions: {
        mochaFile: 'cypress/results/junit/results-[hash].xml'
      }
    },
    
    setupNodeEvents(on, config) {
      // Eventos personalizados
      on('task', {
        log(message) {
          console. log(message)
          return null
        },
        table(message) {
          console. table(message)
          return null
        }
      })
      
      // Configuración dinámica desde variables de entorno
      config.baseUrl = process.env.CYPRESS_BASE_URL || config.baseUrl
      config.env. apiUrl = process.env. CYPRESS_API_URL || config. env.apiUrl
      
      return config
    },
  },
})
```

**3. package.json:**

```json
{
  "name": "e2e-tests",
  "version": "1.0.0",
  "scripts": {
    "cy:open": "cypress open",
    "cy:run": "cypress run",
    "cy:run:chrome": "cypress run --browser chrome",
    "cy:run:firefox": "cypress run --browser firefox",
    "cy:run:edge": "cypress run --browser edge",
    "cy:run:headed": "cypress run --headed",
    "cy:run:spec": "cypress run --spec",
    "report: merge": "mochawesome-merge cypress/results/mochawesome/*. json > cypress/results/report.json",
    "report:generate": "marge cypress/results/report.json --reportDir cypress/results --reportFilename index.html",
    "report:open": "open cypress/results/index.html",
    "clean":  "rm -rf cypress/videos cypress/screenshots cypress/results"
  },
  "devDependencies": {
    "cypress": "^13.6.3",
    "cypress-multi-reporters": "^1.6.4",
    "mocha":  "^10.2.0",
    "mocha-junit-reporter": "^2.2.1",
    "mochawesome":  "^7.1.3",
    "mochawesome-merge": "^4.3.0",
    "mochawesome-report-generator": "^6.2.0"
  }
}
```

**4. Comandos personalizados (cypress/support/commands.js):**

```javascript
// ================================================
// Comando:  Login via API (más rápido)
// ================================================
Cypress.Commands.add('loginAPI', (email, password) => {
  cy.request({
    method: 'POST',
    url: `${Cypress.env('apiUrl')}/auth/login`,
    body: { email, password }
  }).then((response) => {
    expect(response.status).to.eq(200)
    expect(response.body).to.have.property('token')
    
    // Guardar token en localStorage
    window.localStorage.setItem('authToken', response.body.token)
    
    // O en cookie si la app usa cookies
    cy.setCookie('authToken', response.body.token)
  })
})

// ================================================
// Comando: Login via UI (para testear el formulario)
// ================================================
Cypress.Commands.add('loginUI', (email, password) => {
  cy.visit('/login')
  cy.get('[data-cy="email-input"]').type(email)
  cy.get('[data-cy="password-input"]').type(password, { log: false })
  cy.get('[data-cy="login-button"]').click()
  cy.url().should('not.include', '/login')
})

// ================================================
// Comando: Crear usuario de prueba via API
// ================================================
Cypress. Commands.add('createTestUser', (userData) => {
  const defaultData = {
    email: `test-${Date.now()}@example.com`,
    password: 'Test123!',
    name: 'Test User'
  }
  
  const user = { ...defaultData, ...userData }
  
  return cy.request({
    method: 'POST',
    url:  `${Cypress.env('apiUrl')}/users/register`,
    body: user,
    failOnStatusCode: false
  }).then((response) => {
    if (response.status === 201 || response.status === 200) {
      return cy.wrap(user)
    } else {
      throw new Error(`Failed to create user: ${response.body.message}`)
    }
  })
})

// ================================================
// Comando: Limpiar base de datos (solo en test env)
// ================================================
Cypress.Commands.add('resetDatabase', () => {
  cy.request({
    method: 'POST',
    url: `${Cypress.env('apiUrl')}/test/reset`,
    headers: {
      'X-Test-Key':  Cypress.env('testApiKey')
    }
  })
})

// ================================================
// Comando:  Esperar a que un elemento desaparezca
// ================================================
Cypress.Commands.add('waitUntilHidden', (selector, timeout = 10000) => {
  cy.get(selector, { timeout }).should('not.exist')
})

// ================================================
// Comando: Verificar accesibilidad básica
// ================================================
Cypress.Commands.add('checkA11y', () => {
  cy.injectAxe()
  cy.checkA11y(null, {
    rules: {
      'color-contrast': { enabled: false } // Opcional: deshabilitar reglas específicas
    }
  })
})

// ================================================
// Comando: Interceptar y mockear API
// ================================================
Cypress. Commands.add('mockAPI', (method, url, response, statusCode = 200) => {
  cy.intercept(method, url, {
    statusCode,
    body: response
  }).as('mockedRequest')
})
```

**5. Tests E2E críticos:**

**cypress/e2e/critical-flows.cy.js:**

```javascript
describe('Critical User Flows', () => {
  // Datos de test
  const testUser = {
    email: `test-${Date.now()}@example.com`,
    password: 'SecureTest123!',
    name: 'Test User'
  }

  before(() => {
    // Limpiar datos previos (solo en staging)
    if (Cypress.env('environment') === 'staging') {
      cy.resetDatabase()
    }
  })

  describe('User Registration Flow', () => {
    it('should complete full registration journey', () => {
      // 1. Visitar home page
      cy.visit('/')
      cy.get('[data-cy="hero-section"]').should('be.visible')
      
      // 2. Navegar a registro
      cy.get('[data-cy="register-link"]').click()
      cy.url().should('include', '/register')
      
      // 3. Llenar formulario
      cy.get('[data-cy="name-input"]').type(testUser.name)
      cy.get('[data-cy="email-input"]').type(testUser.email)
      cy.get('[data-cy="password-input"]').type(testUser.password)
      cy.get('[data-cy="confirm-password-input"]').type(testUser.password)
      cy.get('[data-cy="terms-checkbox"]').check()
      
      // 4. Interceptar request de registro
      cy.intercept('POST', '**/api/users/register').as('registerRequest')
      
      // 5. Submit
      cy.get('[data-cy="register-button"]').click()
      
      // 6. Verificar llamada exitosa
      cy.wait('@registerRequest').then((interception) => {
        expect(interception.response.statusCode).to.be.oneOf([200, 201])
        expect(interception.response. body).to.have.property('id')
      })
      
      // 7. Verificar redirección
      cy.url().should('include', '/dashboard')
      
      // 8. Verificar mensaje de bienvenida
      cy.get('[data-cy="welcome-message"]')
        .should('be.visible')
        .and('contain', testUser.name)
      
      // 9. Verificar elementos del dashboard
      cy.get('[data-cy="user-menu"]').should('be.visible')
      cy.get('[data-cy="dashboard-content"]').should('be.visible')
      
      // 10. Verificar persistencia (reload)
      cy.reload()
      cy.url().should('include', '/dashboard')
      cy.get('[data-cy="user-menu"]').should('be.visible')
    })

    it('should show validation errors for invalid data', () => {
      cy.visit('/register')
      
      // Intentar submit sin datos
      cy.get('[data-cy="register-button"]').click()
      
      // Verificar errores
      cy.get('[data-cy="name-error"]').should('be.visible')
      cy.get('[data-cy="email-error"]').should('be.visible')
      cy.get('[data-cy="password-error"]').should('be.visible')
      
      // Email inválido
      cy.get('[data-cy="email-input"]').type('not-an-email')
      cy.get('[data-cy="register-button"]').click()
      cy.get('[data-cy="email-error"]').should('contain', 'valid email')
      
      // Password débil
      cy.get('[data-cy="email-input"]').clear().type('valid@example.com')
      cy.get('[data-cy="password-input"]').type('123')
      cy.get('[data-cy="register-button"]').click()
      cy.get('[data-cy="password-error"]').should('contain', 'at least 8')
    })
  })

  describe('Login and Dashboard Flow', () => {
    before(() => {
      // Crear usuario de prueba via API
      cy.createTestUser(testUser)
    })

    it('should login and access protected features', () => {
      // 1. Login via UI
      cy.visit('/login')
      cy.get('[data-cy="email-input"]').type(testUser.email)
      cy.get('[data-cy="password-input"]').type(testUser.password)
      
      cy.intercept('POST', '**/api/auth/login').as('loginRequest')
      cy.get('[data-cy="login-button"]').click()
      
      // 2. Verificar login exitoso
      cy.wait('@loginRequest').its('response.statusCode').should('eq', 200)
      cy.url().should('include', '/dashboard')
      
      // 3. Navegar a perfil
      cy.get('[data-cy="user-menu"]').click()
      cy.get('[data-cy="profile-link"]').click()
      
      // 4. Verificar datos del usuario
      cy.get('[data-cy="profile-email"]').should('contain', testUser.email)
      cy.get('[data-cy="profile-name"]').should('contain', testUser.name)
      
      // 5. Editar perfil
      cy.get('[data-cy="edit-profile-button"]').click()
      const newName = `${testUser.name} Updated`
      cy.get('[data-cy="name-input"]').clear().type(newName)
      
      cy.intercept('PUT', '**/api/users/*').as('updateRequest')
      cy.get('[data-cy="save-button"]').click()
      
      // 6. Verificar actualización
      cy.wait('@updateRequest').its('response.statusCode').should('eq', 200)
      cy.get('[data-cy="success-message"]').should('be.visible')
      cy.get('[data-cy="profile-name"]').should('contain', newName)
      
      // 7. Logout
      cy.get('[data-cy="user-menu"]').click()
      cy.get('[data-cy="logout-button"]').click()
      
      // 8. Verificar logout
      cy.url().should('not.include', '/dashboard')
      cy.url().should('include', '/')
    })

    it('should reject invalid credentials', () => {
      cy.visit('/login')
      cy.get('[data-cy="email-input"]').type('wrong@example.com')
      cy.get('[data-cy="password-input"]').type('wrongpassword')
      cy.get('[data-cy="login-button"]').click()
      
      cy.get('[data-cy="error-message"]')
        .should('be.visible')
        .and('contain', 'Invalid credentials')
    })

    it('should protect routes when not authenticated', () => {
      // Intentar acceder a ruta protegida sin auth
      cy.visit('/dashboard')
      
      // Debe redirigir a login
      cy.url().should('include', '/login')
      cy.get('[data-cy="login-form"]').should('be.visible')
    })
  })

  describe('Performance and Load Times', () => {
    it('should load pages within acceptable time', () => {
      const pages = ['/', '/login', '/register']
      
      pages.forEach(page => {
        const start = Date.now()
        cy.visit(page)
        cy.get('body').should('be.visible')
        const loadTime = Date.now() - start
        
        cy.log(`${page} loaded in ${loadTime}ms`)
        expect(loadTime).to.be.lessThan(3000)
      })
    })

    it('should handle concurrent requests gracefully', () => {
      cy.loginAPI(testUser.email, testUser.password)
      cy.visit('/dashboard')
      
      // Simular múltiples requests simultáneos
      const requests = Array.from({ length: 5 }, (_, i) => 
        cy.request(`${Cypress.env('apiUrl')}/users/me`)
      )
      
      Promise.all(requests).then(responses => {
        responses.forEach(response => {
          expect(response.status).to.eq(200)
        })
      })
    })
  })

  describe('Error Handling', () => {
    it('should handle API errors gracefully', () => {
      // Mockear error del servidor
      cy.intercept('POST', '**/api/auth/login', {
        statusCode: 500,
        body: { message:  'Internal Server Error' }
      }).as('failedLogin')
      
      cy.visit('/login')
      cy.get('[data-cy="email-input"]').type(testUser.email)
      cy.get('[data-cy="password-input"]').type(testUser.password)
      cy.get('[data-cy="login-button"]').click()
      
      cy.wait('@failedLogin')
      
      // Debe mostrar error amigable
      cy.get('[data-cy="error-message"]')
        .should('be. visible')
        .and('contain', 'Something went wrong')
    })

    it('should handle network errors', () => {
      cy.intercept('POST', '**/api/auth/login', { forceNetworkError: true }).as('networkError')
      
      cy.visit('/login')
      cy.get('[data-cy="email-input"]').type(testUser.email)
      cy.get('[data-cy="password-input"]').type(testUser.password)
      cy.get('[data-cy="login-button"]').click()
      
      cy.get('[data-cy="error-message"]')
        .should('be.visible')
        .and('contain', 'network')
    })
  })

  describe('Mobile Responsiveness', () => {
    beforeEach(() => {
      cy.viewport('iphone-x')
    })

    it('should be usable on mobile devices', () => {
      cy.visit('/')
      
      // Menú hamburguesa visible en móvil
      cy.get('[data-cy="mobile-menu-button"]').should('be.visible')
      cy.get('[data-cy="mobile-menu-button"]').click()
      
      // Navegación móvil
      cy.get('[data-cy="mobile-nav"]').should('be.visible')
      cy.get('[data-cy="mobile-login-link"]').click()
      
      // Formulario responsive
      cy.get('[data-cy="login-form"]').should('be.visible')
      cy.get('[data-cy="email-input"]').should('be.visible')
    })
  })
})
```

---

#### GitHub Actions Workflow para Cypress

**.  github/workflows/e2e-tests.yml:**

```yaml
name: E2E Tests

on: 
  workflow_run:
    workflows: ["Deploy Backend to Render"]
    types: [completed]
    branches: [main]
  workflow_dispatch: 
    inputs:
      environment: 
        description: 'Environment to test'
        required: true
        type: choice
        options:
          - staging
          - production

env:
  CYPRESS_BASE_URL: https://staging.myapp.netlify.app
  CYPRESS_API_URL: https://myapp-backend-staging.onrender.com/api

jobs:
  # ==========================================
  # Job 1: Esperar a que Staging esté listo
  # ==========================================
  wait-for-deployment:
    name: Wait for Deployment
    runs-on: ubuntu-latest
    
    steps:
      - name:  Wait for frontend to be ready
        run: |
          echo "Waiting for frontend..."
          max_attempts=30
          attempt=0
          
          while [ $attempt -lt $max_attempts ]; do
            response=$(curl -s -o /dev/null -w "%{http_code}" ${{ env.CYPRESS_BASE_URL }} || echo "000")
            
            if [ "$response" = "200" ]; then
              echo "✅ Frontend is ready"
              break
            fi
            
            echo "Attempt $((attempt + 1))/$max_attempts - Frontend not ready (HTTP $response)"
            sleep 10
            attempt=$((attempt + 1))
          done
          
          if [ $attempt -eq $max_attempts ]; then
            echo "❌ Frontend failed to become ready"
            exit 1
          fi
      
      - name: Wait for backend to be ready
        run: |
          echo "Waiting for backend..."
          max_attempts=30
          attempt=0
          
          while [ $attempt -lt $max_attempts ]; do
            response=$(curl -s -o /dev/null -w "%{http_code}" ${{ env. CYPRESS_API_URL }}/health || echo "000")
            
            if [ "$response" = "200" ]; then
              echo "✅ Backend is ready"
              break
            fi
            
            echo "Attempt $((attempt + 1))/$max_attempts - Backend not ready (HTTP $response)"
            sleep 10
            attempt=$((attempt + 1))
          done
          
          if [ $attempt -eq $max_attempts ]; then
            echo "❌ Backend failed to become ready"
            exit 1
          fi
  
  # ==========================================
  # Job 2: Ejecutar Tests E2E
  # ==========================================
  cypress-run:
    name:  Cypress E2E Tests
    runs-on: ubuntu-latest
    needs: wait-for-deployment
    timeout-minutes: 30
    
    strategy:
      fail-fast: false
      matrix: 
        # Ejecutar en paralelo en múltiples contenedores
        containers: [1, 2, 3]
    
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Setup Node. js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
          cache-dependency-path: e2e-tests/package-lock.json
      
      - name: Install dependencies
        working-directory: e2e-tests
        run: npm ci
      
      - name:  Cypress run
        uses: cypress-io/github-action@v6
        with:
          working-directory: e2e-tests
          browser: chrome
          headed: false
          record: true
          parallel: true
          group: 'E2E Tests'
        env:
          CYPRESS_BASE_URL: ${{ env. CYPRESS_BASE_URL }}
          CYPRESS_API_URL: ${{ env.CYPRESS_API_URL }}
          CYPRESS_RECORD_KEY: ${{ secrets.CYPRESS_RECORD_KEY }}
          GITHUB_TOKEN: ${{ secrets. GITHUB_TOKEN }}
      
      # Subir videos solo si hay fallos
      - name: Upload videos
        uses: actions/upload-artifact@v3
        if: failure()
        with:
          name: cypress-videos-${{ matrix.containers }}
          path: e2e-tests/cypress/videos
          retention-days: 7
      
      # Subir screenshots de fallos
      - name: Upload screenshots
        uses: actions/upload-artifact@v3
        if: failure()
        with:
          name: cypress-screenshots-${{ matrix.containers }}
          path: e2e-tests/cypress/screenshots
          retention-days:  7
      
      # Subir reportes
      - name: Upload test results
        uses: actions/upload-artifact@v3
        if:  always()
        with:
          name: cypress-results-${{ matrix.containers }}
          path: |
            e2e-tests/cypress/results
            e2e-tests/cypress/reports
          retention-days: 30
  
  # ==========================================
  # Job 3: Generar Reporte Consolidado
  # ==========================================
  generate-report:
    name: Generate Test Report
    runs-on: ubuntu-latest
    needs: cypress-run
    if: always()
    
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
      
      - name: Download all artifacts
        uses: actions/download-artifact@v3
        with:
          path: artifacts
      
      - name: Install dependencies
        working-directory: e2e-tests
        run:  npm ci
      
      - name:  Merge reports
        working-directory: e2e-tests
        run:  |
          mkdir -p cypress/results/mochawesome
          cp -r ../artifacts/cypress-results-*/mochawesome/* cypress/results/mochawesome/ || true
          npm run report:merge
          npm run report:generate
      
      - name: Upload consolidated report
        uses: actions/upload-artifact@v3
        with:
          name: e2e-test-report
          path: e2e-tests/cypress/results/index.html
          retention-days: 90
      
      - name: Publish test results
        uses: EnricoMi/publish-unit-test-result-action@v2
        if: always()
        with:
          files: |
            artifacts/cypress-results-*/junit/*. xml
          check_name: E2E Test Results
          comment_title: 🧪 E2E Test Results
  
  # ==========================================
  # Job 4: Lighthouse Performance Audit
  # ==========================================
  lighthouse:
    name:  Lighthouse Audit
    runs-on: ubuntu-latest
    needs: wait-for-deployment
    
    steps:
      - name:  Checkout code
        uses: actions/checkout@v4
      
      - name: Run Lighthouse
        uses: treosh/lighthouse-ci-action@v10
        with:
          urls: |
            ${{ env.CYPRESS_BASE_URL }}
            ${{ env. CYPRESS_BASE_URL }}/login
            ${{ env.CYPRESS_BASE_URL }}/register
          uploadArtifacts: true
          temporaryPublicStorage: true
      
      - name: Check Lighthouse scores
        run: |
          echo "Lighthouse audit completed"
          # Los resultados están en artifacts
  
  # ==========================================
  # Job 5: Notificación de Resultados
  # ==========================================
  notify: 
    name:  Notify Team
    runs-on: ubuntu-latest
    needs: [cypress-run, generate-report, lighthouse]
    if: always()
    
    steps:
      - name: Check test results
        id: test-result
        run: |
          if [[ "${{ needs.cypress-run.result }}" == "success" ]]; then
            echo "status=✅ PASSED" >> $GITHUB_OUTPUT
            echo "color=good" >> $GITHUB_OUTPUT
          else
            echo "status=❌ FAILED" >> $GITHUB_OUTPUT
            echo "color=danger" >> $GITHUB_OUTPUT
          fi
      
      - name:  Notify Slack
        uses: slackapi/slack-github-action@v1
        with:
          payload: |
            {
              "text": "E2E Tests ${{ steps.test-result.outputs.status }}",
              "attachments":  [
                {
                  "color": "${{ steps.test-result.outputs.color }}",
                  "fields": [
                    {
                      "title": "Environment",
                      "value": "Staging",
                      "short": true
                    },
                    {
                      "title":  "Commit",
                      "value": "${{ github.sha }}",
                      "short": true
                    },
                    {
                      "title": "Actor",
                      "value": "${{ github.actor }}",
                      "short": true
                    },
                    {
                      "title": "Results",
                      "value": "<${{ github.server_url }}/${{ github.repository }}/actions/runs/${{ github.run_id }}|View Details>",
                      "short":  true
                    }
                  ]
                }
              ]
            }
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK }}
          SLACK_WEBHOOK_TYPE:  INCOMING_WEBHOOK
      
      - name: Comment on PR
        if: github.event_name == 'pull_request'
        uses: actions/github-script@v7
        with:
          script: |
            const status = '${{ steps.test-result.outputs.status }}'
            const body = `
            ## 🧪 E2E Test Results
            
            **Status:** ${status}
            **Environment:** Staging
            **Frontend:** ${{ env.CYPRESS_BASE_URL }}
            **Backend:** ${{ env.CYPRESS_API_URL }}
            
            [View Full Report](${{ github.server_url }}/${{ github.repository }}/actions/runs/${{ github.run_id }})
            `
            
            github.rest. issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body:  body
            })
```

---

#### Gestión de Artefactos

**Videos y Screenshots:**

Cypress genera automáticamente: 
- **Videos** de cada spec (`.mp4`)
- **Screenshots** de cada fallo (`.png`)

GitHub Actions los preserva como artifacts:  

```yaml
- name: Upload videos
  uses: actions/upload-artifact@v3
  if:  failure()
  with:
    name: cypress-videos
    path: e2e-tests/cypress/videos
    retention-days: 7
```

**Acceder a artifacts:**

```
GitHub repo → Actions → Run específico → Artifacts (abajo)
  - cypress-videos (Download)
  - cypress-screenshots (Download)
  - e2e-test-report (Download)
```

---

### 6. 2. Generación de Documentación Técnica

#### Importancia de la Documentación Automatizada

**Problema**: La documentación manual: 
- Se desactualiza rápidamente
- Nadie tiene tiempo de actualizarla
- Es inconsistente entre componentes

**Solución**:  Generar documentación **automáticamente desde el código**: 
- Siempre está actualizada
- Es parte del pipeline CI/CD
- Se despliega automáticamente

---

#### Javadoc para Java

**🛠️ Paso a Paso:**

**1. Configurar Gradle (build.gradle. kts):**

```kotlin
plugins {
    java
    id("org.springframework. boot") version "3.2.0"
}

tasks.javadoc {
    options {
        this as StandardJavadocDocletOptions
        
        // Configuración
        encoding = "UTF-8"
        charSet = "UTF-8"
        author = true
        version = true
        
        // Links a documentación externa
        links(
            "https://docs.oracle.com/en/java/javase/21/docs/api/",
            "https://docs.spring.io/spring-framework/docs/current/javadoc-api/",
            "https://docs.spring.io/spring-boot/docs/current/api/"
        )
        
        // Título
        windowTitle = "MyApp API Documentation"
        docTitle = "MyApp - User Management API"
        header = "<b>MyApp</b>"
        footer = "Copyright © 2024"
        
        // Opciones adicionales
        addStringOption("Xdoclint:none", "-quiet")
        addBooleanOption("html5", true)
    }
    
    // Incluir solo paquetes públicos
    include("**/controller/**", "**/service/**", "**/model/**")
    exclude("**/internal/**")
}

// Task para generar Javadoc como JAR
tasks.register<Jar>("javadocJar") {
    dependsOn(tasks.javadoc)
    archiveClassifier. set("javadoc")
    from(tasks.javadoc. get().destinationDir)
}
```

**2. Documentar código correctamente:**

```java
package com.example.controller;

import com.example.dto.UserDTO;
import com. example.service.UserService;
import org.springframework.web.bind.annotation.*;

/**
 * REST Controller para gestión de usuarios. 
 * 
 * <p>Este controlador proporciona endpoints para operaciones CRUD
 * sobre usuarios del sistema.</p>
 * 
 * @author Tu Nombre
 * @version 1.0
 * @since 2024-01-01
 */
@RestController
@RequestMapping("/api/users")
public class UserController {
    
    private final UserService userService;
    
    /**
     * Constructor con inyección de dependencias.
     * 
     * @param userService servicio de lógica de negocio de usuarios
     */
    public UserController(UserService userService) {
        this.userService = userService;
    }
    
    /**
     * Obtiene todos los usuarios del sistema.
     * 
     * <p>Retorna una lista paginada de usuarios activos. 
     * Requiere autenticación con rol ADMIN.</p>
     * 
     * @param page número de página (base 0)
     * @param size tamaño de página
     * @return lista de usuarios
     * @throws UnauthorizedException si el usuario no tiene permisos
     * 
     * @see UserDTO
     * @see UserService#getAllUsers(int, int)
     */
    @GetMapping
    public List<UserDTO> getAllUsers(
            @RequestParam(defaultValue = "0") int page,
            @RequestParam(defaultValue = "20") int size) {
        return userService.getAllUsers(page, size);
    }
    
    /**
     * Crea un nuevo usuario.
     * 
     * @param userDTO datos del usuario a crear
     * @return usuario creado con ID asignado
     * @throws ValidationException si los datos no son válidos
     * @throws UserAlreadyExistsException si el email ya está registrado
     */
    @PostMapping
    public UserDTO createUser(@Valid @RequestBody UserDTO userDTO) {
        return userService.createUser(userDTO);
    }
}
```

**3. Generar Javadoc:**

```bash
./gradlew javadoc
```

Resultado en:  `build/docs/javadoc/index.html`

---

#### DocFX para . NET

**🛠️ Paso a Paso:**

**1. Instalar DocFX:**

```bash
dotnet tool install -g docfx
```

**2. Inicializar proyecto de documentación:**

```bash
cd src/MyApp
docfx init -q
```

Esto crea: 
```
docfx_project/
├── docfx.json
├── index.md
├── toc.yml
└── api/
```

**3. Configurar docfx.json:**

```json
{
  "metadata": [
    {
      "src": [
        {
          "files": [ "**/*.csproj" ],
          "src": "../../src"
        }
      ],
      "dest": "api",
      "properties": {
        "TargetFramework": "net10. 0"
      }
    }
  ],
  "build": {
    "content": [
      {
        "files": [ "api/**.yml", "api/index.md" ]
      },
      {
        "files":  [ "*. md", "toc.yml" ]
      }
    ],
    "resource": [
      {
        "files": [ "images/**" ]
      }
    ],
    "output": "_site",
    "template": [ "default", "modern" ],
    "globalMetadata": {
      "_appTitle": "MyApp API Documentation",
      "_appFooter": "Copyright © 2024 MyCompany",
      "_enableSearch": true
    }
  }
}
```

**4. Documentar código con XML Comments:**

```csharp
namespace MyApp.Controllers;

/// <summary>
/// Controlador para gestión de usuarios.
/// </summary>
/// <remarks>
/// Este controlador proporciona endpoints REST para operaciones CRUD
/// sobre usuarios del sistema.
/// </remarks>
[ApiController]
[Route("api/[controller]")]
public class UsersController : ControllerBase
{
    private readonly IUserService _userService;
    
    /// <summary>
    /// Constructor con inyección de dependencias. 
    /// </summary>
    /// <param name="userService">Servicio de lógica de negocio</param>
    public UsersController(IUserService userService)
    {
        _userService = userService;
    }
    
    /// <summary>
    /// Obtiene todos los usuarios del sistema.
    /// </summary>
    /// <param name="page">Número de página (base 0)</param>
    /// <param name="size">Tamaño de página</param>
    /// <returns>Lista paginada de usuarios</returns>
    /// <response code="200">Retorna la lista de usuarios</response>
    /// <response code="401">Usuario no autenticado</response>
    /// <response code="403">Usuario sin permisos</response>
    /// <example>
    /// GET /api/users?page=0&size=20
    /// </example>
    [HttpGet]
    [ProducesResponseType(typeof(List<UserDTO>), StatusCodes.Status200OK)]
    [ProducesResponseType(StatusCodes.Status401Unauthorized)]
    [ProducesResponseType(StatusCodes.Status403Forbidden)]
    public async Task<ActionResult<List<UserDTO>>> GetAllUsers(
        [FromQuery] int page = 0,
        [FromQuery] int size = 20)
    {
        var users = await _userService.GetAllUsersAsync(page, size);
        return Ok(users);
    }
    
    /// <summary>
    /// Crea un nuevo usuario. 
    /// </summary>
    /// <param name="userDTO">Datos del usuario a crear</param>
    /// <returns>Usuario creado con ID asignado</returns>
    /// <exception cref="ValidationException">
    /// Se lanza cuando los datos de entrada no son válidos
    /// </exception>
    /// <exception cref="UserAlreadyExistsException">
    /// Se lanza cuando el email ya está registrado
    /// </exception>
    [HttpPost]
    [ProducesResponseType(typeof(UserDTO), StatusCodes.Status201Created)]
    [ProducesResponseType(StatusCodes.Status400BadRequest)]
    [ProducesResponseType(StatusCodes. Status409Conflict)]
    public async Task<ActionResult<UserDTO>> CreateUser([FromBody] UserDTO userDTO)
    {
        var created = await _userService.CreateUserAsync(userDTO);
        return CreatedAtAction(nameof(GetAllUsers), new { id = created. Id }, created);
    }
}
```

**5. Habilitar generación de XML:**

```xml
<!-- MyApp.csproj -->
<PropertyGroup>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <NoWarn>$(NoWarn);1591</NoWarn>
</PropertyGroup>
```

**6. Generar documentación:**

```bash
docfx docfx.json
```

Resultado en: `_site/index.html`

---

#### Publicación en GitHub Pages

**GitHub Actions Workflow:**

**.  github/workflows/docs.yml:**

```yaml
name: Generate and Deploy Documentation

on:
  push:
    branches: [ main ]
    paths:
      - 'src/**/*. java'
      - 'src/**/*.cs'
      - 'docs/**'
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  # ==========================================
  # Job 1:  Generar Javadoc (Java)
  # ==========================================
  generate-javadoc: 
    name: Generate Javadoc
    runs-on: ubuntu-latest
    if: contains(github.repository, 'java-project')
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup JDK
        uses: actions/setup-java@v4
        with:
          java-version: '21'
          distribution: 'temurin'
      
      - name: Generate Javadoc
        run:  ./gradlew javadoc
      
      - name: Upload Javadoc
        uses:  actions/upload-artifact@v3
        with:
          name:  javadoc
          path: build/docs/javadoc/
  
  # ==========================================
  # Job 2: Generar DocFX (. NET)
  # ==========================================
  generate-docfx: 
    name: Generate DocFX
    runs-on: ubuntu-latest
    if: contains(github.repository, 'dotnet-project')
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup .NET
        uses: actions/setup-dotnet@v4
        with:
          dotnet-version: '10.0.x'
      
      - name: Install DocFX
        run: dotnet tool install -g docfx
      
      - name: Build project (for XML comments)
        run: dotnet build --configuration Release
      
      - name:  Generate documentation
        run: docfx docfx_project/docfx.json
      
      - name: Upload DocFX site
        uses: actions/upload-artifact@v3
        with: 
          name: docfx-site
          path: docfx_project/_site/
  
  # ==========================================
  # Job 3: Deploy a GitHub Pages
  # ==========================================
  deploy-pages:
    name: Deploy to GitHub Pages
    runs-on: ubuntu-latest
    needs: [generate-javadoc, generate-docfx]
    if: always() && (needs.generate-javadoc.result == 'success' || needs. generate-docfx.result == 'success')
    
    environment: 
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    
    steps:
      - name: Download artifacts
        uses: actions/download-artifact@v3
      
      - name:  Prepare pages directory
        run: |
          mkdir -p pages
          
          # Si hay Javadoc
          if [ -d "javadoc" ]; then
            cp -r javadoc pages/api
          fi
          
          # Si hay DocFX
          if [ -d "docfx-site" ]; then
            cp -r docfx-site/* pages/
          fi
          
          # Crear index si no existe
          if [ ! -f "pages/index.html" ]; then
            cat > pages/index.html << 'EOF'
<! DOCTYPE html>
<html>
<head>
    <title>MyApp Documentation</title>
    <style>
        body { font-family:  Arial, sans-serif; max-width: 800px; margin: 50px auto; }
        h1 { color: #333; }
        .links { margin-top: 30px; }
        .links a { display: block; margin: 10px 0; padding: 10px; background: #f5f5f5; text-decoration: none; color: #0366d6; }
        .links a:hover { background: #e5e5e5; }
    </style>
</head>
<body>
    <h1>MyApp Documentation</h1>
    <div class="links">
        <a href="api/">📚 API Documentation</a>
        <a href="https://github.com/user/repo">💻 GitHub Repository</a>
    </div>
</body>
</html>
EOF
          fi
      
      - name:  Setup Pages
        uses: actions/configure-pages@v4
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with: 
          path: pages
      
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

**Resultado:**

Documentación disponible en:   `https://tu-usuario.github.io/tu-repo/`

---

**Flujo completo:**

```
1. Push a main
2. CI:  Build + Tests unitarios/integración
3. Deploy a Staging (Netlify + Render)
4. Tests E2E (Cypress)
   - Si fallan → No deploy a producción
   - Si pasan → Continuar
5. Deploy a Producción
6. Generar y publicar documentación
7. Notificar equipo
```


# Autor

Codificado con :sparkling_heart: por [José Luis González Sánchez](https://twitter.com/JoseLuisGS_)

[![Twitter](https://img.shields.io/twitter/follow/JoseLuisGS_?style=social)](https://twitter.com/JoseLuisGS_)
[![GitHub](https://img.shields.io/github/followers/joseluisgs?style=social)](https://github.com/joseluisgs)
[![GitHub](https://img.shields.io/github/stars/joseluisgs?style=social)](https://github.com/joseluisgs)

## Contacto

<p>
  Cualquier cosa que necesites házmelo saber por si puedo ayudarte 💬.
</p>
<p>
 <a href="https://joseluisgs.dev" target="_blank">
        <img src="https://joseluisgs.github.io/img/favicon.png" 
    height="30">
    </a>  &nbsp;&nbsp;
    <a href="https://github.com/joseluisgs" target="_blank">
        <img src="https://distreau.com/github.svg" 
    height="30">
    </a> &nbsp;&nbsp;
        <a href="https://twitter.com/JoseLuisGS_" target="_blank">
        <img src="https://i.imgur.com/U4Uiaef.png" 
    height="30">
    </a> &nbsp;&nbsp;
    <a href="https://www.linkedin.com/in/joseluisgonsan" target="_blank">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/ca/LinkedIn_logo_initials.png/768px-LinkedIn_logo_initials.png" 
    height="30">
    </a>  &nbsp;&nbsp;
    <a href="https://g.dev/joseluisgs" target="_blank">
        <img loading="lazy" src="https://googlediscovery.com/wp-content/uploads/google-developers.png" 
    height="30">
    </a>  &nbsp;&nbsp;
<a href="https://www.youtube.com/@joseluisgs" target="_blank">
        <img loading="lazy" src="https://upload.wikimedia.org/wikipedia/commons/e/ef/Youtube_logo.png" 
    height="30">
    </a>  
</p>

## Licencia de uso

Este repositorio y todo su contenido está licenciado bajo licencia **Creative Commons**, si desea saber más, vea
la [LICENSE](https://joseluisgs.dev/docs/license/). Por favor si compartes, usas o modificas este proyecto cita a su
autor, y usa las mismas condiciones para su uso docente, formativo o educativo y no comercial.

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Licencia de Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">
JoseLuisGS</span>
by <a xmlns:cc="http://creativecommons.org/ns#" href="https://joseluisgs.dev/" property="cc:attributionName" rel="cc:attributionURL">
José Luis González Sánchez</a> is licensed under
a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons
Reconocimiento-NoComercial-CompartirIgual 4.0 Internacional License</a>.<br />Creado a partir de la obra
en <a xmlns:dct="http://purl.org/dc/terms/" href="https://github.com/joseluisgs" rel="dct:source">https://github.com/joseluisgs</a>.