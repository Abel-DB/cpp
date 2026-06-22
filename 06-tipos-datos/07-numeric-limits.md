# Límites Numéricos

## Introducción

Los tipos numéricos poseen una capacidad limitada de almacenamiento.

Por ejemplo:

```cpp
int
```

no puede representar cualquier entero imaginable.

Existe un valor mínimo y un valor máximo que puede almacenar.

Comprender estos límites es importante para evitar errores relacionados con:

```text
Overflow
Underflow
Pérdida de precisión
```

---

## ¿Por Qué Existen Límites?

La memoria es finita.

Cada tipo ocupa una cantidad determinada de memoria.

Por ejemplo:

```cpp
sizeof(int)
```

puede producir:

```text
4
```

lo que indica que el tipo ocupa 4 bytes en esa plataforma.

Con una cantidad finita de memoria solo es posible representar una cantidad finita de valores.

---

## Consultar Límites

La biblioteca estándar proporciona la clase:

```cpp
std::numeric_limits
```

definida en:

```cpp
#include <limits>
```

---

## Valor Máximo

Sintaxis:

```cpp
std::numeric_limits<T>::max()
```

Ejemplo:

```cpp
std::numeric_limits<int>::max()
```

---

## Valor Mínimo

Sintaxis:

```cpp
std::numeric_limits<T>::min()
```

Ejemplo:

```cpp
std::numeric_limits<int>::min()
```

---

## Ejemplo Básico

```cpp
#include <iostream>
#include <limits>

int main()
{
    std::cout << std::numeric_limits<int>::min() << '\n';
    std::cout << std::numeric_limits<int>::max() << '\n';

    return 0;
}
```

Posible salida:

```text
-2147483648
2147483647
```

---

# Límites de int

```cpp
std::numeric_limits<int>::min()
```

↓

Valor mínimo representable.

---

```cpp
std::numeric_limits<int>::max()
```

↓

Valor máximo representable.

---

## Visualización

```text
int

mínimo
  │
  ▼
[ ............ ]
  ▲
  │
máximo
```

---

# El Caso Especial de float y double

Muchos principiantes esperan que:

```cpp
std::numeric_limits<double>::min()
```

devuelva el número más negativo representable.

No es así.

Para tipos de punto flotante:

```cpp
min()
```

devuelve el menor valor positivo normalizado.

---

Ejemplo:

```cpp
std::numeric_limits<double>::min()
```

Posible resultado:

```text
2.22507e-308
```

---

## Valor Más Negativo

Para obtener el valor más negativo se utiliza:

```cpp
std::numeric_limits<double>::lowest()
```

Posible resultado:

```text
-1.79769e+308
```

---

## Comparación

```cpp
std::numeric_limits<double>::min()
```

↓

Menor valor positivo normalizado.

---

```cpp
std::numeric_limits<double>::lowest()
```

↓

Valor más negativo representable.

---

```cpp
std::numeric_limits<double>::max()
```

↓

Valor más positivo representable.

---

# Overflow

Ocurre cuando un cálculo produce un valor superior al máximo representable.

Ejemplo conceptual:

```cpp
int numero = std::numeric_limits<int>::max();
```

---

Intentar:

```cpp
++numero;
```

produce un resultado que ya no puede representarse correctamente.

---

## Importante

En los enteros con signo (`int`), el overflow produce:

```text
Comportamiento indefinido
```

Esto significa que el estándar no define qué debe ocurrir.

No debe asumirse ningún resultado concreto.

---

# Underflow

Ocurre cuando un cálculo produce un valor inferior al mínimo representable.

Ejemplo conceptual:

```cpp
int numero = std::numeric_limits<int>::min();

--numero;
```

---

En enteros con signo también conduce a:

```text
Comportamiento indefinido
```

---

# Enteros sin Signo

Los tipos:

```cpp
unsigned
```

se comportan de manera diferente.

Ejemplo:

```cpp
unsigned int valor{0};

--valor;
```

Resultado habitual:

```text
Valor máximo representable
```

Este comportamiento está definido por el estándar y se conoce como:

```text
Wrap Around
```

---

# Digits

La constante:

```cpp
std::numeric_limits<T>::digits
```

indica cuántos bits participan en la representación del valor.

Ejemplo:

```cpp
std::numeric_limits<int>::digits
```

Posible resultado:

```text
31
```

---

En una implementación típica:

```text
31 bits para el valor
1 bit para el signo
```

---

## Ejemplo

```cpp
#include <iostream>
#include <limits>

int main()
{
    std::cout << std::numeric_limits<int>::digits << '\n';

    return 0;
}
```

---

# sizeof vs numeric_limits

No deben confundirse.

---

## sizeof

Responde:

```text
¿Cuánta memoria ocupa?
```

Ejemplo:

```cpp
sizeof(int)
```

---

## numeric_limits

Responde:

```text
¿Cuáles son sus límites?
```

Ejemplo:

```cpp
std::numeric_limits<int>::max()
```

---

## Comparación

```text
sizeof
│
└── Tamaño en memoria
```

```text
numeric_limits
│
└── Rango de valores
```

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <limits>

int main()
{
    std::cout << "int min: " << std::numeric_limits<int>::min() << '\n';
    std::cout << "int max: " << std::numeric_limits<int>::max() << '\n';
    std::cout << "double lowest: " << std::numeric_limits<double>::lowest() << '\n';
    std::cout << "double max: " << std::numeric_limits<double>::max() << '\n';

    return 0;
}
```

---

# Buenas Prácticas

## No Escribir Límites Manualmente

Evitar:

```cpp
2147483647
```

como constante mágica.

---

Preferir:

```cpp
std::numeric_limits<int>::max()
```

---

## Verificar Rangos

Especialmente cuando se trabaja con:

- Datos externos.
- Archivos.
- Cálculos numéricos.
- Contadores grandes.

---

## Comprender el Overflow

No asumir que un entero puede crecer indefinidamente.

Todo tipo tiene límites.

---

# Error Común

Pensar que:

```cpp
std::numeric_limits<double>::min()
```

significa:

```text
El valor más negativo
```

Para tipos de punto flotante esto es incorrecto.

Debe utilizarse:

```cpp
lowest()
```

---

# Visualización General

```text
Tipo
 │
 ▼
Tamaño
 │
 ▼
Cantidad de memoria
 │
 ▼
Rango de valores
 │
 ▼
Mínimo y máximo
```

---

## Resumen

- Todos los tipos numéricos poseen límites.
- La biblioteca estándar permite consultarlos mediante `std::numeric_limits`.
- `max()` devuelve el valor máximo representable.
- Para enteros, `min()` devuelve el valor mínimo representable.
- Para tipos de punto flotante, `min()` devuelve el menor valor positivo normalizado.
- `lowest()` devuelve el valor más negativo representable.
- El overflow de enteros con signo produce comportamiento indefinido.
- `sizeof()` informa sobre memoria; `numeric_limits` informa sobre rangos.
- Comprender los límites es fundamental para escribir programas correctos y robustos.
