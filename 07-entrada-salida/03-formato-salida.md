# Formato de Salida

## Introducción

Por defecto, `std::cout` muestra los datos utilizando un formato estándar.

Ejemplo:

```cpp
double precio = 19.99;

std::cout << precio;
```

Salida:

```text
19.99
```

---

Sin embargo, muchas veces necesitamos controlar cómo se muestran los datos.

Por ejemplo:

```text
Cantidad de decimales
Alineación
Ancho de columnas
Valores booleanos
Notación científica
```

Para ello C++ proporciona diversas herramientas de formateo.

---

## Biblioteca Necesaria

Para la mayoría de opciones de formato utilizaremos:

```cpp
#include <iomanip>
```

---

# Manipuladores

Elementos como:

```cpp
std::boolalpha
std::fixed
std::scientific
std::left
std::right
```

se denominan:

```text
Manipuladores
```

porque modifican el comportamiento de los flujos de entrada y salida.

---

## Los Manipuladores Modifican el Estado del Flujo

Muchos manipuladores permanecen activos después de utilizarse.

Ejemplo:

```cpp
std::cout << std::boolalpha;

std::cout << true << '\n';
std::cout << false << '\n';
```

Salida:

```text
true
false
```

---

No es necesario escribir:

```cpp
std::boolalpha
```

en cada línea.

El manipulador modifica el estado interno del flujo.

---

Para restaurar el comportamiento original:

```cpp
std::cout << std::noboolalpha;
```

---

# Mostrar Booleanos

Por defecto:

```cpp
bool activo = true;

std::cout << activo;
```

Salida:

```text
1
```

---

## std::boolalpha

Permite mostrar:

```text
true
false
```

en lugar de:

```text
1
0
```

---

Ejemplo:

```cpp
#include <iostream>

int main()
{
    bool activo = true;

    std::cout << std::boolalpha;
    std::cout << activo << '\n';

    return 0;
}
```

Salida:

```text
true
```

---

## Restaurar Comportamiento Original

```cpp
std::noboolalpha
```

Ejemplo:

```cpp
std::cout << std::noboolalpha;
```

---

# Precisión Decimal

Por defecto:

```cpp
double pi = 3.141592653589793;

std::cout << pi;
```

Salida típica:

```text
3.14159
```

---

## std::setprecision()

Permite controlar la precisión.

Ejemplo:

```cpp
#include <iomanip>

std::cout << std::setprecision(3);
```

---

## setprecision y fixed

Es importante distinguir:

```cpp
std::setprecision()
```

de:

```cpp
std::fixed
```

---

Sin `fixed`:

```cpp
std::cout
    << std::setprecision(3)
    << 123.456;
```

Salida habitual:

```text
123
```

porque se muestran tres cifras significativas.

---

Con `fixed`:

```cpp
std::cout
    << std::fixed
    << std::setprecision(3)
    << 123.456;
```

Salida:

```text
123.456
```

Ahora la precisión representa la cantidad de decimales.

---

## Visualización

```text
123.456
    │
    ▼
setprecision(3)
    │
    ▼
123
```

---

```text
123.456
    │
    ▼
fixed + setprecision(3)
    │
    ▼
123.456
```

---

# Formato Fijo

```cpp
std::fixed
```

indica que queremos trabajar con una cantidad fija de decimales.

---

Ejemplo:

```cpp
double precio = 19.99;

std::cout
    << std::fixed
    << std::setprecision(2)
    << precio;
```

Salida:

```text
19.99
```

---

## Otro Ejemplo

```cpp
double numero = 5;
```

---

Sin formato:

```text
5
```

---

Con formato:

```cpp
std::cout
    << std::fixed
    << std::setprecision(2)
    << numero;
```

Salida:

```text
5.00
```

---

# Notación Científica

```cpp
std::scientific
```

permite mostrar números utilizando notación científica.

Ejemplo:

```cpp
double valor = 12345.6789;

std::cout
    << std::scientific
    << valor;
```

Posible salida:

```text
1.234568e+04
```

---

Puede combinarse con:

```cpp
std::setprecision()
```

---

Ejemplo:

```cpp
std::cout
    << std::scientific
    << std::setprecision(3)
    << valor;
```

Posible salida:

```text
1.235e+04
```

---

# Mostrar Siempre el Punto Decimal

```cpp
std::showpoint
```

fuerza la aparición del punto decimal.

Ejemplo:

```cpp
std::cout
    << std::showpoint
    << 5.0;
```

Posible salida:

```text
5.00000
```

---

Para restaurar el comportamiento original:

```cpp
std::cout << std::noshowpoint;
```

---

# Alineación

Cuando mostramos tablas es útil controlar la alineación.

---

## std::setw()

Permite definir un ancho mínimo.

Ejemplo:

```cpp
#include <iomanip>

std::cout << std::setw(10) << 25;
```

Salida:

```text
        25
```

---

## Visualización

```text
|        25|
```

---

## Particularidad de setw

A diferencia de otros manipuladores:

```cpp
std::setw()
```

solo afecta al siguiente valor enviado al flujo.

Ejemplo:

```cpp
std::cout
    << std::setw(10) << "A"
    << "B";
```

Salida:

```text
         AB
```

---

Si se desea aplicar nuevamente el ancho:

```cpp
std::setw(10)
```

debe escribirse otra vez.

---

# Alineación Izquierda

Por defecto:

```text
Derecha
```

---

Para alinear a la izquierda:

```cpp
std::left
```

---

Ejemplo:

```cpp
std::cout
    << std::left
    << std::setw(10)
    << "Ana";
```

Salida:

```text
Ana
```

---

Visualización:

```text
|Ana       |
```

---

# Alineación Derecha

```cpp
std::right
```

---

Ejemplo:

```cpp
std::cout
    << std::right
    << std::setw(10)
    << "Ana";
```

Salida:

```text
       Ana
```

---

Visualización:

```text
|       Ana|
```

---

# Relleno

Por defecto:

```text
Espacios
```

---

Puede cambiarse mediante:

```cpp
std::setfill()
```

---

Ejemplo:

```cpp
std::cout
    << std::setfill('*')
    << std::setw(10)
    << 25;
```

Salida:

```text
********25
```

---

## Visualización

```text
|********25|
```

---

# Tabla Formateada

```cpp
#include <iostream>
#include <iomanip>

int main()
{
    std::cout
        << std::left
        << std::setw(15) << "Producto"
        << std::setw(10) << "Precio"
        << '\n';

    std::cout
        << std::setw(15) << "Teclado"
        << std::setw(10) << 49.99
        << '\n';

    std::cout
        << std::setw(15) << "Mouse"
        << std::setw(10) << 19.99
        << '\n';

    return 0;
}
```

Salida:

```text
Producto       Precio
Teclado        49.99
Mouse          19.99
```

---

Representación conceptual:

```text
| Producto       | Precio |
|----------------|--------|
| Teclado        | 49.99  |
| Mouse          | 19.99  |
```

---

# Formato Combinado

```cpp
#include <iostream>
#include <iomanip>

int main()
{
    double precio = 19.99;

    std::cout
        << std::fixed
        << std::setprecision(2)
        << precio
        << '\n';

    return 0;
}
```

Salida:

```text
19.99
```

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <iomanip>

int main()
{
    bool activo = true;
    double precio = 19.99;

    std::cout << std::boolalpha;

    std::cout
        << std::fixed
        << std::setprecision(2);

    std::cout
        << "Activo: "
        << activo
        << '\n';

    std::cout
        << "Precio: "
        << precio
        << '\n';

    return 0;
}
```

Salida:

```text
Activo: true
Precio: 19.99
```

---

# Buenas Prácticas

## Utilizar fixed para Dinero

Preferir:

```cpp
std::fixed
<< std::setprecision(2)
```

---

Ejemplo:

```cpp
19.99
```

---

## Utilizar boolalpha para Booleanos

Preferir:

```text
true
false
```

sobre:

```text
1
0
```

cuando la salida esté dirigida a personas.

---

## Utilizar setw para Tablas

Mejora la alineación y legibilidad.

---

## Comprender qué Manipuladores son Persistentes

Recordar:

```cpp
std::boolalpha
std::fixed
std::scientific
std::left
std::right
```

permanecen activos hasta que otro manipulador cambie el estado del flujo.

---

```cpp
std::setw()
```

es una excepción porque solo afecta a la siguiente inserción.

---

# Error Común

Olvidar incluir:

```cpp
#include <iomanip>
```

al utilizar:

```cpp
std::setw
std::setprecision
std::setfill
```

---

Resultado:

```text
error: 'setw' is not a member of 'std'
```

---

## Resumen

* C++ permite controlar el formato de salida mediante manipuladores.
* `<iomanip>` proporciona herramientas de formateo.
* `std::boolalpha` muestra booleanos como `true` y `false`.
* `std::setprecision()` controla la precisión de impresión.
* `std::fixed` interpreta la precisión como cantidad de decimales.
* `std::scientific` utiliza notación científica.
* `std::showpoint` fuerza la visualización del punto decimal.
* `std::setw()` define el ancho mínimo de impresión.
* `std::left` y `std::right` controlan la alineación.
* `std::setfill()` modifica el carácter de relleno.
* Algunos manipuladores son persistentes y modifican el estado del flujo.
* `std::setw()` solo afecta a la siguiente inserción.
* Estas herramientas permiten generar salidas más claras y profesionales.
