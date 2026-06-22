# Operador de Dirección (&)

## Introducción

En el tema anterior aprendimos que toda variable posee una dirección de memoria.

Ejemplo:

```cpp
int edad {25};
```

---

Visualización:

```text
Dirección      Valor

1000   ───►    25
```

---

También vimos que C++ permite obtener esa dirección mediante:

```cpp
&
```

---

Ahora estudiaremos este operador en detalle.

---

# ¿Qué es el Operador &?

El operador:

```cpp
&
```

permite obtener la dirección de memoria de una variable.

---

Sintaxis:

```cpp
&variable
```

---

Ejemplo:

```cpp
int edad {25};

&edad
```

---

Resultado:

```text
Dirección donde está almacenada edad
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

Salida posible:

```text
0x61ff08
```

---

La dirección exacta dependerá del sistema y de la ejecución.

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

# Variable vs Dirección

Observa:

```cpp
int edad {25};
```

---

La expresión:

```cpp
edad
```

produce:

```text
25
```

---

Mientras que:

```cpp
&edad
```

produce:

```text
La dirección de memoria
```

---

# Ejemplo

```cpp
int edad {25};

std::cout
    << edad
    << '\n';
```

Salida:

```text
25
```

---

```cpp
std::cout
    << &edad
    << '\n';
```

Salida posible:

```text
0x61ff08
```

---

# Direcciones de Varias Variables

```cpp
int edad {25};

int altura {180};

double precio {9.99};
```

---

Visualización:

```text
&edad
   │
   ▼
0x61ff08

&altura
   │
   ▼
0x61ff04

&precio
   │
   ▼
0x61fef8
```

---

Cada variable posee una dirección distinta.

---

# Guardar una Dirección

Una dirección puede almacenarse en un puntero.

---

Ejemplo:

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

# ¿Qué Tipo Devuelve &?

Observa:

```cpp
int edad {25};

&edad
```

---

El resultado es una dirección de un:

```cpp
int
```

---

Por ello se almacena en:

```cpp
int*
```

---

Ejemplo:

```cpp
int* puntero_edad {&edad};
```

---

# Más Ejemplos

```cpp
double precio {9.99};

double* puntero_precio {&precio};
```

---

```cpp
char inicial {'J'};

char* puntero_inicial {&inicial};
```

---

El tipo debe coincidir.

---

# Uso Habitual

El operador:

```cpp
&
```

se utiliza constantemente para:

```text
Crear punteros
Pasar argumentos por dirección
Trabajar con memoria
```

---

Más adelante veremos todos estos casos.

---

# Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    int edad {25};

    int* puntero_edad {&edad};

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

# Dirección y Referencias

Recordemos:

```cpp
int edad {25};

int& referencia_edad {edad};
```

---

Una referencia también utiliza:

```cpp
edad
```

---

pero internamente trabaja con la misma dirección.

---

Visualización:

```text
edad
 ▲
 │
referencia_edad
```

---

Más adelante compararemos referencias y punteros directamente.

---

# Operador & en una Expresión

Puede utilizarse en cualquier lugar donde se necesite una dirección.

---

Ejemplo:

```cpp
int edad {25};

int* puntero_edad;

puntero_edad = &edad;
```

---

Resultado:

```text
puntero_edad almacena la dirección de edad
```

---

# Error Común

Intentar obtener la dirección de un literal.

---

Incorrecto:

```cpp
&10
```

---

Resultado:

```text
Error de compilación
```

---

Porque:

```text
10 no es una variable.
```

---

# Otro Error Común

Confundir:

```cpp
&
```

de direcciones con:

```cpp
&
```

de referencias.

---

Observa:

Referencia:

```cpp
int& referencia_edad {edad};
```

---

Dirección:

```cpp
&edad
```

---

Aunque utilizan el mismo símbolo:

```cpp
&
```

---

su significado depende del contexto.

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
&variable
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

# Tabla Resumen

| Expresión | Resultado |
|------------|------------|
| `edad` | Valor |
| `&edad` | Dirección |
| `int*` | Puntero a `int` |
| `int* puntero_edad {&edad};` | Guarda la dirección |

---

## Resumen

- El operador `&` obtiene la dirección de memoria de una variable.
- El resultado es una dirección que puede almacenarse en un puntero.
- Cada variable posee una dirección única.
- `edad` representa el valor; `&edad` representa la dirección.
- El tipo de la dirección debe coincidir con el tipo del puntero.
- El operador `&` es fundamental para trabajar con punteros.
- No debe confundirse con el uso de `&` en referencias.
- Comprender este operador es esencial para los siguientes temas sobre punteros.
