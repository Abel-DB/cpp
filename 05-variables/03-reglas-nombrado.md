# Reglas de Nombrado

## Introducción

Elegir buenos nombres es una de las habilidades más importantes en programación.

Un identificador bien nombrado mejora:

* La legibilidad.
* El mantenimiento.
* La comprensión del código.
* La colaboración entre desarrolladores.

Además de las reglas impuestas por el lenguaje, es recomendable seguir una convención de nombres consistente en todo el proyecto.

---

## ¿Qué es un Identificador?

Un identificador es el nombre utilizado para representar elementos dentro de un programa.

Por ejemplo:

```cpp
int edad_usuario = 20;
```

Aquí:

```text
edad_usuario
```

es un identificador.

También son identificadores:

```cpp
precio_total
calcularTotal
Persona
MAX_USUARIOS
```

---

## Reglas del Lenguaje

### Debe comenzar con una letra o guion bajo

Correcto:

```cpp
edad
_nombre
precio
```

Incorrecto:

```cpp
2edad
100precio
```

---

### Puede contener números

Correcto:

```cpp
edad2
usuario123
contador1
```

---

### No puede contener espacios

Incorrecto:

```cpp
nombre completo
precio total
```

Correcto:

```cpp
nombre_completo
precio_total
```

---

### No puede contener símbolos especiales

Incorrecto:

```cpp
precio-total
edad@
nombre#
```

Correcto:

```cpp
precio_total
edad_usuario
nombre_cliente
```

---

### Distingue mayúsculas y minúsculas

Los siguientes identificadores son diferentes:

```cpp
edad
Edad
EDAD
```

Ejemplo:

```cpp
int edad = 20;
int Edad = 30;
```

---

### No puede utilizar palabras reservadas

Incorrecto:

```cpp
int class = 10;
int while = 20;
int return = 30;
```

---

## Convención Utilizada en Este Repositorio

Para mantener consistencia, todos los ejemplos seguirán la siguiente guía de estilo.

| Elemento      | Convención   |
| ------------- | ------------ |
| Variables     | `snake_case` |
| Funciones     | `camelCase`  |
| Clases        | `PascalCase` |
| Estructuras   | `PascalCase` |
| Namespaces    | `snake_case` |
| Enumeraciones | `PascalCase` |
| Valores enum  | `PascalCase` |
| Templates     | `PascalCase` |
| Constantes    | `UPPER_CASE` |
| Macros        | `UPPER_CASE` |
| Archivos      | `snake_case` |

---

## Variables

Las variables deben utilizar:

```text
snake_case
```

Ejemplos:

```cpp
int edad_usuario;
double salario_mensual;
bool esta_activo;
```

---

## Funciones

Las funciones deben utilizar:

```text
camelCase
```

Ejemplos:

```cpp
void mostrarMenu();
double calcularTotal();
bool validarUsuario();
```

---

## Clases y Estructuras

Las clases y estructuras deben utilizar:

```text
PascalCase
```

Ejemplos:

```cpp
class CuentaBancaria
{
};

struct Punto2D
{
};
```

---

## Namespaces

Los namespaces deben utilizar:

```text
snake_case
```

Ejemplos:

```cpp
namespace matematica
{
}

namespace utilidades_texto
{
}
```

---

## Enumeraciones

Las enumeraciones deben utilizar:

```text
PascalCase
```

Ejemplo:

```cpp
enum class EstadoConexion
{
    Desconectado,
    Conectado,
    Error
};
```

---

## Constantes

Las constantes deben utilizar:

```text
UPPER_CASE
```

Ejemplos:

```cpp
constexpr int MAX_USUARIOS{100};

constexpr double PI{3.1415926535};
```

---

## Macros

Las macros deben diferenciarse claramente del resto del código.

Ejemplos:

```cpp
#define MAX_BUFFER 1024

#define DEBUG_MODE
```

---

## Archivos

Los nombres de archivo utilizarán:

```text
snake_case
```

Ejemplos:

```text
control_flujo.md
operadores_logicos.md
tipos_datos.md
```

---

## Nombres Descriptivos

Evitar:

```cpp
int x;
int y;
int z;
```

Preferir:

```cpp
int cantidad_productos;
double precio_total;
int edad_usuario;
```

---

## Variables Booleanas

Las variables booleanas deberían expresar claramente una condición.

Ejemplos:

```cpp
bool esta_activo;
bool tiene_permiso;
bool es_mayor_de_edad;
bool usuario_autenticado;
```

Uso:

```cpp
if (esta_activo)
{
}
```

---

## Longitud de los Nombres

Evitar nombres demasiado cortos:

```cpp
int a;
```

---

Evitar nombres excesivamente largos:

```cpp
int cantidad_total_de_productos_vendidos_durante_el_mes_actual;
```

---

Buscar un equilibrio:

```cpp
int total_productos;
```

---

## Buenas Prácticas

### Utilizar nombres descriptivos

Preferir:

```cpp
double precio_total;
```

sobre:

```cpp
double p;
```

---

### Evitar abreviaturas innecesarias

Evitar:

```cpp
int num_est;
```

Preferir:

```cpp
int numero_estudiantes;
```

---

### Mantener consistencia

Una vez elegida una convención, debe utilizarse en todo el proyecto.

---

## Error Común

Mezclar convenciones dentro del mismo código.

Evitar:

```cpp
int EdadUsuario;
double precioTotal;
bool esta_activo;
```

Preferir:

```cpp
int edad_usuario;
double precio_total;
bool esta_activo;
```

---

## Resumen

* Los identificadores son nombres utilizados para representar elementos del programa.
* Deben cumplir las reglas sintácticas impuestas por C++.
* No pueden utilizar palabras reservadas.
* Este repositorio utiliza una guía de estilo uniforme para todos los ejemplos.
* Las variables utilizan `snake_case`.
* Las funciones utilizan `camelCase`.
* Las clases utilizan `PascalCase`.
* Las constantes y macros utilizan `UPPER_CASE`.
* Los nombres deben ser descriptivos, claros y consistentes.
