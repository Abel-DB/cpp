# Punteros y Funciones

## Introducción

Hasta ahora aprendimos:

```cpp
int numero {10};

int* puntero_numero {&numero};
```

---

Sabemos que un puntero almacena una dirección de memoria.

---

También aprendimos a acceder al valor apuntado mediante:

```cpp
*puntero_numero
```

---

Sin embargo, los punteros se vuelven especialmente útiles cuando trabajamos con funciones.

---

Permiten:

```text
Modificar variables externas.
Evitar copias innecesarias.
Trabajar con memoria directamente.
```

---

# Pasar un Puntero a una Función

Una función puede recibir un puntero como parámetro.

---

## Sintaxis

```cpp
void funcion(int* puntero_numero)
{
}
```

---

Visualización:

```text
Variable
   │
   ▼
Puntero
   │
   ▼
Función
```

---

# Primer Ejemplo

```cpp
#include <iostream>

void mostrarValor(int* puntero_numero)
{
    std::cout
        << *puntero_numero
        << '\n';
}

int main()
{
    int numero {10};

    mostrarValor(&numero);

    return 0;
}
```

Salida:

```text
10
```

---

# ¿Qué Ocurrió?

La llamada:

```cpp
mostrarValor(&numero);
```

envía:

```cpp
&numero
```

---

Es decir:

```text
La dirección de memoria.
```

---

La función recibe:

```cpp
int* puntero_numero
```

---

Y luego accede al valor mediante:

```cpp
*puntero_numero
```

---

# Visualización

```text
numero
  │
  ▼
 10
  ▲
  │
puntero_numero

mostrarValor()
```

---

# Modificar una Variable

Una función también puede modificar el objeto apuntado.

---

## Ejemplo

```cpp
#include <iostream>

void duplicar(int* puntero_numero)
{
    *puntero_numero *= 2;
}

int main()
{
    int numero {10};

    duplicar(&numero);

    std::cout
        << numero
        << '\n';

    return 0;
}
```

Salida:

```text
20
```

---

# ¿Por Qué Funciona?

La función recibe:

```cpp
&numero
```

---

Por lo tanto:

```cpp
puntero_numero
```

apunta directamente a:

```cpp
numero
```

---

Al ejecutar:

```cpp
*puntero_numero *= 2;
```

realmente estamos haciendo:

```cpp
numero *= 2;
```

---

# Visualización

```text
numero = 10

duplicar(&numero)

*puntero_numero *= 2

numero = 20
```

---

# Comparación con Paso por Valor

## Paso por Valor

```cpp
void duplicar(int numero)
{
    numero *= 2;
}
```

---

Uso:

```cpp
duplicar(numero);
```

---

Resultado:

```text
La variable original no cambia.
```

---

# Paso Mediante Puntero

```cpp
void duplicar(int* puntero_numero)
{
    *puntero_numero *= 2;
}
```

---

Uso:

```cpp
duplicar(&numero);
```

---

Resultado:

```text
La variable original sí cambia.
```

---

# Punteros y nullptr

Cuando una función recibe un puntero:

```cpp
void mostrarValor(int* puntero_numero)
{
}
```

---

Siempre existe la posibilidad de recibir:

```cpp
nullptr
```

---

# Verificación de Seguridad

Correcto:

```cpp
void mostrarValor(int* puntero_numero)
{
    if (puntero_numero == nullptr)
    {
        return;
    }

    std::cout
        << *puntero_numero
        << '\n';
}
```

---

Uso:

```cpp
mostrarValor(nullptr);
```

---

Resultado:

```text
No ocurre ningún error.
```

---

# Error Común

Incorrecto:

```cpp
void mostrarValor(int* puntero_numero)
{
    std::cout
        << *puntero_numero;
}
```

---

Llamada:

```cpp
mostrarValor(nullptr);
```

---

Resultado:

```text
Comportamiento indefinido
```

---

Porque:

```cpp
*nullptr
```

no es válido.

---

# Punteros como Parámetros de Salida

Una función puede devolver información mediante punteros.

---

## Ejemplo

```cpp
void obtenerDatos(
    int* edad,
    double* altura)
{
    *edad = 25;
    *altura = 1.75;
}
```

---

Uso:

```cpp
int edad {};
double altura {};

obtenerDatos(
    &edad,
    &altura);
```

---

Resultado:

```text
edad = 25
altura = 1.75
```

---

# Visualización

```text
obtenerDatos()

   │
   ├── edad
   │
   └── altura

Modifica ambas variables
```

---

# Múltiples Valores

Antes de las referencias y otras técnicas modernas era común utilizar punteros para devolver varios resultados.

---

Ejemplo:

```cpp
void calcular(
    int numero,
    int* cuadrado,
    int* cubo)
{
    *cuadrado = numero * numero;
    *cubo = numero * numero * numero;
}
```

---

Uso:

```cpp
int cuadrado {};
int cubo {};

calcular(
    3,
    &cuadrado,
    &cubo);
```

---

Resultado:

```text
cuadrado = 9
cubo = 27
```

---

# Punteros y Arreglos

Recordemos:

```cpp
int numeros[3]
{
    10,
    20,
    30
};
```

---

Al llamar:

```cpp
procesar(numeros);
```

---

Lo que realmente se envía es:

```text
La dirección del primer elemento.
```

---

Por eso muchas funciones trabajan con:

```cpp
int* puntero_numero
```

---

cuando procesan arreglos.

---

Más adelante profundizaremos en este tema.

---

# Referencias vs Punteros

Observa:

```cpp
void duplicar(int& numero)
{
    numero *= 2;
}
```

---

y:

```cpp
void duplicar(int* puntero_numero)
{
    *puntero_numero *= 2;
}
```

---

Ambas pueden modificar la variable original.

---

Sin embargo:

```cpp
int&
```

---

suele ser más seguro y fácil de usar.

---

Compararemos ambas técnicas en detalle más adelante.

---

# Ejemplo Completo

```cpp
#include <iostream>

void incrementar(int* puntero_numero)
{
    if (puntero_numero == nullptr)
    {
        return;
    }

    ++(*puntero_numero);
}

int main()
{
    int numero {10};

    incrementar(&numero);

    std::cout
        << numero
        << '\n';

    return 0;
}
```

Salida:

```text
11
```

---

# Buenas Prácticas

## Verificar nullptr

Correcto:

```cpp
if (puntero_numero == nullptr)
{
    return;
}
```

---

## Utilizar Nombres Claros

Correcto:

```cpp
int* puntero_numero {};
```

---

Evitar:

```cpp
int* p {};
```

---

## Usar Referencias Cuando Sea Posible

Las referencias suelen expresar mejor la intención.

---

## Utilizar Punteros Cuando nullptr Sea Válido

Ejemplo:

```cpp
procesar(nullptr);
```

---

Las referencias no permiten esto.

---

# Error Común

Olvidar desreferenciar.

---

Incorrecto:

```cpp
void duplicar(int* puntero_numero)
{
    puntero_numero *= 2;
}
```

---

Problema:

```text
Modifica la dirección,
no el valor apuntado.
```

---

Correcto:

```cpp
*puntero_numero *= 2;
```

---

# Visualización General

```text
Variable
   │
   ▼
Dirección
   │
   ▼
Función
   │
   ▼
Modificar valor
```

---

# Tabla Resumen

| Expresión | Significado |
|------------|-------------|
| `funcion(&numero)` | Envía la dirección |
| `int* puntero_numero` | Recibe un puntero |
| `*puntero_numero` | Accede al valor |
| `nullptr` | No apunta a nada |
| `if (puntero_numero)` | Verifica validez |

---

## Resumen

- Una función puede recibir punteros como parámetros.
- Los punteros permiten acceder y modificar variables externas.
- Para enviar un objeto se utiliza normalmente `&variable`.
- Para acceder al valor se utiliza `*puntero`.
- Siempre debe considerarse la posibilidad de recibir `nullptr`.
- Los punteros permiten devolver múltiples resultados mediante parámetros.
- Son una herramienta fundamental para trabajar con memoria y estructuras de datos.
- Comprender su uso en funciones es esencial para dominar C++.
