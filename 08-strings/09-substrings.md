# Substrings

## Introducción

Muchas veces no necesitamos trabajar con una cadena completa.

Por ejemplo:

```text
Extraer un nombre
Obtener una extensión de archivo
Leer una parte de una URL
Separar información
```

Para estos casos `std::string` proporciona:

```cpp
substr()
```

que permite obtener una porción de una cadena.

---

# ¿Qué es una Subcadena?

Una subcadena es una parte de otra cadena.

Ejemplo:

```text
Hola Mundo
```

Subcadenas posibles:

```text
Hola
Mundo
la
Mun
```

---

## Visualización

```text
Hola Mundo
│
├── Hola
├── Mundo
├── la
└── Mun
```

---

# substr()

Permite extraer una parte de un string.

---

## Sintaxis

```cpp
texto.substr(posicion, cantidad)
```

---

Donde:

```cpp
posicion
```

↓

```text
Índice inicial
```

---

```cpp
cantidad
```

↓

```text
Cantidad máxima de caracteres a extraer
```

---

# Ejemplo Básico

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string texto {"Hola Mundo"};

    std::string resultado =
        texto.substr(0, 4);

    std::cout
        << resultado
        << '\n';

    return 0;
}
```

Salida:

```text
Hola
```

---

## Visualización

```text
H o l a _ M u n d o
0 1 2 3 4 5 6 7 8 9

substr(0, 4)
│
▼
Hola
```

---

# Extraer Desde una Posición

```cpp
std::string texto {"Hola Mundo"};

std::string resultado =
    texto.substr(5, 5);
```

Resultado:

```text
Mundo
```

---

## Visualización

```text
Hola Mundo
     │
     ▼
   Mundo
```

---

# Omitiendo la Cantidad

Si no se especifica la cantidad:

```cpp
substr(posicion)
```

extrae desde esa posición hasta el final.

---

## Ejemplo

```cpp
std::string texto {"Hola Mundo"};

std::string resultado =
    texto.substr(5);
```

Salida:

```text
Mundo
```

---

## Visualización

```text
Hola Mundo
     │
     ▼
     Mundo
```

---

# Extraer una Palabra

```cpp
std::string nombre_completo
{
    "Juan Perez"
};

std::string nombre =
    nombre_completo.substr(0, 4);
```

Resultado:

```text
Juan
```

---

# Extraer Caracteres Centrales

```cpp
std::string texto {"Programacion"};
```

---

```cpp
std::string parte =
    texto.substr(3, 4);
```

Resultado:

```text
gram
```

---

## Visualización

```text
P r o g r a m a c i o n
0 1 2 3 4 5 6 7 8 9 10 11

substr(3, 4)
│
▼
g r a m
```

---

# Obtener la Extensión de un Archivo

```cpp
std::string archivo
{
    "documento.txt"
};
```

---

```cpp
std::string extension =
    archivo.substr(9);
```

Resultado:

```text
.txt
```

---

## Alternativa Más Robusta

```cpp
auto posicion =
    archivo.find('.');

if (posicion != std::string::npos)
{
    std::string extension =
        archivo.substr(posicion);
}
```

---

# Uso con find()

Una combinación muy frecuente.

---

## Ejemplo

```cpp
std::string correo
{
    "juan@gmail.com"
};
```

---

```cpp
auto posicion =
    correo.find('@');
```

---

Resultado:

```text
4
```

---

Ahora:

```cpp
std::string dominio =
    correo.substr(posicion + 1);
```

Resultado:

```text
gmail.com
```

---

## Visualización

```text
juan@gmail.com
    │
    ▼
    @
    │
    ▼
gmail.com
```

---

# Posición Inválida

Supongamos:

```cpp
std::string texto {"Hola"};
```

---

```cpp
texto.substr(100);
```

---

Problema:

```text
Posición fuera de rango
```

---

`substr()` lanzará una excepción de tipo:

```cpp
std::out_of_range
```

---

# Cantidad Mayor que el Tamaño Disponible

```cpp
std::string texto {"Hola"};

std::string resultado =
    texto.substr(1, 100);
```

---

Resultado:

```text
ola
```

---

No produce error.

Simplemente devuelve los caracteres disponibles hasta el final.

---

# Subcadena Vacía

```cpp
std::string texto {"Hola"};
```

---

```cpp
std::string resultado =
    texto.substr(0, 0);
```

Resultado:

```text
""
```

---

Longitud:

```text
0
```

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string texto {"Hola Mundo"};

    std::string palabra =
        texto.substr(5);

    std::cout
        << palabra
        << '\n';

    return 0;
}
```

Salida:

```text
Mundo
```

---

# Relación con Índices

Recordemos:

```text
Los índices comienzan en 0
```

---

Ejemplo:

```text
Hola Mundo
0123456789
```

---

Por ello:

```cpp
texto.substr(5)
```

comienza en:

```text
M
```

---

# Casos de Uso Reales

## Extraer Dominio

```text
juan@gmail.com
```

↓

```text
gmail.com
```

---

## Extraer Extensión

```text
imagen.png
```

↓

```text
.png
```

---

## Obtener Nombre

```text
Juan Perez
```

↓

```text
Juan
```

---

## Procesar Datos

```text
ID-2025-001
```

↓

```text
2025
```

---

# Convención Utilizada en Este Repositorio

Cuando sea necesario localizar una posición dentro de una cadena:

```cpp
auto posicion =
    texto.find(valor);
```

---

Y posteriormente:

```cpp
auto parte =
    texto.substr(posicion);
```

---

Esta combinación aparecerá frecuentemente en los ejemplos.

---

# Buenas Prácticas

## Utilizar find() Antes de substr()

Correcto:

```cpp
auto posicion =
    texto.find('@');
```

---

```cpp
if (posicion
    != std::string::npos)
{
}
```

---

## Verificar Posiciones

Evitar:

```cpp
texto.substr(100);
```

---

## Recordar que Devuelve un Nuevo String

```cpp
substr()
```

no modifica el string original.

---

## Utilizar Variables con Nombres Claros

Correcto:

```cpp
std::string dominio;
std::string extension;
std::string nombre_usuario;
```

---

# Error Común

Pensar que:

```cpp
substr()
```

altera el texto original.

---

Ejemplo:

```cpp
std::string texto {"Hola Mundo"};

texto.substr(5);
```

---

Resultado:

```cpp
texto
```

sigue siendo:

```text
Hola Mundo
```

---

Porque:

```cpp
substr()
```

devuelve una copia.

---

# Visualización General

```text
String
 │
 ▼
substr()
 │
 ▼
Nuevo String
```

---

```text
Hola Mundo
     │
     ▼
   Mundo
```

---

## Resumen

- Una subcadena es una parte de una cadena más grande.
- `substr()` permite extraer porciones de texto.
- El primer argumento indica la posición inicial.
- El segundo argumento indica la cantidad máxima de caracteres a extraer.
- Si se omite la cantidad, se extrae hasta el final.
- `substr()` devuelve un nuevo string.
- No modifica la cadena original.
- Una posición inicial inválida provoca una excepción.
- Es muy útil para procesar nombres, archivos, URLs y datos estructurados.
