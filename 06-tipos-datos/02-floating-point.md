# Números de Punto Flotante

## Introducción

Los tipos de punto flotante permiten almacenar números con parte decimal.

Ejemplos:

```cpp
3.14
10.5
0.001
-25.75
```

A diferencia de:

```cpp
int
```

que solo almacena números enteros, los tipos de punto flotante pueden representar valores fraccionarios.

---

## Tipos Disponibles

C++ proporciona tres tipos principales para trabajar con números reales:

| Tipo          | Descripción |
| ------------- | ----------- |
| `float`       | Precisión simple |
| `double`      | Precisión doble |
| `long double` | Precisión extendida (dependiente de la implementación) |

---

## ¿Qué Significa Punto Flotante?

El término:

```text
floating point
```

proviene de la forma en que el hardware representa números reales.

Conceptualmente, estos tipos permiten almacenar una parte entera y una parte fraccionaria:

```text
123.45
0.001
3.141592
```

---

# float

`float` utiliza menos memoria que `double`, pero también ofrece menos precisión.

Ejemplo:

```cpp
float temperatura{25.5f};
```

Observa el sufijo:

```cpp
f
```

que indica que el literal es de tipo `float`.

---

## Ejemplo

```cpp
#include <iostream>

int main()
{
    float temperatura{25.5f};

    std::cout << temperatura << '\n';

    return 0;
}
```

Salida:

```text
25.5
```

---

# double

`double` es el tipo de punto flotante más utilizado en C++.

Ejemplo:

```cpp
double precio{19.99};
```

---

## Ejemplo

```cpp
double pi{3.141592653589793};
```

---

## ¿Por Qué Suele Preferirse?

Porque proporciona:

- Mayor precisión que `float`.
- Buen rendimiento en la mayoría de procesadores modernos.
- Un equilibrio adecuado entre precisión y consumo de memoria.

Por esta razón, cuando se necesita trabajar con números decimales, suele ser la opción recomendada.

---

# long double

`long double` suele proporcionar una precisión igual o superior a `double`.

Ejemplo:

```cpp
long double numero{3.141592653589793238L};
```

Observa el sufijo:

```cpp
L
```

---

## Importante

El tamaño y la precisión exactos de `long double` dependen de la implementación.

Por ejemplo:

```cpp
sizeof(long double)
```

puede variar según el compilador y el sistema operativo.

---

## Uso Habitual

Suele utilizarse en situaciones donde se requiere la máxima precisión disponible:

- Simulaciones científicas.
- Cálculos matemáticos avanzados.
- Aplicaciones numéricas especializadas.

---

# Comparación General

```text
float
│
├── Menos memoria
└── Menor precisión
```

```text
double
│
├── Más memoria
└── Mayor precisión
```

```text
long double
│
└── Precisión igual o superior a double
```

---

## Representación Conceptual

```text
float
│
└── 3.14
```

---

```text
double
│
└── 3.141592653589793
```

---

```text
long double
│
└── 3.141592653589793238...
```

---

# Tipo de los Literales Decimales

Por defecto, un literal decimal es de tipo:

```cpp
double
```

Ejemplo:

```cpp
auto valor{3.14};
```

Tipo deducido:

```cpp
double
```

---

Para crear un literal `float`:

```cpp
3.14f
```

---

Para crear un literal `long double`:

```cpp
3.14L
```

---

# Operaciones Básicas

### Suma

```cpp
double a{10.5};
double b{2.5};

double resultado{a + b};
```

Resultado:

```text
13.0
```

---

### Resta

```cpp
double resultado{10.5 - 2.5};
```

Resultado:

```text
8.0
```

---

### Multiplicación

```cpp
double resultado{4.5 * 2.0};
```

Resultado:

```text
9.0
```

---

### División

```cpp
double resultado{5.0 / 2.0};
```

Resultado:

```text
2.5
```

---

# División Entera vs Decimal

Con enteros:

```cpp
5 / 2
```

Resultado:

```text
2
```

---

Con punto flotante:

```cpp
5.0 / 2.0
```

Resultado:

```text
2.5
```

---

## Visualización

```text
int

5 / 2
 │
 ▼
 2
```

---

```text
double

5.0 / 2.0
   │
   ▼
  2.5
```

---

# Precisión

Los números de punto flotante no pueden representar todos los valores decimales exactamente.

Ejemplo:

```cpp
#include <iostream>

int main()
{
    double valor{0.1 + 0.2};

    std::cout << valor << '\n';

    return 0;
}
```

Posible salida:

```text
0.30000000000000004
```

---

## ¿Por Qué Ocurre?

Los números se almacenan internamente en binario.

Algunos valores decimales no poseen una representación binaria exacta.

Por ello se almacenan utilizando aproximaciones.

```text
0.1
 │
 ▼
Representación binaria aproximada
 │
 ▼
Pequeño error de precisión
```

---

## Importante

Esto no es un error de C++.

Es una consecuencia de cómo los números reales se representan internamente en prácticamente todos los computadores modernos mediante el estándar IEEE 754.

---

# Dinero y Punto Flotante

Aunque resulta tentador utilizar:

```cpp
double saldo{19.99};
```

los tipos de punto flotante no suelen ser adecuados para representar dinero debido a los errores de precisión acumulados.

Por ejemplo:

```cpp
double total{0.1 + 0.2};
```

puede producir:

```text
0.30000000000000004
```

Más adelante estudiaremos alternativas más adecuadas para trabajar con cantidades monetarias.

---

# Comparaciones de Decimales

Evitar:

```cpp
double a{0.1 + 0.2};

if (a == 0.3)
{
}
```

Porque puede producir resultados inesperados.

---

## Comparación Aproximada

Una técnica habitual consiste en comprobar si la diferencia entre dos valores es suficientemente pequeña.

Ejemplo conceptual:

```cpp
std::abs(a - b) < tolerancia
```

Más adelante estudiaremos este tema con detalle.

---

# Notación Científica

También es posible escribir números utilizando exponentes.

Ejemplo:

```cpp
double velocidad_luz{3.0e8};
```

Equivale a:

```text
300000000
```

---

Otro ejemplo:

```cpp
double numero{1.5e-3};
```

Equivale a:

```text
0.0015
```

---

# Tamaño Habitual

Los tamaños más comunes son:

| Tipo | Tamaño Habitual |
| ------ | ---------------- |
| `float` | 4 bytes |
| `double` | 8 bytes |
| `long double` | Variable según la implementación |

Estos valores no están fijados por el estándar y pueden variar entre plataformas.

---

# auto y Punto Flotante

La inferencia de tipos funciona perfectamente con valores decimales.

Ejemplo:

```cpp
auto precio{19.99};
```

Tipo deducido:

```cpp
double
```

---

```cpp
auto temperatura{25.5f};
```

Tipo deducido:

```cpp
float
```

---

# Convención Utilizada en Este Repositorio

Cuando no exista una razón específica para utilizar otro tipo:

```cpp
double
```

será la opción preferida para números decimales.

Ejemplo:

```cpp
double precio{19.99};
```

---

# Buenas Prácticas

## Utilizar double por Defecto

Preferir:

```cpp
double precio{19.99};
```

---

## Evitar Comparaciones Directas

Evitar:

```cpp
a == b
```

cuando se trabaja con números de punto flotante.

---

## Utilizar los Sufijos Correctos

```cpp
float numero{10.5f};
```

---

```cpp
long double numero{10.5L};
```

---

## Comprender las Limitaciones de Precisión

Los números de punto flotante son aproximaciones.

No deben tratarse como valores matemáticos exactos.

---

# Regla Práctica

```text
• Utiliza int para números enteros.
• Utiliza double para números con decimales.
• Utiliza float únicamente cuando exista una razón específica.
• Considera long double cuando necesites la máxima precisión disponible.
```

---

# Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    double precio{19.99};
    double impuesto{3.50};

    double total{precio + impuesto};

    std::cout << total << '\n';

    return 0;
}
```

Salida:

```text
23.49
```

---

## Error Común

Pensar que los números decimales son siempre exactos.

Ejemplo:

```cpp
0.1 + 0.2
```

No necesariamente produce:

```text
0.3
```

de forma exacta debido a la representación binaria utilizada internamente.

---

## Resumen

- Los tipos de punto flotante almacenan números con parte decimal.
- C++ proporciona `float`, `double` y `long double`.
- `double` suele ser la opción recomendada para la mayoría de programas.
- La división entre números de punto flotante conserva la parte decimal.
- Los números de punto flotante tienen precisión limitada.
- Algunas fracciones decimales no pueden representarse exactamente en binario.
- Debe tenerse cuidado al comparar valores decimales.
- Los tamaños y niveles de precisión dependen de la implementación.
- Es posible utilizar notación científica para representar números muy grandes o muy pequeños.
