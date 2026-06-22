# Inferencia de Tipos (`auto`)

## Introducción

Hasta ahora hemos declarado variables indicando explícitamente su tipo.

Ejemplos:

```cpp
int edad{25};

double precio{19.99};

std::string nombre{"Juan"};
```

Sin embargo, desde C++11 es posible pedir al compilador que deduzca automáticamente el tipo utilizando:

```cpp
auto
```

Esto permite escribir código más conciso y evita repetir información que el compilador ya conoce.

---

## ¿Qué es `auto`?

La palabra clave:

```cpp
auto
```

indica al compilador que determine el tipo de una variable a partir de su inicializador.

Ejemplo:

```cpp
auto edad{25};
```

El compilador deduce:

```cpp
int edad{25};
```

---

## ¿Cómo Funciona?

```cpp
auto numero{10};
```

Proceso:

```text
10
│
▼
int
│
▼
numero
```

El compilador analiza el valor inicial y selecciona el tipo correspondiente.

---

## Ejemplos Básicos

### Enteros

```cpp
auto edad{25};
```

Tipo deducido:

```cpp
int
```

---

### Números de Punto Flotante

```cpp
auto precio{19.99};
```

Tipo deducido:

```cpp
double
```

---

### Caracteres

```cpp
auto letra{'A'};
```

Tipo deducido:

```cpp
char
```

---

### Booleanos

```cpp
auto activo{true};
```

Tipo deducido:

```cpp
bool
```

---

### Cadenas de Texto

```cpp
auto mensaje{"Hola"};
```

Tipo deducido:

```cpp
const char*
```

Observa que **no** se deduce:

```cpp
std::string
```

Para obtener un `std::string`:

```cpp
auto mensaje = std::string{"Hola"};
```

---

## Visualización

```text
auto edad{25};
           │
           ▼
          int
```

---

```text
auto precio{10.5};
             │
             ▼
          double
```

---

## Inicialización Obligatoria

`auto` necesita un valor inicial para deducir el tipo.

Correcto:

```cpp
auto edad{20};
```

---

Incorrecto:

```cpp
auto edad;
```

Resultado:

```text
error: declaration of variable with deduced type requires an initializer
```

---

## `auto` y `const`

```cpp
const auto PI{3.141592};
```

Tipo deducido:

```cpp
const double
```

---

También:

```cpp
auto const PI{3.141592};
```

Es equivalente.

---

## `auto` y `constexpr`

```cpp
constexpr auto MAX_SIZE{100};
```

Tipo deducido:

```cpp
constexpr int
```

---

## Inferencia en Expresiones

La deducción se realiza a partir del resultado de la expresión.

```cpp
auto resultado{10 + 5};
```

Tipo deducido:

```cpp
int
```

---

```cpp
auto resultado{10 + 5.5};
```

Tipo deducido:

```cpp
double
```

---

## Ventajas de `auto`

### Reduce Código Repetitivo

Sin `auto`:

```cpp
std::string nombre{"Juan"};
```

Con `auto`:

```cpp
auto nombre = std::string{"Juan"};
```

---

### Facilita Refactorizaciones

```cpp
auto resultado = calcular_valor();
```

Si cambia el tipo retornado por la función, normalmente no es necesario modificar la variable.

---

### Muy Útil con Tipos Complejos

Más adelante veremos tipos como:

```cpp
std::vector<std::string>::iterator
```

Con `auto`:

```cpp
auto it = nombres.begin();
```

El código es más corto y fácil de leer.

---

## `auto` con Funciones

```cpp
int obtener_edad()
{
    return 25;
}

auto edad = obtener_edad();
```

Tipo deducido:

```cpp
int
```

---

## `auto` con Iteradores

Uno de los usos más habituales en C++ moderno.

Sin `auto`:

```cpp
std::vector<int>::iterator it = numeros.begin();
```

---

Con `auto`:

```cpp
auto it = numeros.begin();
```

---

## Limitaciones

### Debe Poder Deducirse el Tipo

Incorrecto:

```cpp
auto valor;
```

---

### No Siempre Mejora la Claridad

Ejemplo:

```cpp
auto resultado = obtener_datos();
```

A simple vista no sabemos qué tipo devuelve la función.

---

Más explícito:

```cpp
std::vector<int> resultado = obtener_datos();
```

---

## ¿Cuándo Utilizar `auto`?

Buena opción:

```cpp
auto edad{25};

auto precio{10.5};

auto activo{true};
```

El tipo es evidente.

---

También:

```cpp
auto it = contenedor.begin();
```

---

```cpp
auto resultado = a + b;
```

cuando el tipo resultante es obvio.

---

## ¿Cuándo Evitar `auto`?

Cuando el tipo aporta información importante.

Ejemplo:

```cpp
auto resultado = procesar_datos();
```

No sabemos qué devuelve la función.

---

Más claro:

```cpp
std::vector<int> resultado = procesar_datos();
```

---

## Regla Práctica

Utiliza `auto` cuando:

```text
El tipo es evidente o irrelevante.
```

---

Evita `auto` cuando:

```text
El tipo ayuda a comprender el código.
```

---

## `auto` No Significa Tipo Dinámico

Error frecuente:

```text
auto cambia de tipo durante la ejecución.
```

Esto es falso.

Ejemplo:

```cpp
auto edad{20};
```

El compilador deduce:

```cpp
int
```

y la variable seguirá siendo un entero durante toda su vida.

---

## Ejemplo Completo

```cpp
#include <iostream>
#include <string>

int main()
{
    auto edad{25};
    auto precio{99.99};
    auto activo{true};
    auto nombre = std::string{"Juan"};

    std::cout << edad << '\n';
    std::cout << precio << '\n';
    std::cout << activo << '\n';
    std::cout << nombre << '\n';

    return 0;
}
```

Salida:

```text
25
99.99
1
Juan
```

---

## Buenas Prácticas

### Utilizar `auto` cuando el tipo sea obvio

```cpp
auto contador{0};
```

---

### Utilizar `auto` con iteradores

```cpp
auto it = valores.begin();
```

---

### No ocultar tipos importantes

Evitar:

```cpp
auto datos = cargar_datos();
```

si el tipo es relevante para entender el código.

---

### Mantener consistencia

Dentro de un mismo proyecto conviene seguir una política uniforme sobre cuándo utilizar `auto`.

---

## Resumen

* `auto` permite que el compilador deduzca automáticamente el tipo de una variable.
* Fue introducido en C++11.
* Requiere una inicialización para funcionar.
* El tipo se determina durante la compilación.
* No crea variables dinámicas ni cambia de tipo durante la ejecución.
* Reduce código repetitivo y facilita refactorizaciones.
* Es especialmente útil con tipos largos o complejos.
* Debe utilizarse cuando mejore la legibilidad y evitarse cuando oculte información importante.
* Uno de sus usos más comunes es trabajar con iteradores y expresiones complejas.
