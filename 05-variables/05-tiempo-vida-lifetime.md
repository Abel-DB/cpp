# Tiempo de Vida (Lifetime)

## Introducción

El tiempo de vida (*lifetime*) determina cuánto tiempo existe un objeto en memoria durante la ejecución de un programa.

Es un concepto fundamental para comprender cómo C++ administra recursos, crea objetos y libera memoria.

Es importante no confundirlo con el alcance (*scope*).

Mientras que el alcance responde a:

```text
¿Dónde puede utilizarse una variable?
```

el tiempo de vida responde a:

```text
¿Cuándo se crea y cuándo se destruye?
```

---

## Scope vs Lifetime

Aunque están relacionados, son conceptos diferentes.

```text
Scope
│
└── ¿Dónde es visible?
```

```text
Lifetime
│
└── ¿Cuánto tiempo existe?
```

Dos variables pueden tener el mismo alcance y distintos tiempos de vida.

---

## Ciclo de Vida de un Objeto

Todo objeto pasa por las siguientes etapas:

```text
Declaración
     │
     ▼
Construcción
     │
     ▼
Uso
     │
     ▼
Destrucción
```

Cuando un objeto es destruido, los recursos asociados pueden ser liberados y la memoria reutilizada.

---

# Objetos con Almacenamiento Automático

La mayoría de las variables locales poseen almacenamiento automático.

Se crean al entrar en su bloque y se destruyen automáticamente al salir de él.

```cpp
int main()
{
    int edad{20};

    return 0;
}
```

Representación:

```text
Entrar a main()
      │
      ▼
Crear edad
      │
      ▼
Usar edad
      │
      ▼
Salir de main()
      │
      ▼
Destruir edad
```

---

## Ejemplo

```cpp
#include <iostream>

void mostrar()
{
    int numero{10};

    std::cout << numero << '\n';
}

int main()
{
    mostrar();
}
```

Cada llamada a la función genera un nuevo objeto:

```text
Llamada 1
│
├── Crear numero
└── Destruir numero

Llamada 2
│
├── Crear numero
└── Destruir numero
```

---

# Lifetime de Bloque

Los objetos declarados dentro de un bloque viven únicamente mientras dicho bloque exista.

```cpp
int main()
{
    {
        int valor{100};
    }

    return 0;
}
```

Representación:

```text
Entrar al bloque
        │
        ▼
Crear valor
        │
        ▼
Usar valor
        │
        ▼
Salir del bloque
        │
        ▼
Destruir valor
```

---

## Ejemplo Visual

```cpp
int main()
{
    int a{10};

    {
        int b{20};
    }

    return 0;
}
```

```text
Inicio main
│
├── Crear a
│
├── Entrar bloque
│   │
│   ├── Crear b
│   └── Destruir b
│
└── Destruir a
```

Observa que:

```text
b
```

se destruye antes que:

```text
a
```

porque pertenece a un bloque más interno.

---

# Objetos Globales

Los objetos globales poseen duración estática.

Se crean antes de que comience `main()` y se destruyen cuando finaliza el programa.

```cpp
int contador{0};

int main()
{
    return 0;
}
```

Representación:

```text
Inicio del programa
         │
         ▼
Crear contador
         │
         ▼
Ejecutar main()
         │
         ▼
Final del programa
         │
         ▼
Destruir contador
```

---

## Características

Los objetos globales:

* Se construyen antes de `main()`.
* Existen durante toda la ejecución.
* Se destruyen al finalizar el programa.

---

# Variables Estáticas Locales

Una variable local declarada con `static` posee alcance local, pero duración estática.

```cpp
#include <iostream>

void incrementar()
{
    static int contador{0};

    ++contador;

    std::cout << contador << '\n';
}
```

---

## Ejecución

```cpp
incrementar();
incrementar();
incrementar();
```

Salida:

```text
1
2
3
```

---

## ¿Qué Ocurre?

La variable:

```cpp
contador
```

solo se crea una vez.

```text
Primera llamada
│
├── Crear contador
└── contador = 1

Segunda llamada
│
└── contador = 2

Tercera llamada
│
└── contador = 3
```

---

## Lifetime de una Variable Estática

```text
Inicio del programa
         │
         ▼
Crear contador
         │
         ▼
Todas las llamadas
         │
         ▼
Fin del programa
         │
         ▼
Destruir contador
```

---

# Comparación General

| Tipo de objeto | Scope | Lifetime |
|----------------|--------|----------|
| Local | Función | Mientras se ejecuta la función |
| Bloque | Bloque | Mientras exista el bloque |
| Global | Archivo o programa | Toda la ejecución |
| Static local | Función | Toda la ejecución |

---

# Mismo Scope, Distinto Lifetime

```cpp
void funcion()
{
    int a{0};

    static int b{0};
}
```

Ambas variables poseen el mismo alcance:

```text
funcion()
```

Pero su tiempo de vida es diferente.

```text
a
│
└── Cada llamada
```

```text
b
│
└── Toda la ejecución
```

Esto demuestra que:

```text
Scope ≠ Lifetime
```

---

# Orden de Destrucción

Los objetos automáticos se destruyen en orden inverso a su creación.

```cpp
int main()
{
    int a{10};
    int b{20};
    int c{30};

    return 0;
}
```

Creación:

```text
a
b
c
```

Destrucción:

```text
c
b
a
```

Este comportamiento se conoce como:

```text
LIFO
(Last In, First Out)
```

y es la base de la gestión automática de recursos en C++.

---

# Lifetime y RAII

Uno de los principios más importantes de C++ es:

```text
RAII
(Resource Acquisition Is Initialization)
```

La idea es sencilla:

```text
Construcción
    │
    ▼
Adquirir recurso

Destrucción
    │
    ▼
Liberar recurso
```

Gracias a esto, los recursos pueden gestionarse automáticamente cuando los objetos entran y salen de su tiempo de vida.

Este concepto será estudiado con mayor profundidad más adelante.

---

# Error Común

Intentar utilizar un objeto después de que haya sido destruido.

```cpp
{
    int numero{10};
}
```

Después de salir del bloque:

```cpp
numero
```

ya no existe.

Su tiempo de vida ha terminado.

---

## Regla Práctica

Siempre que analices una variable, pregúntate:

```text
¿Dónde puedo utilizarla?
```

Eso corresponde a:

```text
Scope
```

---

```text
¿Cuándo se crea y cuándo se destruye?
```

Eso corresponde a:

```text
Lifetime
```

---

## Visualización General

```text
Programa
│
├── Variable Global
│   └── Vive toda la ejecución
│
├── main()
│   │
│   ├── Variable Local
│   │   └── Vive durante main()
│   │
│   └── Bloque
│       │
│       └── Variable de Bloque
│           └── Vive mientras exista el bloque
│
└── Fin del Programa
```

---

## Buenas Prácticas

### Mantener el Lifetime lo Más Corto Posible

Declarar variables cerca de donde se utilizan.

```cpp
if (condicion)
{
    int resultado{0};
}
```

---

### Preferir Objetos Automáticos

Siempre que sea posible, aprovechar la gestión automática que ofrece el lenguaje.

---

### Evitar Variables Globales Innecesarias

Los objetos globales viven durante toda la ejecución y pueden dificultar el mantenimiento del programa.

---

### Comprender el Comportamiento de static

Las variables estáticas conservan estado entre llamadas y deben utilizarse conscientemente.

---

## Resumen

* El lifetime determina cuánto tiempo existe un objeto en memoria.
* El scope determina dónde puede utilizarse.
* Los objetos automáticos viven mientras existe su bloque.
* Los objetos globales viven durante toda la ejecución del programa.
* Las variables `static` locales tienen alcance local pero duración estática.
* Los objetos automáticos se destruyen en orden inverso a su creación.
* Scope y lifetime son conceptos distintos.
* Comprender el lifetime es fundamental para entender la gestión de recursos y memoria en C++.
