# Concatenación de Strings

## Introducción

Una de las operaciones más comunes cuando trabajamos con texto es unir varias cadenas.

Este proceso se conoce como:

```text
Concatenación
```

---

## ¿Qué es Concatenar?

Concatenar significa:

```text
Unir dos o más cadenas de texto
```

para formar una nueva cadena.

Ejemplo:

```text
"Hola"
+
" Mundo"
```

↓

```text
"Hola Mundo"
```

---

## Operador de Concatenación

En C++, los strings pueden concatenarse utilizando:

```cpp
+
```

---

## Ejemplo Básico

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string saludo {"Hola"};
    std::string nombre {"Juan"};

    std::string mensaje = saludo + nombre;

    std::cout << mensaje << '\n';

    return 0;
}
```

Salida:

```text
HolaJuan
```

---

## Visualización

```text
"Hola"
   +
"Juan"
   │
   ▼
"HolaJuan"
```

---

# Agregar Espacios

La concatenación no añade espacios automáticamente.

Ejemplo:

```cpp
std::string nombre {"Juan"};
std::string apellido {"Perez"};

std::string completo = nombre + apellido;
```

Resultado:

```text
JuanPerez
```

---

## Solución

Añadir el espacio manualmente.

```cpp
std::string completo =
    nombre + " " + apellido;
```

Resultado:

```text
Juan Perez
```

---

## Visualización

```text
"Juan"
   +
" "
   +
"Perez"
   │
   ▼
"Juan Perez"
```

---

# Concatenar Varias Cadenas

```cpp
std::string nombre {"Juan"};
std::string apellido {"Perez"};
std::string ciudad {"Madrid"};

std::string texto =
    nombre + " " +
    apellido + " - " +
    ciudad;
```

Resultado:

```text
Juan Perez - Madrid
```

---

# Concatenación con Literales

También es posible concatenar strings con literales de texto.

Ejemplo:

```cpp
std::string nombre {"Ana"};

std::string saludo =
    std::string{"Hola "} + nombre;
```

Resultado:

```text
Hola Ana
```

---

También:

```cpp
std::string saludo =
    nombre + "!";
```

Resultado:

```text
Ana!
```

---

## Nota

Cuando una expresión comienza con un literal de texto, suele ser conveniente convertirlo explícitamente a `std::string`.

Ejemplo:

```cpp
std::string saludo =
    std::string{"Hola "} + nombre;
```

---

# Operador +=

Además de:

```cpp
+
```

existe:

```cpp
+=
```

que permite añadir texto al string actual.

---

## Ejemplo

```cpp
std::string mensaje {"Hola"};

mensaje += " Mundo";
```

Resultado:

```text
Hola Mundo
```

---

## Visualización

Antes:

```text
Hola
```

---

Después:

```text
Hola Mundo
```

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string mensaje {"Hola"};

    mensaje += " Mundo";

    std::cout << mensaje << '\n';

    return 0;
}
```

Salida:

```text
Hola Mundo
```

---

# Construcción Progresiva

```cpp
std::string mensaje {};

mensaje += "Bienvenido";
mensaje += " ";
mensaje += "a";
mensaje += " ";
mensaje += "C++";
```

Resultado:

```text
Bienvenido a C++
```

---

## Visualización

```text
""
 │
 ▼
"Bienvenido"
 │
 ▼
"Bienvenido "
 │
 ▼
"Bienvenido a"
 │
 ▼
"Bienvenido a "
 │
 ▼
"Bienvenido a C++"
```

---

# Concatenar Variables

```cpp
std::string nombre {"Juan"};
std::string ciudad {"Madrid"};

std::string resultado =
    nombre + " vive en " + ciudad;
```

Resultado:

```text
Juan vive en Madrid
```

---

# Uso con cout

Muchas veces no es necesario crear un string nuevo.

Podemos escribir directamente:

```cpp
std::cout
    << nombre
    << " vive en "
    << ciudad
    << '\n';
```

Resultado:

```text
Juan vive en Madrid
```

---

# ¿Cuándo Concatenar?

Cuando necesitemos:

- Construir mensajes.
- Formar rutas.
- Generar reportes.
- Combinar información de varias variables.

---

Ejemplo:

```cpp
std::string usuario {"admin"};

std::string mensaje =
    std::string{"Bienvenido "} + usuario;
```

Resultado:

```text
Bienvenido admin
```

---

# Buenas Prácticas

## Utilizar += para Construcción Progresiva

Correcto:

```cpp
mensaje += "Hola";
mensaje += " Mundo";
```

---

## Agregar Espacios Manualmente

Recordar:

```cpp
+
```

no inserta espacios.

---

Correcto:

```cpp
nombre + " " + apellido
```

---

## Mantener la Legibilidad

Cuando la expresión sea larga:

```cpp
std::string texto =
    nombre + " " +
    apellido + " - " +
    ciudad;
```

---

## Utilizar std::cout Cuando No Sea Necesario Crear un String

Preferir:

```cpp
std::cout
    << nombre
    << " vive en "
    << ciudad
    << '\n';
```

si únicamente se desea mostrar el resultado.

---

# Error Común

Esperar que:

```cpp
nombre + apellido
```

produzca:

```text
Juan Perez
```

---

Realmente produce:

```text
JuanPerez
```

---

Los espacios deben añadirse explícitamente.

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre {"Juan"};
    std::string apellido {"Perez"};

    std::string nombre_completo =
        nombre + " " + apellido;

    std::cout
        << nombre_completo
        << '\n';

    return 0;
}
```

Salida:

```text
Juan Perez
```

---

## Resumen

- Concatenar significa unir cadenas de texto.
- El operador `+` permite crear nuevas cadenas.
- El operador `+=` permite añadir texto a una cadena existente.
- Los espacios deben agregarse manualmente.
- Es posible concatenar variables y literales de texto.
- La concatenación es una de las operaciones más utilizadas al trabajar con strings.
- `+=` suele ser conveniente cuando el texto se construye progresivamente.
- En muchos casos puede utilizarse `std::cout` directamente sin crear una cadena intermedia.
