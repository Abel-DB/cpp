# Referencias en Funciones

## Introducción

En temas anteriores aprendimos dos conceptos importantes:

```cpp
Referencias
```

---

y

```cpp
Parámetros
```

---

Hasta ahora nuestras funciones recibían argumentos por valor.

Ejemplo:

```cpp
void mostrar_edad(int edad)
{
    std::cout
        << edad
        << '\n';
}
```

---

Cuando llamamos:

```cpp
mostrar_edad(25);
```

---

la función recibe una copia del valor.

---

Sin embargo, en muchas situaciones queremos que la función trabaje directamente con la variable original.

Para ello utilizamos:

```cpp
Referencias en funciones
```

---

# Paso por Valor

Recordemos:

```cpp
void incrementar(int numero)
{
    ++numero;
}
```

---

Uso:

```cpp
int edad {20};

incrementar(edad);
```

---

Visualización:

```text
edad = 20
      │
      ▼
 copia = 20
      │
      ▼
 copia = 21
```

---

La variable original:

```cpp
edad
```

no cambia.

---

# Ejemplo Completo

```cpp
#include <iostream>

void incrementar(int numero)
{
    ++numero;
}

int main()
{
    int edad {20};

    incrementar(edad);

    std::cout
        << edad
        << '\n';

    return 0;
}
```

Salida:

```text
20
```

---

# ¿Por Qué?

Porque:

```cpp
numero
```

es una copia.

---

Modificar la copia no afecta a la variable original.

---

# Paso por Referencia

Podemos recibir una referencia.

---

Sintaxis:

```cpp
tipo& parametro
```

---

Ejemplo:

```cpp
void incrementar(int& numero)
{
    ++numero;
}
```

---

Ahora:

```cpp
numero
```

es un alias de la variable original.

---

# Primer Ejemplo

```cpp
#include <iostream>

void incrementar(int& numero)
{
    ++numero;
}

int main()
{
    int edad {20};

    incrementar(edad);

    std::cout
        << edad
        << '\n';

    return 0;
}
```

Salida:

```text
21
```

---

# Visualización

```text
edad
 │
 ▼
20

numero
 │
 ▼
20
```

---

Ambos nombres hacen referencia al mismo objeto.

---

Después:

```cpp
++numero;
```

---

Resultado:

```text
edad = 21
```

---

# Comparación

## Paso por Valor

```cpp
void incrementar(int numero)
{
    ++numero;
}
```

---

Resultado:

```text
No modifica la variable original
```

---

# Paso por Referencia

```cpp
void incrementar(int& numero)
{
    ++numero;
}
```

---

Resultado:

```text
Sí modifica la variable original
```

---

# Múltiples Parámetros por Referencia

```cpp
void intercambiar(
    int& primer_valor,
    int& segundo_valor)
{
    int temporal {primer_valor};

    primer_valor = segundo_valor;
    segundo_valor = temporal;
}
```

---

Uso:

```cpp
int numero_a {10};
int numero_b {20};

intercambiar(
    numero_a,
    numero_b);
```

---

Resultado:

```text
numero_a = 20
numero_b = 10
```

---

# Referencias Constantes en Funciones

Muchas veces queremos evitar copias pero sin permitir modificaciones.

---

Para ello usamos:

```cpp
const tipo&
```

---

Ejemplo:

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
No puede modificar el argumento
```

---

# Ejemplo

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

# Intentar Modificar

```cpp
void mostrar_nombre(
    const std::string& nombre)
{
    nombre = "Ana";
}
```

---

Resultado:

```text
Error de compilación
```

---

Porque:

```cpp
nombre
```

es constante.

---

# ¿Cuándo Utilizar Referencias?

Cuando la función necesita:

```text
Modificar la variable original
```

---

Ejemplo:

```cpp
void incrementar(int& numero)
{
}
```

---

# ¿Cuándo Utilizar Referencias Constantes?

Cuando la función:

```text
Solo necesita leer
```

---

especialmente con objetos grandes.

---

Ejemplos:

```cpp
const std::string&
```

---

Más adelante:

```cpp
const std::vector<int>&
```

---

# Ventaja de Rendimiento

Observa:

```cpp
void mostrar_nombre(
    std::string nombre)
{
}
```

---

Se crea una copia.

---

En cambio:

```cpp
void mostrar_nombre(
    const std::string& nombre)
{
}
```

---

No se crea ninguna copia.

---

Resultado:

```text
Menor uso de memoria
Mayor eficiencia
```

---

# Referencia vs Puntero

También es posible modificar variables mediante punteros.

---

Ejemplo:

```cpp
void incrementar(int* numero)
{
    ++(*numero);
}
```

---

Uso:

```cpp
incrementar(&edad);
```

---

Las referencias suelen ser más simples cuando no necesitamos trabajar con direcciones explícitamente.

---

# Ejemplo Completo

```cpp
#include <iostream>

void duplicar(int& numero)
{
    numero *= 2;
}

int main()
{
    int edad {15};

    duplicar(edad);

    std::cout
        << edad
        << '\n';

    return 0;
}
```

Salida:

```text
30
```

---

# Buenas Prácticas

## Utilizar Referencias para Modificar

Correcto:

```cpp
void incrementar(int& numero)
{
}
```

---

## Utilizar Referencias Constantes para Lectura

Correcto:

```cpp
const std::string& nombre
```

---

## Evitar Copias Innecesarias

Especialmente con objetos grandes.

---

## Hacer Evidente la Intención

Si una función modifica datos, el uso de referencias ayuda a expresarlo claramente.

---

# Error Común

Pensar que:

```cpp
int& numero
```

crea una copia.

---

Realidad:

```text
Trabaja directamente con la variable original.
```

---

Otro error común:

```cpp
void mostrar(
    const std::string& nombre)
{
    nombre = "Ana";
}
```

---

Resultado:

```text
Error de compilación
```

---

Porque la referencia es constante.

---

# Visualización General

```text
Variable
   │
   ▼
Referencia
   │
   ▼
Función
   │
   ▼
Mismo objeto
```

---

# Tabla Resumen

| Parámetro | Copia | Modifica original |
|------------|--------|------------------|
| `int numero` | Sí | No |
| `int& numero` | No | Sí |
| `const int& numero` | No | No |

---

## Resumen

- Una función puede recibir referencias como parámetros.
- Las referencias permiten trabajar directamente con la variable original.
- El paso por referencia evita copias innecesarias.
- Las referencias normales permiten modificar el argumento.
- Las referencias constantes permiten leer sin modificar.
- Son especialmente útiles con objetos grandes como `std::string`.
- Mejoran el rendimiento y la claridad del código.
- Son una de las herramientas más utilizadas en C++ moderno.
