# sizeof

## Introducción

Cuando trabajamos con variables y tipos de datos, es útil conocer cuánta memoria ocupan.

C++ proporciona el operador:

```cpp
sizeof
```

que permite consultar el tamaño de un tipo o de un objeto.

---

## ¿Qué es sizeof?

`sizeof` es un operador del lenguaje que devuelve el tamaño de un tipo o de un objeto.

El resultado se expresa en:

```text
bytes
```

---

## Sintaxis

### Aplicado a un tipo

```cpp
sizeof(int)
```

---

### Aplicado a una variable

```cpp
int edad{25};

sizeof(edad)
```

---

## Tipo del Resultado

El valor devuelto por `sizeof` tiene tipo:

```cpp
std::size_t
```

Más adelante estudiaremos este tipo con detalle.

Por ahora basta con saber que está diseñado para representar tamaños y cantidades de memoria.

---

## Ejemplo Básico

```cpp
#include <iostream>

int main()
{
    std::cout << sizeof(int) << '\n';

    return 0;
}
```

Posible salida:

```text
4
```

---

## Visualización

```text
sizeof(int)
      │
      ▼
      4
      │
      ▼
   4 bytes
```

---

# sizeof con Tipos Fundamentales

```cpp
#include <iostream>

int main()
{
    std::cout << sizeof(char) << '\n';
    std::cout << sizeof(bool) << '\n';
    std::cout << sizeof(int) << '\n';
    std::cout << sizeof(double) << '\n';

    return 0;
}
```

Posible salida:

```text
1
1
4
8
```

---

## Tamaños Habituales

| Tipo | Tamaño Habitual |
| ------ | ------ |
| `char` | 1 byte |
| `bool` | 1 byte |
| `int` | 4 bytes |
| `float` | 4 bytes |
| `double` | 8 bytes |

---

## Importante

Estos tamaños son comunes en sistemas modernos, pero no están garantizados por el estándar.

El tamaño real depende de factores como:

- Arquitectura.
- Sistema operativo.
- Compilador.

Por ello:

```cpp
sizeof(...)
```

es la forma correcta de consultar tamaños.

---

# El Caso Especial de char

El estándar garantiza que:

```cpp
sizeof(char)
```

siempre es:

```cpp
1
```

---

Esto no significa necesariamente:

```text
1 byte = 8 bits
```

aunque en prácticamente todos los sistemas modernos sí ocurre.

Lo que garantiza el lenguaje es que un `char` ocupa exactamente un byte.

---

# sizeof con Variables

Ejemplo:

```cpp
int edad{25};

std::cout << sizeof(edad);
```

Resultado habitual:

```text
4
```

---

Otro ejemplo:

```cpp
double precio{19.99};

std::cout << sizeof(precio);
```

Resultado habitual:

```text
8
```

---

# sizeof con Expresiones

También puede aplicarse a expresiones.

Ejemplo:

```cpp
sizeof(10)
```

Resultado habitual:

```text
4
```

porque:

```cpp
10
```

es un literal de tipo:

```cpp
int
```

---

Otro ejemplo:

```cpp
sizeof(3.14)
```

Resultado habitual:

```text
8
```

porque:

```cpp
3.14
```

es un literal de tipo:

```cpp
double
```

---

# sizeof y auto

```cpp
auto edad = 25;
```

El compilador deduce:

```cpp
int
```

Por tanto:

```cpp
sizeof(edad)
```

tendrá normalmente el mismo resultado que:

```cpp
sizeof(int)
```

---

# Bytes y Bits

En la mayoría de sistemas actuales:

```text
1 byte = 8 bits
```

---

Por tanto:

| Bytes | Bits |
| ------ | ------ |
| 1 | 8 |
| 2 | 16 |
| 4 | 32 |
| 8 | 64 |

---

## Conversión

```text
bits = bytes × 8
```

---

# ¿Por Qué es Importante?

`sizeof` permite:

- Comprender el uso de memoria.
- Comparar tipos.
- Escribir código portable.
- Trabajar con archivos binarios.
- Trabajar con estructuras de datos.
- Calcular tamaños de almacenamiento.

---

# Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    std::cout << "char   : " << sizeof(char) << '\n';
    std::cout << "bool   : " << sizeof(bool) << '\n';
    std::cout << "int    : " << sizeof(int) << '\n';
    std::cout << "float  : " << sizeof(float) << '\n';
    std::cout << "double : " << sizeof(double) << '\n';

    return 0;
}
```

Posible salida:

```text
char   : 1
bool   : 1
int    : 4
float  : 4
double : 8
```

---

# Buenas Prácticas

## No Asumir Tamaños

Evitar razonamientos como:

```text
int siempre ocupa 4 bytes
```

porque no está garantizado por el estándar.

---

Preferir:

```cpp
sizeof(int)
```

cuando el tamaño sea importante.

---

## Utilizar sizeof Cuando el Tamaño Importe

Especialmente en:

- Memoria.
- Archivos binarios.
- Redes.
- Estructuras de datos.
- Programación de sistemas.

---

## Recordar que Devuelve Bytes

`sizeof` devuelve:

```text
bytes
```

no:

```text
bits
```

---

# Error Común

Pensar que:

```cpp
sizeof(variable)
```

devuelve la cantidad de datos almacenados.

No es así.

Devuelve el tamaño del tipo de la variable.

Ejemplo:

```cpp
int a{1};
int b{1000000};
```

---

```cpp
sizeof(a)
sizeof(b)
```

producen el mismo resultado porque ambos son:

```cpp
int
```

---

# Visualización General

```text
char
 │
 ▼
1 byte

bool
 │
 ▼
1 byte

int
 │
 ▼
Tamaño dependiente de la implementación

double
 │
 ▼
Tamaño dependiente de la implementación
```

---

## Resumen

- `sizeof` es un operador del lenguaje.
- Permite conocer el tamaño de tipos, variables y expresiones.
- El resultado se expresa en bytes.
- El valor devuelto tiene tipo `std::size_t`.
- `sizeof(char)` siempre vale `1`.
- Los tamaños concretos de muchos tipos dependen de la implementación.
- Es preferible consultar tamaños mediante `sizeof` en lugar de asumir valores.
- Comprender el tamaño de los tipos ayuda a entender el uso de memoria y la portabilidad del código.
