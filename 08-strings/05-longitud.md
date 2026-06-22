# Longitud de Strings

## Introducción

Una de las operaciones más comunes cuando trabajamos con texto es conocer cuántos caracteres contiene una cadena.

Para ello, `std::string` proporciona varias funciones útiles.

Las más utilizadas son:

```cpp
size()
length()
empty()
```

---

## ¿Qué es la Longitud?

La longitud de un string es la cantidad de caracteres que contiene.

Ejemplo:

```cpp
std::string nombre {"Juan"};
```

Representación:

```text
J u a n
│ │ │ │
1 2 3 4
```

Longitud:

```text
4
```

---

# size()

La función:

```cpp
size()
```

devuelve la cantidad de caracteres almacenados en la cadena.

---

## Sintaxis

```cpp
cadena.size()
```

---

## Ejemplo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre {"Juan"};

    std::cout
        << nombre.size()
        << '\n';

    return 0;
}
```

Salida:

```text
4
```

---

## Visualización

```text
"Juan"

J u a n
│ │ │ │
└─┴─┴─┘
    │
    ▼
    4
```

---

# length()

La función:

```cpp
length()
```

también devuelve la cantidad de caracteres almacenados.

---

## Sintaxis

```cpp
cadena.length()
```

---

## Ejemplo

```cpp
std::string nombre {"Juan"};

std::cout
    << nombre.length()
    << '\n';
```

Salida:

```text
4
```

---

## ¿Cuál es la Diferencia?

Para `std::string`:

```cpp
size()
```

y

```cpp
length()
```

son equivalentes.

Devuelven exactamente el mismo valor.

---

## Comparación

```cpp
nombre.size()
```

↓

```text
4
```

---

```cpp
nombre.length()
```

↓

```text
4
```

---

# Ejemplo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string texto {"Hola Mundo"};

    std::cout
        << texto.size()
        << '\n';

    std::cout
        << texto.length()
        << '\n';

    return 0;
}
```

Salida:

```text
10
10
```

---

# Los Espacios También Cuentan

Los espacios forman parte del contenido de la cadena.

Ejemplo:

```cpp
std::string texto {"Hola Mundo"};
```

Representación:

```text
H o l a _ M u n d o
```

(`_` representa el espacio)

---

Conteo:

```text
10 caracteres
```

---

## Ejemplo

```cpp
std::string texto {"Hola Mundo"};

std::cout
    << texto.size()
    << '\n';
```

Salida:

```text
10
```

---

# String Vacío

```cpp
std::string texto {};
```

Representación:

```text
""
```

Longitud:

```text
0
```

---

## Ejemplo

```cpp
std::string texto {};

std::cout
    << texto.size()
    << '\n';
```

Salida:

```text
0
```

---

# empty()

Permite comprobar si una cadena está vacía.

---

## Sintaxis

```cpp
cadena.empty()
```

---

Resultado:

```cpp
true
```

o

```cpp
false
```

---

# Ejemplo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string texto {};

    std::cout
        << std::boolalpha
        << texto.empty()
        << '\n';

    return 0;
}
```

Salida:

```text
true
```

---

# Visualización

```text
""
 │
 ▼
empty()
 │
 ▼
true
```

---

## Ejemplo con Texto

```cpp
std::string texto {"Hola"};
```

---

```cpp
texto.empty()
```

Resultado:

```text
false
```

---

## Visualización

```text
"Hola"
 │
 ▼
empty()
 │
 ▼
false
```

---

# Comparación

Puede hacerse:

```cpp
if (texto.size() == 0)
{
}
```

---

Sin embargo, suele preferirse:

```cpp
if (texto.empty())
{
}
```

---

Porque expresa mejor la intención del código.

---

# Uso Habitual

```cpp
std::string usuario {};

if (usuario.empty())
{
    std::cout
        << "Usuario vacío\n";
}
```

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre {"Juan"};

    std::cout
        << "Longitud: "
        << nombre.size()
        << '\n';

    std::cout
        << std::boolalpha
        << nombre.empty()
        << '\n';

    return 0;
}
```

Salida:

```text
Longitud: 4
false
```

---

# size() vs length()

Para `std::string`:

```cpp
size()
```

↓

```text
Cantidad de caracteres almacenados
```

---

```cpp
length()
```

↓

```text
Cantidad de caracteres almacenados
```

---

Son equivalentes.

---

## Recomendación

Utilizar:

```cpp
size()
```

porque mantiene consistencia con otros contenedores de la biblioteca estándar que veremos más adelante.

---

# Convención Utilizada en Este Repositorio

Para obtener la longitud:

```cpp
texto.size()
```

---

Para comprobar si está vacío:

```cpp
texto.empty()
```

---

Ejemplos:

```cpp
if (nombre.empty())
{
}
```

---

```cpp
auto longitud = nombre.size();
```

---

# Buenas Prácticas

## Utilizar empty()

Preferir:

```cpp
if (texto.empty())
{
}
```

---

## Recordar que los Espacios Cuentan

```cpp
"Hola Mundo"
```

contiene:

```text
10 caracteres
```

porque el espacio también forma parte de la cadena.

---

## Utilizar size() para la Longitud

Es la convención más habitual en código moderno.

---

# Error Común

Pensar que:

```cpp
" "
```

es un string vacío.

---

Realmente contiene:

```text
1 carácter
```

(el espacio).

---

Comparación:

```text
""
```

↓

```text
0 caracteres
```

---

```text
" "
```

↓

```text
1 carácter
```

---

## Resumen

- La longitud de un string es la cantidad de caracteres que contiene.
- `size()` devuelve la longitud de la cadena.
- `length()` también devuelve la longitud.
- Para `std::string`, `size()` y `length()` son equivalentes.
- Los espacios forman parte del contenido y cuentan como caracteres.
- `empty()` permite comprobar si una cadena está vacía.
- Se suele preferir `size()` para obtener la longitud.
- Se suele preferir `empty()` para comprobar si una cadena no contiene caracteres.
