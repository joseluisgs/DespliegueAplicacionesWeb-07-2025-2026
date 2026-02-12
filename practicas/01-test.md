# Test UD07: Integración y Despliegue Continuo (CI/CD)

## 📋 Instrucciones

Lee atentamente cada pregunta y selecciona la respuesta correcta. Cada pregunta vale 1 punto.


---

## Bloque 1: Fundamentos DevOps y CI/CD

1. **DevOps es principalmente:**
   - a) Una herramienta de desarrollo.
   - b) Una cultura de colaboración entre Desarrollo y Operaciones.
   - c) Un lenguaje de programación.
   - d) Un tipo de servidor.

2. **¿Qué significa el concepto de "Falla Rápido" en CI?**
   - a) Ignorar los errores para avanzar más rápido.
   - b) Detectar problemas inmediatamente para corregirlos mientras el contexto está fresco.
   - c) Eliminar todos los tests del pipeline.
   - d) Desplegar sin pasar los tests.

3. **¿Cuál es el objetivo principal de la Integración Continua (CI)?**
   - a) Desplegar código a producción automáticamente.
   - b) Integrar código frecuentemente con validación automática.
   - c) Eliminar la necesidad de desarrolladores.
   - d) Reducir el número de tests.

4. **El "Shift Left" en DevOps significa:**
   - a) Desplegar a producción más rápido.
   - b) Realizar actividades de validación lo más temprano posible en el ciclo.
   - c) Mover el equipo de desarrollo a otro país.
   - d) Eliminar la fase de testing.

5. **¿Cuál de estas es una métrica DORA?**
   - a) Número de líneas de código.
   - b) Deployment Frequency.
   - c) Cantidad de café consumida.
   - d) Tamaño del repositorio.

6. **Las métricas DORA incluyen (selecciona todas las correctas):**
   - a) Deployment Frequency.
   - b) Lead Time for Changes.
   - c) Change Failure Rate.
   - d) Time to Restore Service.

7. **En el flujo de valor de DevOps, el código pasa por:**
   - a) Solo desarrollo y producción.
   - b) Planificación, código, build, test, deploy, monitorización.
   - c) Solo build y deploy.
   - d) Código y nada más.

---

## Bloque 2: Integración Continua (CI)

8. **¿Qué es un "build" en el contexto de CI?**
   - a) El proceso de construir un edificio.
   - b) El proceso de transformar código fuente en artefactos ejecutables.
   - c) El proceso de contratar nuevos desarrolladores.
   - d) Solo ejecutar tests.

9. **¿Por qué es importante usar entornos limpios para el build?**
   - a) Para gastar más recursos.
   - b) Para eliminar el problema de "funciona en mi máquina".
   - c) No es importante.
   - d) Para hacer más lento el proceso.

10. **Los tests unitarios en el pipeline CI deben ser:**
    - a) Lentos y con muchas dependencias externas.
    - b) Rápidos, aislados y ejecutarse en cada push.
    - c) Solo ejecutarlos una vez al mes.
    - d) Dependientes del estado del servidor.

11. **¿Qué es un artefacto en CI/CD?**
    - a) Un error de programación.
    - b) Un archivo generado durante el build para compartir entre jobs.
    - c) Un tipo de test.
    - d) Un empleado de la empresa.

12. **¿Cuál es el propósito del linting en el pipeline?**
    - a) Aumentar el tamaño del código.
    - b) Analizar el código sin ejecutarlo para verificar estilo y calidad.
    - c) Eliminar todos los comentarios.
    - d) Hacer el código más confuso.

---

## Bloque 3: Entrega y Despliegue Continuo (CD)

13. **¿Cuál es la diferencia entre Continuous Delivery y Continuous Deployment?**
    - a) No hay diferencia, son lo mismo.
    - b) Continuous Delivery requiere aprobación manual; Continuous Deployment no.
    - c) Continuous Deployment requiere aprobación manual; Continuous Delivery no.
    - d) Continuous Delivery es solo para frontend.

14. **El entorno de Staging debe ser:**
    - a) Totalmente diferente a producción.
    - b) Una réplica exacta de producción.
    - c) No es necesario.
    - d) Solo para pruebas manuales.

15. **¿Qué estrategia de despliegue NO causa downtime?**
    - a) Recreate.
    - b) Rolling deployment.
    - c) Despliegue manual.
    - d) Deploy a medianoche.

16. **En un Blue-Green deployment:**
    - a) Se elimina el servidor anterior completamente.
    - b) Se mantiene un ambiente paralelo y se hace switch.
    - c) Solo se usa para frontend.
    - d) Requiere aprobación del usuario final.

17. **¿Qué es un Canary Release?**
    - a) Un lanzamiento para pájaros.
    - b) Despliegue gradual a un pequeño porcentaje de usuarios.
    - c) Eliminar todos los tests.
    - d) Deploy solo en Fridays.

18. **¿Qué configuración de Environment Protection es correcta?**
    - a) No configurar nada.
    - b) Required reviewers y wait timer.
    - c) Permitir que cualquiera despliegue.
    - d) Desactivar los tests.

---

## Bloque 4: GitHub Actions

19. **¿Dónde se definen los workflows de GitHub Actions?**
    - a) En el archivo `main.py`.
    - b) En la carpeta `.github/workflows/`.
    - c) En el archivo `README.md`.
    - d) En el directorio `src/`.

20. **¿Cuál es la jerarquía correcta en GitHub Actions?**
    - a) Workflow → Jobs → Steps → Runners.
    - b) Runners → Steps → Jobs → Workflows.
    - c) Steps → Workflow → Runners → Jobs.
    - d) Jobs → Workflow → Runners → Steps.

21. **Un "Job" en GitHub Actions:**
    - a) Es una tarea individual.
    - b) Es una unidad de ejecución que contiene steps.
    - c) Es el servidor donde se ejecuta todo.
    - d) No existe en GitHub Actions.

22. **¿Qué hace el comando `needs` en un workflow?**
    - a) No hace nada.
    - b) Especifica dependencias entre jobs.
    - c) Elimina los jobs anteriores.
    - d) Crea nuevos jobs.

23. **Los "Secrets" en GitHub Actions sirven para:**
    - a) Almacenar claves de forma insegura.
    - b) Almacenar credenciales de forma cifrada.
    - c) Ocultar el código.
    - d) Eliminar variables de entorno.

24. **¿Qué tipo de runner proporciona GitHub por defecto?**
    - a) Solo Windows.
    - b) Solo Linux.
    - c) Ubuntu, Windows y macOS.
    - d) Solo macOS.

---

## Bloque 5: Calidad y Protección

25. **El propósito de "Branch Protection" es:**
    - a) Proteger físicamente las ramas de código.
    - b) Impedir que código defectuoso llegue a ramas protegidas.
    - c) Eliminar todas las ramas.
    - d) Solo proteger la rama develop.

26. **Los "Required Status Checks":**
    - a) Son opcionales siempre.
    - b) Tests que deben pasar antes de poder hacer merge.
    - c) No tienen relación con los tests.
    - d) Solo funcionan en producción.

27. **¿Qué es un archivo CODEOWNERS?**
    - a) Un archivo para eliminar código.
    - b) Un archivo que especifica quién debe revisar ciertos archivos.
    - c) Un archivo de configuración de Docker.
    - d) Un archivo de base de datos.

28. **¿Cuál es una buena práctica con Pull Requests?**
    - a) Hacer merge sin revisar el código.
    - b) Requerir reviews y que los tests pasen antes del merge.
    - c) No hacer Pull Requests.
    - d) Merge directamente a main sin PR.

29. **Los "Checks" en GitHub:**
    - a) No aparecen en la UI.
    - b) Son verificaciones detalladas que aparecen en el PR.
    - c) Solo funcionan offline.
    - d) Eliminan el código automáticamente.

---

## Bloque 6: Despliegue

30. **¿Qué plataforma es ideal para desplegar aplicaciones estáticas de forma gratuita?**
    - a) AWS EC2.
    - b) GitHub Pages.
    - c) Servidor dedicado.
    - d) Mainframe.

31. **¿Qué beneficio ofrece Netlify sobre GitHub Pages?**
    - a) No ofrece nada.
    - b) Serverless functions y forms.
    - c) Solo funciona con Java.
    - d) Es más caro que AWS.

32. **Un Dockerfile multi-stage sirve para:**
    - a) Hacer más lento el build.
    - b) Reducir el tamaño de la imagen final.
    - c) Eliminar todas las dependencias.
    - d) No tiene beneficios.

33. **El "rollback" es:**
    - a) Volver a una versión anterior cuando algo falla.
    - b) Eliminar todo el código.
    - c) Desplegar sin tests.
    - d) Contratar más desarrolladores.

34. **¿Qué es crítico monitorizar después de un despliegue?**
    - a) El tiempo que hace.
    - b) Error rate y latencia.
    - c) El color del cielo.
    - d) La cantidad de café tomado.

35. **¿Qué herramienta se usa para crear contenedores Docker?**
    - a) Dockerfile.
    - b) GitHub Actions.
    - c) Jenkins.
    - d) Solo AWS.

