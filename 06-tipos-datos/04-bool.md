# bool

## Introducción

El tipo:

```cpp
bool
```

se utiliza para representar valores lógicos.

Solo puede almacenar dos estados posibles:

```cpp
true
false
```

Es uno de los tipos más importantes del lenguaje porque constituye la base de:

- Condiciones.
- Comparaciones.
- Operadores lógicos.
- Control de flujo.

---

## ¿Qué Significa bool?

La palabra:

```text
bool
```

proviene de:

```text
boolean
```

en honor al matemático:

```text
George Boole
```

quien desarrolló el álgebra booleana utilizada en lógica y computación.

---

## Valores Posibles

Un objeto de tipo `bool` únicamente puede contener:

```cpp
true
```

o

```cpp
false
```

---

## Declaración

```cpp
bool esta_activo{true};
```

Representación:

```text
Nombre : esta_activo
Tipo   : bool
Valor  : true
```

---

## Uso Básico

```cpp
#include <iostream>

int main()
{
    bool esta_activo{true};

    std::cout << esta_activo << '\n';

    return 0;
}
```

Salida:

```text
1
```

---

## Representación en Salida

Por defecto:

```cpp
true
```

se imprime como:

```text
1
```

---

```cpp
false
```

se imprime como:

```text
0
```

---

## Mostrar true y false

Puede utilizarse:

```cpp
std::boolalpha
```

para mostrar los valores booleanos como texto.

Ejemplo:

```cpp
#include <iostream>

int main()
{
    bool esta_activo{true};

    std::cout << std::boolalpha;
    std::cout << esta_activo << '\n';

    return 0;
}
```

Salida:

```text
true
```

---

## Comparaciones

Las comparaciones producen valores de tipo:

```cpp
bool
```

Ejemplo:

```cpp
bool resultado{5 > 3};
```

Contenido:

```cpp
true
```

---

```cpp
bool resultado{10 == 20};
```

Contenido:

```cpp
false
```

---

## Visualización

```text
5 > 3
 │
 ▼
true
 │
 ▼
resultado
```

---

# Operadores Lógicos

Los operadores lógicos trabajan con valores booleanos.

---

## AND

```cpp
true && true
```

Resultado:

```cpp
true
```

---

```cpp
true && false
```

Resultado:

```cpp
false
```

---

## OR

```cpp
true || false
```

Resultado:

```cpp
true
```

---

```cpp
false || false
```

Resultado:

```cpp
false
```

---

## NOT

```cpp
!true
```

Resultado:

```cpp
false
```

---

```cpp
!false
```

Resultado:

```cpp
true
```

---

## Uso en if

Uno de los usos más importantes de `bool`.

```cpp
bool esta_activo{true};

if (esta_activo)
{
    std::cout << "Activo\n";
}
```

Salida:

```text
Activo
```

---

## Conversión desde int

Un entero puede convertirse automáticamente a `bool`.

### Cero

```cpp
bool activo{0};
```

Resultado:

```cpp
false
```

---

### Distinto de Cero

```cpp
bool activo{10};
```

Resultado:

```cpp
true
```

---

```cpp
bool activo{-5};
```

Resultado:

```cpp
true
```

---

## Tabla Resumen

| Valor Entero | Resultado |
| ------------ | --------- |
| `0` | `false` |
| Distinto de `0` | `true` |

---

## Conversión a int

```cpp
bool activo{true};

int valor{activo};
```

Resultado:

```text
1
```

---

```cpp
bool activo{false};

int valor{activo};
```

Resultado:

```text
0
```

---

# bool es un Tipo Entero Especial

Aunque normalmente se utiliza para representar valores lógicos, `bool` forma parte de los tipos enteros del lenguaje.

Por ello puede convertirse automáticamente a:

```cpp
int
```

y viceversa.

Sin embargo, conceptualmente debe utilizarse para representar estados lógicos y no como un número.

---

## Tamaño en Memoria

Un objeto de tipo:

```cpp
bool
```

debe ser capaz de almacenar los valores:

```cpp
true
false
```

Habitualmente ocupa:

```text
1 byte
```

aunque internamente solo represente dos estados posibles.

El tamaño exacto depende de la implementación.

---

## Variables Booleanas

Las variables booleanas deberían expresar una condición o estado.

Correcto:

```cpp
bool esta_activo;
bool tiene_permiso;
bool es_mayor_de_edad;
bool usuario_autenticado;
```

---

## Lectura Natural

```cpp
if (esta_activo)
{
}
```

---

```cpp
if (tiene_permiso)
{
}
```

---

```cpp
if (es_mayor_de_edad)
{
}
```

El código se vuelve más fácil de leer y comprender.

---

## Buenas Prácticas

### Utilizar Nombres Descriptivos

Preferir:

```cpp
bool tiene_permiso;
```

en lugar de:

```cpp
bool permiso;
```

---

### Evitar Comparaciones Innecesarias

Preferir:

```cpp
if (esta_activo)
{
}
```

en lugar de:

```cpp
if (esta_activo == true)
{
}
```

---

### Utilizar std::boolalpha al Depurar

```cpp
std::cout << std::boolalpha;
```

facilita la lectura de los resultados.

---

## Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    bool esta_activo{true};
    bool tiene_permiso{false};

    std::cout << std::boolalpha;

    std::cout << esta_activo << '\n';
    std::cout << tiene_permiso << '\n';

    return 0;
}
```

Salida:

```text
true
false
```

---

## Error Común

Confundir:

```cpp
=
```

con:

```cpp
==
```

Incorrecto:

```cpp
if (esta_activo = true)
{
}
```

---

Correcto:

```cpp
if (esta_activo)
{
}
```

o:

```cpp
if (esta_activo == true)
{
}
```

aunque normalmente la primera forma es preferible.

---

## Resumen

- `bool` representa valores lógicos.
- Solo puede almacenar `true` o `false`.
- Es la base de las condiciones y decisiones en un programa.
- Los operadores relacionales producen valores booleanos.
- Los operadores lógicos trabajan con valores booleanos.
- Por defecto, `true` se muestra como `1` y `false` como `0`.
- `std::boolalpha` permite mostrar `true` y `false` como texto.
- Los enteros pueden convertirse automáticamente a booleanos.
- `bool` es un tipo entero especial diseñado para representar estados lógicos.
- Las variables booleanas deberían expresar condiciones o estados.
