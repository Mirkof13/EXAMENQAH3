# Casos de Prueba – Caja Negra

**Aplicación bajo prueba:** Swag Labs — [https://www.saucedemo.com/](https://www.saucedemo.com/)  
**Fecha de ejecución:** 20/10/2026  
**Ejecutado por:** Miguel Mirkof Becerra Guzman — Estudiante TQA · UNIFRANZ  
**Repositorio GitHub:** [https://github.com/Mirkof13/EXAMENQAH3.git](https://github.com/Mirkof13/EXAMENQAH3.git)

---

## Tabla Resumen de Ejecución

| ID | Título | Tipo | Prioridad | Módulo | Estado |
|---|---|---|---|---|:---:|
| **TC-001** | Inicio de sesión exitoso | Funcional | Alta | Inicio de sesión | **PASS** |
| **TC-002** | Inicio de sesión con usuario bloqueado | Negativa | Alta | Inicio de sesión | **PASS** |
| **TC-003** | Agregar un producto al carrito | Funcional | Alta | Catálogo y carrito | **PASS** |
| **TC-004** | Eliminar un producto del carrito | Funcional | Media | Catálogo y carrito | **PASS** |
| **TC-005** | Validar campos obligatorios en el checkout | Negativa | Alta | Checkout | **PASS** |

---

## Caso TC-001 · Inicio de sesión exitoso con credenciales válidas

### Parte 1 · Diseño del caso de prueba

| Campo | Valor |
|---|---|
| **ID del TC** | TC-001 |
| **Prioridad** | Alta |
| **Título** | Inicio de sesión exitoso con usuario estándar |
| **Tipo** | Funcional |
| **Módulo** | Autenticación / Login |
| **Ambiente** | Sitio público de demostración (SauceDemo) |

**1. Objetivo / ¿Qué se quiere validar?**

Comprobar que un usuario válido (`standard_user`) accede al catálogo de productos al ingresar sus credenciales correctas.

**2. Precondiciones**

| Precondición | Detalle |
|---|---|
| Estado inicial | Navegador abierto y sin sesión iniciada en SauceDemo |
| Usuario / permisos | `standard_user` — usuario estándar de demostración |
| Configuración | Conexión a internet y acceso a `https://www.saucedemo.com/` |

**3. Datos de prueba**

| Dato | Valor | Origen | Observación |
|---|---|---|---|
| Usuario | `standard_user` | Usuarios de demostración en página de login | Usuario estándar sin restricciones |
| Contraseña | `secret_sauce` | Provisto por Sauce Labs | Contraseña compartida de demostración |

**4. Pasos y resultados esperados**

| # | Paso / acción | Dato utilizado | Resultado esperado |
|---|---|---|---|
| 1 | Abrir la dirección del sitio en el navegador | `https://www.saucedemo.com/` | Se muestra la página de login con los campos Username y Password y el botón Login. |
| 2 | Escribir el nombre de usuario en el campo Username | `standard_user` | El campo muestra el texto ingresado. |
| 3 | Escribir la contraseña en el campo Password | `secret_sauce` | El campo oculta los caracteres con puntos. |
| 4 | Presionar el botón Login | Clic | El sistema redirige a la página `inventory.html` con el título Products y la lista de productos. |
| 5 | Verificar el encabezado de la página | Observación visual | Se visualizan el menú de hamburguesa y el ícono del carrito sin contador. |

**5. Criterio de éxito**

El usuario accede al catálogo de productos (`inventory.html`) y no se muestra ningún mensaje de error.

---

### Parte 2 · Ejecución de la prueba

| Campo | Valor |
|---|---|
| **ID del TC** | TC-001 |
| **Ejecutado por** | Miguel Mirkof Becerra Guzman |
| **Fecha** | 20/10/2026 |
| **Hora** | 21:35 |
| **Ambiente** | Sitio público de demostración (Google Chrome / Windows) |
| **Versión** | SauceDemo v1 |

**1. Resultado de la ejecución**

| ☑ PASS | ☐ FAIL | ☐ BLOCKED | ☐ NOT RUN |
|:---:|:---:|:---:|:---:|

**2. ¿Qué ocurrió realmente? (Resultado observado)**

El usuario `standard_user` inició sesión correctamente y fue redirigido al catálogo de productos (`inventory.html`) mostrando los 6 artículos disponibles con sus respectivas descripciones, precios y botones "Add to cart".

**3. Comparación con el resultado esperado**

Coincide exactamente con el resultado esperado. No se presentaron demoras ni errores en la autenticación.

**4. Registro de ejecución por paso**

| # | Paso ejecutado | Resultado observado | Estado | Observación |
|---|---|---|:---:|---|
| 1 | Navegar a `https://www.saucedemo.com/` | Se muestra la página de login con logo Swag Labs, campos Username y Password, y botón Login. | **PASS** | Carga correcta e inmediata |
| 2 | Ingresar `standard_user` en Username | El campo muestra `standard_user`. | **PASS** | Entrada de texto correcta |
| 3 | Ingresar `secret_sauce` en Password | El campo oculta los caracteres con puntos de contraseña. | **PASS** | Ocultamiento de clave verificado |
| 4 | Clic en el botón Login | El sistema procesa la solicitud y redirige a `inventory.html`. | **PASS** | Sin demora perceptible |
| 5 | Verificar encabezado y catálogo | Se visualiza menú hamburguesa, carrito vacío y catálogo de 6 productos. | **PASS** | Catálogo completo visible |

**5. Evidencias y Capturas de Pantalla**

| Tipo | Nombre o referencia | Descripción |
|---|---|---|
| Captura | `TC001_login_page.png` | Página de login antes de ingresar credenciales |
| Captura | `TC001_products_page.png` | Página de inventario después del login exitoso |

#### Capturas adjuntas del caso TC-001:

**Figura 1.1: Pantalla inicial de autenticación de SauceDemo (TC-001)**  
![Página de Login](../evidencias/capturas/TC001_login_page.png)

**Figura 1.2: Catálogo de productos tras inicio de sesión exitoso (TC-001)**  
![Página de Productos](../evidencias/capturas/TC001_products_page.png)

**6. Si el resultado es FAIL**

| Desviación encontrada | No aplica (el caso resultó PASS) |
|---|---|
| Referencia del defecto | N/A |

**7. Observaciones de ejecución**

El login se completó de forma instantánea. La página de inventario cargó correctamente todos los elementos UI, estilos CSS y recursos gráficos.

---

## Caso TC-002 · Inicio de sesión con usuario bloqueado

### Parte 1 · Diseño del caso de prueba

| Campo | Valor |
|---|---|
| **ID del TC** | TC-002 |
| **Prioridad** | Alta |
| **Título** | Inicio de sesión con usuario bloqueado |
| **Tipo** | Negativa / Funcional |
| **Módulo** | Autenticación / Login |
| **Ambiente** | Sitio público de demostración (SauceDemo) |

**1. Objetivo / ¿Qué se quiere validar?**

Comprobar que un usuario bloqueado (`locked_out_user`) no puede acceder al sistema y que se muestra un mensaje de error claro.

**2. Precondiciones**

| Precondición | Detalle |
|---|---|
| Estado inicial | Navegador abierto y sin sesión iniciada en SauceDemo |
| Usuario / permisos | `locked_out_user` — usuario bloqueado intencionalmente |
| Configuración | Conexión a internet y acceso a `https://www.saucedemo.com/` |

**3. Datos de prueba**

| Dato | Valor | Origen | Observación |
|---|---|---|---|
| Usuario | `locked_out_user` | Usuarios de demostración listados en login | Usuario designado como bloqueado |
| Contraseña | `secret_sauce` | Provisto por Sauce Labs | Contraseña válida de demostración |

**4. Pasos y resultados esperados**

| # | Paso / acción | Dato utilizado | Resultado esperado |
|---|---|---|---|
| 1 | Abrir la dirección del sitio en el navegador | `https://www.saucedemo.com/` | Se muestra la página de login. |
| 2 | Escribir el nombre de usuario en el campo Username | `locked_out_user` | El campo muestra el texto ingresado. |
| 3 | Escribir la contraseña en el campo Password | `secret_sauce` | El campo oculta los caracteres con puntos. |
| 4 | Presionar el botón Login | Clic | El sistema deniega el acceso y no redirige a `inventory.html`. |
| 5 | Verificar el mensaje de error en pantalla | Observación visual | Se muestra en un banner rojo el mensaje: `Epic sadface: Sorry, this user has been locked out.` |

**5. Criterio de éxito**

El acceso es denegado y se muestra el mensaje de usuario bloqueado, sin ingresar al catálogo.

---

### Parte 2 · Ejecución de la prueba

| Campo | Valor |
|---|---|
| **ID del TC** | TC-002 |
| **Ejecutado por** | Miguel Mirkof Becerra Guzman |
| **Fecha** | 20/10/2026 |
| **Hora** | 21:38 |
| **Ambiente** | Sitio público de demostración (Google Chrome / Windows) |
| **Versión** | SauceDemo v1 |

**1. Resultado de la ejecución**

| ☑ PASS | ☐ FAIL | ☐ BLOCKED | ☐ NOT RUN |
|:---:|:---:|:---:|:---:|

**2. ¿Qué ocurrió realmente? (Resultado observado)**

El sistema bloqueó el acceso del usuario `locked_out_user` y desplegó inmediatamente el mensaje de error con ícono y fondo rojo: *"Epic sadface: Sorry, this user has been locked out."*, impidiendo el paso al inventario.

**3. Comparación con el resultado esperado**

Coincide exactamente con el resultado esperado. El usuario bloqueado no pudo ingresar y el mensaje fue completamente explícito.

**4. Registro de ejecución por paso**

| # | Paso ejecutado | Resultado observado | Estado | Observación |
|---|---|---|:---:|---|
| 1 | Navegar a `https://www.saucedemo.com/` | Página de login cargada correctamente con todos sus elementos. | **PASS** | Carga correcta |
| 2 | Ingresar `locked_out_user` en Username | El campo muestra `locked_out_user`. | **PASS** | Sin observaciones |
| 3 | Ingresar `secret_sauce` en Password | El campo oculta los caracteres con puntos de contraseña. | **PASS** | Sin observaciones |
| 4 | Clic en el botón Login | El sistema deniega el acceso y permanece en la página de login. | **PASS** | Acceso rechazado |
| 5 | Verificar mensaje de error | Se muestra el mensaje "Epic sadface: Sorry, this user has been locked out." con botón de cierre (X). | **PASS** | Mensaje claro y visible |

**5. Evidencias y Capturas de Pantalla**

| Tipo | Nombre o referencia | Descripción |
|---|---|---|
| Captura | `TC002_locked_out_error.png` | Banner de error mostrado al intentar acceder con `locked_out_user` |

#### Captura adjunta del caso TC-002:

**Figura 2: Rechazo de acceso con mensaje de usuario bloqueado (TC-002)**  
![Mensaje de Usuario Bloqueado](../evidencias/capturas/TC002_locked_out_error.png)

**6. Si el resultado es FAIL**

| Desviación encontrada | No aplica (el caso resultó PASS) |
|---|---|
| Referencia del defecto | N/A |

**7. Observaciones de ejecución**

El control de acceso por estado de usuario responde adecuadamente. No se produce fuga de información ni redirección accidental al catálogo.

---

## Caso TC-003 · Agregar un producto al carrito

### Parte 1 · Diseño del caso de prueba

| Campo | Valor |
|---|---|
| **ID del TC** | TC-003 |
| **Prioridad** | Alta |
| **Título** | Agregar un producto al carrito |
| **Tipo** | Funcional |
| **Módulo** | Catálogo y carrito |
| **Ambiente** | Sitio público de demostración (SauceDemo) |

**1. Objetivo / ¿Qué se quiere validar?**

Comprobar que un producto agregado desde el catálogo se refleja en el contador numérico del carrito y en el contenido de la página `cart.html`.

**2. Precondiciones**

| Precondición | Detalle |
|---|---|
| Estado inicial | Sesión iniciada en SauceDemo y carrito vacío |
| Usuario / permisos | `standard_user` — sesión activa |
| Configuración | Catálogo de productos accesible en `inventory.html` |

**3. Datos de prueba**

| Dato | Valor | Origen | Observación |
|---|---|---|---|
| Producto | Sauce Labs Backpack | Catálogo principal | Primer producto listado |
| Cantidad | 1 unidad | Acción de usuario | Precio listado: $29.99 |

**4. Pasos y resultados esperados**

| # | Paso / acción | Dato utilizado | Resultado esperado |
|---|---|---|---|
| 1 | Estar en la página de catálogo con el carrito vacío | `standard_user` autenticado | Catálogo cargado y carrito sin contador. |
| 2 | Presionar el botón "Add to cart" del producto "Sauce Labs Backpack" | Clic en Add to cart | El texto del botón cambia a "Remove" con texto rojo. |
| 3 | Verificar el ícono del carrito en el encabezado | Observación visual | El ícono del carrito muestra un badge rojo con el número "1". |
| 4 | Presionar el ícono del carrito para ingresar a `cart.html` | Clic en el carrito | Se muestra la página "Your Cart". |
| 5 | Verificar el contenido de la lista del carrito | Observación visual | Aparece "Sauce Labs Backpack" con cantidad 1 y precio $29.99. |

**5. Criterio de éxito**

El producto aparece en el carrito con cantidad 1, precio correcto y el contador del carrito muestra 1.

---

### Parte 2 · Ejecución de la prueba

| Campo | Valor |
|---|---|
| **ID del TC** | TC-003 |
| **Ejecutado por** | Miguel Mirkof Becerra Guzman |
| **Fecha** | 20/10/2026 |
| **Hora** | 21:40 |
| **Ambiente** | Sitio público de demostración (Google Chrome / Windows) |
| **Versión** | SauceDemo v1 |

**1. Resultado de la ejecución**

| ☑ PASS | ☐ FAIL | ☐ BLOCKED | ☐ NOT RUN |
|:---:|:---:|:---:|:---:|

**2. ¿Qué ocurrió realmente? (Resultado observado)**

Al presionar "Add to cart" en "Sauce Labs Backpack", el botón cambió inmediatamente a "Remove" y apareció el badge rojo con el número 1 en el carrito. Al ingresar a `cart.html`, el producto se muestra correctamente listado con QTY 1 y precio de $29.99.

**3. Comparación con el resultado esperado**

Coincide plenamente con el resultado esperado. La actualización reactiva del badge y el almacenamiento en el carrito se ejecutaron sin fallos.

**4. Registro de ejecución por paso**

| # | Paso ejecutado | Resultado observado | Estado | Observación |
|---|---|---|:---:|---|
| 1 | Sesión activa en `inventory.html` con carrito vacío | Catálogo visible, sin badge en carrito. | **PASS** | Estado inicial verificado |
| 2 | Clic en "Add to cart" de Sauce Labs Backpack | El botón cambia a "Remove" con texto blanco/borde rojo. | **PASS** | Cambio visual inmediato |
| 3 | Verificar contador del carrito | El badge numérico rojo muestra el valor "1". | **PASS** | Contador reactivo actualizado |
| 4 | Clic en el ícono del carrito | Redirige exitosamente a `cart.html` con título "Your Cart". | **PASS** | Navegación exitosa |
| 5 | Verificar detalle del ítem en carrito | Aparece "Sauce Labs Backpack", QTY 1, precio $29.99 y botón Remove. | **PASS** | Producto verificado en lista |

**5. Evidencias y Capturas de Pantalla**

| Tipo | Nombre o referencia | Descripción |
|---|---|---|
| Captura | `TC003_cart_badge.png` | Catálogo con botón Remove y badge "1" en el carrito |
| Captura | `TC003_cart_page.png` | Página del carrito con el producto agregado y precio $29.99 |

#### Capturas adjuntas del caso TC-003:

**Figura 3.1: Catálogo con badge de carrito en "1" (TC-003)**  
![Badge de Carrito](../evidencias/capturas/TC003_cart_badge.png)

**Figura 3.2: Vista del carrito con el producto agregado (TC-003)**  
![Página de Carrito](../evidencias/capturas/TC003_cart_page.png)

**6. Si el resultado es FAIL**

| Desviación encontrada | No aplica (el caso resultó PASS) |
|---|---|
| Referencia del defecto | N/A |

**7. Observaciones de ejecución**

El estado del carrito persiste correctamente en el almacenamiento del navegador (sessionStorage / localStorage) durante la navegación entre páginas.

---

## Caso TC-004 · Eliminar un producto del carrito

### Parte 1 · Diseño del caso de prueba

| Campo | Valor |
|---|---|
| **ID del TC** | TC-004 |
| **Prioridad** | Media |
| **Título** | Eliminar un producto del carrito |
| **Tipo** | Funcional |
| **Módulo** | Catálogo y carrito |
| **Ambiente** | Sitio público de demostración (SauceDemo) |

**1. Objetivo / ¿Qué se quiere validar?**

Comprobar que un producto puede eliminarse del carrito y que el contador se actualiza correctamente hasta desaparecer al quedar vacío.

**2. Precondiciones**

| Precondición | Detalle |
|---|---|
| Estado inicial | Sesión iniciada en SauceDemo con el producto "Sauce Labs Backpack" dentro del carrito |
| Usuario / permisos | `standard_user` — sesión activa |
| Configuración | En la página `cart.html` con al menos 1 producto |

**3. Datos de prueba**

| Dato | Valor | Origen | Observación |
|---|---|---|---|
| Producto a eliminar | Sauce Labs Backpack | Producto previamente agregado | Debe eliminarse completamente |

**4. Pasos y resultados esperados**

| # | Paso / acción | Dato utilizado | Resultado esperado |
|---|---|---|---|
| 1 | Estar en la página `cart.html` con el producto en la lista | Producto en carrito | Se visualiza el ítem con su botón Remove. |
| 2 | Presionar el botón "Remove" del producto | Clic en Remove | El producto desaparece de la lista del carrito. |
| 3 | Verificar el ícono del carrito en el encabezado | Observación visual | El badge rojo desaparece del ícono del carrito. |
| 4 | Presionar "Continue Shopping" para volver al catálogo | Clic en botón | Redirige a la página `inventory.html`. |
| 5 | Verificar el botón del producto en el catálogo | Observación visual | El botón de "Sauce Labs Backpack" vuelve a mostrar "Add to cart". |

**5. Criterio de éxito**

El producto se elimina del carrito, el contador desaparece y el catálogo vuelve a ofrecer "Add to cart".

---

### Parte 2 · Ejecución de la prueba

| Campo | Valor |
|---|---|
| **ID del TC** | TC-004 |
| **Ejecutado por** | Miguel Mirkof Becerra Guzman |
| **Fecha** | 20/10/2026 |
| **Hora** | 21:42 |
| **Ambiente** | Sitio público de demostración (Google Chrome / Windows) |
| **Versión** | SauceDemo v1 |

**1. Resultado de la ejecución**

| ☑ PASS | ☐ FAIL | ☐ BLOCKED | ☐ NOT RUN |
|:---:|:---:|:---:|:---:|

**2. ¿Qué ocurrió realmente? (Resultado observado)**

Al presionar "Remove" en la página del carrito, el ítem "Sauce Labs Backpack" fue eliminado instantáneamente de la lista y el contador numérico del carrito desapareció. Al regresar al catálogo, el botón correspondiente volvió al estado original "Add to cart".

**3. Comparación con el resultado esperado**

Coincide totalmente con el resultado esperado. La eliminación fue reactiva y limpia.

**4. Registro de ejecución por paso**

| # | Paso ejecutado | Resultado observado | Estado | Observación |
|---|---|---|:---:|---|
| 1 | Verificar producto en `cart.html` | Se visualiza Sauce Labs Backpack y badge con "1". | **PASS** | Estado inicial verificado |
| 2 | Clic en botón "Remove" | El producto desaparece inmediatamente de la lista. | **PASS** | Eliminación reactiva |
| 3 | Verificar contador del carrito | El badge numérico rojo desaparece del ícono del carrito. | **PASS** | Contador actualizado |
| 4 | Clic en "Continue Shopping" | Redirige a `inventory.html`. | **PASS** | Navegación correcta |
| 5 | Verificar botón en catálogo | El botón de Sauce Labs Backpack muestra nuevamente "Add to cart". | **PASS** | Estado del catálogo sincronizado |

**5. Evidencias y Capturas de Pantalla**

| Tipo | Nombre o referencia | Descripción |
|---|---|---|
| Captura | `TC004_empty_cart.png` | Carrito vacío tras presionar Remove, sin ítems ni badge |

#### Captura adjunta del caso TC-004:

**Figura 4: Carrito de compras vacío tras eliminar el producto (TC-004)**  
![Carrito Vacío](../evidencias/capturas/TC004_empty_cart.png)

**6. Si el resultado es FAIL**

| Desviación encontrada | No aplica (el caso resultó PASS) |
|---|---|
| Referencia del defecto | N/A |

**7. Observaciones de ejecución**

El ciclo de agregar y remover ítems funciona de manera consistente en ambas direcciones (desde catálogo y desde carrito).

---

## Caso TC-005 · Validar campos obligatorios en el checkout

### Parte 1 · Diseño del caso de prueba

| Campo | Valor |
|---|---|
| **ID del TC** | TC-005 |
| **Prioridad** | Alta |
| **Título** | Validar campos obligatorios en el checkout |
| **Tipo** | Negativa / Funcional |
| **Módulo** | Checkout |
| **Ambiente** | Sitio público de demostración (SauceDemo) |

**1. Objetivo / ¿Qué se quiere validar?**

Comprobar que el formulario de información del checkout exige nombre, apellido y código postal antes de continuar, impidiendo compras con datos incompletos.

**2. Precondiciones**

| Precondición | Detalle |
|---|---|
| Estado inicial | Sesión iniciada en SauceDemo con el producto "Sauce Labs Backpack" dentro del carrito |
| Usuario / permisos | `standard_user` — sesión activa |
| Configuración | En la página `cart.html` y avanzar a `checkout-step-one.html` |

**3. Datos de prueba**

| Dato | Valor | Origen | Observación |
|---|---|---|---|
| First Name | *(campo vacío)* | Prueba negativa | Se deja en blanco intencionalmente |
| Last Name | *(campo vacío)* | Prueba negativa | Se deja en blanco intencionalmente |
| Zip/Postal Code | *(campo vacío)* | Prueba negativa | Se deja en blanco intencionalmente |

**4. Pasos y resultados esperados**

| # | Paso / acción | Dato utilizado | Resultado esperado |
|---|---|---|---|
| 1 | Estar en `cart.html` con un producto y presionar "Checkout" | Clic en Checkout | Redirige a la página `checkout-step-one.html`. |
| 2 | Verificar los campos del formulario | Observación visual | Se muestran los campos First Name, Last Name y Zip/Postal Code vacíos. |
| 3 | Dejar los tres campos vacíos sin ingresar texto | Sin datos | Los campos permanecen en blanco. |
| 4 | Presionar el botón "Continue" | Clic en Continue | El sistema no avanza y muestra un mensaje de error en un banner rojo. |
| 5 | Verificar el mensaje de validación desplegado | Observación visual | Se muestra `Error: First Name is required` y los campos se marcan con bordes rojos. |

**5. Criterio de éxito**

El sistema impide continuar al resumen de compra y despliega el mensaje de error indicando que el primer campo obligatorio es requerido.

---

### Parte 2 · Ejecución de la prueba

| Campo | Valor |
|---|---|
| **ID del TC** | TC-005 |
| **Ejecutado por** | Miguel Mirkof Becerra Guzman |
| **Fecha** | 20/10/2026 |
| **Hora** | 21:45 |
| **Ambiente** | Sitio público de demostración (Google Chrome / Windows) |
| **Versión** | SauceDemo v1 |

**1. Resultado de la ejecución**

| ☑ PASS | ☐ FAIL | ☐ BLOCKED | ☐ NOT RUN |
|:---:|:---:|:---:|:---:|

**2. ¿Qué ocurrió realmente? (Resultado observado)**

Al presionar "Continue" con los campos en blanco, el sistema impidió el avance a `checkout-step-two.html`, mantuvo la página actual y mostró el mensaje *"Error: First Name is required"* con íconos de advertencia y bordes de entrada en color rojo.

**3. Comparación con el resultado esperado**

Coincide con el resultado esperado. El bloqueo fue efectivo y la notificación clara.

**4. Registro de ejecución por paso**

| # | Paso ejecutado | Resultado observado | Estado | Observación |
|---|---|---|:---:|---|
| 1 | Presionar Checkout desde `cart.html` | Redirige a `checkout-step-one.html` con título "Checkout: Your Information". | **PASS** | Transición al checkout |
| 2 | Verificar presencia de formulario | Campos First Name, Last Name, Zip/Postal Code visibles y vacíos. | **PASS** | Formulario listo |
| 3 | Dejar los campos sin texto | Campos en blanco. | **PASS** | Intencional para validación |
| 4 | Clic en botón Continue | El sistema bloquea el avance y despliega banner de error rojo. | **PASS** | Validación efectiva |
| 5 | Verificar mensaje y estilos | Muestra "Error: First Name is required" e íconos de error en cada campo. | **PASS** | Mensaje claro y específico |

**5. Evidencias y Capturas de Pantalla**

| Tipo | Nombre o referencia | Descripción |
|---|---|---|
| Captura | `TC005_checkout_error.png` | Banner de error y campos resaltados al enviar formulario vacío |

#### Captura adjunta del caso TC-005:

**Figura 5: Validación de campos obligatorios en el checkout (TC-005)**  
![Error en Checkout](../evidencias/capturas/TC005_checkout_error.png)

**6. Si el resultado es FAIL**

| Desviación encontrada | No aplica (el caso resultó PASS) |
|---|---|
| Referencia del defecto | N/A |

**7. Observaciones de ejecución**

El formulario valida secuencialmente los campos requeridos en el orden de lectura (First Name -> Last Name -> Zip/Postal Code). Al corregir cada uno, avanza a validar el siguiente hasta completar los tres.
