# Escenarios Gherkin (BDD)

**Aplicación bajo prueba:** Swag Labs — [https://www.saucedemo.com/](https://www.saucedemo.com/)  
**Fecha:** 20/10/2026  
**Autor:** Miguel Mirkof Becerra Guzman — UNIFRANZ  
**Repositorio:** [https://github.com/Mirkof13/EXAMENQAH3.git](https://github.com/Mirkof13/EXAMENQAH3.git)

> Gherkin describe el comportamiento esperado con las palabras clave `Feature`, `Scenario`, `Given`, `When` y `Then`, y admite `And` y `But` para encadenar pasos. Por sí solo no automatiza las pruebas.

---

## Feature 1: Inicio de sesión

```gherkin
Feature: Inicio de sesión en Swag Labs
  Como usuario de SauceDemo
  Quiero iniciar sesión con mis credenciales
  Para acceder al catálogo de productos

  Scenario: Acceso exitoso con usuario estándar
    Given que estoy en la página de login de SauceDemo
    And los campos de usuario y contraseña están vacíos
    When ingreso "standard_user" en el campo Username
    And ingreso "secret_sauce" en el campo Password
    And hago clic en el botón "Login"
    Then debería ser redirigido a la página de inventario
    And debería ver el catálogo con los productos disponibles

  Scenario: Acceso denegado con usuario bloqueado
    Given que estoy en la página de login de SauceDemo
    And no tengo una sesión activa
    When ingreso "locked_out_user" en el campo Username
    And ingreso "secret_sauce" en el campo Password
    And hago clic en el botón "Login"
    Then debería permanecer en la página de login
    And debería ver el mensaje de error "Epic sadface: Sorry, this user has been locked out."
    But no debería acceder al catálogo de productos
```

---

## Feature 2: Carrito de compras

```gherkin
Feature: Gestión del carrito de compras
  Como usuario autenticado en SauceDemo
  Quiero agregar y eliminar productos del carrito
  Para gestionar mi compra antes del checkout

  Scenario: Agregar un producto al carrito
    Given que estoy autenticado como "standard_user"
    And estoy en la página de inventario
    And el carrito está vacío
    When hago clic en "Add to cart" del producto "Sauce Labs Backpack"
    Then el botón debería cambiar a "Remove"
    And el badge del carrito debería mostrar "1"
    And al acceder al carrito debería ver "Sauce Labs Backpack" con precio "$29.99"

  Scenario: Eliminar un producto del carrito
    Given que estoy autenticado como "standard_user"
    And tengo el producto "Sauce Labs Backpack" en el carrito
    And estoy en la página del carrito
    When hago clic en el botón "Remove" del producto
    Then el producto debería desaparecer del carrito
    And el carrito debería estar vacío
    And el badge del carrito debería desaparecer
```

---

## Feature 3: Validación del checkout

```gherkin
Feature: Validación de campos obligatorios en el checkout
  Como usuario de SauceDemo con productos en el carrito
  Quiero que el sistema valide los campos obligatorios
  Para evitar enviar información incompleta

  Scenario: Error al intentar continuar con campos vacíos
    Given que estoy autenticado como "standard_user"
    And tengo al menos un producto en el carrito
    And estoy en la página de checkout (paso 1)
    When dejo los campos First Name, Last Name y Zip Code vacíos
    And hago clic en "Continue"
    Then debería ver el mensaje de error "Error: First Name is required"
    And no debería avanzar al paso 2 del checkout
    And los campos con error deberían resaltarse con borde rojo

  Scenario: Error al ingresar solo el nombre
    Given que estoy autenticado como "standard_user"
    And tengo al menos un producto en el carrito
    And estoy en la página de checkout (paso 1)
    When ingreso "Juan" en el campo First Name
    But dejo los campos Last Name y Zip Code vacíos
    And hago clic en "Continue"
    Then debería ver el mensaje de error "Error: Last Name is required"
    And no debería avanzar al paso 2 del checkout
```

---

## Resumen de escenarios

| Feature | Escenario | Tipo | Palabras clave usadas |
|---------|-----------|------|----------------------|
| Inicio de sesión | Acceso exitoso con usuario estándar | Exitoso | Given, And, When, Then |
| Inicio de sesión | Acceso denegado con usuario bloqueado | Error / Alternativo | Given, And, When, Then, But |
| Carrito de compras | Agregar un producto al carrito | Exitoso | Given, And, When, Then |
| Carrito de compras | Eliminar un producto del carrito | Exitoso | Given, And, When, Then |
| Checkout | Error al intentar continuar con campos vacíos | Error / Negativa | Given, And, When, Then |
| Checkout | Error al ingresar solo el nombre | Error / Alternativo | Given, When, But, And, Then |

> **Nota:** Los escenarios Gherkin describen el comportamiento esperado de forma clara y verificable, y sirven de puente entre los casos de prueba manuales y una futura automatización con herramientas como Cucumber o Behave.
