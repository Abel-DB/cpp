# ¿Qué es un Puntero?

## Introducción

Hasta ahora hemos trabajado con variables como:

```cpp
int edad {25};
```

---

Sabemos que una variable:

```text
Tiene un nombre
Tiene un valor
Ocupa memoria
```

---

Por ejemplo:

```cpp
int edad {25};
```

almacena:

```text
25
```

---

Sin embargo, además del valor, existe otra información importante:

```text
¿Dónde está almacenada la variable?
```

---

Para trabajar con esa información C++ proporciona:

```cpp
Punteros
```

---

# ¿Qué es un Puntero?

Un puntero es una variable que almacena una dirección de memoria.

---

Mientras una variable normal almacena:

```text
Un valor
```

---

un puntero almacena:

```text
Una dirección
```

---

## Visualización

```text
Variable

edad
 │
 ▼
25
```

---

```text
Puntero

puntero_edad
      │
      ▼
 Dirección de edad
```

---

# Analogía

Imagina una ciudad.

---

Una casa contiene:

```text
Personas
```

---

Pero también posee:

```text
Una dirección
```

---

Ejemplo:

```text
Casa
  │
  ▼
25
```

---

```text
Dirección
  │
  ▼
Av. Principal 123
```

---

Un puntero almacena algo parecido a:

```text
La dirección
```

---

no el contenido de la casa.

---

# ¿Por Qué Existen?

Permiten:

```text
Acceder indirectamente a variables
Compartir datos
Trabajar con memoria dinámica
Implementar estructuras complejas
```

---

Más adelante veremos todos estos usos.

---

# Declaración de un Puntero

Sintaxis:

```cpp
tipo* nombre;
```

---

Ejemplo:

```cpp
int* puntero_edad;
```

---

Visualización:

```text
puntero_edad

Puede almacenar
la dirección de un int
```

---

# ¿Qué Significa el *?

En una declaración:

```cpp
int* puntero_edad;
```

el símbolo:

```cpp
*
```

indica:

```text
Esto es un puntero.
```

---

No significa multiplicación.

---

# Primer Ejemplo

```cpp
#include <iostream>

int main()
{
    int edad {25};

    int* puntero_edad {&edad};

    return 0;
}
```

---

Por ahora observa solamente:

```cpp
int* puntero_edad
```

---

Más adelante estudiaremos:

```cpp
&edad
```

en detalle.

---

# Variable vs Puntero

## Variable

```cpp
int edad {25};
```

---

Contiene:

```text
25
```

---

# Puntero

```cpp
int* puntero_edad;
```

---

Contiene:

```text
Una dirección de memoria
```

---

# Visualización

```text
edad
 │
 ▼
25
```

---

```text
puntero_edad
 │
 ▼
Dirección donde está edad
```

---

# Tipos de Punteros

Un puntero debe indicar el tipo de dato al que apunta.

---

Ejemplos:

```cpp
int* puntero_numero;
```

---

```cpp
double* puntero_precio;
```

---

```cpp
char* puntero_letra;
```

---

```cpp
bool* puntero_estado;
```

---

Visualización:

```text
int*    → dirección de un int
double* → dirección de un double
char*   → dirección de un char
bool*   → dirección de un bool
```

---

# ¿Por Qué Importa el Tipo?

Porque el compilador necesita saber:

```text
Qué tipo de dato existe
en esa dirección.
```

---

Por ejemplo:

```cpp
int* puntero_numero;
```

---

indica:

```text
Aquí habrá un int.
```

---

# Inicialización

Un puntero nunca debería quedar sin inicializar.

---

Incorrecto:

```cpp
int* puntero_numero;
```

---

Porque contiene:

```text
Basura
```

---

Correcto:

```cpp
int* puntero_numero {nullptr};
```

---

Veremos:

```cpp
nullptr
```

en profundidad más adelante.

---

Por ahora basta saber que significa:

```text
No apunta a nada.
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

# Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    int edad {25};

    int* puntero_edad {nullptr};

    return 0;
}
```

---

Variables:

```cpp
edad
```

---

y:

```cpp
puntero_edad
```

---

son diferentes.

---

Una almacena:

```text
Un valor
```

---

La otra almacena:

```text
Una dirección
```

---

# ¿Qué Veremos Después?

Para entender realmente los punteros necesitamos aprender:

```text
Direcciones de memoria
```

---

porque un puntero almacena precisamente:

```text
Una dirección
```

---

Ese será el siguiente tema.

---

# Buenas Prácticas

## Inicializar Siempre los Punteros

Correcto:

```cpp
int* puntero_numero {nullptr};
```

---

## Utilizar Nombres Claros

Correcto:

```cpp
int* puntero_edad;
```

---

```cpp
double* puntero_precio;
```

---

## Recordar que un Puntero No Almacena el Valor

Almacena:

```text
La dirección del valor.
```

---

# Error Común

Pensar que:

```cpp
int* puntero_edad;
```

contiene un entero.

---

Realidad:

```text
Contiene una dirección de memoria.
```

---

El entero estará en otro lugar.

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

| Concepto | Almacena |
|-----------|-----------|
| Variable | Un valor |
| Puntero | Una dirección de memoria |
| `int*` | Dirección de un `int` |
| `double*` | Dirección de un `double` |
| `nullptr` | Ninguna dirección válida |

---

## Resumen

- Un puntero es una variable que almacena una dirección de memoria.
- Se declara utilizando el operador `*`.
- El tipo del puntero indica qué tipo de dato existe en la dirección almacenada.
- Los punteros son diferentes de las variables normales.
- Una variable almacena un valor; un puntero almacena una dirección.
- Es recomendable inicializar los punteros con `nullptr`.
- Los punteros son fundamentales para comprender cómo funciona la memoria en C++.
- Son la base de muchas características avanzadas del lenguaje.
