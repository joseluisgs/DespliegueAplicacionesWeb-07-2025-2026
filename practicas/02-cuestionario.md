# Cuestionario UD07: Integración y Despliegue Continuo (CI/CD)

## 📋 Instrucciones

Responde a las siguientes preguntas de investigación de forma detallada. Cada pregunta debe responderse con un mínimo de 150 palabras, justificando tu respuesta con ejemplos prácticos y referencias a los conceptos vistos en la unidad.


---

## 1. ROI de la Automatización CI/CD

**Pregunta:** Teniendo en cuenta que un bug detectado en producción puede costar hasta 1000 veces más que uno detectado en desarrollo, investiga y desarrolla un informe sobre cómo la automatización del pipeline CI/CD impacta en el **retorno de inversión (ROI)** de un proyecto de software. ¿Es rentable invertir tiempo en configurar pipelines automatizados desde el principio?


## 2. Estrategias de Branching y su Impacto en CI/CD

**Pregunta:** Compara las tres principales estrategias de branching (Git Flow, GitHub Flow y Trunk-Based Development) y evalúa cómo cada una afecta la implementación de **Integración Continua**. ¿Es posible implementar CI efectivo con Git Flow? ¿Qué ventajas ofrece Trunk-Based para equipos que practican Continuous Deployment?


## 3. Trade-offs entre Velocidad y Calidad en el Pipeline

**Pregunta:** Los tests en el pipeline CI/CD consumen tiempo y recursos. Investiga y propone una estrategia para encontrar el equilibrio entre **velocidad de feedback** y **exhaustividad de tests**. ¿Cuántos tests unitarios vs. integración vs. E2E son recomendables para un proyecto típico?


## 4. Secretos y Seguridad en GitHub Actions

**Pregunta:** Los secrets en GitHub Actions están cifrados, pero no son completamente seguros. Investiga y desarrolla un informe sobre los **riesgos de seguridad** asociados al uso de secrets en workflows, incluyendo casos conocidos de filtraciones. ¿Qué buenas prácticas adicionales recomiendas para proteger credenciales?


## 5. Estrategias de Despliegue y Tolerancia a Fallos

**Pregunta:** Evalúa las estrategias de despliegue (Recreate, Rolling, Blue-Green, Canary) en términos de **tolerancia a fallos** y **recuperación ante desastres**. ¿Cuál es la mejor estrategia para una aplicación crítica de comercio electrónico? Justifica tu respuesta.


## 6. Feature Flags vs. Blue-Green Deployment

**Pregunta:** Los Feature Flags permiten activar/desactivar funcionalidades sin desplegar código, mientras que Blue-Green mantiene dos entornos completos. Investiga y compara ambas técnicas en términos de **complejidad operacional**, **coste de infraestructura** y **velocidad de rollback**. ¿Cuándo usarías una sobre la otra?


## 7. GitHub Actions vs. Jenkins vs. GitLab CI

**Pregunta:** Realiza un análisis comparativo de las tres principales plataformas de CI/CD (GitHub Actions, Jenkins y GitLab CI) considerando: **coste**, **curva de aprendizaje**, **flexibilidad** y **mantenimiento**. ¿Para qué tipo de proyecto recomendaría cada una?


## 8. El Problema de los Flaky Tests en CI/CD

**Pregunta:** Los "flaky tests" son tests que pasan o fallan sin que el código cambie. Investiga las **causas comunes** de flaky tests y desarrolla una estrategia para detectarlos y eliminarlos del pipeline. ¿Qué impacto tiene tolerarlos en la confianza del equipo en el pipeline?


## 9. Monitorización y Alertas Post-Despliegue

**Pregunta:** El despliegue es solo el principio. Investiga qué **métricas críticas** deben monitorizarse después de un despliegue a producción y diseña un sistema de alertas que notifique al equipo solo cuando sea necesario, evitando la fatiga de alertas.


## 10. Compliance y Auditoría en Pipelines CI/CD

**Pregunta:** En entornos regulados (sanidad, finanzas), es necesario auditar cada cambio que llega a producción. Investiga cómo configurar **pipelines CI/CD** que cumplan con requisitos de **compliance**, incluyendo firmas digitales, logs inmutables y trazabilidad completa del código.


---
