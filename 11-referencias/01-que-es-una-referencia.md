# ¿Qué es una Referencia?

## Introducción

En el módulo de funciones estudiamos los parámetros por referencia.

Por ejemplo:

```cpp
void intercambiarValores(
    int& primer_numero,
    int& segundo_numero)
{
    int temporal {primer_numero};

    primer_numero = segundo_numero;
    segundo_numero = temporal;
}
```

---

Observa el símbolo:

```cpp
&
```

---

Ese símbolo indica que estamos trabajando con:

```text
Referencias
```

---

Hasta ahora las hemos utilizado sin estudiarlas formalmente.

En este módulo veremos qué son realmente las referencias y cómo funcionan.

---

# ¿Qué es una Referencia?

Una referencia es un alias para una variable existente.

---

Alias significa:

```text
Otro nombre para la misma variable.
```

---

## Visualización

```text
edad
 │
 ▼
25
```

---

Referencia:

```text
edad
 │
 ├────► 25
 │
referencia_edad
```

---

Ambos nombres hacen referencia al mismo dato.

---

# Primera Referencia

```cpp
#include <iostream>

int main()
{
    int edad {25};

    int& referencia_edad {edad};

    std::cout
        << edad
        << '\n';

    std::cout
        << referencia_edad
        << '\n';

    return 0;
}
```

Salida:

```text
25
25
```

---

# Sintaxis

```cpp
tipo& nombre_referencia {variable};
```

---

Ejemplo:

```cpp
int edad {25};

int& referencia_edad {edad};
```

---

Visualización:

```text
edad
 │
 ▼
25
 │
 ▲
referencia_edad
```

---

# Mismo Valor

Observa:

```cpp
int edad {25};

int& referencia_edad {edad};
```

---

Acceso mediante la variable original:

```cpp
std::cout
    << edad;
```

---

Acceso mediante la referencia:

```cpp
std::cout
    << referencia_edad;
```

---

Resultado:

```text
25
25
```

---

Porque ambas representan el mismo objeto.

---

# Modificar a Través de la Referencia

Una referencia no es una copia.

---

Ejemplo:

```cpp
int edad {25};

int& referencia_edad {edad};

referencia_edad = 30;
```

---

Ahora:

```cpp
std::cout
    << edad;
```

---

Salida:

```text
30
```

---

# Visualización

Antes:

```text
edad
 │
 ▼
25
```

---

Después:

```cpp
referencia_edad = 30;
```

---

Resultado:

```text
edad
 │
 ▼
30
```

---

# Modificar la Variable Original

También ocurre en sentido contrario.

---

Ejemplo:

```cpp
int edad {25};

int& referencia_edad {edad};

edad = 40;
```

---

Ahora:

```cpp
std::cout
    << referencia_edad;
```

---

Salida:

```text
40
```

---

Porque siguen siendo el mismo objeto.

---

# No es una Copia

Observa:

```cpp
int edad {25};

int copia_edad {edad};
```

---

Visualización:

```text
edad        copia_edad
 │              │
 ▼              ▼
25             25
```

---

Son variables distintas.

---

Modificar:

```cpp
copia_edad = 50;
```

---

No afecta a:

```cpp
edad
```

---

# Referencia

```cpp
int edad {25};

int& referencia_edad {edad};
```

---

Visualización:

```text
edad
 │
 ▼
25
 ▲
 │
referencia_edad
```

---

No existen dos valores.

Existe un único valor con dos nombres.

---

# Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    int temperatura {20};

    int& referencia_temperatura {temperatura};

    referencia_temperatura = 35;

    std::cout
        << temperatura
        << '\n';

    return 0;
}
```

Salida:

```text
35
```

---

# ¿Por Qué Existen?

Las referencias permiten:

- Evitar copias innecesarias.
- Modificar variables externas.
- Simplificar la sintaxis.
- Trabajar eficientemente con funciones.

---

Ejemplo:

```cpp
void actualizarEdad(int& edad)
{
    edad = 30;
}
```

---

La función modifica directamente la variable original.

---

Más adelante estudiaremos esto en profundidad.

---

# Referencias y Memoria

Conceptualmente podemos imaginar:

```text
edad
```

y

```text
referencia_edad
```

como dos nombres para la misma ubicación de memoria.

---

Visualización:

```text
┌───────┐
│  25   │
└───────┘
   ▲
   │
 edad

   ▲
   │
 referencia_edad
```

---

# Diferencia con una Variable Normal

## Variable

```cpp
int edad {25};

int copia_edad {edad};
```

---

Resultado:

```text
Dos variables
```

---

## Referencia

```cpp
int edad {25};

int& referencia_edad {edad};
```

---

Resultado:

```text
Una variable
Dos nombres
```

---

# Buenas Prácticas

## Utilizar Nombres Claros

Correcto:

```cpp
int& referencia_edad {edad};
```

---

Evitar:

```cpp
int& r {edad};
```

---

## Recordar que No es una Copia

Modificar la referencia modifica la variable original.

---

## Utilizar Inicialización

Correcto:

```cpp
int& referencia_edad {edad};
```

---

Las referencias siempre deben asociarse a una variable existente.

---

# Error Común

Pensar que una referencia crea una copia.

---

Incorrecto:

```cpp
int edad {25};

int& referencia_edad {edad};

referencia_edad = 50;
```

---

Esperar:

```text
edad = 25
```

---

Realidad:

```text
edad = 50
```

---

Porque ambos nombres representan el mismo objeto.

---

# Visualización General

```text
Variable
    │
    ▼
 Referencia
    │
    ▼
 Mismo objeto
```

---

# Tabla Resumen

| Concepto | Descripción |
|-----------|-------------|
| Referencia | Alias de una variable |
| Copia | Variable independiente |
| Modificar referencia | Modifica la variable original |
| Modificar original | Modifica lo visto por la referencia |

---

## Resumen

- Una referencia es un alias para una variable existente.
- Una referencia no crea una copia.
- Variable y referencia representan el mismo objeto.
- Modificar una referencia modifica la variable original.
- Modificar la variable original afecta a la referencia.
- Las referencias son fundamentales para trabajar con funciones eficientes.
- Se declaran utilizando el operador `&`.
- Constituyen una de las herramientas más importantes de C++ moderno.
