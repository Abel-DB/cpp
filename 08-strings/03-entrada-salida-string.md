# Entrada y Salida de Strings

## Introducción

Hasta ahora hemos utilizado:

```cpp
std::cout
```

para mostrar información en pantalla y:

```cpp
std::cin
```

para leer datos desde el teclado.

Cuando trabajamos con:

```cpp
std::string
```

aparece una diferencia importante entre:

```cpp
std::cin
```

y

```cpp
std::getline()
```

Comprender esta diferencia es fundamental para evitar errores al leer texto.

---

## Mostrar Strings

Los strings pueden mostrarse igual que otros tipos.

Ejemplo:

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre {"Juan"};

    std::cout << nombre << '\n';

    return 0;
}
```

Salida:

```text
Juan
```

---

## Mostrar Texto y Variables

```cpp
std::string nombre {"Ana"};

std::cout
    << "Nombre: "
    << nombre
    << '\n';
```

Salida:

```text
Nombre: Ana
```

---

# Leer Strings con std::cin

La forma más sencilla de leer texto es:

```cpp
std::cin >> nombre;
```

---

## Ejemplo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre {};

    std::cin >> nombre;

    std::cout << nombre << '\n';

    return 0;
}
```

Entrada:

```text
Juan
```

Salida:

```text
Juan
```

---

## Visualización

```text
Teclado
   │
   ▼
 Juan
   │
   ▼
std::cin
   │
   ▼
nombre
```

---

# Limitación de std::cin

`std::cin` deja de leer cuando encuentra un carácter de espacio en blanco:

```text
Espacio
Tabulación
Salto de línea
```

---

## Ejemplo

Código:

```cpp
std::string nombre {};

std::cin >> nombre;
```

Entrada:

```text
Juan Perez
```

Resultado:

```text
Juan
```

---

## Visualización

```text
Juan Perez
     │
     ▼
Primer espacio
     │
     ▼
Fin de lectura
```

---

Contenido almacenado:

```text
Juan
```

---

# ¿Por Qué Ocurre?

Porque:

```cpp
std::cin
```

extrae una palabra, no una línea completa.

---

Representación:

```text
Juan Perez Gomez
│
└── Solo "Juan"
```

---

# std::getline()

Para leer líneas completas utilizamos:

```cpp
std::getline()
```

---

## Sintaxis

```cpp
std::getline(std::cin, variable);
```

---

## Ejemplo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre_completo {};

    std::getline(std::cin, nombre_completo);

    std::cout << nombre_completo << '\n';

    return 0;
}
```

Entrada:

```text
Juan Perez
```

Salida:

```text
Juan Perez
```

---

## Visualización

```text
Juan Perez
     │
     ▼
getline()
     │
     ▼
Leer toda la línea
```

---

# Comparación

## std::cin

```cpp
std::cin >> nombre;
```

Entrada:

```text
Juan Perez
```

Resultado:

```text
Juan
```

---

## std::getline()

```cpp
std::getline(std::cin, nombre);
```

Entrada:

```text
Juan Perez
```

Resultado:

```text
Juan Perez
```

---

# ¿Cuándo Utilizar Cada Uno?

### Una sola palabra

```cpp
std::cin >> usuario;
```

---

Ejemplos:

```text
Juan
Madrid
C++
```

---

### Texto completo

```cpp
std::getline(std::cin, nombre_completo);
```

---

Ejemplos:

```text
Juan Perez
Ciudad de México
Hola Mundo
```

---

# Problema Común al Mezclar std::cin y std::getline()

Observa:

```cpp
int edad {};

std::string nombre {};

std::cin >> edad;

std::getline(std::cin, nombre);
```

---

Entrada:

```text
25
Juan Perez
```

---

Resultado inesperado:

```text
nombre = ""
```

---

# ¿Qué Ocurrió?

Después de:

```cpp
std::cin >> edad;
```

queda pendiente el carácter:

```text
'\n'
```

en el flujo de entrada.

---

Representación:

```text
25\n
  │
  ▼
getline() encuentra '\n'
  │
  ▼
Línea vacía
```

---

# Solución

Consumir el salto de línea pendiente antes de llamar a `std::getline()`.

```cpp
std::cin.ignore();
```

---

Ejemplo:

```cpp
int edad {};

std::string nombre {};

std::cin >> edad;

std::cin.ignore();

std::getline(std::cin, nombre);
```

---

Ahora funciona correctamente.

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre_completo {};

    std::cout
        << "Ingrese su nombre: ";

    std::getline(std::cin, nombre_completo);

    std::cout
        << "Hola "
        << nombre_completo
        << '\n';

    return 0;
}
```

Entrada:

```text
Juan Perez
```

Salida:

```text
Hola Juan Perez
```

---

# Flujo de Lectura

```text
Usuario
   │
   ▼
Teclado
   │
   ▼
getline()
   │
   ▼
std::string
```

---

# Convención Utilizada en Este Repositorio

Cuando se espere:

```text
Una sola palabra
```

se utilizará:

```cpp
std::cin
```

---

Cuando se espere:

```text
Texto completo
```

se utilizará:

```cpp
std::getline()
```

---

Ejemplos:

```cpp
std::string usuario {};
std::cin >> usuario;
```

---

```cpp
std::string nombre_completo {};
std::getline(std::cin, nombre_completo);
```

---

# Buenas Prácticas

## Utilizar getline() para Nombres Completos

Correcto:

```cpp
std::getline(std::cin, nombre_completo);
```

---

## Utilizar cin para Palabras Simples

Correcto:

```cpp
std::cin >> usuario;
```

---

## Tener Cuidado al Mezclar cin y getline()

Cuando se mezclen:

```cpp
std::cin
```

y

```cpp
std::getline()
```

puede ser necesario consumir el salto de línea pendiente.

Ejemplo:

```cpp
std::cin.ignore();
```

---

## Utilizar Mensajes Claros para el Usuario

Correcto:

```cpp
std::cout << "Ingrese su nombre completo: ";
```

---

# Error Común

Esperar que:

```cpp
std::cin >> nombre;
```

lea:

```text
Juan Perez
```

completo.

---

Realmente lee:

```text
Juan
```

---

Para leer toda la línea debe utilizarse:

```cpp
std::getline()
```

---

## Resumen

- Los strings pueden mostrarse utilizando `std::cout`.
- `std::cin` lee una palabra hasta encontrar un carácter de espacio en blanco.
- `std::getline()` lee una línea completa.
- Los espacios forman parte del texto leído por `std::getline()`.
- Mezclar `std::cin` y `std::getline()` puede producir resultados inesperados si queda un salto de línea pendiente.
- `std::cin.ignore()` permite consumir ese salto de línea.
- En programas reales, `std::getline()` suele utilizarse para nombres, frases y textos completos.
```**Principales correcciones aplicadas:**
- Cambié "Problema de `std::cin`" por "Limitación de `std::cin`" (es más preciso).
- Cambié "lee una palabra" por "extrae una palabra" (terminología más cercana a los flujos de C++).
- Corregí "Ciudad de Mexico" → "Ciudad de México".
- Aclaré que `'\n'` queda pendiente en el **flujo de entrada**, no en el buffer de forma simplificada.
- Ajusté algunas redacciones para mayor precisión técnica sin perder el nivel introductorio.
