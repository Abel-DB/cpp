# signed vs unsigned

## Introducción

Los tipos enteros pueden clasificarse en dos grandes grupos:

```cpp
signed
```

y

```cpp
unsigned
```

La diferencia principal es sencilla:

- Los tipos `signed` pueden representar valores negativos y positivos.
- Los tipos `unsigned` solo pueden representar valores positivos y cero.

Comprender esta diferencia es importante para evitar errores sutiles en comparaciones y operaciones aritméticas.

---

## signed

Un tipo:

```cpp
signed
```

puede almacenar:

```text
Valores negativos
Cero
Valores positivos
```

Ejemplo:

```cpp
signed int temperatura{-10};
```

---

En realidad:

```cpp
int temperatura{-10};
```

es equivalente a:

```cpp
signed int temperatura{-10};
```

porque `int` es `signed` por defecto.

---

## unsigned

Un tipo:

```cpp
unsigned
```

solo puede almacenar:

```text
Cero
Valores positivos
```

Ejemplo:

```cpp
unsigned int cantidad{100};
```

---

Intentar representar un valor negativo con un tipo unsigned produce conversiones que normalmente no representan lo que el programador espera.

---

## Comparación Conceptual

```text
signed

Negativos
    │
    ▼
    0
    │
    ▼
Positivos
```

---

```text
unsigned

0
│
▼
Positivos
```

---

## Tamaño en Memoria

Habitualmente:

```cpp
sizeof(int)
```

y

```cpp
sizeof(unsigned int)
```

producen el mismo resultado.

Por ejemplo, en muchos sistemas modernos:

```text
4 bytes
```

Sin embargo, el estándar no obliga a que tengan un tamaño concreto.

---

## Diferencia de Rango

Como `unsigned` no necesita representar números negativos, puede dedicar todo su rango a valores positivos.

Por ello:

```cpp
unsigned int
```

puede representar valores positivos mayores que:

```cpp
int
```

cuando ambos tienen el mismo tamaño.

---

## Consultar los Límites

La forma correcta de conocer los límites reales de un tipo es utilizar:

```cpp
#include <limits>
```

Ejemplo:

```cpp
std::numeric_limits<int>::min()
std::numeric_limits<int>::max()
```

---

```cpp
std::numeric_limits<unsigned int>::min()
std::numeric_limits<unsigned int>::max()
```

---

## Ejemplo

```cpp
#include <iostream>
#include <limits>

int main()
{
    std::cout << std::numeric_limits<int>::min() << '\n';
    std::cout << std::numeric_limits<int>::max() << '\n';
    std::cout << std::numeric_limits<unsigned int>::max() << '\n';

    return 0;
}
```

---

# Problema Común

Muchos principiantes piensan:

```text
unsigned = mejor
```

porque puede representar números positivos más grandes.

En la práctica esto no suele ser cierto.

Con frecuencia, los problemas causados por las conversiones entre tipos `signed` y `unsigned` superan cualquier posible beneficio.

---

## Ejemplo de Conversión Inesperada

```cpp
unsigned int cantidad{-1};
```

El resultado no será:

```text
-1
```

porque un tipo unsigned no puede representar valores negativos.

Se producirá una conversión a un valor positivo grande.

---

## Underflow

Ejemplo:

```cpp
unsigned int cantidad{0};

--cantidad;
```

Resultado habitual:

```text
4294967295
```

(en sistemas donde `unsigned int` ocupa 4 bytes).

---

Visualización:

```text
0
│
▼
Intentar restar 1
│
▼
Máximo valor representable
```

Este comportamiento se conoce como:

```text
Wrap Around
```

---

## Comparaciones Peligrosas

Ejemplo:

```cpp
int a{-1};
unsigned int b{1};
```

---

```cpp
if (a < b)
{
}
```

Muchos programadores esperan:

```text
true
```

Sin embargo, las conversiones implícitas realizadas por el compilador pueden producir resultados inesperados.

---

## Regla Práctica

Evitar mezclar:

```cpp
signed
```

y

```cpp
unsigned
```

en operaciones y comparaciones.

---

# size_t

Más adelante encontrarás el tipo:

```cpp
std::size_t
```

o simplemente:

```cpp
size_t
```

después de incluir los encabezados apropiados.

Este tipo suele utilizarse para:

- Tamaños.
- Cantidades de elementos.
- Índices de contenedores.

Ejemplo:

```cpp
std::size_t longitud{100};
```

En la mayoría de plataformas modernas es un tipo unsigned.

---

# Recomendación Moderna

En código moderno suele recomendarse:

```cpp
int
```

como tipo entero por defecto.

Ejemplo:

```cpp
int contador{0};
```

---

Utilizar:

```cpp
unsigned
```

solo cuando exista una razón clara para hacerlo.

---

## Buenas Prácticas

### Utilizar int por Defecto

Preferir:

```cpp
int contador{0};
```

---

### Evitar Mezclar signed y unsigned

Evitar:

```cpp
int a{-1};
unsigned int b{1};
```

en comparaciones y operaciones.

---

### Consultar los Límites Reales

Utilizar:

```cpp
std::numeric_limits
```

en lugar de asumir tamaños o rangos concretos.

---

### Comprender el Wrap Around

Recordar que:

```cpp
unsigned
```

no puede representar valores negativos.

Por ello ciertas restas pueden producir resultados sorprendentes.

---

## Error Común

Pensar que:

```cpp
unsigned
```

es simplemente:

```text
Un int más grande
```

No es así.

La diferencia fundamental es:

```text
Permite o no permite valores negativos.
```

---

## Visualización General

```text
signed
│
├── Negativos
├── Cero
└── Positivos
```

---

```text
unsigned
│
├── Cero
└── Positivos
```

---

## Resumen

- Los tipos `signed` permiten valores negativos y positivos.
- Los tipos `unsigned` solo permiten valores positivos y cero.
- Ambos suelen ocupar la misma cantidad de memoria.
- `unsigned` dispone de un rango positivo mayor cuando ambos tipos tienen el mismo tamaño.
- Mezclar tipos signed y unsigned puede producir resultados inesperados.
- El comportamiento de wrap around es una fuente frecuente de errores.
- En código moderno suele preferirse `int` como tipo entero por defecto.
- `size_t` se utiliza habitualmente para tamaños e índices.
- Comprender esta diferencia ayuda a evitar errores difíciles de detectar.
