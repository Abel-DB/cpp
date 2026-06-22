# char

## Introducción

El tipo:

```cpp
char
```

se utiliza para almacenar un único carácter.

Ejemplos:

```cpp
'A'
'B'
'Z'
'0'
'@'
```

Un carácter representa un único símbolo.

---

## ¿Qué es un Carácter?

Un carácter puede ser:

- Una letra.
- Un dígito.
- Un símbolo.
- Un espacio.
- Un carácter especial.

Ejemplos:

```cpp
'A'
'b'
'7'
'#'
' '
```

---

## Declaración

```cpp
char letra{'A'};
```

Representación:

```text
Nombre : letra
Tipo   : char
Valor  : 'A'
```

---

## Uso Básico

```cpp
#include <iostream>

int main()
{
    char letra{'A'};

    std::cout << letra << '\n';

    return 0;
}
```

Salida:

```text
A
```

---

## Lectura de Caracteres

También es posible leer un carácter desde la entrada estándar.

```cpp
#include <iostream>

int main()
{
    char opcion{};

    std::cin >> opcion;

    std::cout << opcion << '\n';

    return 0;
}
```

Entrada:

```text
S
```

Salida:

```text
S
```

---

## Comillas Simples

Los caracteres se escriben utilizando comillas simples.

Correcto:

```cpp
char letra{'A'};
```

---

Incorrecto:

```cpp
char letra{"A"};
```

porque:

```cpp
"A"
```

representa una secuencia de caracteres y no un único carácter.

---

## Caracteres Comunes

### Letras

```cpp
'A'
'B'
'C'
```

---

### Dígitos

```cpp
'0'
'1'
'2'
```

---

### Símbolos

```cpp
'+'
'-'
'*'
'/'
'@'
'#'
```

---

### Espacio

```cpp
' '
```

---

# Representación Interna

Aunque vemos caracteres:

```cpp
'A'
```

internamente se almacenan como valores numéricos.

Representación conceptual:

```text
'A'
 │
 ▼
Valor numérico interno
```

---

## ASCII

Muchos sistemas modernos utilizan ASCII o codificaciones compatibles con ASCII para los caracteres básicos.

Por ejemplo:

| Carácter | Valor Habitual |
| --------- | -------------- |
| `'A'` | 65 |
| `'B'` | 66 |
| `'C'` | 67 |
| `'a'` | 97 |
| `'b'` | 98 |
| `'0'` | 48 |
| `'1'` | 49 |

---

## Conversión a int

```cpp
char letra{'A'};

int codigo{letra};
```

Resultado habitual:

```text
65
```

---

## Ejemplo

```cpp
#include <iostream>

int main()
{
    char letra{'A'};

    std::cout << static_cast<int>(letra) << '\n';

    return 0;
}
```

Salida habitual:

```text
65
```

---

## Conversión desde int

```cpp
int codigo{65};

char letra{static_cast<char>(codigo)};
```

Resultado habitual:

```text
A
```

---

## Ejemplo

```cpp
#include <iostream>

int main()
{
    int codigo{66};

    char letra{static_cast<char>(codigo)};

    std::cout << letra << '\n';

    return 0;
}
```

Salida habitual:

```text
B
```

---

# char es un Tipo Entero

Aunque normalmente se utiliza para representar caracteres, `char` es un tipo entero.

Por esta razón puede participar en operaciones aritméticas.

Ejemplo:

```cpp
char letra{'A'};

++letra;
```

Resultado habitual:

```text
B
```

---

## Visualización

```text
'A'
 │
 ▼
65
 │
 ▼
66
 │
 ▼
'B'
```

---

## Otro Ejemplo

```cpp
char letra{'A'};

char siguiente{
    static_cast<char>(letra + 1)
};
```

Resultado:

```text
B
```

---

# Comparación de Caracteres

Los caracteres pueden compararse utilizando operadores relacionales.

```cpp
char letra{'A'};

if (letra == 'A')
{
}
```

---

También:

```cpp
if (letra != 'B')
{
}
```

---

## Orden de Comparación

Las comparaciones se realizan utilizando los valores numéricos internos asociados a los caracteres.

Ejemplo:

```cpp
'A' < 'B'
```

Resultado habitual:

```text
true
```

Porque:

```text
65 < 66
```

---

# Caracteres Especiales

Existen caracteres que no pueden escribirse directamente.

Para ello se utilizan secuencias de escape.

---

### Salto de Línea

```cpp
'\n'
```

---

### Tabulación

```cpp
'\t'
```

---

### Comilla Simple

```cpp
'\''
```

---

### Barra Invertida

```cpp
'\\'
```

---

## Ejemplo

```cpp
#include <iostream>

int main()
{
    std::cout << 'A' << '\n';
    std::cout << 'B' << '\n';

    return 0;
}
```

Salida:

```text
A
B
```

---

# Caracteres Más Allá del Inglés

Los ejemplos de este capítulo utilizan caracteres básicos como:

```cpp
'A'
'B'
'0'
'#'
```

Caracteres como:

```cpp
'á'
'ñ'
'€'
```

pueden requerir consideraciones adicionales relacionadas con la codificación utilizada.

Más adelante estudiaremos cómo C++ trabaja con texto y Unicode.

---

# Tamaño en Memoria

Un objeto de tipo:

```cpp
char
```

ocupa exactamente:

```text
1 byte
```

En C++, un byte es la unidad mínima direccionable de memoria.

Habitualmente un byte contiene:

```text
8 bits
```

aunque el estándar permite otras implementaciones.

---

## Visualización

```text
char letra{'A'};

Memoria

┌─────────┐
│   65    │
└─────────┘
```

---

# Diferencia entre char y una Cadena

```cpp
'A'
```

Representa:

```text
Un único carácter
```

---

```cpp
"A"
```

Representa:

```text
Una secuencia de caracteres
```

---

## Comparación

```text
char
 │
 └── Un carácter
```

```text
Cadena
 │
 └── Varios caracteres
```

---

# Buenas Prácticas

## Utilizar Comillas Simples

Correcto:

```cpp
char letra{'A'};
```

---

Incorrecto:

```cpp
char letra{"A"};
```

---

## Utilizar Nombres Descriptivos

Correcto:

```cpp
char letra_inicial{};
char opcion_menu{};
char simbolo{};
```

---

## Comprender la Relación con los Valores Numéricos

Recordar que:

```cpp
char
```

almacena un carácter utilizando internamente un valor numérico.

---

# Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    char letra{'A'};

    std::cout << letra << '\n';
    std::cout << static_cast<int>(letra) << '\n';

    return 0;
}
```

Salida:

```text
A
65
```

---

## Error Común

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

Representa:

```text
Un único carácter
```

---

```cpp
"A"
```

Representa:

```text
Una secuencia de caracteres
```

---

## Resumen

- `char` se utiliza para almacenar un único carácter.
- Los caracteres se escriben entre comillas simples.
- Internamente se almacenan mediante valores numéricos.
- Muchos sistemas utilizan ASCII o codificaciones compatibles para los caracteres básicos.
- `char` es un tipo entero y puede participar en operaciones aritméticas.
- Los caracteres pueden compararse utilizando operadores relacionales.
- Existen secuencias de escape para representar caracteres especiales.
- Un objeto de tipo `char` ocupa exactamente 1 byte.
- Debe diferenciarse claramente entre un carácter (`'A'`) y una secuencia de caracteres (`"A"`).
- Más adelante estudiaremos cadenas de texto y Unicode con mayor profundidad.
