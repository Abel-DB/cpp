# Alcance (Scope)

## Introducción

El alcance (*scope*) determina desde qué partes del programa una variable puede ser utilizada.

En otras palabras, define dónde una variable es visible y accesible para el compilador.

Comprender el alcance es fundamental para evitar errores, reducir dependencias innecesarias y escribir programas más organizados.

---

## Idea Fundamental

Cuando una variable es declarada, no puede utilizarse en cualquier parte del programa.

Su visibilidad depende del bloque donde fue creada.

```text
Declaración
     │
     ▼
┌─────────────┐
│   Scope     │
└─────────────┘
     │
     ▼
¿Puede usarse aquí?
```

Si una instrucción intenta acceder a una variable fuera de su alcance, el compilador generará un error.

---

## Tipos de Alcance

Los tipos más comunes son:

```text
Scope
│
├── Global
├── Función (Local)
└── Bloque
```

---

# Alcance de Función (Local)

Una variable local se declara dentro de una función.

```cpp
int main()
{
    int edad{20};

    return 0;
}
```

Representación:

```text
main()
│
└── edad
```

La variable solo existe dentro de la función donde fue declarada.

---

## Visibilidad de una Variable Local

```cpp
int main()
{
    int edad{20};

    std::cout << edad << '\n';

    return 0;
}
```

La variable puede utilizarse desde su declaración hasta el final del bloque donde fue creada.

```text
main()
│
├── int edad{20};
│
├── Visible
│
├── Visible
│
└── Visible
```

---

## Error de Acceso

```cpp
int main()
{
    int edad{20};

    return 0;
}

void mostrar()
{
    std::cout << edad;
}
```

Resultado:

```text
error: 'edad' was not declared in this scope
```

La variable solo existe dentro de `main()`.

---

# Alcance de Bloque

Un bloque es cualquier región delimitada por llaves.

```cpp
{
}
```

Ejemplo:

```cpp
int main()
{
    {
        int numero{10};
    }

    return 0;
}
```

Representación:

```text
main()
│
└── bloque
     │
     └── numero
```

---

## Acceso Dentro del Bloque

```cpp
int main()
{
    {
        int numero{10};

        std::cout << numero << '\n';
    }

    return 0;
}
```

Salida:

```text
10
```

---

## Acceso Fuera del Bloque

```cpp
int main()
{
    {
        int numero{10};
    }

    std::cout << numero << '\n';

    return 0;
}
```

Resultado:

```text
error: 'numero' was not declared in this scope
```

---

## Bloques Anidados

```cpp
int main()
{
    int a{10};

    {
        int b{20};

        {
            int c{30};
        }
    }
}
```

Visibilidad:

```text
main()
│
├── a
│
└── bloque
    │
    ├── a
    ├── b
    │
    └── bloque
        │
        ├── a
        ├── b
        └── c
```

Las variables externas son visibles dentro de bloques internos.

Las variables internas no son visibles fuera de su bloque.

---

# Scope en if

```cpp
if (true)
{
    int valor{100};
}
```

La variable:

```cpp
valor
```

solo existe dentro del bloque del `if`.

---

## Ejemplo

```cpp
if (true)
{
    int valor{100};
}

std::cout << valor;
```

Resultado:

```text
error: 'valor' was not declared in this scope
```

---

# Scope en Bucles

Las variables declaradas dentro de un bucle también tienen alcance de bloque.

```cpp
for (int i{0}; i < 5; ++i)
{
}
```

La variable:

```cpp
i
```

solo existe dentro del bucle.

---

## Error

```cpp
for (int i{0}; i < 5; ++i)
{
}

std::cout << i;
```

Resultado:

```text
error: 'i' was not declared in this scope
```

---

## Regla Fundamental

Una variable puede acceder a elementos definidos en bloques externos.

Sin embargo, los elementos definidos dentro de un bloque no pueden utilizarse desde el exterior.

Permitido:

```text
Exterior
   │
   ▼
 Interior
```

No permitido:

```text
Interior
   │
   ▼
 Exterior
```

---

# Ocultamiento de Variables (Shadowing)

Una variable declarada en un bloque interno puede ocultar otra variable con el mismo nombre.

```cpp
int main()
{
    int numero{10};

    {
        int numero{20};

        std::cout << numero << '\n';
    }

    std::cout << numero << '\n';

    return 0;
}
```

Salida:

```text
20
10
```

Dentro del bloque interno se utiliza la variable más cercana.

---

## Representación

```text
main()
│
├── numero = 10
│
└── bloque
    │
    └── numero = 20
```

La variable interna oculta temporalmente a la externa.

---

# Alcance Global

Una variable global se declara fuera de cualquier función.

```cpp
#include <iostream>

int contador{0};

int main()
{
    std::cout << contador << '\n';

    return 0;
}
```

Representación:

```text
Programa
│
├── contador
│
├── main()
│
└── otras funciones
```

Generalmente puede utilizarse desde cualquier función del archivo declarada después de ella.

---

## Ejemplo

```cpp
#include <iostream>

int contador{10};

void mostrarContador()
{
    std::cout << contador << '\n';
}

int main()
{
    mostrarContador();

    return 0;
}
```

Salida:

```text
10
```

---

## Acceso a Variables Globales Ocultadas

El operador de resolución de ámbito:

```cpp
::
```

permite acceder a una variable global que ha sido ocultada por una variable local.

```cpp
#include <iostream>

int numero{10};

int main()
{
    int numero{20};

    std::cout << numero << '\n';
    std::cout << ::numero << '\n';

    return 0;
}
```

Salida:

```text
20
10
```

---

# Scope y Visibilidad

El alcance responde a la pregunta:

```text
¿Dónde puede utilizarse una variable?
```

Si una región del código se encuentra fuera de ese alcance, la variable será invisible para el compilador.

```text
Variable declarada
        │
        ▼
      Scope
        │
        ▼
     Visible
```

Fuera del alcance:

```text
Variable declarada
        │
        ▼
 Fuera del Scope
        │
        ▼
    Invisible
```

---

## Regla Práctica

Al declarar una variable, intenta hacerlo en el bloque más pequeño posible.

Preferir:

```cpp
if (usuario_autenticado)
{
    int intentos{0};
}
```

sobre:

```cpp
int intentos{0};

if (usuario_autenticado)
{
}
```

Reducir el alcance:

* Mejora la legibilidad.
* Reduce errores.
* Evita usos accidentales de la variable.

---

## Buenas Prácticas

### Mantener el Scope lo Más Reducido Posible

Preferir:

```cpp
void procesar()
{
    int resultado{0};
}
```

en lugar de:

```cpp
int resultado;

void procesar()
{
}
```

---

### Preferir Variables Locales

Las variables locales suelen ser más fáciles de comprender, probar y mantener.

Siempre que sea posible, preferir variables locales frente a variables globales.

---

### Evitar Variables Globales Innecesarias

Las variables globales pueden aumentar el acoplamiento entre distintas partes del programa y dificultar la depuración.

---

### Evitar Shadowing

Evitar:

```cpp
int total{100};

void calcular()
{
    int total{50};
}
```

porque puede generar confusión y dificultar la lectura del código.

---

## Visualización General

```text
Global
│
├── variable_global
│
├── main()
│   │
│   ├── variable_local
│   │
│   └── if
│       │
│       └── variable_bloque
│
└── otra_funcion()
```

---

## Scope vs Lifetime

Aunque suelen estar relacionados, alcance (*scope*) y tiempo de vida (*lifetime*) son conceptos diferentes.

El alcance responde a:

```text
¿Dónde puede utilizarse una variable?
```

El tiempo de vida responde a:

```text
¿Cuánto tiempo existe una variable durante la ejecución?
```

El siguiente tema estudiará el tiempo de vida (*lifetime*) con más detalle.

---

## Resumen

* El alcance (*scope*) determina dónde una variable puede utilizarse.
* Los alcances más comunes son global, de función y de bloque.
* Las variables locales solo son visibles dentro de la función donde fueron declaradas.
* Las variables de bloque solo son visibles dentro de sus llaves.
* Los bloques internos pueden acceder a variables externas.
* Los bloques externos no pueden acceder a variables internas.
* Una variable interna puede ocultar otra variable externa (*shadowing*).
* El operador `::` permite acceder a variables globales ocultadas.
* Mantener un alcance reducido mejora la legibilidad y disminuye errores.
* El alcance (*scope*) y el tiempo de vida (*lifetime*) son conceptos diferentes.
