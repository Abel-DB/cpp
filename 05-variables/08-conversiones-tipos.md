# Conversiones de Tipos

## Introducción

Los programas suelen trabajar con distintos tipos de datos.

Por esta razón, en muchas ocasiones es necesario transformar un valor de un tipo a otro.

Ejemplos:

```cpp
int
double
char
bool
```

C++ permite realizar estas conversiones de forma automática o explícita.

Comprender cómo funcionan es importante para evitar errores, pérdidas de información y comportamientos inesperados.

---

## ¿Qué es una Conversión de Tipo?

Una conversión de tipo consiste en transformar un valor de un tipo a otro.

Ejemplo:

```cpp
int numero{10};

double valor{numero};
```

Representación:

```text
10
│
▼
int
│
▼
double
│
▼
10.0
```

---

# Conversión Implícita

Una conversión implícita es realizada automáticamente por el compilador.

Ejemplo:

```cpp
int numero{10};

double valor{numero};
```

Resultado:

```text
10
▼
10.0
```

No es necesario indicar la conversión.

---

## Conversiones Implícitas Seguras

Generalmente son seguras cuando el tipo destino puede representar todos los valores del tipo origen.

Ejemplo:

```cpp
int numero{10};

double valor{numero};
```

Representación:

```text
int
 │
 ▼
double
```

No se pierde información.

---

## Promoción de Tipos

Durante muchas expresiones el compilador convierte automáticamente los operandos a tipos más amplios.

Ejemplo:

```cpp
char letra{'A'};

int codigo{letra};
```

Proceso:

```text
char
 │
 ▼
int
```

Este mecanismo se conoce como promoción de tipos (*type promotion*).

---

# Conversión Explícita

Una conversión explícita es solicitada directamente por el programador.

Ejemplo:

```cpp
double precio{19.99};

int entero{static_cast<int>(precio)};
```

Resultado:

```text
19
```

---

## Visualización

```text
19.99
  │
  ▼
static_cast<int>
  │
  ▼
19
```

La parte decimal se descarta.

---

# static_cast

Es la forma recomendada de realizar conversiones explícitas en C++ moderno.

Sintaxis:

```cpp
static_cast<TIPO>(valor)
```

Ejemplo:

```cpp
double precio{19.99};

int entero{static_cast<int>(precio)};
```

---

## ¿Por qué usar static_cast?

Hace que la conversión sea visible e intencionada.

Preferir:

```cpp
int numero{static_cast<int>(valor)};
```

en lugar de:

```cpp
int numero{(int)valor};
```

porque resulta más claro y seguro.

---

# Narrowing Conversion

Una conversión *narrowing* ocurre cuando el tipo destino no puede representar toda la información del tipo original.

Ejemplo:

```cpp
double precio{19.99};

int entero{static_cast<int>(precio)};
```

Resultado:

```text
19
```

Información perdida:

```text
0.99
```

---

## Visualización

```text
19.99
 │
 ▼
 int
 │
 ▼
19

Información perdida
```

---

## Otro Ejemplo

```cpp
int numero{300};

char letra{static_cast<char>(numero)};
```

El resultado depende de la implementación y puede no ser el esperado.

Esto ocurre porque `char` suele disponer de menos capacidad de almacenamiento que `int`.

---

# Inicialización Uniforme y Narrowing

Una ventaja de la inicialización uniforme es que detecta muchas conversiones potencialmente peligrosas.

Correcto:

```cpp
int numero{10};
```

---

Incorrecto:

```cpp
int numero{10.5};
```

Resultado:

```text
error: narrowing conversion
```

---

# Conversión entre Enteros y Decimales

## Entero → Decimal

```cpp
int numero{10};

double valor{numero};
```

Resultado:

```text
10.0
```

---

## Decimal → Entero

```cpp
double valor{10.75};

int numero{static_cast<int>(valor)};
```

Resultado:

```text
10
```

La parte decimal se descarta.

---

# Conversión entre char e int

Los caracteres poseen una representación numérica.

Ejemplo:

```cpp
char letra{'A'};

int codigo{letra};
```

Resultado habitual:

```text
65
```

---

## Visualización

```text
'A'
 │
 ▼
65
```

---

## Conversión Inversa

```cpp
int codigo{65};

char letra{static_cast<char>(codigo)};
```

Resultado:

```text
A
```

---

# Conversión entre bool e int

## bool → int

```cpp
bool activo{true};

int valor{activo};
```

Resultado:

```text
1
```

---

```cpp
bool activo{false};

int valor{activo};
```

Resultado:

```text
0
```

---

## int → bool

```cpp
bool activo{10};
```

Resultado:

```text
true
```

---

```cpp
bool activo{0};
```

Resultado:

```text
false
```

---

## Regla General

| Valor entero | Resultado booleano |
|-------------|-------------------|
| `0` | `false` |
| Distinto de `0` | `true` |

---

# Conversiones en Expresiones

El compilador puede realizar conversiones automáticas durante una operación.

Ejemplo:

```cpp
int a{10};
double b{5.5};

auto resultado{a + b};
```

Proceso:

```text
10
│
▼
10.0
│
▼
10.0 + 5.5
│
▼
15.5
```

Tipo resultante:

```cpp
double
```

---

# Conversiones Peligrosas

Especial atención a:

```cpp
double valor{1000000.99};

float numero{static_cast<float>(valor)};
```

---

```cpp
int numero{300};

char letra{static_cast<char>(numero)};
```

---

```cpp
long long numero{10000000000};

int copia{static_cast<int>(numero)};
```

Estas conversiones pueden provocar pérdida de información.

---

# Buenas Prácticas

## Utilizar static_cast

Preferir:

```cpp
int numero{static_cast<int>(valor)};
```

en lugar de:

```cpp
int numero{(int)valor};
```

---

## Utilizar Inicialización Uniforme

Preferir:

```cpp
int numero{10};
```

porque ayuda a detectar conversiones peligrosas.

---

## Evitar Conversiones Implícitas Innecesarias

Cuando la conversión sea importante para la lógica del programa, hacerla explícita.

---

## Prestar Atención al Narrowing

Especialmente al convertir:

```text
double → int
long long → int
int → char
double → float
```

---

## Regla Práctica

Si existe riesgo de pérdida de información:

```text
Realiza la conversión explícitamente.
```

---

## Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    double precio{19.99};

    int entero{static_cast<int>(precio)};

    char letra{static_cast<char>(65)};

    std::cout << entero << '\n';
    std::cout << letra << '\n';

    return 0;
}
```

Salida:

```text
19
A
```

---

## Resumen

* Una conversión transforma un valor de un tipo a otro.
* Las conversiones pueden ser implícitas o explícitas.
* El compilador realiza automáticamente muchas conversiones seguras.
* `static_cast` es la forma recomendada para conversiones explícitas.
* Algunas conversiones pueden provocar pérdida de información (*narrowing*).
* La inicialización uniforme ayuda a detectar conversiones peligrosas.
* Los caracteres poseen representación numérica.
* Los valores booleanos pueden convertirse a enteros y viceversa.
* Durante las expresiones el compilador realiza promociones de tipos automáticamente.
* Comprender las conversiones es fundamental para escribir programas correctos y seguros.
