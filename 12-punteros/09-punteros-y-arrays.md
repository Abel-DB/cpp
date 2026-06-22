# Punteros y Arrays

## Introducción

En el tema anterior vimos que los punteros pueden desplazarse mediante:

```cpp
++puntero_numero
```

---

o:

```cpp
puntero_numero + n
```

---

Esto nos permitió recorrer elementos almacenados de forma contigua en memoria.

---

La razón es que existe una relación muy estrecha entre:

```cpp
Arrays
```

y

```cpp
Punteros
```

---

Comprender esta relación es fundamental para entender cómo funciona C++ internamente.

---

# Un Array en Memoria

Supongamos:

```cpp
int numeros[3]
{
    10,
    20,
    30
};
```

---

Visualización:

```text
┌────┬────┬────┐
│ 10 │ 20 │ 30 │
└────┴────┴────┘
```

---

Cada elemento ocupa una posición consecutiva en memoria.

---

# El Nombre del Array

Observa:

```cpp
numeros
```

---

En muchas expresiones:

```cpp
numeros
```

se convierte automáticamente en:

```cpp
&numeros[0]
```

---

Es decir:

```text
La dirección del primer elemento.
```

---

# Ejemplo

```cpp
int numeros[3]
{
    10,
    20,
    30
};

std::cout
    << numeros
    << '\n';
```

---

Salida aproximada:

```text
0x61ff08
```

---

Lo que se muestra es:

```text
Una dirección de memoria.
```

---

# Equivalencia Fundamental

Estas expresiones son equivalentes:

```cpp
numeros
```

---

```cpp
&numeros[0]
```

---

Visualización:

```text
numeros
   │
   ▼
Primer elemento
```

---

# Crear un Puntero

Podemos hacer:

```cpp
int* puntero_numero {numeros};
```

---

porque:

```cpp
numeros
```

se convierte automáticamente en:

```cpp
&numeros[0]
```

---

Visualización:

```text
numeros

┌────┬────┬────┐
│ 10 │ 20 │ 30 │
└────┴────┴────┘
  ^
  │
puntero_numero
```

---

# Acceso Mediante Índices

Forma habitual:

```cpp
numeros[1]
```

---

Resultado:

```text
20
```

---

# Acceso Mediante Punteros

Equivalente:

```cpp
*(numeros + 1)
```

---

Resultado:

```text
20
```

---

# Ejemplo

```cpp
#include <iostream>

int main()
{
    int numeros[3]
    {
        10,
        20,
        30
    };

    std::cout
        << numeros[1]
        << '\n';

    std::cout
        << *(numeros + 1)
        << '\n';

    return 0;
}
```

Salida:

```text
20
20
```

---

# Cómo Funciona

Recordemos:

```cpp
numeros
```

↓

```cpp
&numeros[0]
```

---

Entonces:

```cpp
numeros + 1
```

↓

```cpp
&numeros[1]
```

---

Y:

```cpp
*(numeros + 1)
```

↓

```cpp
numeros[1]
```

---

# Relación General

```cpp
numeros[i]
```

es equivalente a:

```cpp
*(numeros + i)
```

---

Ejemplo:

```cpp
numeros[2]
```

↓

```cpp
*(numeros + 2)
```

↓

```text
30
```

---

# Recorrer un Array con Punteros

```cpp
int numeros[3]
{
    10,
    20,
    30
};

for (
    int* puntero_numero {numeros};
    puntero_numero < numeros + 3;
    ++puntero_numero)
{
    std::cout
        << *puntero_numero
        << '\n';
}
```

Salida:

```text
10
20
30
```

---

# Arrays como Parámetros

Observa:

```cpp
void mostrarNumeros(
    int numeros[])
{
}
```

---

En realidad:

```cpp
int numeros[]
```

se transforma en:

```cpp
int* numeros
```

---

Por eso estas declaraciones son equivalentes:

```cpp
void mostrarNumeros(
    int numeros[])
```

---

```cpp
void mostrarNumeros(
    int* numeros)
```

---

# Ejemplo

```cpp
void mostrarNumeros(
    int* numeros)
{
    std::cout
        << numeros[0]
        << '\n';
}
```

---

Uso:

```cpp
int numeros[3]
{
    10,
    20,
    30
};

mostrarNumeros(numeros);
```

Salida:

```text
10
```

---

# Tamaño del Array

Observa:

```cpp
sizeof(numeros)
```

---

Fuera de la función:

```text
Tamaño completo del array.
```

---

Pero dentro de:

```cpp
void mostrarNumeros(
    int* numeros)
{
}
```

---

```cpp
sizeof(numeros)
```

devuelve:

```text
Tamaño del puntero.
```

---

Porque el array ya se convirtió en:

```cpp
int*
```

---

# Error Común

Intentar obtener el tamaño del array dentro de una función.

---

Ejemplo:

```cpp
void mostrarNumeros(
    int* numeros)
{
    std::cout
        << sizeof(numeros);
}
```

---

Resultado:

```text
Tamaño del puntero
```

---

No:

```text
Cantidad de elementos.
```

---

# Visualización

```text
main()

numeros[5]

       │
       ▼

mostrarNumeros()

int* numeros
```

---

El tamaño original se pierde.

---

# Solución Habitual

Enviar también la cantidad de elementos.

---

Ejemplo:

```cpp
void mostrarNumeros(
    int* numeros,
    int cantidad)
{
}
```

---

Uso:

```cpp
mostrarNumeros(
    numeros,
    5);
```

---

# Diferencia Entre Array y Puntero

Aunque están relacionados:

```cpp
No son lo mismo.
```

---

Array:

```cpp
int numeros[3];
```

---

Puntero:

```cpp
int* puntero_numero;
```

---

Un array:

```text
Reserva memoria para elementos.
```

---

Un puntero:

```text
Solo almacena una dirección.
```

---

# Ejemplo

```cpp
int numeros[3]
{
    10,
    20,
    30
};

int* puntero_numero {numeros};
```

---

Visualización:

```text
numeros

┌────┬────┬────┐
│ 10 │ 20 │ 30 │
└────┴────┴────┘

puntero_numero
      │
      ▼
Primer elemento
```

---

# Buenas Prácticas

## Recordar la Conversión Implícita

```cpp
numeros
```

↓

```cpp
&numeros[0]
```

---

## Enviar el Tamaño del Array

Correcto:

```cpp
mostrarNumeros(
    numeros,
    cantidad);
```

---

## Mantenerse Dentro de los Límites

Nunca acceder más allá del último elemento.

---

## Preferir Contenedores Modernos

Cuando sea posible:

```cpp
std::array
```

---

```cpp
std::vector
```

---

# Error Común

Pensar que:

```cpp
int numeros[5];
```

---

y:

```cpp
int* puntero_numero;
```

---

son exactamente iguales.

---

Realidad:

```text
Están relacionados,
pero no son el mismo tipo.
```

---

# Visualización General

```text
Array
  │
  ▼
Primer elemento
  │
  ▼
Puntero
```

---

```cpp
numeros[i]
```

↓

```cpp
*(numeros + i)
```

---

# Tabla Resumen

| Expresión | Significado |
|------------|-------------|
| `numeros` | Dirección del primer elemento |
| `&numeros[0]` | Dirección del primer elemento |
| `numeros[i]` | Elemento i |
| `*(numeros + i)` | Elemento i |
| `int numeros[]` | Se convierte en `int* numeros` al pasar a funciones |

---

## Resumen

- El nombre de un array suele convertirse en la dirección de su primer elemento.
- Un puntero puede apuntar al primer elemento de un array.
- `numeros[i]` es equivalente a `*(numeros + i)`.
- Los arrays y los punteros están estrechamente relacionados.
- Al pasar un array a una función, este se convierte en un puntero.
- El tamaño original del array se pierde durante esa conversión.
- Los arrays reservan memoria; los punteros solo almacenan direcciones.
- Comprender esta relación es fundamental para dominar los punteros en C++.
