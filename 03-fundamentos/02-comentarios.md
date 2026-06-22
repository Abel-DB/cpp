# Comentarios

## Introducción

Los comentarios son fragmentos de texto ignorados por el compilador.

Su propósito es documentar el código, explicar decisiones de diseño y facilitar el mantenimiento de los programas.

Los comentarios no afectan la ejecución del programa ni generan código máquina.

---

## ¿Por qué utilizar comentarios?

Los comentarios permiten:

* Explicar partes complejas del código.
* Documentar algoritmos.
* Justificar decisiones de diseño.
* Facilitar el trabajo en equipo.
* Mejorar la mantenibilidad del software.
* Generar documentación automática en proyectos grandes.

Un buen comentario puede ahorrar mucho tiempo a otros desarrolladores e incluso a uno mismo en el futuro.

---

## Comentarios de una línea

Se escriben utilizando dos barras (`//`).

Ejemplo:

```cpp
// Esto es un comentario

int edad {20};
```

También pueden colocarse al final de una instrucción.

```cpp
int edad {20}; // Edad del usuario
```

Todo lo que aparece después de `//` en la misma línea será ignorado por el compilador.

---

## Comentarios de múltiples líneas

Se escriben utilizando `/*` y `*/`.

Ejemplo:

```
/*
    Este comentario
    ocupa varias
    lineas.
*/
```

También pueden utilizarse para documentar bloques más extensos.

```
/*
    Calculo del area
    de un circulo.
*/
double area {3.1416 * radio * radio};
```

---

## Comparación

| Tipo          | Sintaxis           | Uso recomendado       |
| ------------- | ------------------ | --------------------- |
| Una línea     | `// comentario`    | Explicaciones breves  |
| Varias líneas | `/* comentario */` | Documentación extensa |

---

## Ejemplo práctico

```
#include <iostream>

int main()
{
    // Mostrar mensaje por pantalla
    std::cout << "Hola Mundo\n";

    return 0;
}
```

---

## Comentar temporalmente código

Durante el desarrollo es común desactivar temporalmente una instrucción sin eliminarla.

```
#include <iostream>

int main()
{
    // std::cout << "Mensaje deshabilitado\n";

    std::cout << "Hola Mundo\n";

    return 0;
}
```

Esto puede ser útil durante pruebas rápidas o depuración.

---

## Comentario de bloques

También es posible desactivar varias líneas mediante comentarios multilínea.

```
/*
std::cout << "Linea 1\n";
std::cout << "Linea 2\n";
std::cout << "Linea 3\n";
*/
```

Sin embargo, esta técnica debe utilizarse únicamente de forma temporal.

---

## Cómo escribe comentarios un desarrollador experimentado

Un error común es describir exactamente lo que ya puede leerse en el código.

Ejemplo poco útil:

```
// Incrementar contador
contador++;
```

El comentario no aporta información nueva.

Es mejor explicar la intención:

```
// Avanzar al siguiente elemento del recorrido
contador++;
```

Ahora el comentario aporta contexto.

---

## Buenas prácticas

### Explicar el porqué

Es preferible explicar la razón detrás del código.

Correcto:

```
// Se utiliza busqueda binaria para reducir la complejidad temporal
```

Menos útil:

```
// Incrementar i en 1
i++;
```

---

### Mantener comentarios actualizados

Los comentarios deben reflejar siempre el comportamiento real del programa.

Incorrecto:

```
// Multiplica dos numeros
return a + b;
```

El comentario y el código se contradicen.

---

### Escribir código claro primero

La primera herramienta para documentar un programa es un código bien escrito.

Preferir:

```
int edad_usuario {20};
```

en lugar de:

```
int x {20}; // Edad del usuario
```

Los nombres descriptivos reducen la necesidad de comentarios.

---

### Evitar comentarios redundantes

Evitar:

```
// Declarar variable edad
int edad {20};
```

Preferir:

```
int edad {20};
```

---

## Comentarios de documentación

En proyectos grandes suelen utilizarse herramientas como Doxygen.

Ejemplo:

```
/**
 * Calcula el area de un circulo.
 *
 * @param radio Radio del circulo.
 * @return Area calculada.
 */
double calcularArea(double radio);
```

Este tipo de comentarios permite generar documentación automáticamente.

---

## Comentarios TODO

Es habitual utilizar comentarios especiales para indicar trabajo pendiente.

Ejemplo:

```
// TODO: Implementar validacion de entrada
```

Estos comentarios ayudan a identificar tareas futuras.

---

## Comentarios FIXME

También pueden utilizarse para señalar problemas conocidos.

```
// FIXME: Posible division por cero
```

Indican código que requiere revisión o corrección.

---

## Qué no hacer

### No utilizar comentarios para ocultar código permanentemente

Incorrecto:

```
// int edad {20};
// int salario {1500};
// int antiguedad {5};
```

Si el código ya no se utiliza, normalmente debe eliminarse.

Git conservará el historial de cambios.

---

### No comentar código obvio

Incorrecto:

```
// Retornar cero
return 0;
```

El comentario no aporta información adicional.

---

### No escribir comentarios desactualizados

Los comentarios incorrectos son más peligrosos que no tener comentarios.

Siempre deben mantenerse sincronizados con el código.

---

## Comentarios y mantenimiento

A medida que un proyecto crece, la documentación se vuelve más importante.

Un comentario útil debe responder alguna de estas preguntas:

* ¿Por qué se hizo así?
* ¿Qué problema resuelve?
* ¿Qué restricción existe?
* ¿Qué debe tenerse en cuenta al modificar este código?

Si no responde ninguna de ellas, probablemente no sea necesario.

---

## Resumen

* Los comentarios son ignorados por el compilador.
* Existen comentarios de una línea (`//`) y multilínea (`/* */`).
* Deben utilizarse para explicar decisiones, contexto o restricciones.
* Un buen comentario explica el motivo, no lo que el código ya expresa claramente.
* Los nombres descriptivos reducen la necesidad de comentarios.
* Los comentarios deben mantenerse actualizados.
* Herramientas como Doxygen permiten generar documentación automáticamente.
* Comentarios especiales como `TODO` y `FIXME` ayudan durante el desarrollo y mantenimiento.
