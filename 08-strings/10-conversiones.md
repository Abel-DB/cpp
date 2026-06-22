# Conversiones de Strings

## Introducción

En muchos programas los datos llegan inicialmente como texto.

Por ejemplo:

```text
"25"
"3.14"
"1000"
```

Aunque representan números, en realidad son valores de tipo:

```cpp
std::string
```

---

Frecuentemente necesitaremos convertir entre:

```cpp
std::string → número
```

o

```cpp
número → std::string
```

C++ proporciona herramientas para realizar estas conversiones de forma sencilla.

---

# String a Número

La biblioteca estándar proporciona varias funciones para convertir texto en valores numéricos.

---

## Biblioteca Necesaria

```cpp
#include <string>
```

---

# std::stoi()

Convierte un string a:

```cpp
int
```

---

## Sintaxis

```cpp
std::stoi(texto)
```

---

## Ejemplo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string texto {"25"};

    int numero =
        std::stoi(texto);

    std::cout
        << numero
        << '\n';

    return 0;
}
```

Salida:

```text
25
```

---

## Visualización

```text
"25"
 │
 ▼
stoi()
 │
 ▼
25
```

---

# std::stol()

Convierte un string a:

```cpp
long
```

---

## Ejemplo

```cpp
std::string texto {"100000"};

long numero =
    std::stol(texto);
```

---

# std::stoll()

Convierte un string a:

```cpp
long long
```

---

## Ejemplo

```cpp
std::string texto {"9999999999"};

long long numero =
    std::stoll(texto);
```

---

# std::stof()

Convierte un string a:

```cpp
float
```

---

## Ejemplo

```cpp
std::string texto {"3.14"};

float numero =
    std::stof(texto);
```

---

## Visualización

```text
"3.14"
  │
  ▼
stof()
  │
  ▼
3.14f
```

---

# std::stod()

Convierte un string a:

```cpp
double
```

---

## Ejemplo

```cpp
std::string texto {"3.141592"};

double numero =
    std::stod(texto);
```

---

# Resumen de Conversión

| Función | Tipo Resultante |
|----------|----------------|
| `stoi()` | `int` |
| `stol()` | `long` |
| `stoll()` | `long long` |
| `stof()` | `float` |
| `stod()` | `double` |

---

# Número a String

La función principal es:

```cpp
std::to_string()
```

---

## Sintaxis

```cpp
std::to_string(valor)
```

---

## Ejemplo

```cpp
int edad = 25;

std::string texto =
    std::to_string(edad);
```

Resultado:

```text
"25"
```

---

## Visualización

```text
25
 │
 ▼
to_string()
 │
 ▼
"25"
```

---

# Ejemplo con double

```cpp
double precio = 19.99;

std::string texto =
    std::to_string(precio);
```

Resultado habitual:

```text
"19.990000"
```

---

## Importante

`std::to_string()` utiliza un formato predeterminado que puede incluir más decimales de los esperados.

---

## Visualización

```text
19.99
  │
  ▼
to_string()
  │
  ▼
"19.990000"
```

---

# Construcción de Mensajes

Una utilidad muy común.

---

## Ejemplo

```cpp
int edad = 25;

std::string mensaje =
    "Edad: "
    + std::to_string(edad);
```

Este código no compila porque:

```cpp
"Edad: "
```

es un literal de cadena y no un `std::string`.

---

## Forma Recomendada

```cpp
int edad = 25;

std::string mensaje =
    std::string{"Edad: "}
    + std::to_string(edad);
```

---

Resultado:

```text
Edad: 25
```

---

## Alternativa Más Simple

```cpp
std::cout
    << "Edad: "
    << edad
    << '\n';
```

---

# Conversión de Entrada

Supongamos:

```cpp
std::string texto {};
```

---

Entrada:

```text
123
```

---

Conversión:

```cpp
int valor =
    std::stoi(texto);
```

---

Resultado:

```text
123
```

como entero.

---

# Operaciones Numéricas

Antes:

```cpp
std::string a {"10"};
std::string b {"20"};
```

---

```cpp
a + b
```

Resultado:

```text
1020
```

---

Porque realiza:

```text
Concatenación
```

---

Convertidos:

```cpp
int x = std::stoi(a);
int y = std::stoi(b);
```

---

```cpp
x + y
```

Resultado:

```text
30
```

---

# Problema con Texto Inválido

Supongamos:

```cpp
std::string texto {"Hola"};
```

---

```cpp
std::stoi(texto);
```

---

Problema:

```text
No representa un número válido
```

---

La función lanzará una excepción.

---

# Ejemplo

```cpp
std::string texto {"abc"};

int valor =
    std::stoi(texto);
```

Resultado:

```text
Error
```

---

# Conversión Parcial

Las funciones de conversión aceptan texto numérico seguido de otros caracteres.

Ejemplo:

```cpp
std::string texto {"123abc"};

int valor =
    std::stoi(texto);
```

Resultado:

```text
123
```

---

La conversión se detiene cuando encuentra un carácter no válido.

---

# Ejemplo Completo

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string texto {"50"};

    int numero =
        std::stoi(texto);

    numero += 10;

    std::cout
        << numero
        << '\n';

    return 0;
}
```

Salida:

```text
60
```

---

# Conversión Inversa

```cpp
#include <iostream>
#include <string>

int main()
{
    int numero = 42;

    std::string texto =
        std::to_string(numero);

    std::cout
        << texto
        << '\n';

    return 0;
}
```

Salida:

```text
42
```

---

# Casos de Uso Reales

## Datos de Usuario

```text
"25"
```

↓

```cpp
int
```

---

## Archivos

```text
"1024"
```

↓

```cpp
int
```

---

## Configuración

```text
"3.14"
```

↓

```cpp
double
```

---

## Construcción de Mensajes

```cpp
std::string{"Usuario "}
+ std::to_string(id)
```

---

# Convención Utilizada en Este Repositorio

Para convertir texto numérico:

```cpp
std::stoi()
```

---

```cpp
std::stod()
```

---

Para convertir números a texto:

```cpp
std::to_string()
```

---

Y para mostrar valores en pantalla:

```cpp
std::cout
```

seguirá siendo la opción preferida cuando no sea necesario almacenar el resultado en un string.

---

# Buenas Prácticas

## Convertir Solo Cuando Sea Necesario

Mantener los datos en formato numérico si van a utilizarse para cálculos.

---

## Utilizar to_string() para Generar Texto

Correcto:

```cpp
auto texto =
    std::to_string(valor);
```

---

## Verificar Datos Externos

Cuando el texto provenga de:

- Usuarios.
- Archivos.
- Redes.

---

Puede contener valores inválidos.

---

## Considerar el Manejo de Excepciones

Las funciones de conversión pueden lanzar excepciones si la entrada no es válida.

---

# Error Común

Pensar que:

```cpp
"10" + "20"
```

produce:

```text
30
```

---

Realmente no representa una suma numérica.

Cuando se trabaja con strings, el resultado esperado sería:

```text
1020
```

mediante concatenación.

---

Para sumar:

```cpp
std::stoi("10")
+
std::stoi("20")
```

---

Resultado:

```text
30
```

---

# Visualización General

```text
String
  │
  ├── stoi()
  ├── stol()
  ├── stoll()
  ├── stof()
  └── stod()
         │
         ▼
      Número
```

---

```text
Número
   │
   ▼
to_string()
   │
   ▼
 String
```

---

## Resumen

- C++ permite convertir strings en valores numéricos.
- `stoi()` convierte a `int`.
- `stof()` convierte a `float`.
- `stod()` convierte a `double`.
- `to_string()` convierte números en strings.
- Las funciones de conversión pueden lanzar excepciones si el texto no es válido.
- Los strings representan texto; los números permiten realizar cálculos.
- Convertir correctamente entre ambos tipos es una habilidad fundamental en programación.
