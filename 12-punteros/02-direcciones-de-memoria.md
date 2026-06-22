# Direcciones de Memoria

## Introducción

En el tema anterior aprendimos que un puntero es una variable que almacena:

```text
Una dirección de memoria
```

---

Por ejemplo:

```cpp
int* puntero_edad;
```

---

Sin embargo, todavía no sabemos:

```text
¿Qué es una dirección de memoria?
```

---

Para comprender realmente los punteros primero debemos entender cómo se almacenan las variables en memoria.

---

# Memoria

Cuando un programa se ejecuta, el sistema operativo le asigna memoria.

---

Visualización:

```text
Memoria

┌───────┐
│       │
├───────┤
│       │
├───────┤
│       │
├───────┤
│       │
└───────┘
```

---

Podemos imaginarla como una gran colección de ubicaciones.

---

Cada ubicación posee:

```text
Una dirección
```

---

# Una Variable en Memoria

Observa:

```cpp
int edad {25};
```

---

El valor:

```text
25
```

se almacena en alguna posición de memoria.

---

Visualización:

```text
Dirección      Valor

1000   ───►    25
```

---

La dirección exacta depende del sistema y de la ejecución.

---

# ¿Qué es una Dirección?

Una dirección es un identificador que permite localizar una posición de memoria.

---

Visualización:

```text
Casa
 │
 ▼
Dirección

Av. Principal 123
```

---

De forma similar:

```text
Variable
 │
 ▼
Dirección de memoria
```

---

# Cada Variable Tiene una Dirección

Ejemplo:

```cpp
int edad {25};

double precio {9.99};

char inicial {'J'};
```

---

Visualización:

```text
Dirección      Valor

1000   ───►    25
2000   ───►    9.99
3000   ───►    'J'
```

---

Cada variable ocupa un lugar distinto.

---

# Operador de Dirección

C++ permite obtener la dirección de una variable mediante:

```cpp
&
```

---

Ejemplo:

```cpp
int edad {25};

std::cout
    << &edad;
```

---

Salida aproximada:

```text
0x61ff08
```

---

La dirección exacta cambia en cada ejecución.

---

# Visualización

```text
edad
 │
 ▼
25

&edad
 │
 ▼
0x61ff08
```

---

# Primer Ejemplo

```cpp
#include <iostream>

int main()
{
    int edad {25};

    std::cout
        << &edad
        << '\n';

    return 0;
}
```

---

Salida posible:

```text
0x61ff08
```

---

Tu resultado será diferente.

---

# Direcciones Diferentes

Observa:

```cpp
int edad {25};

int altura {180};
```

---

Visualización:

```text
Dirección      Variable

1000   ───►    edad
1004   ───►    altura
```

---

Cada variable posee su propia dirección.

---

# Tamaño y Direcciones

Recordemos:

```cpp
sizeof(int)
```

---

Normalmente:

```text
4 bytes
```

---

Por eso dos enteros suelen ocupar posiciones cercanas.

---

Visualización:

```text
1000 → edad
1004 → altura
```

---

Aunque esto depende de la implementación.

---

# Direcciones y Punteros

Ahora podemos entender:

```cpp
int edad {25};

int* puntero_edad {&edad};
```

---

Visualización:

```text
edad
 │
 ▼
25

puntero_edad
 │
 ▼
Dirección de edad
```

---

El puntero almacena:

```cpp
&edad
```

---

es decir:

```text
La dirección de edad
```

---

# Mostrar una Dirección

```cpp
int edad {25};

std::cout
    << &edad
    << '\n';
```

---

Salida posible:

```text
0x61ff08
```

---

# Mostrar Varias Direcciones

```cpp
int edad {25};

int altura {180};

double precio {9.99};

std::cout
    << &edad
    << '\n';

std::cout
    << &altura
    << '\n';

std::cout
    << &precio
    << '\n';
```

---

Salida posible:

```text
0x61ff08
0x61ff04
0x61fef8
```

---

# ¿Debemos Memorizar las Direcciones?

No.

---

Las direcciones:

```text
Cambian
```

---

entre:

```text
Ejecuciones
Computadoras
Sistemas operativos
```

---

Lo importante es comprender que:

```text
Existen
```

---

y que los punteros las almacenan.

---

# Representación Hexadecimal

Las direcciones suelen mostrarse en:

```text
Hexadecimal
```

---

Ejemplo:

```text
0x61ff08
```

---

El prefijo:

```text
0x
```

indica hexadecimal.

---

No es necesario profundizar en ello por ahora.

---

# Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    int edad {25};

    std::cout
        << "Valor: "
        << edad
        << '\n';

    std::cout
        << "Direccion: "
        << &edad
        << '\n';

    return 0;
}
```

Salida posible:

```text
Valor: 25
Direccion: 0x61ff08
```

---

# Relación con los Punteros

Hasta ahora sabemos:

---

Variable:

```cpp
int edad {25};
```

---

Dirección:

```cpp
&edad
```

---

Puntero:

```cpp
int* puntero_edad {&edad};
```

---

Visualización:

```text
edad
 │
 ▼
25

&edad
 │
 ▼
0x61ff08

puntero_edad
 │
 ▼
0x61ff08
```

---

# Buenas Prácticas

## Entender la Diferencia

Correcto:

```text
edad
```

↓

```text
Valor
```

---

```text
&edad
```

↓

```text
Dirección
```

---

## No Depender de Direcciones Específicas

Las direcciones pueden cambiar.

---

## Pensar en los Punteros como Direcciones

Esto facilitará todos los temas siguientes.

---

# Error Común

Confundir:

```cpp
edad
```

con:

```cpp
&edad
```

---

Observa:

```cpp
edad
```

↓

```text
25
```

---

```cpp
&edad
```

↓

```text
Dirección donde está almacenado 25
```

---

Son conceptos completamente distintos.

---

# Visualización General

```text
Variable
   │
   ▼
 Valor

&

   │
   ▼

Dirección
```

---

```text
Puntero
   │
   ▼
Dirección
   │
   ▼
Valor
```

---

# Tabla Resumen

| Expresión | Significado |
|------------|-------------|
| `edad` | Valor almacenado |
| `&edad` | Dirección de memoria |
| `puntero_edad` | Dirección almacenada en el puntero |
| `int*` | Puntero a `int` |

---

## Resumen

- Toda variable ocupa memoria.
- Cada variable posee una dirección única.
- Una dirección identifica una ubicación en memoria.
- El operador `&` permite obtener la dirección de una variable.
- Las direcciones suelen mostrarse en hexadecimal.
- Los punteros almacenan direcciones de memoria.
- Comprender las direcciones es esencial para entender los punteros.
- El siguiente paso será estudiar en detalle el operador `&`.
