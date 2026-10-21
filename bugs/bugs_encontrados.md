# Registro de Defectos (Bugs)

**Aplicación bajo prueba:** Swag Labs — [https://www.saucedemo.com/](https://www.saucedemo.com/)  
**Fecha:** 20/10/2026  
**Autor:** Miguel Mirkof Becerra Guzman — UNIFRANZ  
**Repositorio:** [https://github.com/Mirkof13/EXAMENQAH3.git](https://github.com/Mirkof13/EXAMENQAH3.git)

> Los defectos se documentan por separado con la plantilla de reporte de bugs de la materia y se relacionan con el caso que los detectó mediante el campo de referencia. Cada reporte incluye identificador y título, descripción, pasos para reproducir, resultado actual, resultado esperado, prioridad, severidad, ambiente, adjuntos y comentarios.  
> **Si un caso resulta PASS no se registra defecto**, tal como indica la consigna del examen.

---

## Resultado de la ejecución

| Caso | Descripción | Estado | Bug encontrado |
|------|-------------|--------|---------------|
| TC-001 | Inicio de sesión exitoso | PASS | No |
| TC-002 | Inicio de sesión con usuario bloqueado | PASS | No |
| TC-003 | Agregar producto al carrito | PASS | No |
| TC-004 | Eliminar producto del carrito | PASS | No |
| TC-005 | Validar campos obligatorios en checkout | PASS | No |

---

## Observación general

Durante la ejecución de los cinco casos de prueba sobre SauceDemo, todas las funcionalidades probadas se comportaron según lo esperado. No se encontraron defectos reproducibles en los flujos evaluados:

- El sistema de autenticación valida correctamente credenciales válidas e inválidas.
- El carrito de compras permite agregar y eliminar productos sin errores.
- La validación de campos obligatorios en el checkout funciona correctamente, mostrando mensajes específicos y claros.

Al no existir defectos reproducibles, no se generan reportes de bugs. A continuación se incluye la plantilla de referencia (vacía) para documentar futuros hallazgos.

---

## Plantilla de reporte de bugs (referencia)

La siguiente es la plantilla estándar de la materia. Se incluye como referencia para documentar defectos en caso de encontrarlos en pruebas futuras.

| Campo | Descripción |
|-------|-------------|
| **#BUG-XX-X** | **Bug Report** |
| **Title** | [Título descriptivo del defecto] |
| **Descripción** | [Descripción detallada del problema encontrado] |
| **Pasos** | 1. [Paso para reproducir] <br> 2. [Paso para reproducir] <br> 3. [Paso para reproducir] <br><br> **Referencia:** TC-XXX |
| **Resultado actual** | [Lo que ocurrió realmente] |
| **Resultado esperado** | [Lo que debería haber ocurrido] |
| **Prioridad** | Alta / Media / Baja (1-5) |
| **Severidad** | Crítica / Mayor / Menor / Trivial (1-5) |
| **Ambiente** | Dispositivo: PC/Laptop <br> Sistema operativo: Windows <br> Navegador: Chrome <br> Versión del software: N/A |
| **Adjuntos** | [Capturas de pantalla o evidencia] |
| **Comentarios** | [Información adicional relevante] |

---

> **Nota:** La prueba resulta PASS → no se inventa un bug. Solo se registran defectos reproducibles encontrados durante la ejecución real, tal como indican las instrucciones del examen.
