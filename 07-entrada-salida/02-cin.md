# cin

## Introducción

Hasta ahora hemos mostrado información en pantalla utilizando:

```cpp
std::cout
```

Sin embargo, los programas también necesitan recibir información del usuario.

Para ello C++ proporciona:

```cpp
std::cin
```

que permite leer datos desde la entrada estándar.

Normalmente la entrada estándar está asociada al:

```text
Teclado
```

---

## ¿Qué Significa cin?

El nombre:

```text
cin
```

proviene de:

```text
character input
```

y forma parte del sistema de flujos (*streams*) de C++.

Conceptualmente:

```text
Teclado
   │
   ▼
std::cin
   │
   ▼
Programa
```

---

## ¿Qué es un Stream?

Un *stream* (flujo) es una secuencia de datos que fluye desde una fuente hacia un destino.

En el caso de:

```cpp
std::cin
```

los datos fluyen desde la entrada estándar hacia el programa.

Representación:

```text
Usuario
   │
   ▼
Teclado
   │
   ▼
std::cin
   │
   ▼
Variables
```

---

## ¿Qué Tipo Tiene std::cin?

`std::cin` es un objeto de tipo:

```cpp
std::istream
```

especializado en leer datos desde la entrada estándar.

Más adelante veremos otros flujos de entrada asociados a archivos.

---

## Biblioteca Necesaria

Para utilizar `std::cin` es necesario incluir:

```cpp
#include <iostream>
```

---

## Primer Ejemplo

```cpp
#include <iostream>

int main()
{
    int edad;

    std::cin >> edad;

    std::cout << edad << '\n';

    return 0;
}
```

Entrada:

```text
25
```

Salida:

```text
25
```

---

## Estructura Básica

```cpp
std::cin >> edad;
```

Representación:

```text
Teclado
   │
   ▼
std::cin
   │
   ▼
 edad
```

---

## Operador de Extracción

El operador:

```cpp
>>
```

permite extraer datos desde un flujo de entrada.

Ejemplo:

```cpp
std::cin >> edad;
```

---

Visualización:

```text
Entrada
   │
   ▼
std::cin
   │
   ▼
   >>
   │
   ▼
Variable
```

---

## Leer un Entero

```cpp
#include <iostream>

int main()
{
    int edad;

    std::cin >> edad;

    std::cout << edad << '\n';

    return 0;
}
```

Entrada:

```text
30
```

Salida:

```text
30
```

---

## Leer un Decimal

```cpp
double precio;

std::cin >> precio;
```

Entrada:

```text
19.99
```

Resultado almacenado:

```text
19.99
```

---

## Leer un Carácter

```cpp
char letra;

std::cin >> letra;
```

Entrada:

```text
A
```

Resultado almacenado:

```text
'A'
```

---

## Leer un Booleano

```cpp
bool activo;

std::cin >> activo;
```

Entrada:

```text
1
```

Resultado:

```cpp
true
```

---

Entrada:

```text
0
```

Resultado:

```cpp
false
```

---

## Leer y Mostrar

```cpp
#include <iostream>

int main()
{
    int edad;

    std::cout << "Ingrese su edad: ";

    std::cin >> edad;

    std::cout << "Edad: " << edad << '\n';

    return 0;
}
```

Entrada:

```text
25
```

Salida:

```text
Ingrese su edad: 25
Edad: 25
```

---

## Flujo de Entrada

```text
Usuario
   │
   ▼
Teclado
   │
   ▼
std::cin
   │
   ▼
Variable
```

---

## Leer Varias Variables

```cpp
int edad;
double salario;

std::cin >> edad >> salario;
```

Entrada:

```text
25 2500.50
```

Resultado almacenado:

```text
edad    = 25
salario = 2500.50
```

---

## Encadenamiento

Al igual que `std::cout`, `std::cin` permite encadenar operaciones.

Ejemplo:

```cpp
std::cin >> edad >> salario;
```

Representación:

```text
Entrada
   │
   ▼
 edad
   │
   ▼
salario
```

---

## Separadores de Entrada

`std::cin` considera como separadores:

- Espacios.
- Tabulaciones.
- Saltos de línea.

Por ello las siguientes entradas son equivalentes:

```text
10 20
```

---

```text
10
20
```

---

Ambas producen:

```text
Primer valor  = 10
Segundo valor = 20
```

---

## Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    int edad;
    double salario;

    std::cout << "Edad: ";
    std::cin >> edad;

    std::cout << "Salario: ";
    std::cin >> salario;

    std::cout << '\n';

    std::cout << "Edad: " << edad << '\n';
    std::cout << "Salario: " << salario << '\n';

    return 0;
}
```

---

## Problema con Textos

Supongamos:

```cpp
std::string nombre;
```

---

```cpp
std::cin >> nombre;
```

Entrada:

```text
Juan Perez
```

Resultado:

```text
Juan
```

---

### ¿Por Qué Ocurre?

Porque:

```cpp
operator>>
```

lee únicamente hasta encontrar el primer separador.

Representación:

```text
Juan Perez
 │
 ▼
Espacio
 │
 ▼
Detener lectura
```

---

Resultado:

```text
Juan
```

---

## Leer una Línea Completa

Para leer texto que puede contener espacios se utiliza:

```cpp
std::getline()
```

Ejemplo:

```cpp
std::string nombre;

std::getline(std::cin, nombre);
```

Entrada:

```text
Juan Perez
```

Resultado:

```text
Juan Perez
```

Más adelante estudiaremos esta función en detalle.

---

## Estado de Error

Si el usuario introduce un tipo incompatible con la variable, la lectura falla.

Ejemplo:

```cpp
int edad;
```

Entrada:

```text
hola
```

Lectura:

```cpp
std::cin >> edad;
```

---

Representación:

```text
Entrada inválida
       │
       ▼
 Error de lectura
```

---

Cuando esto ocurre:

```cpp
std::cin
```

entra en estado de error y las lecturas posteriores pueden fallar.

Más adelante aprenderemos a detectar y recuperar estos errores.

---

## Ejemplo de Interacción

```cpp
#include <iostream>

int main()
{
    int edad;

    std::cout << "Ingrese su edad: ";

    std::cin >> edad;

    std::cout
        << "Usted tiene "
        << edad
        << " años.\n";

    return 0;
}
```

Entrada:

```text
25
```

Salida:

```text
Ingrese su edad: 25
Usted tiene 25 años.
```

---

## Relación entre cout y cin

```text
std::cout

Programa
   │
   ▼
Pantalla
```

---

```text
std::cin

Teclado
   │
   ▼
Programa
```

---

## Buenas Prácticas

### Mostrar Siempre una Instrucción

Preferir:

```cpp
std::cout << "Ingrese la edad: ";
std::cin >> edad;
```

en lugar de:

```cpp
std::cin >> edad;
```

porque el usuario necesita saber qué dato introducir.

---

### Utilizar Variables con Nombres Claros

Correcto:

```cpp
int edad_usuario;
double salario_mensual;
```

---

### Validar Entradas

Cuando el dato sea importante, verificar que la lectura fue exitosa.

Más adelante veremos técnicas de validación.

---

### Utilizar getline para Textos Completos

Si el texto puede contener espacios:

```cpp
std::getline(std::cin, texto);
```

suele ser más apropiado que:

```cpp
std::cin >> texto;
```

---

## Error Común

Olvidar el operador:

```cpp
>>
```

Incorrecto:

```cpp
std::cin << edad;
```

---

Correcto:

```cpp
std::cin >> edad;
```

---

Otro error frecuente es intentar leer una frase completa utilizando:

```cpp
std::cin >> nombre;
```

cuando se debería utilizar:

```cpp
std::getline()
```

---

## Visualización General

```text
Usuario
   │
   ▼
Teclado
   │
   ▼
std::cin
   │
   ▼
Variables
```

---

## Resumen

- `std::cin` permite leer datos desde la entrada estándar.
- Forma parte de la biblioteca `<iostream>`.
- Es un objeto de tipo `std::istream`.
- Utiliza el operador `>>` para extraer datos.
- Puede leer enteros, decimales, caracteres y otros tipos básicos.
- Los espacios, tabulaciones y saltos de línea actúan como separadores.
- Es posible encadenar varias lecturas en una sola expresión.
- `std::getline()` permite leer líneas completas de texto.
- Las entradas inválidas colocan al flujo en estado de error.
- `std::cin` constituye la base de la interacción del usuario con programas de consola.
