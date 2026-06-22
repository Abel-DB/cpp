# cout

## Introducción

La mayoría de los programas necesitan mostrar información al usuario.

En C++, la salida estándar se realiza mediante:

```cpp
std::cout
```

Este objeto permite enviar datos a la consola o terminal.

---

## ¿Qué Significa cout?

El nombre:

```text
cout
```

proviene de:

```text
character output
```

y forma parte del sistema de flujos (*streams*) de C++.

Conceptualmente:

```text
Programa
   │
   ▼
std::cout
   │
   ▼
Salida estándar
   │
   ▼
Terminal
```

`std::cout` es un objeto de tipo:

```cpp
std::ostream
```

especializado en enviar datos a la salida estándar.

---

## ¿Qué es un Stream?

Un *stream* (flujo) es una secuencia de datos que fluye desde una fuente hacia un destino.

En el caso de:

```cpp
std::cout
```

los datos fluyen desde el programa hacia la salida estándar.

Representación:

```text
Programa
   │
   ▼
Datos
   │
   ▼
std::cout
   │
   ▼
Pantalla
```

Más adelante estudiaremos otros flujos como:

```cpp
std::cin
```

para entrada de datos y flujos asociados a archivos.

---

## Biblioteca Necesaria

Para utilizar `std::cout` es necesario incluir:

```cpp
#include <iostream>
```

---

## Primer Ejemplo

```cpp
#include <iostream>

int main()
{
    std::cout << "Hola Mundo";

    return 0;
}
```

Salida:

```text
Hola Mundo
```

---

## Estructura Básica

```cpp
std::cout << "Hola Mundo";
```

Representación:

```text
std::cout
     │
     ▼
Enviar datos
     │
     ▼
Consola
```

---

## Operador de Inserción

El operador:

```cpp
<<
```

permite enviar información a `std::cout`.

Ejemplo:

```cpp
std::cout << "Hola";
```

---

Visualización:

```text
"Hola"
   │
   ▼
  <<
   │
   ▼
std::cout
   │
   ▼
Pantalla
```

---

## Mostrar Texto

```cpp
#include <iostream>

int main()
{
    std::cout << "Bienvenido";

    return 0;
}
```

Salida:

```text
Bienvenido
```

---

## Mostrar Números

```cpp
#include <iostream>

int main()
{
    std::cout << 25;

    return 0;
}
```

Salida:

```text
25
```

---

## Mostrar Variables

```cpp
#include <iostream>

int main()
{
    int edad = 25;

    std::cout << edad;

    return 0;
}
```

Salida:

```text
25
```

---

## Mostrar Múltiples Valores

```cpp
#include <iostream>

int main()
{
    int edad = 25;

    std::cout << "Edad: " << edad;

    return 0;
}
```

Salida:

```text
Edad: 25
```

---

## Encadenamiento

El operador `<<` puede utilizarse varias veces en una misma expresión.

Ejemplo:

```cpp
std::cout << "Edad: " << edad;
```

Representación:

```text
"Edad: "
     │
     ▼
   cout
     │
     ▼
   edad
     │
     ▼
 Pantalla
```

---

## Mostrar Diferentes Tipos

```cpp
#include <iostream>

int main()
{
    int edad = 25;
    double precio = 19.99;
    char letra = 'A';
    bool activo = true;

    std::cout << edad << '\n';
    std::cout << precio << '\n';
    std::cout << letra << '\n';
    std::cout << activo << '\n';

    return 0;
}
```

Posible salida:

```text
25
19.99
A
1
```

---

## Mostrar Texto y Variables

```cpp
#include <iostream>

int main()
{
    int edad = 25;

    std::cout << "La edad es: " << edad;

    return 0;
}
```

Salida:

```text
La edad es: 25
```

---

## Salida en Varias Líneas

```cpp
#include <iostream>

int main()
{
    std::cout << "Linea 1\n";
    std::cout << "Linea 2\n";

    return 0;
}
```

Salida:

```text
Linea 1
Linea 2
```

---

## ¿Qué es '\n'?

La secuencia:

```cpp
'\n'
```

representa un salto de línea.

Visualización:

```text
Texto
  │
  ▼
 \n
  │
  ▼
Nueva línea
```

---

## Ejemplo

```cpp
std::cout << "Hola\n";
std::cout << "Mundo\n";
```

Salida:

```text
Hola
Mundo
```

---

## '\n' vs std::endl

Ambos producen un salto de línea.

Ejemplo:

```cpp
std::cout << "Hola\n";
```

---

```cpp
std::cout << "Hola" << std::endl;
```

---

Resultado:

```text
Hola
```

en ambos casos.

---

### Diferencia

```cpp
'\n'
```

solo inserta un salto de línea.

---

```cpp
std::endl
```

inserta un salto de línea y además fuerza el vaciado (*flush*) del búfer de salida.

Representación:

```text
std::endl
│
├── Nueva línea
└── Flush
```

---

### ¿Qué es el Búfer?

La salida de `std::cout` normalmente no se envía inmediatamente a la pantalla.

Los datos suelen almacenarse temporalmente en una zona llamada:

```text
Buffer
```

Representación:

```text
Programa
   │
   ▼
 Buffer
   │
   ▼
 Pantalla
```

Esto mejora el rendimiento al reducir la cantidad de operaciones de entrada/salida.

---

### Recomendación

En la mayoría de los programas:

```cpp
'\n'
```

es la opción preferida porque evita vaciados innecesarios del búfer y suele ser más eficiente.

Preferir:

```cpp
std::cout << "Hola\n";
```

sobre:

```cpp
std::cout << "Hola" << std::endl;
```

salvo que realmente se necesite forzar la salida inmediata.

---

## Formato de Código

Cuando una línea es larga:

```cpp
std::cout << "Nombre: " << nombre << " Edad: " << edad;
```

puede escribirse así:

```cpp
std::cout
    << "Nombre: "
    << nombre
    << " Edad: "
    << edad;
```

Resultado idéntico.

---

## Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    int edad = 25;
    double salario = 2500.50;

    std::cout << "Edad: " << edad << '\n';
    std::cout << "Salario: " << salario << '\n';

    return 0;
}
```

Salida:

```text
Edad: 25
Salario: 2500.5
```

---

## Buenas Prácticas

### Utilizar '\n' para Saltos de Línea

Preferir:

```cpp
std::cout << "Hola\n";
```

sobre:

```cpp
std::cout << "Hola" << std::endl;
```

cuando no sea necesario forzar el vaciado del búfer.

---

### Mantener la Salida Legible

Correcto:

```cpp
std::cout
    << "Edad: "
    << edad
    << '\n';
```

---

### Mostrar Información Clara

Preferir:

```cpp
std::cout << "Edad: " << edad;
```

en lugar de:

```cpp
std::cout << edad;
```

cuando el contexto no sea evidente.

---

## Error Común

Olvidar incluir:

```cpp
#include <iostream>
```

o escribir:

```cpp
cout
```

sin el prefijo:

```cpp
std::
```

---

Posibles errores:

```text
'cout' is not a member of 'std'
```

o

```text
'cout' was not declared in this scope
```

dependiendo del compilador.

---

## Visualización General

```text
Dato
 │
 ▼
 <<
 │
 ▼
std::cout
 │
 ▼
Salida estándar
 │
 ▼
Terminal
```

---

## Resumen

- `std::cout` permite mostrar información en la salida estándar.
- Forma parte de la biblioteca `<iostream>`.
- Es un objeto de tipo `std::ostream`.
- Utiliza el operador `<<` para enviar datos a la salida.
- Puede mostrar texto, números, caracteres y variables.
- Es posible encadenar múltiples operaciones de salida.
- `'\n'` inserta un salto de línea.
- `std::endl` inserta un salto de línea y fuerza un *flush* del búfer.
- En la mayoría de los casos se prefiere `'\n'`.
- `std::cout` es una de las herramientas fundamentales para interactuar con el usuario en programas de consola.
