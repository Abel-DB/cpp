# std::string vs char

## Introducción

A lo largo del curso hemos trabajado con dos formas distintas de representar texto:

```cpp
char
```

y

```cpp
std::string
```

Aunque ambos están relacionados con caracteres, tienen propósitos diferentes.

Comprender cuándo utilizar cada uno es importante para escribir código claro y eficiente.

---

# char

El tipo:

```cpp
char
```

permite almacenar un único carácter.

---

## Ejemplo

```cpp
char letra {'A'};
```

Representación:

```text
A
```

---

## Más Ejemplos

```cpp
char inicial {'J'};
```

---

```cpp
char simbolo {'#'};
```

---

```cpp
char digito {'7'};
```

---

# Características de char

Puede almacenar:

```text
Letras
Dígitos
Símbolos
Espacios
```

---

Ejemplos:

```cpp
'A'
```

---

```cpp
'9'
```

---

```cpp
'?'
```

---

```cpp
' '
```

---

# Limitación

Un `char` almacena solamente un carácter.

---

Incorrecto:

```cpp
char nombre {'Juan'};
```

---

Porque:

```text
char
=
1 carácter
```

---

# std::string

Permite almacenar una secuencia de caracteres.

---

## Ejemplo

```cpp
std::string nombre {"Juan"};
```

Representación:

```text
J u a n
```

---

## Visualización

```text
┌───┬───┬───┬───┐
│ J │ u │ a │ n │
└───┴───┴───┴───┘
```

---

# Comparación Básica

## char

```cpp
char letra {'A'};
```

Resultado:

```text
Un carácter
```

---

## std::string

```cpp
std::string texto {"Hola"};
```

Resultado:

```text
Varios caracteres
```

---

# Comillas

## char

Utiliza:

```cpp
'A'
```

---

## std::string

Utiliza:

```cpp
"Hola"
```

---

## Comparación

```cpp
'A'
```

↓

```text
char
```

---

```cpp
"A"
```

↓

```text
Literal de cadena
```

---

Ese literal puede utilizarse para inicializar un:

```cpp
std::string
```

---

# Acceso a Caracteres

Aunque un string almacena varios caracteres, cada uno sigue siendo un:

```cpp
char
```

---

Ejemplo:

```cpp
std::string nombre {"Juan"};
```

---

```cpp
char letra =
    nombre[0];
```

Resultado:

```text
J
```

---

## Visualización

```text
"Juan"

J u a n
│
▼
char
```

---

# Relación Entre Ambos

Un string puede verse como:

```text
Una secuencia de char
```

---

Representación:

```text
std::string

J u a n
│ │ │ │
│ │ │ └── char
│ │ └──── char
│ └────── char
└──────── char
```

---

# Tamaño

## char

```cpp
sizeof(char)
```

Resultado:

```text
1 byte
```

---

## std::string

```cpp
sizeof(std::string)
```

Resultado:

```text
Depende de la implementación
```

---

Un string necesita almacenar más información:

- Caracteres.
- Longitud.
- Capacidad.
- Gestión de memoria.

---

# Operaciones Disponibles

## char

Permite operaciones simples.

Ejemplo:

```cpp
char letra {'A'};
```

---

```cpp
std::cout << letra;
```

---

## std::string

Permite muchas operaciones.

Ejemplo:

```cpp
texto.size();
```

---

```cpp
texto.find("abc");
```

---

```cpp
texto.substr(2, 3);
```

---

```cpp
texto += "!";
```

---

# Lectura de Datos

## char

```cpp
char letra {};

std::cin >> letra;
```

Entrada:

```text
A
```

---

## std::string

```cpp
std::string nombre {};

std::cin >> nombre;
```

Entrada:

```text
Juan
```

---

# Casos de Uso

## Utilizar char

Cuando se necesite:

- Un único carácter.
- Una inicial.
- Un símbolo.
- Un operador.
- Una opción de menú.

---

Ejemplos:

```cpp
char opcion {'S'};
```

---

```cpp
char inicial {'J'};
```

---

# Utilizar std::string

Cuando se necesite:

- Texto.
- Palabras.
- Frases.
- Nombres.
- Direcciones.
- Mensajes.

---

Ejemplos:

```cpp
std::string nombre {};
```

---

```cpp
std::string correo {};
```

---

```cpp
std::string mensaje {};
```

---

# Ejemplo Comparativo

```cpp
#include <iostream>
#include <string>

int main()
{
    char inicial {'J'};

    std::string nombre {"Juan"};

    std::cout
        << inicial
        << '\n';

    std::cout
        << nombre
        << '\n';

    return 0;
}
```

Salida:

```text
J
Juan
```

---

# char[]

Antes de `std::string`, el texto se representaba habitualmente mediante arreglos de caracteres.

Ejemplo:

```cpp
char nombre[] {"Juan"};
```

---

Representación:

```text
J u a n
```

---

Más adelante estudiaremos:

```cpp
arrays
```

y veremos esta estructura en profundidad.

---

# char[] vs std::string

## char[]

```cpp
char nombre[] {"Juan"};
```

---

Ventajas:

- Muy cercano al hardware.
- Compatible con bibliotecas antiguas.

---

Desventajas:

- Más difícil de utilizar.
- Gestión manual.
- Mayor riesgo de errores.

---

## std::string

```cpp
std::string nombre {"Juan"};
```

---

Ventajas:

- Más seguro.
- Más sencillo.
- Más expresivo.
- Más funcionalidades.

---

# Recomendación Moderna

En C++ moderno:

```cpp
std::string
```

es la opción preferida para trabajar con texto.

---

`char` se utiliza cuando realmente necesitamos un único carácter.

---

# Tabla Comparativa

| Característica | char | std::string |
|---------------|------|-------------|
| Un carácter | Sí | No |
| Texto completo | No | Sí |
| Usa comillas simples | Sí | No |
| Usa comillas dobles | No | No* |
| Permite size() | No | Sí |
| Permite find() | No | Sí |
| Permite substr() | No | Sí |
| Recomendado para texto | No | Sí |

\* Las comillas dobles crean un literal de cadena, que puede utilizarse para inicializar un `std::string`.

---

# Buenas Prácticas

## Utilizar char para Caracteres Individuales

Correcto:

```cpp
char inicial {'J'};
```

---

## Utilizar std::string para Texto

Correcto:

```cpp
std::string nombre {"Juan"};
```

---

## Preferir std::string Frente a char[]

En código moderno.

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
char
```

---

```cpp
"A"
```

↓

```text
Literal de cadena
```

---

Ejemplo:

```cpp
std::string texto {"A"};
```

---

# Visualización General

```text
char
 │
 ▼
Un carácter
```

---

```text
std::string
 │
 ▼
Varios caracteres
```

---

```text
std::string

J u a n
│ │ │ │
└─┴─┴─┘
  char
```

---

## Resumen

- `char` almacena un único carácter.
- `std::string` almacena una secuencia de caracteres.
- Los caracteres utilizan comillas simples.
- Los literales de cadena utilizan comillas dobles.
- Un string puede verse como una colección de caracteres.
- `std::string` ofrece muchas más funcionalidades que `char`.
- En C++ moderno se recomienda utilizar `std::string` para trabajar con texto.
- `char` debe reservarse para situaciones donde realmente se necesite un único carácter.
