# int

## Introducción

El tipo `int` se utiliza para almacenar números enteros.

Un número entero es un número sin parte decimal.

Ejemplos:

```cpp
10
-5
0
250
```

No son enteros:

```cpp
10.5
3.14
0.25
```

`int` es uno de los tipos fundamentales más utilizados en C++.

---

## ¿Qué Significa int?

La palabra:

```cpp
int
```

proviene de:

```text
integer
```

que significa:

```text
entero
```

---

## Declaración

Ejemplo:

```cpp
int edad_usuario{25};
```

Representación:

```text
Nombre : edad_usuario
Tipo   : int
Valor  : 25
```

---

## Uso Básico

```cpp
#include <iostream>

int main()
{
    int edad_usuario{25};

    std::cout << edad_usuario << '\n';

    return 0;
}
```

Salida:

```text
25
```

---

## Valores Positivos

```cpp
int cantidad_productos{150};
```

---

## Valores Negativos

```cpp
int temperatura{-5};
```

---

## Cero

```cpp
int contador{0};
```

---

## Operaciones con int

### Suma

```cpp
int resultado{10 + 5};
```

Resultado:

```text
15
```

---

### Resta

```cpp
int resultado{10 - 5};
```

Resultado:

```text
5
```

---

### Multiplicación

```cpp
int resultado{4 * 3};
```

Resultado:

```text
12
```

---

### División

```cpp
int resultado{10 / 2};
```

Resultado:

```text
5
```

---

## División Entera

Cuando ambos operandos son enteros, el resultado también será un entero.

Ejemplo:

```cpp
int resultado{10 / 3};
```

Resultado:

```text
3
```

Proceso:

```text
10 ÷ 3 = 3.333...

Resultado almacenado = 3
```

La parte decimal se descarta.

---

## Comparación

```cpp
int resultado{5 / 2};
```

Resultado:

```text
2
```

---

```cpp
double resultado{5.0 / 2};
```

Resultado:

```text
2.5
```

---

## Operador Módulo

Permite obtener el resto de una división entera.

Operador:

```cpp
%
```

Ejemplo:

```cpp
int resto{10 % 3};
```

Resultado:

```text
1
```

Proceso:

```text
10 = (3 × 3) + 1
```

---

## Comprobar si un Número es Par

```cpp
int numero{10};

bool es_par{numero % 2 == 0};
```

Resultado:

```text
true
```

---

## Modificación de Variables

```cpp
int edad_usuario{20};

edad_usuario = 25;
```

Representación:

```text
Antes

edad_usuario
     │
     ▼
    20

Después

edad_usuario
     │
     ▼
    25
```

---

## Incremento

```cpp
int contador{0};

++contador;
```

Resultado:

```text
1
```

---

## Decremento

```cpp
int contador{10};

--contador;
```

Resultado:

```text
9
```

---

## Tamaño en Memoria

El estándar de C++ no fija un tamaño exacto para `int`.

Únicamente garantiza que:

```text
sizeof(short) <= sizeof(int) <= sizeof(long)
```

En la mayoría de sistemas modernos:

```text
int = 4 bytes (32 bits)
```

pero esto no debe asumirse como una regla universal.

---

## Rango de Valores

Si un `int` ocupa 32 bits, normalmente puede almacenar aproximadamente:

```text
-2,147,483,648
```

hasta:

```text
2,147,483,647
```

Más adelante aprenderemos a consultar estos límites utilizando:

```cpp
std::numeric_limits
```

---

## Representación Conceptual

```cpp
int edad_usuario{25};
```

```text
Memoria

┌─────────────┐
│     25      │
└─────────────┘
```

---

## Desbordamiento (Overflow)

Un entero tiene capacidad limitada.

Si se intenta almacenar un valor fuera de su rango, el resultado puede ser incorrecto.

Ejemplo conceptual:

```cpp
int valor{2147483647};

++valor;
```

El resultado ya no puede representarse correctamente en un `int`.

Por esta razón es importante conocer los límites de cada tipo.

---

## Buenas Prácticas

### Inicializar Siempre

Correcto:

```cpp
int contador{};
```

---

También:

```cpp
int contador{0};
```

---

### Utilizar Nombres Descriptivos

Correcto:

```cpp
int total_productos;
int edad_usuario;
int numero_estudiantes;
```

---

### Evitar Variables Sin Inicializar

Evitar:

```cpp
int numero;
```

si se va a utilizar inmediatamente.

---

### Utilizar el Tipo Adecuado

Si se necesitan decimales:

```cpp
double
```

es más apropiado que:

```cpp
int
```

---

## Error Común

Esperar que la división entre enteros conserve decimales.

Ejemplo:

```cpp
int resultado{5 / 2};
```

Resultado:

```text
2
```

No:

```text
2.5
```

---

## Visualización

```text
5 / 2

Resultado matemático
       │
       ▼
      2.5
       │
       ▼
 Conversión a int
       │
       ▼
       2
```

---

## Resumen

* `int` se utiliza para almacenar números enteros.
* Puede contener valores positivos, negativos y cero.
* Permite realizar operaciones aritméticas.
* La división entre enteros produce división entera.
* El operador `%` devuelve el resto de una división.
* El tamaño exacto de `int` depende de la plataforma.
* En muchos sistemas modernos ocupa 4 bytes.
* Tiene una capacidad limitada de almacenamiento.
* Es uno de los tipos fundamentales más utilizados en C++.
* Debe inicializarse antes de utilizarse.
