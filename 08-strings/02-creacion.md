# Creación e Inicialización de Strings

## Introducción

Una vez que conocemos:

```cpp
std::string
```

es importante aprender las distintas formas de crear e inicializar cadenas de texto.

Aunque muchas veces utilizaremos una única forma, conocer las alternativas ayuda a comprender mejor el lenguaje y a leer código escrito por otros desarrolladores.

---

## Biblioteca Necesaria

Para trabajar con strings debemos incluir:

```cpp
#include <string>
```

---

# Declaración

Podemos declarar una variable sin proporcionarle un valor inicial explícito.

```cpp
std::string nombre;
```

Representación:

```text
nombre
   │
   ▼
String vacío
```

---

## Ejemplo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre;

    std::cout << nombre << '\n';

    return 0;
}
```

Salida:

```text

```

(No contiene texto.)

---

# Inicialización con Asignación

Una forma muy común de inicializar un string.

```cpp
std::string nombre = "Juan";
```

---

## Visualización

```text
nombre
   │
   ▼
"Juan"
```

---

## Ejemplo

```cpp
std::string ciudad = "Madrid";
```

---

```cpp
std::string lenguaje = "C++";
```

---

# Inicialización Uniforme

También podemos utilizar llaves.

```cpp
std::string nombre {"Juan"};
```

---

## Ejemplo

```cpp
std::string pais {"España"};
```

---

Esta forma es ampliamente utilizada en C++ moderno.

---

# Inicialización Directa

Otra alternativa válida.

```cpp
std::string nombre("Juan");
```

---

## Visualización

```text
nombre
   │
   ▼
"Juan"
```

---

Las tres formas siguientes producen el mismo resultado:

```cpp
std::string nombre = "Juan";
```

---

```cpp
std::string nombre {"Juan"};
```

---

```cpp
std::string nombre("Juan");
```

---

# String Vacío

También es posible crear explícitamente un string vacío.

```cpp
std::string texto = "";
```

---

```cpp
std::string texto {};
```

---

Representación:

```text
texto
 │
 ▼
""
```

---

# Inicialización con un Carácter

Podemos crear un string a partir de un carácter.

```cpp
std::string letra(1, 'A');
```

Resultado:

```text
A
```

---

## Visualización

```text
1 vez
 │
 ▼
'A'
 │
 ▼
"A"
```

---

# Repetición de Caracteres

También podemos generar cadenas repetidas.

```cpp
std::string linea(10, '-');
```

Resultado:

```text
----------
```

---

## Visualización

```text
'-'
 │
 ▼
10 veces
 │
 ▼
----------
```

---

# Strings Vacíos vs Strings con Espacios

String vacío:

```cpp
std::string texto = "";
```

---

Contenido:

```text
Nada
```

---

String con un espacio:

```cpp
std::string texto = " ";
```

---

Contenido:

```text
Un espacio
```

---

## Visualización

```text
""
```

↓

```text
0 caracteres
```

---

```text
" "
```

↓

```text
1 carácter
```

---

# Uso Habitual

La mayoría de los programas utilizan:

```cpp
std::string nombre = "Juan";
```

---

o:

```cpp
std::string nombre {"Juan"};
```

---

# auto y Strings

También puede utilizarse:

```cpp
auto nombre = std::string{"Juan"};
```

---

Tipo deducido:

```cpp
std::string
```

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string nombre {"Juan"};
    std::string ciudad {"Madrid"};
    std::string linea(10, '-');

    std::cout << nombre << '\n';
    std::cout << ciudad << '\n';
    std::cout << linea << '\n';

    return 0;
}
```

Salida:

```text
Juan
Madrid
----------
```

---

# Convención Utilizada en Este Repositorio

Se utilizará preferentemente:

```cpp
std::string nombre {};
```

para variables vacías.

---

Y:

```cpp
std::string nombre {"Juan"};
```

para variables inicializadas.

---

Ejemplos:

```cpp
std::string nombre_usuario {};
```

---

```cpp
std::string mensaje {"Bienvenido"};
```

---

# Buenas Prácticas

## Inicializar Siempre

Preferir:

```cpp
std::string nombre {};
```

---

o:

```cpp
std::string nombre {"Juan"};
```

---

## Utilizar Inicialización Uniforme

Recomendado:

```cpp
std::string nombre {"Juan"};
```

---

## Utilizar Nombres Descriptivos

Correcto:

```cpp
std::string nombre_completo;
```

---

```cpp
std::string correo_electronico;
```

---

# Error Común

Confundir:

```cpp
char letra = 'A';
```

con:

```cpp
std::string letra = "A";
```

---

```cpp
'A'
```

↓

```text
Un carácter
```

---

```cpp
"A"
```

↓

```text
Un string de un carácter
```

---

## Resumen

- Existen varias formas de crear e inicializar strings.
- La forma más común es `std::string nombre = "Juan";`.
- La inicialización uniforme (`{}`) es ampliamente utilizada en C++ moderno.
- Un string puede estar vacío.
- Es posible crear strings repitiendo caracteres.
- Los strings utilizan comillas dobles.
- Se recomienda inicializar las variables al declararlas.
- `std::string` es la herramienta principal para almacenar y manipular texto en C++.
