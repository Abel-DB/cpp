# Punteros Constantes

## Introducción

Hasta ahora hemos trabajado con punteros como:

```cpp
int numero {10};

int* puntero_numero {&numero};
```

---

Podemos:

```cpp
*puntero_numero = 20;
```

---

y también:

```cpp
puntero_numero = &otro_numero;
```

---

Es decir:

```text
Modificar el valor apuntado.
Modificar la dirección almacenada.
```

---

Sin embargo, en muchas situaciones queremos restringir alguno de estos comportamientos.

Para ello C++ proporciona:

```cpp
const
```

aplicado a punteros.

---

# ¿Por Qué Existen?

A veces necesitamos garantizar que:

```text
El valor no será modificado.
```

---

o que:

```text
La dirección no cambiará.
```

---

Esto ayuda a:

```text
Evitar errores.
Expresar intención.
Escribir código más seguro.
```

---

# Dos Conceptos Distintos

Cuando usamos:

```cpp
const
```

con punteros existen dos posibilidades:

---

```cpp
const int* puntero_numero;
```

↓

```text
Valor constante
```

---

```cpp
int* const puntero_numero;
```

↓

```text
Puntero constante
```

---

Son conceptos diferentes.

---

# Valor Constante

## Sintaxis

```cpp
const int* puntero_numero;
```

---

También es válido:

```cpp
int const* puntero_numero;
```

---

Ambas formas significan exactamente lo mismo.

---

# Ejemplo

```cpp
int numero {10};

const int* puntero_numero {&numero};
```

---

Ahora:

```cpp
*puntero_numero = 20;
```

---

Resultado:

```text
Error de compilación
```

---

Porque:

```text
El valor apuntado es de solo lectura.
```

---

# Visualización

```text
puntero_numero
      │
      ▼
     10

Lectura:  Sí
Escritura: No
```

---

# Lectura Permitida

Correcto:

```cpp
std::cout
    << *puntero_numero;
```

---

Salida:

```text
10
```

---

# Cambio de Dirección Permitido

Aunque el valor es constante:

```cpp
const int* puntero_numero;
```

---

La dirección sí puede cambiar.

---

Ejemplo:

```cpp
int numero_1 {10};
int numero_2 {20};

const int* puntero_numero {&numero_1};

puntero_numero = &numero_2;
```

---

Correcto.

---

Visualización:

```text
Antes

puntero_numero ──► numero_1

Después

puntero_numero ──► numero_2
```

---

# Puntero Constante

## Sintaxis

```cpp
int* const puntero_numero {&numero};
```

---

Ahora el puntero es constante.

---

Esto significa:

```text
La dirección no puede cambiar.
```

---

# Ejemplo

```cpp
int numero {10};

int* const puntero_numero {&numero};
```

---

Intentar:

```cpp
puntero_numero = nullptr;
```

---

Resultado:

```text
Error de compilación
```

---

Porque:

```text
La dirección es constante.
```

---

# Visualización

```text
puntero_numero
      │
      ▼
     10

Cambiar dirección: No
Modificar valor: Sí
```

---

# Modificar el Valor

Correcto:

```cpp
*puntero_numero = 20;
```

---

Resultado:

```cpp
numero == 20
```

---

Porque:

```text
El valor no es constante.
```

---

# Comparación

## Valor Constante

```cpp
const int* puntero_numero;
```

---

Permite:

```text
Cambiar dirección
```

---

No permite:

```text
Modificar valor
```

---

# Puntero Constante

```cpp
int* const puntero_numero;
```

---

Permite:

```text
Modificar valor
```

---

No permite:

```text
Cambiar dirección
```

---

# Ambos Constantes

También es posible combinar ambos conceptos.

---

## Sintaxis

```cpp
const int* const puntero_numero {&numero};
```

---

Resultado:

```text
No puede cambiar la dirección.
No puede modificar el valor.
```

---

# Visualización

```text
puntero_numero
      │
      ▼
     10

Cambiar dirección: No
Modificar valor: No
```

---

# Ejemplo

```cpp
int numero {10};

const int* const puntero_numero {&numero};
```

---

Incorrecto:

```cpp
*puntero_numero = 20;
```

---

Incorrecto:

```cpp
puntero_numero = nullptr;
```

---

Ambas operaciones producen:

```text
Error de compilación
```

---

# Lectura de Derecha a Izquierda

Una técnica útil.

---

Ejemplo:

```cpp
int* const puntero_numero;
```

---

Leemos:

```text
puntero_numero es un puntero constante a int.
```

---

Ejemplo:

```cpp
const int* puntero_numero;
```

---

Leemos:

```text
puntero_numero es un puntero a int constante.
```

---

# Uso Habitual en Funciones

Muy frecuente:

```cpp
void mostrarValor(
    const int* puntero_numero)
{
    std::cout
        << *puntero_numero;
}
```

---

Esto garantiza:

```text
La función no modificará el valor.
```

---

# Ejemplo Completo

```cpp
#include <iostream>

void mostrarValor(
    const int* puntero_numero)
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

# Relación con Referencias Constantes

Recordemos:

```cpp
void mostrarValor(
    const int& numero)
{
}
```

---

y:

```cpp
void mostrarValor(
    const int* puntero_numero)
{
}
```

---

Ambos permiten:

```text
Solo lectura.
```

---

La diferencia es que:

```cpp
const int*
```

puede recibir:

```cpp
nullptr
```

---

Una referencia no.

---

# Buenas Prácticas

## Utilizar const Siempre que Sea Posible

Correcto:

```cpp
const int* puntero_numero;
```

---

## Expresar Intención

Si la función no modifica el valor:

```cpp
const
```

debe aparecer en el parámetro.

---

## Evitar Modificaciones Accidentales

Las restricciones del compilador ayudan a detectar errores.

---

# Error Común

Confundir:

```cpp
const int* puntero_numero;
```

---

con:

```cpp
int* const puntero_numero;
```

---

Recordar:

```text
const int*
```

↓

```text
Valor constante
```

---

```text
int* const
```

↓

```text
Puntero constante
```

---

# Visualización General

```text
const int*
```

↓

```text
No modificar valor
```

---

```text
int* const
```

↓

```text
No cambiar dirección
```

---

```text
const int* const
```

↓

```text
No modificar nada
```

---

# Tabla Resumen

| Declaración | Modificar valor | Cambiar dirección |
|-------------|----------------|------------------|
| `int* puntero_numero` | Sí | Sí |
| `const int* puntero_numero` | No | Sí |
| `int* const puntero_numero` | Sí | No |
| `const int* const puntero_numero` | No | No |

---

## Resumen

- `const` puede aplicarse al valor apuntado o al propio puntero.
- `const int*` impide modificar el valor.
- `int* const` impide cambiar la dirección almacenada.
- `const int* const` impide ambas operaciones.
- Estas restricciones mejoran la seguridad y la claridad del código.
- Son muy utilizadas en parámetros de funciones.
- Ayudan al compilador a detectar modificaciones indebidas.
- Comprender la diferencia entre ambos tipos de const es fundamental al trabajar con punteros.
