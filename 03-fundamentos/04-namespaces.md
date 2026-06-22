# Namespaces

## Introducción

A medida que los programas crecen, es común que diferentes partes del código utilicen los mismos nombres para variables, funciones, clases o constantes.

Los *namespaces* permiten organizar el código y evitar conflictos de nombres.

Un namespace actúa como un contenedor lógico que agrupa identificadores relacionados.

---

## El problema que resuelven

Supongamos dos bibliotecas distintas que contienen una función llamada `imprimir`.

Sin namespaces:

```cpp
void imprimir()
{
}

void imprimir()
{
}
```

Esto produce un error porque el compilador encuentra dos definiciones con el mismo nombre.

Los namespaces permiten separar ambos identificadores.

---

## ¿Qué es un Namespace?

Un namespace es una región declarativa que contiene nombres.

Dentro de un namespace pueden existir:

* Funciones.
* Variables.
* Constantes.
* Clases.
* Estructuras.
* Enumeraciones.
* Otros namespaces.

Representación conceptual:

```text
Matematica
│
├── sumar()
├── restar()
├── PI
└── Vector2D
```

---

## Definición de un Namespace

Sintaxis básica:

```cpp
namespace matematica
{
    void imprimir()
    {
    }
}
```

Todo lo que se encuentre dentro de las llaves pertenece al namespace.

Según la convención utilizada en este curso:

```cpp
namespace matematica
{
}
```

los namespaces utilizarán:

```text
snake_case
```

---

## Acceso a un Namespace

Para acceder a los elementos contenidos en un namespace se utiliza el operador de resolución de ámbito:

```cpp
::
```

Ejemplo:

```cpp
namespace matematica
{
    void sumar()
    {
    }
}

int main()
{
    matematica::sumar();

    return 0;
}
```

---

## Operador de resolución de ámbito

El operador:

```
::
```

permite indicar exactamente dónde se encuentra un identificador.

Ejemplos:

```cpp
std::cout
```

```cpp
matematica::sumar()
```

```cpp
empresa::recursos_humanos::mostrar()
```

Representación conceptual:

```text
Namespace
    │
    ▼
Elemento
```

---

## El Namespace `std`

La biblioteca estándar de C++ coloca la mayoría de sus componentes dentro del namespace:

```cpp
std
```

Por ello escribimos:

```cpp
std::cout
std::cin
std::string
std::vector
```

Ejemplo:

```cpp
#include <iostream>

int main()
{
    std::cout << "Hola Mundo\n";

    return 0;
}
```

---

## Estructura simplificada de `std`

Conceptualmente:

```text
std
│
├── cout
├── cin
├── cerr
├── clog
├── string
├── vector
├── map
├── array
└── ...
```

---

## Namespace personalizado

```cpp
#include <iostream>

namespace mensajes
{
    void saludar()
    {
        std::cout << "Hola\n";
    }
}

int main()
{
    mensajes::saludar();

    return 0;
}
```

Salida:

```text
Hola
```

---

## Namespaces anidados

Es posible definir namespaces dentro de otros namespaces.

```cpp
namespace empresa
{
    namespace recursos_humanos
    {
        void mostrar()
        {
        }
    }
}
```

Acceso:

```cpp
empresa::recursos_humanos::mostrar();
```

---

## Sintaxis moderna (C++17)

Desde C++17 puede utilizarse una sintaxis más compacta:

```cpp
namespace empresa::recursos_humanos
{
    void mostrar()
    {
    }
}
```

Es completamente equivalente al ejemplo anterior.

---

## Uso de `using`

Es posible importar un identificador específico.

Ejemplo:

```cpp
using std::cout;

int main()
{
    cout << "Hola Mundo\n";

    return 0;
}
```

En este caso únicamente se importa:

```cpp
cout
```

---

## Uso de `using namespace`

También es posible importar todos los elementos de un namespace.

```cpp
using namespace std;

int main()
{
    cout << "Hola Mundo\n";

    return 0;
}
```

Ahora todos los elementos de `std` son accesibles sin escribir:

```cpp
std::
```

---

## Ventajas de `using namespace`

Reduce la cantidad de código escrito.

```cpp
cout << "Hola";
cin >> edad;
string nombre;
```

Puede resultar cómodo en programas pequeños y ejemplos educativos.

---

## Desventajas de `using namespace`

Puede provocar conflictos de nombres.

Ejemplo:

```cpp
namespace a
{
    void imprimir()
    {
    }
}

namespace b
{
    void imprimir()
    {
    }
}
```

Si ambos namespaces se importan completamente:

```cpp
using namespace a;
using namespace b;
```

Entonces:

```cpp
imprimir();
```

produce ambigüedad.

El compilador no sabe qué función debe utilizar.

---

## Recomendación

En proyectos profesionales suele preferirse:

```cpp
std::cout
std::cin
std::string
```

en lugar de:

```cpp
using namespace std;
```

Esto:

* Evita conflictos.
* Hace explícito el origen de cada identificador.
* Mejora la legibilidad en proyectos grandes.

---

## Alias de Namespace

Cuando un namespace tiene un nombre largo, puede crearse un alias.

Ejemplo:

```cpp
namespace rh = empresa::recursos_humanos;
```

Uso:

```cpp
rh::mostrar();
```

Esto simplifica la escritura sin perder claridad.

---

## Namespace anónimo

Un namespace sin nombre limita la visibilidad al archivo actual.

```cpp
namespace
{
    int contador {};
}
```

Los elementos definidos dentro de él solo pueden utilizarse en ese archivo fuente.

Representa una alternativa moderna a ciertas técnicas antiguas basadas en:

```cpp
static
```

---

## Buenas prácticas

* Utilizar nombres descriptivos para los namespaces.
* Seguir una convención consistente (`snake_case` en este curso).
* Evitar `using namespace` en archivos de cabecera.
* Preferir `std::` explícito en proyectos grandes.
* Utilizar aliases cuando los nombres sean excesivamente largos.
* Organizar el código relacionado dentro del mismo namespace.

---

## Error común

Importar múltiples namespaces completos:

```cpp
using namespace a;
using namespace b;
```

Esto aumenta la probabilidad de conflictos y ambigüedades.

---

## Resumen

* Los namespaces permiten organizar código y evitar conflictos de nombres.
* Se definen mediante la palabra clave `namespace`.
* El operador `::` permite acceder a los elementos de un namespace.
* La biblioteca estándar utiliza el namespace `std`.
* `using` permite importar identificadores específicos.
* `using namespace` importa todos los elementos de un namespace.
* Los namespaces pueden anidarse.
* Los aliases simplifican nombres largos.
* Los namespaces anónimos limitan la visibilidad al archivo actual.
* En proyectos grandes suele recomendarse utilizar explícitamente `std::`.
