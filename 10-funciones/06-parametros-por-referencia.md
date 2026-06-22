# Parámetros por Referencia

## Introducción

En temas anteriores aprendimos que las funciones pueden recibir información mediante parámetros.

Ejemplo:

```cpp
void mostrarNumero(int numero)
{
    std::cout << numero << '\n';
}
```

---

Cuando llamamos la función:

```cpp
int valor {10};

mostrarNumero(valor);
```

---

La función recibe una copia del valor.

Esto se conoce como:

```text
Paso por valor
```

---

En muchas situaciones esto es suficiente.

Sin embargo, a veces necesitamos que la función pueda modificar la variable original.

Para ello utilizamos:

```cpp
parámetros por referencia
```

---

# El Problema

Observa:

```cpp
#include <iostream>

void incrementar(int numero)
{
    ++numero;
}

int main()
{
    int valor {10};

    incrementar(valor);

    std::cout << valor << '\n';

    return 0;
}
```

Salida:

```text
10
```

---

Muchos principiantes esperan:

```text
11
```

---

Pero la función recibe una copia.

---

## Visualización

```text
valor = 10
    │
    ▼
copia = 10
    │
    ▼
incrementar()
```

---

La variable original no cambia.

---

# ¿Qué es una Referencia?

Una referencia es un alias para una variable existente.

---

Ejemplo:

```cpp
int valor {10};

int& referencia {valor};
```

---

Visualización:

```text
valor
  ▲
  │
referencia
```

---

Ambos nombres hacen referencia al mismo dato.

---

# Parámetros por Referencia

Podemos indicar que un parámetro sea una referencia utilizando:

```cpp
&
```

---

Sintaxis:

```cpp
void funcion(tipo& parametro)
{
}
```

---

Ejemplo:

```cpp
void incrementar(int& numero)
{
    ++numero;
}
```

---

# Primer Ejemplo

```cpp
#include <iostream>

void incrementar(int& numero)
{
    ++numero;
}

int main()
{
    int valor {10};

    incrementar(valor);

    std::cout << valor << '\n';

    return 0;
}
```

Salida:

```text
11
```

---

# ¿Qué Ocurrió?

La función ya no trabaja sobre una copia.

Trabaja directamente sobre:

```cpp
valor
```

---

Visualización:

```text
valor
  │
  ▼
incrementar()
  │
  ▼
valor modificado
```

---

# Comparación

## Paso por Valor

```cpp
void incrementar(int numero)
{
    ++numero;
}
```

---

Visualización:

```text
valor
  │
  └──► copia
           │
           ▼
      función
```

---

Resultado:

```text
La variable original no cambia.
```

---

## Paso por Referencia

```cpp
void incrementar(int& numero)
{
    ++numero;
}
```

---

Visualización:

```text
valor
  │
  ▼
función
```

---

Resultado:

```text
La variable original sí cambia.
```

---

# Ejemplo con Strings

```cpp
#include <iostream>
#include <string>

void agregarExclamacion(std::string& texto)
{
    texto += "!";
}

int main()
{
    std::string mensaje {"Hola"};

    agregarExclamacion(mensaje);

    std::cout << mensaje << '\n';

    return 0;
}
```

Salida:

```text
Hola!
```

---

# Múltiples Parámetros por Referencia

```cpp
void intercambiar(int& a, int& b)
{
    int temporal {a};

    a = b;
    b = temporal;
}
```

---

Uso:

```cpp
int x {10};
int y {20};

intercambiar(x, y);
```

---

Resultado:

```text
x = 20
y = 10
```

---

# Uso Habitual

Los parámetros por referencia suelen utilizarse cuando:

* Queremos modificar argumentos.
* Queremos evitar copias costosas.
* Necesitamos devolver varios resultados.

---

# Referencias Constantes

A veces queremos evitar copias pero impedir modificaciones.

Para ello utilizamos:

```cpp
const
```

---

Ejemplo:

```cpp
void mostrar(const std::string& texto)
{
    std::cout << texto << '\n';
}
```

---

La función recibe una referencia.

Pero no puede modificar:

```cpp
texto
```

---

# ¿Por Qué Utilizar const&?

Sin referencia:

```cpp
void mostrar(std::string texto)
{
}
```

---

Se crea una copia.

---

Con referencia constante:

```cpp
void mostrar(const std::string& texto)
{
}
```

---

No se crea copia.

---

Y además:

```text
La función no puede modificar el argumento.
```

---

# Ejemplo Completo

```cpp
#include <iostream>

void duplicar(int& numero)
{
    numero *= 2;
}

int main()
{
    int valor {15};

    duplicar(valor);

    std::cout << valor << '\n';

    return 0;
}
```

Salida:

```text
30
```

---

# Buenas Prácticas

## Utilizar Referencias Cuando Deba Modificarse el Argumento

Correcto:

```cpp
void incrementar(int& numero)
{
}
```

---

## Utilizar const& para Objetos Grandes de Solo Lectura

Correcto:

```cpp
void mostrar(const std::string& texto)
{
}
```

---

## Mantener Claridad

El lector debe entender fácilmente cuándo una función modifica sus argumentos.

---

# Error Común

Olvidar el símbolo:

```cpp
&
```

---

Incorrecto:

```cpp
void incrementar(int numero)
{
    ++numero;
}
```

---

Resultado:

```text
Solo se modifica una copia.
```

---

Correcto:

```cpp
void incrementar(int& numero)
{
    ++numero;
}
```

---

# Visualización General

```text
Paso por valor

Variable
   │
   ▼
 Copia
   │
   ▼
Función
```

---

```text
Paso por referencia

Variable
   │
   ▼
Función
```

---

# Tabla Comparativa

| Característica                     | Por valor | Por referencia |
| ---------------------------------- | --------- | -------------- |
| Crea copia                         | Sí        | No             |
| Modifica original                  | No        | Sí             |
| Usa `&`                            | No        | Sí             |
| Más eficiente para objetos grandes | No        | Sí             |

---

## Resumen

* Un parámetro por referencia utiliza el símbolo `&`.
* La función trabaja directamente sobre la variable original.
* No se crea una copia del argumento.
* Permite modificar variables fuera de la función.
* Es útil para evitar copias innecesarias.
* `const&` permite evitar copias sin permitir modificaciones.
* Debe utilizarse cuando la función necesite acceder directamente al dato original.
* Es una de las herramientas más importantes para escribir funciones eficientes en C++.
