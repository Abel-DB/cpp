# Aritmética de Punteros

## Introducción

Hasta ahora aprendimos:

```cpp
&variable
```

↓

```text
Obtiene una dirección de memoria.
```

---

```cpp
*puntero_numero
```

↓

```text
Accede al valor apuntado.
```

---

```cpp
nullptr
```

↓

```text
No apunta a ningún objeto.
```

---

También vimos que un puntero almacena una dirección.

---

Sin embargo, los punteros tienen una característica especial:

```text
Pueden desplazarse por memoria.
```

---

Para ello existe:

```cpp
Aritmética de punteros
```

---

# ¿Qué es la Aritmética de Punteros?

Permite mover un puntero hacia otras posiciones de memoria.

---

Ejemplo:

```cpp
++puntero_numero;
```

---

o:

```cpp
puntero_numero + 1
```

---

Visualización:

```text
Elemento 0
    │
    ▼
Elemento 1
    │
    ▼
Elemento 2
```

---

# Primer Ejemplo

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
┌────┬────┬────┐
│ 10 │ 20 │ 30 │
└────┴────┴────┘
  ^
  │
puntero_numero
```

---

# Incrementar un Puntero

```cpp
++puntero_numero;
```

---

Ahora apunta al siguiente elemento.

---

Visualización:

```text
┌────┬────┬────┐
│ 10 │ 20 │ 30 │
└────┴────┴────┘
       ^
       │
puntero_numero
```

---

# Ejemplo Completo

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

    int* puntero_numero {numeros};

    std::cout
        << *puntero_numero
        << '\n';

    ++puntero_numero;

    std::cout
        << *puntero_numero
        << '\n';

    return 0;
}
```

Salida:

```text
10
20
```

---

# ¿Qué Suma Realmente?

Observa:

```cpp
++puntero_numero;
```

---

No suma:

```text
1 byte
```

---

Suma:

```text
sizeof(tipo)
```

---

Si:

```cpp
int
```

ocupa:

```text
4 bytes
```

---

Entonces:

```cpp
puntero_numero + 1
```

↓

```text
Avanza 4 bytes.
```

---

# Visualización de Direcciones

Supongamos:

```cpp
int numeros[3];
```

---

Direcciones:

```text
1000
1004
1008
```

---

Entonces:

```cpp
puntero_numero
```

↓

```text
1000
```

---

```cpp
puntero_numero + 1
```

↓

```text
1004
```

---

```cpp
puntero_numero + 2
```

↓

```text
1008
```

---

# Sumar Varias Posiciones

```cpp
puntero_numero += 2;
```

---

Ejemplo:

```cpp
int numeros[5]
{
    10,
    20,
    30,
    40,
    50
};

int* puntero_numero {numeros};

puntero_numero += 2;

std::cout
    << *puntero_numero;
```

Salida:

```text
30
```

---

# Restar Posiciones

También podemos retroceder.

---

Ejemplo:

```cpp
--puntero_numero;
```

---

o:

```cpp
puntero_numero -= 1;
```

---

Visualización:

```text
Elemento 2
    │
    ▼
Elemento 1
```

---

# Acceso Mediante Offset

Recordemos:

```cpp
numeros[2]
```

---

Es equivalente a:

```cpp
*(puntero_numero + 2)
```

---

Ejemplo:

```cpp
int numeros[3]
{
    10,
    20,
    30
};

int* puntero_numero {numeros};

std::cout
    << *(puntero_numero + 2);
```

Salida:

```text
30
```

---

# Visualización

```text
puntero_numero
      │
      ▼
Elemento 0

puntero_numero + 2
      │
      ▼
Elemento 2
```

---

# Diferencia Entre Punteros

Dos punteros que pertenecen al mismo arreglo pueden restarse.

---

Ejemplo:

```cpp
int numeros[5];

int* puntero_inicio {numeros};
int* puntero_fin {numeros + 5};

std::cout
    << (puntero_fin - puntero_inicio);
```

Salida:

```text
5
```

---

Resultado:

```text
Cantidad de elementos
entre ambos punteros.
```

---

# Recorrer un Arreglo

Una aplicación clásica.

---

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

# La Posición Final

Observa:

```cpp
numeros + 3
```

---

Representa:

```text
Una posición después
del último elemento.
```

---

Es válido:

```cpp
puntero_numero < numeros + 3
```

---

Pero NO es válido:

```cpp
*(numeros + 3)
```

---

Porque ya está fuera del arreglo.

---

# Error Grave

```cpp
int numeros[3]
{
    10,
    20,
    30
};

std::cout
    << *(numeros + 10);
```

---

Resultado:

```text
Comportamiento indefinido
```

---

Porque:

```text
Se accede fuera del arreglo.
```

---

# Relación con los Arreglos

La aritmética de punteros existe principalmente porque:

```cpp
arreglo
```

y

```cpp
puntero
```

están estrechamente relacionados.

---

Más adelante veremos esta relación con más detalle.

---

# Buenas Prácticas

## Mantenerse Dentro de los Límites

Correcto:

```cpp
0
...
size - 1
```

---

## Comprender sizeof(tipo)

Recordar:

```cpp
puntero_numero + 1
```

↓

```text
Avanza un elemento,
no un byte.
```

---

## Evitar Accesos Fuera del Arreglo

Nunca asumir que una posición existe.

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
puntero_numero + 1
```

significa:

```text
Sumar un byte.
```

---

Realidad:

```text
Avanza sizeof(tipo).
```

---

Otro error:

```cpp
*(numeros + 100)
```

---

Resultado:

```text
Comportamiento indefinido.
```

---

# Visualización General

```text
Elemento 0
    │
    ▼
Elemento 1
    │
    ▼
Elemento 2
```

---

```cpp
++puntero_numero
```

↓

```text
Siguiente elemento.
```

---

# Tabla Resumen

| Expresión | Significado |
|------------|-------------|
| `++puntero_numero` | Siguiente elemento |
| `--puntero_numero` | Elemento anterior |
| `puntero_numero + n` | Avanza n elementos |
| `puntero_numero - n` | Retrocede n elementos |
| `*(puntero_numero + n)` | Accede al elemento n |
| `puntero_final - puntero_inicio` | Distancia entre elementos |

---

## Resumen

- Los punteros pueden desplazarse mediante aritmética de punteros.
- Al sumar o restar se avanza por elementos, no por bytes.
- La cantidad de bytes depende de `sizeof(tipo)`.
- Es posible recorrer arreglos utilizando punteros.
- Dos punteros del mismo arreglo pueden restarse.
- Nunca debe accederse fuera de los límites de un arreglo.
- La aritmética de punteros está estrechamente relacionada con los arreglos.
- Es una característica poderosa que debe utilizarse con cuidado.
