# Examen Práctico – Hito 3 · Testing & Quality Assurance

**Universidad Privada Franz Tamayo (UNIFRANZ)**  
**Materia:** Testing & Quality Assurance (TQA) — Séptimo Semestre  
**Estudiante:** Miguel Mirkof Becerra Guzman  
**Fecha:** 20 de Octubre de 2026  
**Repositorio GitHub:** [https://github.com/Mirkof13/EXAMENQAH3.git](https://github.com/Mirkof13/EXAMENQAH3.git)  

---

## Propósito

Repositorio individual del **Examen Práctico Hito 3** de la materia *Testing & Quality Assurance*.  
Contiene los cinco casos de prueba de caja negra con diseño, ejecución real y capturas de evidencia, el análisis exhaustivo de caja blanca, los escenarios Gherkin (BDD), la gestión de bugs y el informe final consolidado en formatos PDF, Word y Markdown.

---

## Aplicación bajo prueba

| Dato | Valor |
|---|---|
| **Nombre** | Swag Labs (SauceDemo) |
| **URL** | [https://www.saucedemo.com/](https://www.saucedemo.com/) |
| **Tipo** | Aplicación web de demostración para e-commerce (SPA) |
| **Proveedor** | Sauce Labs |
| **Ambiente de prueba** | Producción pública de demostración |

---

## Estructura del Repositorio

```
EXAMENQAH3/
├── README.md
├── docs/
│   ├── casos_caja_negra.md       # 5 Casos de prueba: Diseño, ejecución y capturas
│   ├── analisis_caja_blanca.md   # Análisis de validar_compra, decisiones, caminos y cobertura
│   └── escenarios_gherkin.md     # Escenarios BDD Given / When / Then / And / But
├── bugs/
│   └── bugs_encontrados.md       # Registro de defectos y plantilla estándar de reporte
├── evidencias/
│   └── capturas/                 # Capturas reales de la ejecución
│       ├── TC001_login_page.png
│       ├── TC001_products_page.png
│       ├── TC002_locked_out_error.png
│       ├── TC003_cart_badge.png
│       ├── TC003_cart_page.png
│       ├── TC004_empty_cart.png
│       └── TC005_checkout_error.png
└── entregable/
    ├── examen H3 TQA Mirkof Guzman.pdf      # Informe final formal consolidado en PDF
    └── evalicion h3 QA Mirkof Guzman.docx   # Documento editable Word con tablas e imágenes
```

---

## Resumen de Resultados de Pruebas

| Caso | Descripción | Tipo | Prioridad | Estado | Evidencia |
|---|---|---|---|:---:|---|
| **TC-001** | Inicio de sesión exitoso (`standard_user`) | Funcional | Alta | ✅ **PASS** | [Captura](evidencias/capturas/TC001_products_page.png) |
| **TC-002** | Inicio de sesión con usuario bloqueado (`locked_out_user`) | Negativa | Alta | ✅ **PASS** | [Captura](evidencias/capturas/TC002_locked_out_error.png) |
| **TC-003** | Agregar producto al carrito (`Sauce Labs Backpack`) | Funcional | Alta | ✅ **PASS** | [Captura](evidencias/capturas/TC003_cart_badge.png) |
| **TC-004** | Eliminar producto del carrito | Funcional | Media | ✅ **PASS** | [Captura](evidencias/capturas/TC004_empty_cart.png) |
| **TC-005** | Validar campos obligatorios en el checkout | Negativa | Alta | ✅ **PASS** | [Captura](evidencias/capturas/TC005_checkout_error.png) |

---

## Técnicas y Entregables Aplicados

1. **Caja Negra (Black Box Testing):** 5 casos funcionales sobre SauceDemo, siguiendo la plantilla oficial de la materia con especificación previa de objetivos, precondiciones, datos, pasos, criterios de éxito, resultados observados, comparación y capturas.
2. **Caja Blanca (White Box Testing):** Análisis de la función `validar_compra` en Python. Se identificaron 3 decisiones y 4 condiciones simples. Se calculó el mínimo de 4 casos para cobertura de decisiones y sentencias, demostrando por qué 3 casos eran insuficientes (83.3%) y proponiendo el ajuste necesario (CB4) y el caso para cobertura de condiciones (CB5).
3. **BDD / Gherkin:** Escenarios formales para Login, Carrito y Checkout empleando `Feature`, `Scenario`, `Given`, `When`, `Then`, `And`, `But`.
4. **Registro de Defectos:** Documentación siguiendo la plantilla oficial de la materia. Al resultar todos los casos PASS, no se registraron defectos artificiales, adjuntando la plantilla formal de referencia.
5. **Informe Consolidado:** Archivos formalizados en [`entregable/examen H3 TQA Mirkof Guzman.pdf`](entregable/examen%20H3%20TQA%20Mirkof%20Guzman.pdf) y [`entregable/evalicion h3 QA Mirkof Guzman.docx`](entregable/evalicion%20h3%20QA%20Mirkof%20Guzman.docx).
6. **Gestión de Proyecto en GitHub:** Planificación con GitHub Issues y tablero Kanban.

---

## Herramientas y Ambiente de Ejecución

| Herramienta | Detalle |
|---|---|
| **Navegador** | Google Chrome (Versión actualizada) |
| **Sistema Operativo** | Windows |
| **Ambiente de Prueba** | Producción pública (SauceDemo) |
| **Control de Versiones** | Git + GitHub |
| **Gestión Ágil** | GitHub Issues & Projects |

---

## Autor

- **Nombre:** Miguel Mirkof Becerra Guzman
- **Carrera:** Ingeniería de Sistemas / Software
- **Asignatura:** Testing & Quality Assurance (TQA)
- **Docente:** UNIFRANZ

---

## Referencias (Normas APA)

- Sauce Labs. (s. f.). *Swag Labs* [Aplicación web de demostración]. https://www.saucedemo.com/
- Universidad Privada Franz Tamayo. (s. f.). *Caja blanca y Gherkin* [Diapositivas de clase]. Testing y Quality Assurance.
- Universidad Privada Franz Tamayo. (s. f.). *Examen práctico Hito 3 TQA: Instrucciones* [Diapositivas]. Testing y Quality Assurance.
- Universidad Privada Franz Tamayo. (s. f.). *Plantilla para diseño y ejecución de casos de prueba* [Documento de clase]. Testing y Quality Assurance.
- Universidad Privada Franz Tamayo. (s. f.). *Técnicas de pruebas de caja blanca* [Diapositivas de clase]. Testing y Quality Assurance.
