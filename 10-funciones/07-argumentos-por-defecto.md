# Argumentos por Defecto

## Introducción

En el tema anterior estudiamos los parámetros de las funciones.

Ejemplo:

```cpp
void saludar(std::string nombre)
{
    std::cout
        << "Hola "
        << nombre
        << '\n';
}
```

---

Llamada:

```cpp
saludar("Juan");
```

---

En este caso es obligatorio proporcionar un argumento.

Si olvidamos hacerlo:

```cpp
saludar();
```

---

Resultado:

```text
Error de compilación
```

---

Sin embargo, existen situaciones donde un parámetro suele tener un valor habitual.

Por ejemplo:

```text
Cantidad = 1
Descuento = 0
Color = "Negro"
```

---

Para estos casos C++ proporciona:

```cpp
argumentos por defecto
```

---

# ¿Qué es un Argumento por Defecto?

Es un valor que se utiliza automáticamente cuando el argumento no se proporciona durante la llamada.

---

## Sintaxis

```cpp
tipo funcion(
    tipo parametro = valor);
```

---

Ejemplo:

```cpp
void saludar(
    std::string nombre = "Invitado")
{
}
```

---

# Primer Ejemplo

```cpp
#include <iostream>
#include <string>

void saludar(
    std::string nombre = "Invitado")
{
    std::cout
        << "Hola "
        << nombre
        << '\n';
}

int main()
{
    saludar();

    return 0;
}
```

Salida:

```text
Hola Invitado
```

---

# ¿Qué Ocurrió?

La llamada:

```cpp
saludar();
```

---

No proporciona argumentos.

---

Entonces la función utiliza:

```cpp
"Invitado"
```

---

Visualización:

```text
saludar()
    │
    ▼
nombre = "Invitado"
```

---

# Sobrescribir el Valor por Defecto

También podemos proporcionar un argumento.

---

Ejemplo:

```cpp
saludar("Juan");
```

---

Salida:

```text
Hola Juan
```

---

El valor por defecto se ignora.

---

Visualización

```text
Argumento proporcionado
         │
         ▼
Se utiliza ese valor
```

---

# Comparación

## Sin argumento

```cpp
saludar();
```

↓

```text
Hola Invitado
```

---

## Con argumento

```cpp
saludar("Ana");
```

↓

```text
Hola Ana
```

---

# Ejemplo Numérico

```cpp
void mostrarCantidad(
    int cantidad = 1)
{
    std::cout
        << cantidad
        << '\n';
}
```

---

Llamada:

```cpp
mostrarCantidad();
```

Salida:

```text
1
```

---

Llamada:

```cpp
mostrarCantidad(10);
```

Salida:

```text
10
```

---

# Múltiples Parámetros

Una función puede tener varios parámetros con valores por defecto.

---

Ejemplo:

```cpp
void crearPersonaje(
    std::string nombre = "Jugador",
    int nivel = 1)
{
    std::cout
        << nombre
        << " "
        << nivel
        << '\n';
}
```

---

Llamada:

```cpp
crearPersonaje();
```

Salida:

```text
Jugador 1
```

---

# Argumentos Parciales

Es posible proporcionar algunos argumentos y dejar que otros utilicen sus valores por defecto.

---

Ejemplo:

```cpp
void crearPersonaje(
    std::string nombre,
    int nivel = 1)
{
    std::cout
        << nombre
        << " "
        << nivel
        << '\n';
}
```

---

Llamada:

```cpp
crearPersonaje("Juan");
```

Salida:

```text
Juan 1
```

---

# Regla Importante

Los parámetros con valores por defecto deben aparecer al final.

---

Correcto:

```cpp
void funcion(
    int a,
    int b = 10);
```

---

Incorrecto:

```cpp
void funcion(
    int a = 10,
    int b);
```

---

Resultado:

```text
Error de compilación
```

---

# ¿Por Qué?

La llamada:

```cpp
funcion(5);
```

sería ambigua.

---

El compilador no podría determinar qué parámetro falta.

---

Por ello los argumentos por defecto siempre se colocan desde la derecha hacia la izquierda.

---

# Declaración y Definición

Normalmente los argumentos por defecto se colocan en la declaración.

---

Declaración:

```cpp
void saludar(
    std::string nombre = "Invitado");
```

---

Definición:

```cpp
void saludar(
    std::string nombre)
{
    std::cout
        << nombre
        << '\n';
}
```

---

# Ejemplo Completo

```cpp
#include <iostream>

void mostrar_linea(
    char caracter = '-',
    int cantidad = 10)
{
    for (int i {0};
         i < cantidad;
         ++i)
    {
        std::cout
            << caracter;
    }

    std::cout
        << '\n';
}

int main()
{
    mostrar_linea();

    mostrar_linea('*');

    mostrar_linea('#', 5);

    return 0;
}
```

Salida:

```text
----------
**********
#####
```

---

# Ventajas

## Menos Código

Sin argumentos por defecto:

```cpp
funcion(10, 20, 30);
```

---

Con argumentos por defecto:

```cpp
funcion();
```

---

## Interfaces Más Simples

Permiten ofrecer configuraciones habituales automáticamente.

---

## Mayor Flexibilidad

El usuario puede proporcionar solo los valores que necesite modificar.

---

# Buenas Prácticas

## Utilizar Valores Lógicos

Correcto:

```cpp
int cantidad = 1
```

---

```cpp
double descuento = 0.0
```

---

## Colocar los Parámetros por Defecto al Final

Correcto:

```cpp
void funcion(
    int valor,
    int limite = 100);
```

---

## Definirlos en la Declaración

Es la práctica habitual en proyectos reales.

---

# Error Común

Pensar que el valor por defecto se utiliza siempre.

---

Ejemplo:

```cpp
saludar("Ana");
```

---

Resultado:

```text
Hola Ana
```

---

El valor:

```cpp
"Invitado"
```

no se utiliza.

---

Porque se proporcionó un argumento explícito.

---

# Visualización General

```text
Llamada
   │
   ▼
¿Argumento presente?
   │
 ┌─┴─┐
 ▼   ▼
Sí   No
 │    │
 ▼    ▼
Usar  Valor
dato  por defecto
```

---

# Tabla Comparativa

| Llamada                | Resultado                   |
| ---------------------- | --------------------------- |
| `saludar();`           | Usa valor por defecto       |
| `saludar("Juan");`     | Usa argumento proporcionado |
| `mostrarCantidad();`  | Usa valor por defecto       |
| `mostrarCantidad(5);` | Usa argumento proporcionado |

---

## Resumen

* Los argumentos por defecto proporcionan valores automáticos para los parámetros.
* Se utilizan cuando el argumento no es especificado durante la llamada.
* Si se proporciona un argumento, el valor por defecto se ignora.
* Los parámetros con valores por defecto deben colocarse al final de la lista de parámetros.
* Normalmente se especifican en la declaración de la función.
* Permiten crear interfaces más simples y flexibles.
* Reducen la cantidad de llamadas repetitivas.
* Son una herramienta muy utilizada en bibliotecas y programas reales de C++.
