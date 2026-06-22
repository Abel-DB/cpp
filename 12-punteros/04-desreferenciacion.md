# Desreferenciación (*)

## Introducción

En los temas anteriores aprendimos:

```cpp
int edad {25};
```

---

que una variable tiene:

```text
Valor
Dirección
```

---

y que podemos obtener la dirección mediante:

```cpp
&edad
```

---

También vimos que un puntero puede almacenar esa dirección:

```cpp
int* puntero_edad {&edad};
```

---

Ahora surge una pregunta importante:

```text
¿Cómo obtenemos el valor
a partir del puntero?
```

---

Para ello utilizamos:

```cpp
*
```

conocido como:

```text
Operador de desreferenciación
```

---

# ¿Qué es la Desreferenciación?

Desreferenciar significa:

```text
Acceder al objeto
apuntado por un puntero.
```

---

Sintaxis:

```cpp
*puntero
```

---

Visualización:

```text
puntero_edad
      │
      ▼
 Dirección
      │
      ▼
    edad
      │
      ▼
      25
```

---

La expresión:

```cpp
*puntero_edad
```

produce:

```text
25
```

---

# Primer Ejemplo

```cpp
#include <iostream>

int main()
{
    int edad {25};

    int* puntero_edad {&edad};

    std::cout
        << *puntero_edad
        << '\n';

    return 0;
}
```

Salida:

```text
25
```

---

# ¿Qué Ocurrió?

Recordemos:

```cpp
puntero_edad
```

contiene:

```text
La dirección de edad
```

---

Al escribir:

```cpp
*puntero_edad
```

le estamos diciendo al programa:

```text
Ve a esa dirección
y obtén el valor.
```

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

puntero_edad
 │
 ▼
0x61ff08

*puntero_edad
 │
 ▼
25
```

---

# Diferencia Fundamental

## Puntero

```cpp
puntero_edad
```

---

Contiene:

```text
Una dirección
```

---

# Desreferenciación

```cpp
*puntero_edad
```

---

Produce:

```text
El valor almacenado
en esa dirección
```

---

# Comparación

```cpp
std::cout
    << puntero_edad;
```

Salida posible:

```text
0x61ff08
```

---

```cpp
std::cout
    << *puntero_edad;
```

Salida:

```text
25
```

---

# Modificar un Valor Mediante un Puntero

La desreferenciación no solo permite leer.

---

También permite modificar.

---

Ejemplo:

```cpp
int edad {25};

int* puntero_edad {&edad};

*puntero_edad = 30;
```

---

Ahora:

```cpp
std::cout
    << edad;
```

Salida:

```text
30
```

---

# Visualización

Antes:

```text
edad = 25
```

---

Después:

```cpp
*puntero_edad = 30;
```

---

Resultado:

```text
edad = 30
```

---

Porque ambos acceden al mismo objeto.

---

# Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    int edad {25};

    int* puntero_edad {&edad};

    *puntero_edad = 30;

    std::cout
        << edad
        << '\n';

    return 0;
}
```

Salida:

```text
30
```

---

# Lectura y Escritura

Lectura:

```cpp
std::cout
    << *puntero_edad;
```

---

Escritura:

```cpp
*puntero_edad = 30;
```

---

Ambas operaciones utilizan:

```cpp
*
```

---

# Relación con Referencias

Recordemos:

```cpp
int edad {25};

int& referencia_edad {edad};
```

---

Modificar:

```cpp
referencia_edad = 30;
```

---

produce:

```text
edad = 30
```

---

Con punteros:

```cpp
*puntero_edad = 30;
```

---

Resultado idéntico.

---

# Desreferenciar Diferentes Tipos

## int

```cpp
int numero {10};

int* puntero_numero {&numero};

std::cout
    << *puntero_numero;
```

---

# double

```cpp
double precio {9.99};

double* puntero_precio {&precio};

std::cout
    << *puntero_precio;
```

---

# char

```cpp
char inicial {'J'};

char* puntero_inicial {&inicial};

std::cout
    << *puntero_inicial;
```

---

Siempre:

```text
Obtiene el valor real
```

---

# Desreferenciar nullptr

Observa:

```cpp
int* puntero_numero {nullptr};

std::cout
    << *puntero_numero;
```

---

Resultado:

```text
Comportamiento indefinido
```

---

Porque:

```text
No existe un objeto válido.
```

---

# Visualización

```text
puntero_numero
      │
      ▼
   nullptr
```

---

Intentar:

```cpp
*puntero_numero
```

---

equivale a:

```text
Intentar acceder a nada.
```

---

# Regla Fundamental

Antes de desreferenciar un puntero:

```text
Debe apuntar a un objeto válido.
```

---

Correcto:

```cpp
int edad {25};

int* puntero_edad {&edad};

std::cout
    << *puntero_edad;
```

---

# Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    int edad {25};

    int* puntero_edad {&edad};

    std::cout
        << "Direccion: "
        << puntero_edad
        << '\n';

    std::cout
        << "Valor: "
        << *puntero_edad
        << '\n';

    return 0;
}
```

Salida posible:

```text
Direccion: 0x61ff08
Valor: 25
```

---

# ¿Por Qué se Utiliza el Mismo Símbolo?

Observa:

Declaración:

```cpp
int* puntero_edad;
```

---

Desreferenciación:

```cpp
*puntero_edad
```

---

Aunque ambos usan:

```cpp
*
```

---

el significado depende del contexto.

---

En una declaración:

```text
Indica que es un puntero.
```

---

En una expresión:

```text
Desreferencia el puntero.
```

---

# Buenas Prácticas

## Desreferenciar Solo Punteros Válidos

Correcto:

```cpp
int* puntero_edad {&edad};
```

---

## Inicializar los Punteros

Correcto:

```cpp
int* puntero_numero {nullptr};
```

---

## Comprender la Diferencia

```cpp
puntero_edad
```

↓

```text
Dirección
```

---

```cpp
*puntero_edad
```

↓

```text
Valor
```

---

# Error Común

Confundir:

```cpp
puntero_edad
```

con:

```cpp
*puntero_edad
```

---

Observa:

```cpp
puntero_edad
```

↓

```text
0x61ff08
```

---

```cpp
*puntero_edad
```

↓

```text
25
```

---

Son cosas completamente distintas.

---

# Visualización General

```text
Variable
   │
   ▼
 Valor
```

---

```text
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
```

---

```text
*
   │
   ▼
Valor
```

---

# Tabla Resumen

| Expresión | Resultado |
|------------|------------|
| `edad` | Valor |
| `&edad` | Dirección |
| `puntero_edad` | Dirección almacenada |
| `*puntero_edad` | Valor apuntado |

---

## Resumen

- El operador `*` permite desreferenciar un puntero.
- Desreferenciar significa acceder al objeto apuntado.
- `puntero_edad` contiene una dirección.
- `*puntero_edad` produce el valor almacenado en esa dirección.
- La desreferenciación permite leer y modificar datos.
- Nunca debe desreferenciarse un puntero nulo (`nullptr`).
- El operador `*` es una de las herramientas fundamentales al trabajar con punteros.
- Comprender la diferencia entre dirección y valor es esencial para dominar los punteros.
