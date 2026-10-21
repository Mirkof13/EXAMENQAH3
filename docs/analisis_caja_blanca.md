# Análisis de Caja Blanca

**Función analizada:** `validar_compra`  
**Fecha:** 20/10/2026  
**Criterio de cobertura:** Cobertura de decisiones  
**Autor:** Miguel Mirkof Becerra Guzman — UNIFRANZ  
**Repositorio:** [https://github.com/Mirkof13/EXAMENQAH3.git](https://github.com/Mirkof13/EXAMENQAH3.git)

---

## Código analizado

La función recibe la edad, si la cuenta está activa, el saldo y el monto de la compra, y devuelve uno de cuatro textos posibles: compra no permitida por edad, compra no permitida por cuenta, compra aprobada o compra rechazada.

```python
def validar_compra(edad, cuenta_activa, saldo, monto):
    if edad < 18:
        return "Compra no permitida: edad"

    if not cuenta_activa:
        return "Compra no permitida: cuenta"

    if saldo >= monto and monto > 0:
        return "Compra aprobada"

    return "Compra rechazada"
```

### Entradas y salidas

| Parámetro | Tipo | Descripción |
|-----------|------|-------------|
| `edad` | int | Edad del comprador |
| `cuenta_activa` | bool | Estado de la cuenta del usuario |
| `saldo` | float | Saldo disponible del usuario |
| `monto` | float | Monto de la compra a realizar |

| Salida posible | Condición |
|---------------|-----------|
| "Compra no permitida: edad" | `edad < 18` |
| "Compra no permitida: cuenta" | `edad >= 18` y `not cuenta_activa` |
| "Compra aprobada" | `edad >= 18`, `cuenta_activa`, `saldo >= monto` y `monto > 0` |
| "Compra rechazada" | `edad >= 18`, `cuenta_activa`, pero `saldo < monto` o `monto <= 0` |

---

## Decisiones y condiciones simples

El código contiene **3 decisiones** y **4 condiciones simples**. La tercera decisión es compuesta porque une dos condiciones con el operador `and`. Además hay **4 sentencias return** (S1, S2, S3, S4), una por cada salida posible.

| ID | Decisión / Condición | Tipo | Línea |
|----|---------------------|------|-------|
| **D1** | `edad < 18` | Decisión simple | `if edad < 18:` |
| **C1** | `edad < 18` | Condición simple | — |
| **D2** | `not cuenta_activa` | Decisión simple | `if not cuenta_activa:` |
| **C2** | `cuenta_activa` (negada) | Condición simple | — |
| **D3** | `saldo >= monto and monto > 0` | Decisión compuesta | `if saldo >= monto and monto > 0:` |
| **C3** | `saldo >= monto` | Condición simple | Primera parte del `and` |
| **C4** | `monto > 0` | Condición simple | Segunda parte del `and` |

| ID | Sentencia return | Salida |
|----|-----------------|--------|
| **S1** | `return "Compra no permitida: edad"` | D1 = True |
| **S2** | `return "Compra no permitida: cuenta"` | D1 = False, D2 = True |
| **S3** | `return "Compra aprobada"` | D1 = False, D2 = False, D3 = True |
| **S4** | `return "Compra rechazada"` | D1 = False, D2 = False, D3 = False |

---

## Criterio de cobertura y mínimo de casos

### Criterio utilizado: Cobertura de decisiones

La cobertura de decisiones exige que cada decisión tome el resultado **verdadero** y el resultado **falso** al menos una vez. Este criterio incluye la cobertura de sentencias, porque al recorrer todos los resultados de las decisiones se ejecutan los cuatro `return`.

### Cálculo del mínimo

Las decisiones son secuenciales y cada una puede terminar la ejecución, por lo que existen **4 caminos** distintos:

| Camino | D1 | D2 | D3 | Salida |
|--------|----|----|-----|--------|
| 1 | True | — | — | S1: "Compra no permitida: edad" |
| 2 | False | True | — | S2: "Compra no permitida: cuenta" |
| 3 | False | False | True | S3: "Compra aprobada" |
| 4 | False | False | False | S4: "Compra rechazada" |

Un solo caso recorre un único camino, y cada resultado verdadero o falso de D1, D2 y D3 pertenece a alguno de esos caminos, de modo que **el mínimo para el criterio de decisiones es de 4 casos**.

---

## Casos diseñados (3 casos)

Se diseñaron tres casos con valores de entrada concretos:

| ID | edad | cuenta_activa | saldo | monto | Resultado esperado | Decisión cubierta |
|----|------|---------------|-------|-------|-------------------|------------------|
| **CB-01** | 15 | True | 500 | 100 | "Compra no permitida: edad" | D1 = True → S1 |
| **CB-02** | 25 | False | 500 | 100 | "Compra no permitida: cuenta" | D1 = False, D2 = True → S2 |
| **CB-03** | 30 | True | 500 | 200 | "Compra aprobada" | D1 = False, D2 = False, D3 = True → S3 |

### Detalle de cada caso

**CB-01: Menor de edad**
- Entrada: `validar_compra(15, True, 500, 100)`
- La primera decisión `edad < 18` es **verdadera** (15 < 18)
- Se ejecuta S1, retorna *"Compra no permitida: edad"*
- **Cubre:** D1 = True, S1

**CB-02: Cuenta inactiva**
- Entrada: `validar_compra(25, False, 500, 100)`
- D1: `25 < 18` es **falso** → continúa
- D2: `not False` es **verdadero** → se ejecuta S2
- **Cubre:** D1 = False, D2 = True, S2

**CB-03: Compra aprobada**
- Entrada: `validar_compra(30, True, 500, 200)`
- D1: `30 < 18` es **falso** → continúa
- D2: `not True` es **falso** → continúa
- D3: `500 >= 200 and 200 > 0` es **verdadero** → se ejecuta S3
- **Cubre:** D2 = False, D3 = True, S3

---

## Ajuste necesario

Los tres casos **no alcanzan el criterio**. La decisión D3 nunca resulta **falsa** y la sentencia S4 no se ejecuta.

### Cobertura con 3 casos

| Decisión | Resultado True | Resultado False | Cobertura |
|----------|---------------|-----------------|-----------|
| D1 | ✅ CB-01 | ✅ CB-02, CB-03 | 100% |
| D2 | ✅ CB-02 | ✅ CB-03 | 100% |
| D3 | ✅ CB-03 | ❌ No cubierto | 50% |

- Cobertura de decisiones: **5 de 6 resultados** (83.3%)
- Cobertura de sentencias: **3 de 4 return** (75%)

### Caso adicional: CB-04

Se requiere un cuarto caso para cubrir D3 = False y ejecutar S4:

| ID | edad | cuenta_activa | saldo | monto | Resultado esperado | Decisión cubierta |
|----|------|---------------|-------|-------|-------------------|------------------|
| **CB-04** | 30 | True | 50 | 100 | "Compra rechazada" | D3 = False → S4 |

**CB-04: Saldo insuficiente**
- Entrada: `validar_compra(30, True, 50, 100)`
- D1: `30 < 18` es **falso** → continúa
- D2: `not True` es **falso** → continúa
- D3: `50 >= 100` es **falso** → la decisión completa es **falsa** (por short-circuit, no evalúa `monto > 0`)
- Se ejecuta S4, retorna *"Compra rechazada"*
- **Cubre:** D3 = False, S4

### Cobertura con 4 casos (CB-01 a CB-04)

| Decisión | Resultado True | Resultado False | Cobertura |
|----------|---------------|-----------------|-----------|
| D1 | ✅ CB-01 | ✅ CB-02, CB-03, CB-04 | 100% |
| D2 | ✅ CB-02 | ✅ CB-03, CB-04 | 100% |
| D3 | ✅ CB-03 | ✅ CB-04 | 100% |

- **Cobertura de decisiones: 6 de 6 resultados (100%)**
- **Cobertura de sentencias: 4 de 4 return (100%)**

---

## Cobertura de condiciones como complemento

La cobertura de condiciones es un criterio **distinto**: exige que cada condición simple sea verdadera y falsa al menos una vez, y **no equivale a la cobertura de decisiones**.

En Python el operador `and` evalúa `monto > 0` solo cuando `saldo >= monto` es verdadera, por lo que con CB-01 a CB-04 la condición C4 (`monto > 0`) nunca resulta **falsa**.

Se requiere un quinto caso:

| ID | edad | cuenta_activa | saldo | monto | Resultado esperado | Condición cubierta |
|----|------|---------------|-------|-------|-------------------|-------------------|
| **CB-05** | 30 | True | 500 | 0 | "Compra rechazada" | C4 = False (monto > 0 es falso) |

### Cobertura de condiciones con 5 casos

| Condición | True | False | Cobertura |
|-----------|------|-------|-----------|
| C1: `edad < 18` | ✅ CB-01 | ✅ CB-02 | 100% |
| C2: `cuenta_activa` | ✅ CB-01, CB-03 | ✅ CB-02 | 100% |
| C3: `saldo >= monto` | ✅ CB-03, CB-05 | ✅ CB-04 | 100% |
| C4: `monto > 0` | ✅ CB-03 | ✅ CB-05 | 100% |

**El mínimo para cobertura de condiciones en este código es de 5 casos.**

> **Nota:** Como prueba adicional de límites funcionales pueden usarse `edad = 17` y `edad = 18`, `monto = 0` y `saldo` igual al `monto`, aunque no son necesarios para el criterio solicitado.
