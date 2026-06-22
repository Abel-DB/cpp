# Acceso a Caracteres

## Introducción

Un:

```cpp
std::string
```

es una secuencia de caracteres.

Por esta razón, es posible acceder a cada carácter individualmente.

Ejemplo:

```cpp
std::string nombre {"Juan"};
```

Representación:

```text
┌───┬───┬───┬───┐
│ J │ u │ a │ n │
└───┴───┴───┴───┘
  0   1   2   3
```

Cada carácter posee una posición denominada:

```text
Índice
```

---

## Índices

Los índices comienzan en:

```text
0
```

y no en:

```text
1
```

---

Ejemplo:

```cpp
std::string nombre {"Juan"};
```

```text
Carácter  Índice

J            0
u            1
a            2
n            3
```

---

# Operador []

La forma más utilizada para acceder a un carácter.

---

## Sintaxis

```cpp
string[indice]
```

---

## Ejemplo

```cpp
std::string nombre {"Juan"};

std::cout
    << nombre[0]
    << '\n';
```

Salida:

```text
J
```

---

## Visualización

```text
"Juan"

0 1 2 3
│ │ │ │
J u a n

nombre[0]
     │
     ▼
     J
```

---

## Más Ejemplos

```cpp
std::cout << nombre[1];
```

Resultado:

```text
u
```

---

```cpp
std::cout << nombre[2];
```

Resultado:

```text
a
```

---

```cpp
std::cout << nombre[3];
```

Resultado:

```text
n
```

---

# Modificar Caracteres

El operador:

```cpp
[]
```

también permite modificar caracteres.

---

## Ejemplo

```cpp
std::string nombre {"Juan"};

nombre[0] = 'R';
```

Resultado:

```text
Ruan
```

---

## Visualización

Antes:

```text
J u a n
```

---

Después:

```text
R u a n
```

---

# at()

Otra forma de acceder a caracteres.

---

## Sintaxis

```cpp
string.at(indice)
```

---

## Ejemplo

```cpp
std::string nombre {"Juan"};

std::cout
    << nombre.at(0)
    << '\n';
```

Salida:

```text
J
```

---

# Diferencia entre [] y at()

## []

```cpp
nombre[100]
```

No verifica límites.

Si el índice está fuera del rango válido:

```text
Comportamiento indefinido
```

---

## at()

```cpp
nombre.at(100)
```

Verifica límites.

Si el índice es inválido:

```text
Lanza una excepción
```

de tipo:

```cpp
std::out_of_range
```

---

## Comparación

| Método | Verifica límites |
|----------|----------------|
| `[]` | No |
| `at()` | Sí |

---

# front()

Devuelve el primer carácter.

---

## Sintaxis

```cpp
string.front()
```

---

## Ejemplo

```cpp
std::string nombre {"Juan"};

std::cout
    << nombre.front()
    << '\n';
```

Salida:

```text
J
```

---

## Visualización

```text
J u a n
│
└── front()
```

---

## Importante

El string no debe estar vacío.

Llamar a:

```cpp
front()
```

sobre un string vacío produce:

```text
Comportamiento indefinido
```

---

# back()

Devuelve el último carácter.

---

## Sintaxis

```cpp
string.back()
```

---

## Ejemplo

```cpp
std::string nombre {"Juan"};

std::cout
    << nombre.back()
    << '\n';
```

Salida:

```text
n
```

---

## Visualización

```text
J u a n
      │
      └── back()
```

---

## Importante

El string no debe estar vacío.

Llamar a:

```cpp
back()
```

sobre un string vacío produce:

```text
Comportamiento indefinido
```

---

# Primer y Último Carácter

```cpp
std::string nombre {"Juan"};

std::cout << nombre.front() << '\n';
std::cout << nombre.back() << '\n';
```

Salida:

```text
J
n
```

---

# Acceso Mediante Variables

```cpp
std::string nombre {"Juan"};

std::size_t indice = 2;

std::cout
    << nombre[indice]
    << '\n';
```

Salida:

```text
a
```

---

## Nota

La función:

```cpp
size()
```

devuelve un valor de tipo:

```cpp
std::size_t
```

Por esta razón, suele ser el tipo adecuado para representar índices.

---

# Relación con size()

Último índice válido:

```text
size() - 1
```

---

Ejemplo:

```cpp
std::string nombre {"Juan"};
```

Longitud:

```text
4
```

---

Último índice:

```text
3
```

---

Visualización:

```text
J u a n
0 1 2 3

size() = 4

último índice = 3
```

---

También:

```cpp
nombre[nombre.size() - 1]
```

equivale a:

```cpp
nombre.back()
```

---

# Error Común

Pensar que:

```cpp
nombre[4]
```

es el último carácter.

---

Realmente:

```cpp
nombre[3]
```

es el último carácter.

---

Porque:

```text
Los índices comienzan en 0
```

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string lenguaje {"C++"};

    std::cout
        << lenguaje[0]
        << '\n';

    std::cout
        << lenguaje.front()
        << '\n';

    std::cout
        << lenguaje.back()
        << '\n';

    return 0;
}
```

Salida:

```text
C
C
+
```

---

# Buenas Prácticas

## Utilizar at() Cuando la Seguridad Sea Importante

```cpp
texto.at(indice);
```

---

## Utilizar [] Cuando el Índice Sea Válido

```cpp
texto[0];
```

---

## Recordar que los Índices Comienzan en 0

```text
Primer carácter → índice 0
```

---

## Verificar que el String No Esté Vacío

Antes de utilizar:

```cpp
front()
back()
```

es recomendable comprobar:

```cpp
if (!texto.empty())
{
}
```

---

# Resumen

- Un string está formado por caracteres indexados.
- Los índices comienzan en 0.
- `[]` permite acceder y modificar caracteres.
- `[]` no verifica límites.
- Acceder fuera de rango mediante `[]` produce comportamiento indefinido.
- `at()` permite acceder con verificación de límites.
- `at()` lanza una excepción si el índice es inválido.
- `front()` devuelve el primer carácter.
- `back()` devuelve el último carácter.
- `front()` y `back()` requieren que el string no esté vacío.
- El último índice válido es `size() - 1`.
- Comprender los índices es fundamental para trabajar con strings y colecciones en C++.
