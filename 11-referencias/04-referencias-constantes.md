# Referencias Constantes

## Introducción

En los temas anteriores aprendimos que una referencia es un alias para una variable existente.

Ejemplo:

```cpp
int edad {25};

int& referencia_edad {edad};
```

---

La referencia permite:

```text
Leer
Modificar
```

la variable original.

---

Sin embargo, muchas veces queremos:

```text
Acceder a un valor
sin permitir modificaciones.
```

---

Para ello C++ proporciona:

```cpp
const
```

aplicado a referencias.

---

# ¿Qué es una Referencia Constante?

Una referencia constante es una referencia que no permite modificar el objeto a través de ella.

---

Sintaxis:

```cpp
const tipo& nombre {variable};
```

---

Ejemplo:

```cpp
const int& referencia_edad {edad};
```

---

Visualización:

```text
edad
 │
 ▼
25
 ▲
 │
referencia_edad

Lectura: Sí
Modificación: No
```

---

# Primer Ejemplo

```cpp
#include <iostream>

int main()
{
    int edad {25};

    const int& referencia_edad {edad};

    std::cout
        << referencia_edad
        << '\n';

    return 0;
}
```

Salida:

```text
25
```

---

La lectura funciona normalmente.

---

# Intentar Modificar

Observa:

```cpp
int edad {25};

const int& referencia_edad {edad};

referencia_edad = 30;
```

---

Resultado:

```text
Error de compilación
```

---

Porque:

```text
La referencia es constante.
```

---

# ¿La Variable Sigue Siendo Modificable?

Sí.

---

La restricción se aplica a:

```cpp
referencia_edad
```

---

No a:

```cpp
edad
```

---

Ejemplo:

```cpp
int edad {25};

const int& referencia_edad {edad};

edad = 40;
```

---

Ahora:

```cpp
std::cout
    << referencia_edad;
```

---

Salida:

```text
40
```

---

# Visualización

Antes:

```text
edad = 25
```

---

Después:

```cpp
edad = 40;
```

---

Resultado:

```text
edad = 40
referencia_edad = 40
```

---

Porque ambos siguen apuntando al mismo objeto.

---

# ¿Por Qué Existen?

Las referencias constantes son extremadamente utilizadas.

---

Permiten:

```text
Evitar copias
```

y al mismo tiempo:

```text
Proteger los datos
```

---

# Referencia Constante a Constante

También podemos referenciar una variable constante.

---

Ejemplo:

```cpp
const int EDAD_MINIMA {18};

const int& referencia_edad {EDAD_MINIMA};
```

---

Esto es correcto.

---

# Referencia Normal a Constante

Observa:

```cpp
const int EDAD_MINIMA {18};

int& referencia_edad {EDAD_MINIMA};
```

---

Resultado:

```text
Error de compilación
```

---

Porque una referencia modificable podría alterar una constante.

---

# Referencias Constantes y Literales

Una referencia normal requiere una variable.

---

Incorrecto:

```cpp
int& referencia_numero {10};
```

---

Resultado:

```text
Error de compilación
```

---

# Referencia Constante

Correcto:

```cpp
const int& referencia_numero {10};
```

---

Esto sí compila.

---

# ¿Por Qué Funciona?

El compilador crea un objeto temporal.

---

Visualización:

```text
10
 │
 ▼
objeto temporal
 │
 ▼
referencia constante
```

---

Por esta razón las referencias constantes son muy flexibles.

---

# Ejemplo con Expresiones

```cpp
const int& resultado {5 + 5};

std::cout
    << resultado
    << '\n';
```

Salida:

```text
10
```

---

También funciona correctamente.

---

# Uso Habitual en Funciones

Uno de los usos más importantes.

---

Observa:

```cpp
void mostrar_nombre(
    const std::string& nombre)
{
    std::cout
        << nombre
        << '\n';
}
```

---

Ventajas:

```text
No realiza copias
```

---

y además:

```text
La función no puede modificar el string.
```

---

# Comparación

## Paso por Valor

```cpp
void mostrar_nombre(
    std::string nombre)
{
}
```

---

Se crea una copia.

---

# Paso por Referencia Constante

```cpp
void mostrar_nombre(
    const std::string& nombre)
{
}
```

---

No se crea copia.

---

Resultado:

```text
Más eficiente
```

---

# Visualización

Paso por valor:

```text
string original
       │
       ▼
      copia
```

---

Referencia constante:

```text
string original
       ▲
       │
 referencia
```

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <string>

void mostrar_nombre(
    const std::string& nombre)
{
    std::cout
        << nombre
        << '\n';
}

int main()
{
    std::string nombre {"Juan"};

    mostrar_nombre(nombre);

    return 0;
}
```

Salida:

```text
Juan
```

---

# Buenas Prácticas

## Utilizar Referencias Constantes para Lectura

Correcto:

```cpp
const std::string& nombre
```

---

## Evitar Copias Innecesarias

Especialmente con:

```cpp
std::string
```

---

y más adelante:

```cpp
std::vector
```

---

## Utilizar Const Siempre que Sea Posible

Ayuda a prevenir modificaciones accidentales.

---

# Error Común

Pensar que:

```cpp
const int& referencia_edad {edad};
```

convierte a:

```cpp
edad
```

en constante.

---

Realidad:

```text
Solo la referencia es constante.
```

---

La variable original sigue siendo modificable.

---

# Visualización General

```text
Variable
    │
    ▼
Referencia Constante
    │
    ▼
Lectura permitida
    │
    ▼
Modificación prohibida
```

---

# Tabla Resumen

| Tipo | Lectura | Modificación |
|--------|----------|-------------|
| `int&` | Sí | Sí |
| `const int&` | Sí | No |
| `const int` | Sí | No |

---

## Resumen

- Una referencia constante utiliza la sintaxis `const tipo&`.
- Permite acceder a un objeto sin modificarlo.
- La variable original puede seguir siendo modificable.
- Puede enlazarse a constantes, literales y temporales.
- Es una herramienta fundamental para evitar copias innecesarias.
- Se utiliza ampliamente en parámetros de funciones.
- Mejora la seguridad y la eficiencia del código.
- Es una de las formas más comunes de utilizar referencias en C++ moderno.
