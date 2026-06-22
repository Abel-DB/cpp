# Búsqueda en Strings

## Introducción

Una de las tareas más frecuentes cuando trabajamos con texto consiste en buscar caracteres o secuencias de caracteres dentro de una cadena.

Por ejemplo:

```text
¿Contiene un '@'?
¿Aparece la palabra "admin"?
¿Empieza con "https"?
¿Termina con ".txt"?
```

Para resolver estos problemas `std::string` proporciona varias herramientas.

---

# find()

La función más importante para realizar búsquedas.

---

## ¿Qué Hace?

Busca una secuencia de caracteres dentro del string.

Si la encuentra:

```text
Devuelve la posición de la primera coincidencia.
```

---

Si no la encuentra:

```cpp
std::string::npos
```

---

## Sintaxis

```cpp
texto.find(valor)
```

---

# Buscar un Carácter

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string texto {"Hola"};

    std::cout
        << texto.find('o')
        << '\n';

    return 0;
}
```

Salida:

```text
1
```

---

## Visualización

```text
H o l a
0 1 2 3
  │
  ▼
posición 1
```

---

# Buscar una Subcadena

```cpp
std::string texto {"Hola Mundo"};

std::cout
    << texto.find("Mundo")
    << '\n';
```

Salida:

```text
5
```

---

## Visualización

```text
Hola Mundo
     │
     ▼
     M
```

---

# Cuando No Existe

```cpp
std::string texto {"Hola"};

auto posicion =
    texto.find("Python");
```

---

Resultado:

```cpp
std::string::npos
```

---

## ¿Qué es npos?

Representa:

```text
No encontrado
```

---

Visualización:

```text
Buscar
   │
   ▼
No existe
   │
   ▼
npos
```

---

# Comprobar si Existe

Forma recomendada:

```cpp
if (texto.find("Hola")
    != std::string::npos)
{
}
```

---

## Ejemplo

```cpp
std::string texto {"Hola Mundo"};

if (texto.find("Mundo")
    != std::string::npos)
{
    std::cout
        << "Encontrado\n";
}
```

Salida:

```text
Encontrado
```

---

# Buscar Desde una Posición

También es posible indicar dónde comenzar la búsqueda.

---

## Sintaxis

```cpp
texto.find(valor, posicion)
```

---

## Ejemplo

```cpp
std::string texto {"abcabc"};

std::cout
    << texto.find("abc", 1)
    << '\n';
```

Salida:

```text
3
```

---

## Visualización

```text
a b c a b c
0 1 2 3 4 5

buscar desde 1
        │
        ▼
        3
```

---

# Buscar la Primera Aparición

```cpp
std::string texto {"banana"};

auto posicion =
    texto.find('a');
```

Resultado:

```text
1
```

---

Solo devuelve:

```text
La primera coincidencia
```

---

# contains() (C++23)

Desde C++23 existe:

```cpp
contains()
```

---

## Sintaxis

```cpp
texto.contains(valor)
```

---

## Ejemplo

```cpp
std::string texto {"Hola Mundo"};

if (texto.contains("Mundo"))
{
    std::cout
        << "Existe\n";
}
```

Salida:

```text
Existe
```

---

## Resultado

Devuelve:

```cpp
true
```

o

```cpp
false
```

---

# Comparación

Antes:

```cpp
texto.find("Mundo")
!= std::string::npos
```

---

C++23:

```cpp
texto.contains("Mundo")
```

---

Mucho más legible.

---

# starts_with() (C++20)

Permite comprobar si un string comienza con un texto determinado.

---

## Ejemplo

```cpp
std::string url {"https://google.com"};

std::cout
    << std::boolalpha
    << url.starts_with("https");
```

Salida:

```text
true
```

---

## Visualización

```text
https://google.com
│
└── empieza con "https"
```

---

# ends_with() (C++20)

Permite comprobar si una cadena termina con un texto específico.

---

## Ejemplo

```cpp
std::string archivo {"documento.txt"};

std::cout
    << std::boolalpha
    << archivo.ends_with(".txt");
```

Salida:

```text
true
```

---

## Visualización

```text
documento.txt
            │
            └── termina con ".txt"
```

---

# Casos de Uso

## Validar Correos

```cpp
correo.find('@')
```

---

## Verificar Extensiones

```cpp
archivo.ends_with(".txt")
```

---

## Verificar URLs

```cpp
url.starts_with("https")
```

---

## Buscar Texto

```cpp
texto.contains("admin")
```

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string texto {"Hola Mundo"};

    auto posicion =
        texto.find("Mundo");

    if (posicion != std::string::npos)
    {
        std::cout
            << "Encontrado en: "
            << posicion
            << '\n';
    }

    return 0;
}
```

Salida:

```text
Encontrado en: 5
```

---

# Comparación de Herramientas

| Función | Resultado |
|----------|------------|
| `find()` | Posición de la primera coincidencia |
| `contains()` | `true` / `false` |
| `starts_with()` | `true` / `false` |
| `ends_with()` | `true` / `false` |

---

# Convención Utilizada en Este Repositorio

Cuando sea necesario conocer la posición de una coincidencia:

```cpp
auto posicion =
    texto.find("abc");
```

---

Cuando solo importe saber si existe:

```cpp
texto.contains("abc");
```

---

Y cuando se quiera validar prefijos o sufijos:

```cpp
texto.starts_with("https");
```

---

```cpp
texto.ends_with(".txt");
```

---

# Buenas Prácticas

## Utilizar find() Cuando Necesites la Posición

```cpp
auto posicion =
    texto.find("abc");
```

---

## Utilizar contains() Cuando Solo Importe la Existencia

```cpp
texto.contains("admin");
```

---

## Utilizar starts_with() y ends_with()

Son más expresivos que implementar la lógica manualmente.

---

## Comparar Siempre Contra npos

Correcto:

```cpp
if (texto.find("abc")
    != std::string::npos)
{
}
```

---

# Error Común

Escribir:

```cpp
if (texto.find("abc"))
{
}
```

---

Problema:

```text
find() devuelve una posición,
no un valor booleano.
```

Además, si la coincidencia se encuentra en la posición:

```text
0
```

la condición evaluará como:

```cpp
false
```

aunque el texto sí exista.

---

Correcto:

```cpp
if (texto.find("abc")
    != std::string::npos)
{
}
```

---

O en C++23:

```cpp
if (texto.contains("abc"))
{
}
```

---

# Visualización General

```text
String
  │
  ├── find()
  │       │
  │       ▼
  │   Posición
  │
  ├── contains()
  │       │
  │       ▼
  │   true / false
  │
  ├── starts_with()
  │
  └── ends_with()
```

---

## Resumen

- `find()` busca una secuencia de caracteres y devuelve la posición de la primera coincidencia.
- Si no encuentra coincidencias devuelve `std::string::npos`.
- `contains()` permite comprobar si existe un texto (C++23).
- `starts_with()` verifica el inicio de una cadena (C++20).
- `ends_with()` verifica el final de una cadena (C++20).
- `find()` devuelve una posición, no un valor booleano.
- Estas funciones permiten realizar búsquedas de forma sencilla y eficiente.
- Son herramientas fundamentales para trabajar con texto en C++ moderno.
```**```
