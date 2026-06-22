# Alias de Tipos

## Introducción

A medida que los programas crecen, algunos tipos pueden resultar largos o difíciles de leer.

Por ejemplo:

```cpp
unsigned long long
```

o

```cpp
std::vector<std::string>
```

Para mejorar la legibilidad, C++ permite crear nombres alternativos para tipos existentes.

Estos nombres alternativos se conocen como:

```text
Alias de tipos
```

---

## ¿Qué es un Alias?

Un alias es simplemente otro nombre para un tipo ya existente.

Ejemplo:

```cpp
using Entero = int;
```

Ahora:

```cpp
Entero edad = 25;
```

es equivalente a:

```cpp
int edad = 25;
```

---

## Visualización

```text
Entero
   │
   ▼
   int
```

---

# using

La forma moderna de crear alias es mediante:

```cpp
using
```

Sintaxis:

```cpp
using NombreAlias = Tipo;
```

---

## Ejemplo

```cpp
using Entero = int;
```

Uso:

```cpp
Entero edad = 25;
```

---

## Otro Ejemplo

```cpp
using Real = double;
```

Uso:

```cpp
Real precio = 19.99;
```

---

# Ejemplo Completo

```cpp
#include <iostream>

using Entero = int;
using Real = double;

int main()
{
    Entero edad = 25;
    Real precio = 19.99;

    std::cout << edad << '\n';
    std::cout << precio << '\n';
}
```

---

# typedef

Antes de C++11 se utilizaba:

```cpp
typedef
```

Sintaxis:

```cpp
typedef tipo nombre_alias;
```

---

## Ejemplo

```cpp
typedef int Entero;
```

---

## Comparación

### typedef

```cpp
typedef int Entero;
```

### using

```cpp
using Entero = int;
```

Ambos producen exactamente el mismo resultado.

---

## ¿Cuál Debo Utilizar?

En C++ moderno se recomienda:

```cpp
using
```

porque:

- Es más legible.
- Tiene una sintaxis consistente.
- Funciona mejor con plantillas.
- Es la alternativa moderna.

---

# Alias para Tipos Complejos

Uno de los usos más comunes.

Sin alias:

```cpp
std::vector<std::string> nombres;
```

Con alias:

```cpp
using ListaNombres = std::vector<std::string>;

ListaNombres nombres;
```

---

## Visualización

```text
ListaNombres
       │
       ▼
std::vector<std::string>
```

---

# Alias para Punteros

```cpp
using EnteroPtr = int*;
```

Uso:

```cpp
EnteroPtr ptr;
```

Equivale a:

```cpp
int* ptr;
```

---

# Alias y Expresión de Intención

Un alias puede utilizarse para comunicar mejor el significado de un valor.

Ejemplo:

```cpp
using Edad = int;
```

---

```cpp
Edad edad_usuario = 25;
```

Aunque sigue siendo un `int`, el propósito resulta más claro.

---

# Un Alias No Crea un Tipo Nuevo

Es importante comprender que:

```cpp
using Edad = int;
using Peso = int;
```

no crea tipos distintos.

Por ejemplo:

```cpp
Edad edad = 20;
Peso peso = 80;

edad = peso;
```

es perfectamente válido porque ambos siguen siendo:

```cpp
int
```

---

## Visualización

```text
Edad
 │
 ▼
int

Peso
 │
 ▼
int
```

---

# Alias de Plantillas

Una de las ventajas más importantes de `using` es que permite crear alias de plantillas.

Ejemplo:

```cpp
template<typename T>
using Vector = std::vector<T>;
```

Uso:

```cpp
Vector<int> numeros;
Vector<double> precios;
```

Esta sintaxis no puede expresarse de forma sencilla con `typedef`.

---

# ¿Cuándo Crear un Alias?

Es recomendable cuando:

- El tipo es largo.
- El alias mejora la comprensión.
- Se desea expresar una intención específica.
- Se quiere simplificar el uso de plantillas complejas.

---

# ¿Cuándo Evitar Alias?

Evitar alias que no aporten significado.

Por ejemplo:

```cpp
using Numero = int;
```

o

```cpp
using Valor = double;
```

si el nuevo nombre no mejora la claridad del código.

---

# Convención Utilizada en Este Repositorio

Los alias utilizarán:

```text
PascalCase
```

Ejemplos:

```cpp
using Edad = int;

using Salario = double;

using ListaNombres = std::vector<std::string>;
```

Esta es una convención específica de este repositorio.

---

# Buenas Prácticas

## Preferir using

Correcto:

```cpp
using ListaNombres = std::vector<std::string>;
```

---

## Utilizar Alias Significativos

Correcto:

```cpp
using Edad = int;
```

---

```cpp
using Poblacion = unsigned long long;
```

---

## No Abusar

Los alias deben mejorar la legibilidad, no ocultar información importante.

---

# Error Común

Pensar que:

```cpp
using Edad = int;
```

crea un tipo nuevo.

No es cierto.

---

```cpp
Edad
```

sigue siendo:

```cpp
int
```

Simplemente tiene otro nombre.

---

## Resumen

- Un alias es un nombre alternativo para un tipo existente.
- `using` es la forma moderna de crear alias.
- `typedef` es la forma tradicional.
- Los alias mejoran la legibilidad del código.
- Son especialmente útiles con tipos largos y plantillas complejas.
- Un alias no crea un tipo nuevo.
- En C++ moderno se recomienda utilizar `using`.
- Los alias deben aportar claridad y significado al código.
