# Operadores Aritméticos

## Introducción

Los operadores aritméticos permiten realizar operaciones matemáticas sobre valores numéricos.

Son algunos de los operadores más utilizados en C++ y constituyen la base de cálculos, algoritmos y manipulación de datos.

Las operaciones aritméticas producen expresiones cuyo resultado puede utilizarse para inicializar variables, realizar comparaciones o formar parte de expresiones más complejas.

---

## Operadores disponibles

| Operador | Descripción                    |
| -------- | ------------------------------ |
| `+`      | Suma                           |
| `-`      | Resta                          |
| `*`      | Multiplicación                 |
| `/`      | División                       |
| `%`      | Módulo (resto de una división) |

---

## Operador de suma (`+`)

Permite sumar dos operandos.

```cpp
int resultado {5 + 3};
```

Resultado:

```text
8
```

---

## Operador de resta (`-`)

Permite calcular la diferencia entre dos valores.

```cpp
int resultado {10 - 4};
```

Resultado:

```text
6
```

---

## Operador de multiplicación (`*`)

Permite multiplicar dos operandos.

```cpp
int resultado {5 * 4};
```

Resultado:

```text
20
```

---

## Operador de división (`/`)

Permite dividir un operando entre otro.

```cpp
int resultado {20 / 4};
```

Resultado:

```text
5
```

---

## División entera

Cuando ambos operandos son enteros, el resultado también será entero.

```cpp
int resultado {5 / 2};
```

Resultado:

```text
2
```

Proceso:

```text
5 / 2 = 2.5
↓
Se descarta la parte decimal
↓
2
```

---

## División en coma flotante

Si al menos uno de los operandos es de tipo flotante, el resultado conserva la parte decimal.

```cpp
double resultado {5.0 / 2};
```

Resultado:

```text
2.5
```

También:

```cpp
double resultado {5 / 2.0};
```

Resultado:

```text
2.5
```

---

## Operador módulo (`%`)

Devuelve el resto de una división entera.

```cpp
int resultado {10 % 3};
```

Resultado:

```text
1
```

Proceso:

```text
10 / 3 = 3
3 * 3 = 9
10 - 9 = 1
```

---

## Restricción del operador módulo

El operador `%` únicamente puede utilizarse con tipos enteros.

Correcto:

```cpp
int resto {10 % 3};
```

Incorrecto:

```cpp
double resto {10.5 % 3.0};
```

Resultado:

```text
Error de compilacion
```

---

## Uso común del operador módulo

Determinar si un número es par:

```cpp
int numero {8};

bool es_par {numero % 2 == 0};
```

Resultado:

```text
true
```

Determinar si es impar:

```cpp
bool es_impar {numero % 2 != 0};
```

---

## Operadores unarios

### Operador unario positivo (`+`)

Indica explícitamente un valor positivo.

```cpp
int numero {+10};
```

Resultado:

```text
10
```

---

### Operador unario negativo (`-`)

Invierte el signo de un valor.

```cpp
int numero {-10};
```

Resultado:

```text
-10
```

También puede aplicarse a variables:

```cpp
int numero {5};

int resultado {-numero};
```

Resultado:

```text
-5
```

---

## Expresiones combinadas

Los operadores pueden combinarse.

```cpp
int resultado {5 + 3 * 2};
```

Evaluación:

```text
3 * 2 = 6
5 + 6 = 11
```

Resultado:

```text
11
```

---

## Uso de paréntesis

Los paréntesis permiten modificar el orden de evaluación.

```cpp
int resultado {(5 + 3) * 2};
```

Evaluación:

```text
5 + 3 = 8
8 * 2 = 16
```

Resultado:

```text
16
```

---

## Promoción de tipos

Cuando participan diferentes tipos numéricos, C++ realiza conversiones automáticas.

```cpp
int entero {10};
double decimal {3.5};

auto resultado {entero + decimal};
```

Resultado:

```text
13.5
```

Tipo resultante:

```text
double
```

Representación:

```text
int + double
      │
      ▼
double
```

---

## Desbordamiento (Overflow)

Los tipos enteros tienen un rango limitado.

```cpp
int numero {2147483647};

numero = numero + 1;
```

El resultado depende de la implementación y puede producir comportamiento inesperado.

Por esta razón es importante conocer los límites de cada tipo numérico.

---

## Ejemplo completo

```cpp
#include <iostream>

int main()
{
    int numero_a {10};
    int numero_b {3};

    std::cout << "Suma: " << numero_a + numero_b << '\n';
    std::cout << "Resta: " << numero_a - numero_b << '\n';
    std::cout << "Multiplicacion: " << numero_a * numero_b << '\n';
    std::cout << "Division: " << numero_a / numero_b << '\n';
    std::cout << "Modulo: " << numero_a % numero_b << '\n';

    return 0;
}
```

Salida:

```text
Suma: 13
Resta: 7
Multiplicacion: 30
Division: 3
Modulo: 1
```

---

## Error común: división por cero

Código:

```cpp
int resultado {10 / 0};
```

Resultado:

```text
Comportamiento indefinido
```

La división por cero debe evitarse siempre.

Ejemplo seguro:

```cpp
if (divisor != 0)
{
    resultado = numero / divisor;
}
```

---

## Error común: esperar decimales en una división entera

Código:

```cpp
int resultado {5 / 2};
```

Resultado:

```text
2
```

Muchos principiantes esperan:

```text
2.5
```

Para obtenerlo es necesario utilizar tipos de coma flotante:

```cpp
double resultado {5.0 / 2};
```

---

## Precedencia de operadores aritméticos

| Prioridad | Operadores             |
| --------- | ---------------------- |
| Alta      | `+` unario, `-` unario |
| Media     | `*`, `/`, `%`          |
| Baja      | `+`, `-`               |

Ejemplo:

```cpp
5 + 4 * 2
```

Resultado:

```text
13
```

porque:

```text
4 * 2 = 8
5 + 8 = 13
```

---

## Buenas prácticas

* Utilizar paréntesis cuando mejoren la claridad.
* Evitar expresiones excesivamente complejas.
* Comprobar divisiones antes de dividir por cero.
* Utilizar nombres descriptivos para las variables.
* No asumir que una división entera conservará decimales.

---

## Resumen

* Los operadores aritméticos permiten realizar cálculos matemáticos.
* C++ dispone de suma, resta, multiplicación, división y módulo.
* La división entre enteros elimina la parte decimal.
* El operador `%` devuelve el resto de una división entera.
* `%` solo puede utilizarse con tipos enteros.
* Los paréntesis permiten controlar el orden de evaluación.
* C++ realiza promociones automáticas de tipos cuando es necesario.
* La división por cero debe evitarse siempre.
* La multiplicación, división y módulo tienen mayor precedencia que la suma y la resta.
* Los operadores aritméticos forman la base de la mayoría de las expresiones numéricas.
