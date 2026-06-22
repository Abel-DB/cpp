# Constantes y Expresiones Constantes

## Introducción

Hasta ahora hemos trabajado con variables cuyo valor puede modificarse durante la ejecución de un programa.

Sin embargo, existen situaciones donde queremos garantizar que un valor permanezca inalterable durante toda su existencia.

Para ello C++ proporciona mecanismos como:

```cpp
const
```

y

```cpp
constexpr
```

Ambos permiten crear objetos inmutables, aunque poseen objetivos y capacidades diferentes.

Comprender esta diferencia es fundamental para escribir código más seguro, expresivo y eficiente.

---

## ¿Qué es una Constante?

Una constante es un valor que no puede modificarse después de su inicialización.

Ejemplo:

```cpp
const int EDAD_MINIMA{18};
```

Una vez creada:

```cpp
EDAD_MINIMA
```

mantendrá siempre el mismo valor.

---

## Variables vs Constantes

Variable:

```cpp
int edad{20};

edad = 25;
```

Correcto.

---

Constante:

```cpp
const int EDAD_MINIMA{18};
```

Intentar modificarla:

```cpp
EDAD_MINIMA = 21;
```

Resultado:

```text
error: assignment of read-only variable
```

---

## Representación Conceptual

Variable:

```text
edad
 │
 ▼
20
 │
 ▼
25
```

---

Constante:

```text
EDAD_MINIMA
     │
     ▼
    18
```

No puede cambiar.

---

# const

La palabra clave:

```cpp
const
```

indica que un objeto no podrá modificarse directamente a través de ese identificador.

Ejemplo:

```cpp
const double PI{3.141592};
```

---

## Inicialización Obligatoria

Una constante debe inicializarse en el momento de su creación.

Correcto:

```cpp
const int MAX_SIZE{100};
```

---

Incorrecto:

```cpp
const int MAX_SIZE;
```

Resultado:

```text
error: uninitialized const
```

---

## Uso de Constantes

```cpp
#include <iostream>

int main()
{
    const int MAX_ESTUDIANTES{30};

    std::cout << MAX_ESTUDIANTES << '\n';

    return 0;
}
```

Salida:

```text
30
```

---

## Beneficios

### Evita modificaciones accidentales

```cpp
const int DIAS_SEMANA{7};
```

---

### Mejora la legibilidad

```cpp
const double PI{3.141592};
```

es más claro que repetir:

```cpp
3.141592
```

por todo el código.

---

### Centraliza valores importantes

```cpp
const int MAX_INTENTOS{3};
```

---

# constexpr

Introducido en C++11.

Permite indicar que un valor debe poder evaluarse durante la compilación.

Ejemplo:

```cpp
constexpr int MAX_SIZE{100};
```

---

## Diferencia Conceptual

```cpp
const
```

significa:

```text
Objeto inmutable
```

---

```cpp
constexpr
```

significa:

```text
Objeto inmutable

y además

Expresión constante evaluable en compilación
```

---

## Ejemplo

```cpp
constexpr int TAMANIO{50};
```

El compilador conoce este valor antes de ejecutar el programa.

---

## Visualización

```text
Código Fuente
       │
       ▼
Compilación
       │
       ▼
constexpr resuelto aquí
       │
       ▼
Ejecutable
```

---

## Uso en Arreglos

```cpp
constexpr int TAMANIO{10};

int numeros[TAMANIO];
```

El tamaño puede determinarse durante la compilación.

---

## Funciones constexpr

También pueden existir funciones evaluables durante la compilación.

```cpp
constexpr int cuadrado(int x)
{
    return x * x;
}
```

Uso:

```cpp
constexpr int resultado{cuadrado(5)};
```

Resultado:

```text
25
```

---

## Comparación Práctica

### const

```cpp
int valor{};

std::cin >> valor;

const int numero{valor};
```

El valor es constante después de crearse, pero solo se conoce durante la ejecución.

---

### constexpr

```cpp
constexpr int numero{100};
```

El valor es conocido por el compilador antes de ejecutar el programa.

---

## Tabla Comparativa

| Característica | const | constexpr |
|---------------|--------|------------|
| Inmutable | Sí | Sí |
| Debe ser expresión constante | No | Sí |
| Puede evaluarse en compilación | A veces | Siempre |
| Disponible desde | C++98 | C++11 |

---

## Nota sobre constinit

Desde C++20 existe:

```cpp
constinit int contador{0};
```

Su objetivo es garantizar la inicialización en tiempo de compilación de objetos con almacenamiento estático.

No reemplaza a:

```cpp
const
```

ni a:

```cpp
constexpr
```

y se estudiará más adelante.

---

## Convención Utilizada en Este Repositorio

Las constantes utilizarán:

```text
UPPER_CASE
```

Ejemplos:

```cpp
const int MAX_ESTUDIANTES{30};

constexpr double PI{3.141592};

constexpr int MAX_SIZE{100};
```

---

## Nota de Estilo

En muchos proyectos modernos de C++ se utiliza:

```cpp
constexpr int max_size{100};
```

siguiendo la misma convención utilizada para variables.

En este repositorio utilizaremos:

```text
UPPER_CASE
```

para identificar rápidamente valores constantes.

---

## ¿Cuándo Utilizar const?

Cuando el valor no debe cambiar después de ser creado.

Ejemplo:

```cpp
const std::string NOMBRE{"Juan"};
```

---

```cpp
const int EDAD_MINIMA{18};
```

---

## ¿Cuándo Utilizar constexpr?

Cuando el valor puede conocerse durante la compilación.

Ejemplo:

```cpp
constexpr int MAX_SIZE{100};
```

---

```cpp
constexpr double PI{3.141592};
```

---

## Regla Moderna

Si un valor puede ser `constexpr`, normalmente debería ser `constexpr`.

Preferir:

```cpp
constexpr int MAX_SIZE{100};
```

sobre:

```cpp
const int MAX_SIZE{100};
```

porque proporciona más información al compilador y permite utilizar el valor en más contextos.

---

## Ejemplo Completo

```cpp
#include <iostream>

constexpr double PI{3.141592};

int main()
{
    const int EDAD_MINIMA{18};

    std::cout << PI << '\n';
    std::cout << EDAD_MINIMA << '\n';

    return 0;
}
```

Salida:

```text
3.141592
18
```

---

## Error Común

Pensar que:

```cpp
const
```

y

```cpp
constexpr
```

son equivalentes.

Aunque ambos producen objetos inmutables:

```text
constexpr
```

impone requisitos adicionales relacionados con la evaluación en tiempo de compilación.

---

## Regla Práctica

Pregúntate:

```text
¿Este valor puede conocerse durante la compilación?
```

Si la respuesta es:

```text
Sí
```

considera utilizar:

```cpp
constexpr
```

Si la respuesta es:

```text
No
```

utiliza:

```cpp
const
```

---

## Resumen

* Una constante es un valor que no puede modificarse después de su inicialización.
* `const` crea objetos inmutables.
* Las constantes deben inicializarse al declararse.
* `constexpr` define expresiones constantes evaluables durante la compilación.
* Todo objeto `constexpr` es también inmutable.
* Si un valor puede ser `constexpr`, normalmente debería ser `constexpr`.
* `constinit` fue introducido en C++20 para objetos con almacenamiento estático.
* En este repositorio las constantes utilizan la convención `UPPER_CASE`.
* Las constantes mejoran la seguridad, la claridad y el mantenimiento del código.
