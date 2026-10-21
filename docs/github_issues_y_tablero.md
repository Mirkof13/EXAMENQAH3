# Gestión del Proyecto en GitHub: Issues y Project Board

**Materia:** Testing & Quality Assurance (TQA)  
**Estudiante:** Miguel Mirkof Becerra Guzman — UNIFRANZ  
**Repositorio:** [https://github.com/Mirkof13/EXAMENQAH3.git](https://github.com/Mirkof13/EXAMENQAH3.git)  
**Tablero del Proyecto:** Examen Práctico Hito 3 TQA Board  

---

## 1. Estructura del Tablero Kanban (Project Board)

Siguiendo las instrucciones de la presentación de la materia (Slide 14), se organizaron las tareas en cuatro estados del ciclo de vida de QA:

```
+------------------+------------------+------------------+------------------+
|      TO DO       |   IN PROGRESS    |    IN REVIEW     |       DONE       |
+------------------+------------------+------------------+------------------+
|                  |                  |                  | [x] Diseñar TC   |
|                  |                  |                  | [x] Ejecutar TC  |
|                  |                  |                  | [x] Caja Blanca  |
|                  |                  |                  | [x] BDD Gherkin  |
|                  |                  |                  | [x] Evaluar Bugs |
|                  |                  |                  | [x] Evidencias   |
|                  |                  |                  | [x] Docx / PDF   |
|                  |                  |                  | [x] README.md    |
+------------------+------------------+------------------+------------------+
```

---

## 2. Registro de Issues de Trabajo

A continuación se detalla cada una de las tareas creadas como Issues en el repositorio para el seguimiento del trabajo:

### Issue #1: Diseñar 5 casos de prueba de caja negra para SauceDemo
- **Estado:** `Done`
- **Etiquetas:** `caja-negra`, `documentacion`, `fase-diseño`
- **Asignado a:** Miguel Mirkof Becerra Guzman
- **Descripción:** Diseñar cinco casos de prueba funcionales sobre el sitio SauceDemo cubriendo login (exitoso y usuario bloqueado), carrito de compras (agregar y eliminar ítem) y checkout (validación de campos obligatorios).
- **Entregable:** `docs/casos_caja_negra.md`

### Issue #2: Ejecutar casos de prueba y recopilar evidencias fotográficas
- **Estado:** `Done`
- **Etiquetas:** `caja-negra`, `ejecucion`, `evidencias`
- **Asignado a:** Miguel Mirkof Becerra Guzman
- **Descripción:** Ejecutar paso a paso cada uno de los 5 casos de prueba en Google Chrome sobre `https://www.saucedemo.com/`, capturando pantallas clave y registrando los resultados observados, comparación y estado PASS/FAIL.
- **Entregables:** `evidencias/capturas/` (7 capturas PNG) y `docs/casos_caja_negra.md`

### Issue #3: Realizar análisis de caja blanca de la función `validar_compra`
- **Estado:** `Done`
- **Etiquetas:** `caja-blanca`, `cobertura`, `logica`
- **Asignado a:** Miguel Mirkof Becerra Guzman
- **Descripción:** Identificar decisiones simples y compuestas, condiciones simples, calcular el mínimo de casos para cobertura de decisiones (4 casos) y condiciones (5 casos), diseñar 3 casos iniciales y proponer el ajuste necesario para alcanzar el 100% de cobertura.
- **Entregable:** `docs/analisis_caja_blanca.md`

### Issue #4: Redactar escenarios BDD en lenguaje Gherkin
- **Estado:** `Done`
- **Etiquetas:** `bdd`, `gherkin`, `actividad-adicional`
- **Asignado a:** Miguel Mirkof Becerra Guzman
- **Descripción:** Especificar escenarios exitosos y de error en formato BDD utilizando las palabras clave `Feature`, `Scenario`, `Given`, `When`, `Then`, `And`, `But` para autenticación, carrito y checkout.
- **Entregable:** `docs/escenarios_gherkin.md`

### Issue #5: Evaluar y documentar registro de defectos (Bugs)
- **Estado:** `Done`
- **Etiquetas:** `bugs`, `reporte-defectos`, `calidad`
- **Asignado a:** Miguel Mirkof Becerra Guzman
- **Descripción:** Documentar los resultados de los casos ejecutados. Al haber resultado todos los casos PASS, justificar la no creación de bugs artificiales y registrar la plantilla estándar de reporte de bugs de la materia para futuros ciclos.
- **Entregable:** `bugs/bugs_encontrados.md`

### Issue #6: Consolidar informe final en formato Word y PDF
- **Estado:** `Done`
- **Etiquetas:** `entregable`, `informe-final`, `pdf`
- **Asignado a:** Miguel Mirkof Becerra Guzman
- **Descripción:** Integrar la totalidad del trabajo académico en un único documento formal con portada institucional, tablas de diseño y ejecución completas, imágenes de evidencia insertadas, análisis de caja blanca, escenarios BDD, conclusiones y referencias en formato APA 7.ª edición.
- **Entregables:** `entregable/informe_hito3.pdf`, `entregable/informe_hito3.docx`, `entregable/informe_hito3.md`

### Issue #7: Estructurar repositorio Git y documentar README.md
- **Estado:** `Done`
- **Etiquetas:** `git`, `github`, `versionamiento`
- **Asignado a:** Miguel Mirkof Becerra Guzman
- **Descripción:** Organizar el árbol de directorios del proyecto, redactar el archivo README con resumen ejecutivo, enlaces a evidencias, tabla de resultados y vincular el repositorio remoto `https://github.com/Mirkof13/EXAMENQAH3.git`.
- **Entregable:** `README.md`
