# ¿Qué es std::string?

## Introducción

Hasta ahora hemos visto el tipo:

```cpp
char
```

que permite almacenar un único carácter.

Ejemplo:

```cpp
char letra = 'A';
```

---

Sin embargo, en programas reales normalmente necesitamos trabajar con texto completo.

Por ejemplo:

```text
Juan
Hola Mundo
C++
Programación
```

Para ello C++ proporciona:

```cpp
std::string
```

---

## Limitación de char

Un `char` solo puede almacenar un carácter.

Ejemplo:

```cpp
char letra = 'A';
```

Correcto.

---

No puede utilizarse para almacenar texto completo.

Por ejemplo:

```cpp
char nombre = 'J';
```

almacena únicamente un carácter.

Si necesitamos almacenar varias letras formando una palabra o una frase, debemos utilizar:

```cpp
std::string
```

---

## ¿Qué es std::string?

`std::string` es una clase de la biblioteca estándar que representa y permite manipular una secuencia de caracteres.

Ejemplo:

```cpp
std::string nombre = "Juan";
```

Representación conceptual:

```text
J
u
a
n
```

agrupados en un único objeto.

---

## Visualización

```text
nombre
   │
   ▼
┌───┬───┬───┬───┐
│ J │ u │ a │ n │
└───┴───┴───┴───┘
```

---

## Biblioteca Necesaria

Para utilizar `std::string` debemos incluir:

```cpp
#include <string>
```

---

## Primer Ejemplo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre = "Juan";

    std::cout << nombre << '\n';

    return 0;
}
```

Salida:

```text
Juan
```

---

## Declaración

```cpp
std::string nombre;
```

---

## Inicialización

```cpp
std::string nombre = "Juan";
```

---

También:

```cpp
std::string ciudad{"Madrid"};
```

---

## Comparación con char

### char

```cpp
char letra = 'A';
```

Representa:

```text
Un carácter
```

---

### std::string

```cpp
std::string texto = "Hola";
```

Representa:

```text
Una secuencia de caracteres
```

---

## Visualización

```text
char

'A'
```

---

```text
std::string

"Hola"
```

---

# Comillas

Los caracteres utilizan:

```cpp
'A'
```

---

Las cadenas utilizan:

```cpp
"Hola"
```

---

## Diferencia

```cpp
'A'
```

↓

```text
Un carácter
```

---

```cpp
"Hola"
```

↓

```text
Una cadena de caracteres
```

---

# Uso Habitual

```cpp
std::string nombre = "Ana";

std::string apellido = "Gomez";

std::string mensaje = "Bienvenido";
```

---

# Mostrar Strings

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string lenguaje = "C++";

    std::cout << lenguaje << '\n';

    return 0;
}
```

Salida:

```text
C++
```

---

# Representación Conceptual

Conceptualmente:

```cpp
std::string nombre = "Juan";
```

contiene una secuencia de caracteres:

```text
┌───┬───┬───┬───┐
│ J │ u │ a │ n │
└───┴───┴───┴───┘
```

Cada posición almacena un carácter.

---

# Ventajas de std::string

## Fácil de Utilizar

```cpp
std::string nombre = "Juan";
```

---

## Gestiona la Memoria Automáticamente

Gestiona automáticamente la memoria necesaria para almacenar sus caracteres.

---

## Permite Operaciones de Texto

Más adelante veremos:

```text
Concatenación
Longitud
Búsquedas
Subcadenas
Recorridos
```

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre = "Juan";

    std::cout << "Nombre: "
              << nombre
              << '\n';

    return 0;
}
```

Salida:

```text
Nombre: Juan
```

---

# Convención Utilizada en Este Repositorio

Las variables de tipo `std::string` utilizarán:

```text
snake_case
```

Ejemplos:

```cpp
std::string nombre_usuario;

std::string nombre_completo;

std::string mensaje_error;
```

---

# Buenas Prácticas

## Utilizar std::string para Texto

Preferir:

```cpp
std::string nombre;
```

cuando se trabaje con texto.

---

## Utilizar Nombres Descriptivos

Correcto:

```cpp
std::string nombre_completo;
```

---

```cpp
std::string correo_electronico;
```

---

## Incluir la Cabecera Correcta

```cpp
#include <string>
```

---

# Error Común

Confundir:

```cpp
'A'
```

con:

```cpp
"A"
```

---

```cpp
'A'
```

↓

```text
Un carácter
```

---

```cpp
"A"
```

↓

```text
Una cadena de caracteres
```

---

## Resumen

- `char` almacena un único carácter.
- `std::string` representa una secuencia de caracteres.
- Para utilizar `std::string` es necesario incluir `<string>`.
- Las cadenas se escriben entre comillas dobles.
- `std::string` es la herramienta principal para trabajar con texto en C++.
- Gestiona automáticamente la memoria necesaria para almacenar caracteres.
- Proporciona numerosas operaciones para manipular texto de forma cómoda y segura.
