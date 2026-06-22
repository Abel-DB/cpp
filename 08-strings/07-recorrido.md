# Recorrido de Strings

## Introducción

Hasta ahora hemos aprendido a acceder a caracteres individuales utilizando:

```cpp
[]
```

---

```cpp
at()
```

---

```cpp
front()
```

---

```cpp
back()
```

---

Sin embargo, en muchas situaciones necesitamos procesar todos los caracteres de una cadena.

Por ejemplo:

- Mostrar cada carácter.
- Contar letras.
- Buscar símbolos.
- Convertir texto.
- Validar entradas.

Para ello debemos recorrer el string.

---

## ¿Qué es Recorrer un String?

Recorrer significa:

```text
Visitar cada carácter
uno por uno.
```

---

Ejemplo:

```cpp
std::string nombre {"Juan"};
```

Representación:

```text
J u a n
│ │ │ │
▼ ▼ ▼ ▼
Visitar cada carácter
```

---

# Recorrido con for

La forma más común.

---

## Ejemplo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre {"Juan"};

    for (std::size_t i = 0;
         i < nombre.size();
         ++i)
    {
        std::cout
            << nombre[i]
            << '\n';
    }

    return 0;
}
```

Salida:

```text
J
u
a
n
```

---

## Visualización

```text
i = 0 → J
i = 1 → u
i = 2 → a
i = 3 → n
```

---

# Explicación

```cpp
i = 0
```

Comienza en el primer carácter.

---

```cpp
i < nombre.size()
```

Continúa mientras existan caracteres.

---

```cpp
++i
```

Avanza al siguiente índice.

---

# Recorrido Horizontal

```cpp
for (std::size_t i = 0;
     i < nombre.size();
     ++i)
{
    std::cout
        << nombre[i]
        << ' ';
}
```

Salida:

```text
J u a n
```

---

# Recorrido con while

También es posible utilizar:

```cpp
while
```

---

## Ejemplo

```cpp
std::string nombre {"Juan"};

std::size_t i = 0;

while (i < nombre.size())
{
    std::cout
        << nombre[i]
        << '\n';

    ++i;
}
```

Salida:

```text
J
u
a
n
```

---

# Range-Based For

Desde C++11 existe una forma más sencilla.

---

## Sintaxis

```cpp
for (char caracter : texto)
{
}
```

---

## Ejemplo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre {"Juan"};

    for (const char caracter : nombre)
    {
        std::cout
            << caracter
            << '\n';
    }

    return 0;
}
```

Salida:

```text
J
u
a
n
```

---

## Visualización

```text
nombre

J u a n
│ │ │ │
▼ ▼ ▼ ▼
caracter
```

---

# Ventajas del Range-Based For

Más simple:

```cpp
for (const char caracter : nombre)
```

---

No requiere:

```cpp
índices
size()
contador
```

---

Es ideal cuando solo necesitamos leer caracteres.

---

# Acceso al Índice

Si necesitamos conocer la posición actual:

```cpp
for (std::size_t i = 0;
     i < nombre.size();
     ++i)
{
}
```

---

es la mejor opción.

---

# Modificar Caracteres

También podemos modificar un string durante el recorrido.

---

## Con Índices

```cpp
std::string texto {"juan"};

for (std::size_t i = 0;
     i < texto.size();
     ++i)
{
    texto[i] = 'X';
}
```

Resultado:

```text
XXXX
```

---

# Recorrido por Referencia

Más adelante estudiaremos referencias.

Por ahora basta saber que:

```cpp
for (char& caracter : texto)
{
    caracter = 'X';
}
```

modifica directamente el string original.

---

## Importante

Sin la referencia:

```cpp
for (char caracter : texto)
{
    caracter = 'X';
}
```

la modificación afectaría únicamente a una copia del carácter y el string original permanecería sin cambios.

---

# Contar Caracteres

Ejemplo:

```cpp
std::string texto {"Hola"};

std::size_t contador = 0;

for (const char caracter : texto)
{
    ++contador;
}
```

Resultado:

```text
4
```

---

Aunque normalmente utilizaríamos:

```cpp
texto.size()
```

---

# Buscar un Carácter

```cpp
std::string texto {"Hola"};

for (const char caracter : texto)
{
    if (caracter == 'o')
    {
        std::cout
            << "Encontrado\n";
    }
}
```

Salida:

```text
Encontrado
```

---

# Mostrar Índice y Carácter

```cpp
std::string texto {"Juan"};

for (std::size_t i = 0;
     i < texto.size();
     ++i)
{
    std::cout
        << i
        << " -> "
        << texto[i]
        << '\n';
}
```

Salida:

```text
0 -> J
1 -> u
2 -> a
3 -> n
```

---

# Recorrido de String Vacío

```cpp
std::string texto {};
```

---

```cpp
for (const char caracter : texto)
{
}
```

---

Resultado:

```text
No se ejecuta ninguna iteración
```

---

# Comparación

## Con Índices

```cpp
for (std::size_t i = 0;
     i < texto.size();
     ++i)
{
}
```

Ventajas:

- Conoces la posición.
- Puedes acceder a cualquier índice.

---

## Range-Based For

```cpp
for (const char caracter : texto)
{
}
```

Ventajas:

- Más simple.
- Más legible.
- Menos errores.

---

# Convención Utilizada en Este Repositorio

Cuando no sea necesario el índice:

```cpp
for (const char caracter : texto)
{
}
```

---

Cuando sea necesario conocer posiciones:

```cpp
for (std::size_t i = 0;
     i < texto.size();
     ++i)
{
}
```

---

# Buenas Prácticas

## Utilizar Range-Based For para Lectura

Correcto:

```cpp
for (const char caracter : texto)
{
}
```

---

## Utilizar Índices Cuando Se Necesite la Posición

Correcto:

```cpp
texto[i]
```

---

## Utilizar std::size_t para Índices

Correcto:

```cpp
std::size_t i = 0;
```

---

## Evitar Índices Fuera de Rango

Incorrecto:

```cpp
texto[texto.size()]
```

---

Último índice válido:

```cpp
texto.size() - 1
```

---

# Error Común

Pensar que:

```cpp
i <= texto.size()
```

es correcto.

---

Ejemplo:

```cpp
for (std::size_t i = 0;
     i <= texto.size();
     ++i)
{
}
```

---

Problema:

```text
Última iteración inválida
```

Cuando:

```text
i == texto.size()
```

la expresión:

```cpp
texto[i]
```

accede fuera del rango válido.

---

Debe utilizarse:

```cpp
i < texto.size()
```

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string lenguaje {"C++"};

    for (const char caracter : lenguaje)
    {
        std::cout
            << caracter
            << '\n';
    }

    return 0;
}
```

Salida:

```text
C
+
+
```

---

## Resumen

- Recorrer un string significa visitar cada uno de sus caracteres.
- Puede realizarse mediante `for`, `while` o `range-based for`.
- El recorrido con índices permite conocer posiciones.
- El recorrido con `range-based for` es más simple y legible.
- Los caracteres pueden leerse y modificarse durante el recorrido.
- Para modificar caracteres con `range-based for` es necesario utilizar referencias.
- Los índices suelen representarse mediante `std::size_t`.
- El último índice válido es `size() - 1`.
- Recorrer strings es una habilidad fundamental para procesar texto en C++.
```**```
