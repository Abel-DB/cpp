# Referencias y Variables

## Introducción

En los temas anteriores aprendimos que una referencia es un alias para una variable existente.

Por ejemplo:

```cpp
int edad {25};

int& referencia_edad {edad};
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
```

---

Ahora profundizaremos en la relación entre una variable y sus referencias.

---

# Una Variable, Varios Nombres

Observa:

```cpp
int edad {25};

int& referencia_edad {edad};
```

---

Tenemos:

```text
edad
```

y

```text
referencia_edad
```

---

Pero:

```text
No existen dos variables.
```

---

Existe:

```text
Una sola variable
```

con:

```text
Dos nombres
```

---

# Primer Ejemplo

```cpp
#include <iostream>

int main()
{
    int edad {25};

    int& referencia_edad {edad};

    std::cout
        << edad
        << '\n';

    std::cout
        << referencia_edad
        << '\n';

    return 0;
}
```

Salida:

```text
25
25
```

---

# Modificar la Variable Original

```cpp
int edad {25};

int& referencia_edad {edad};

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

Porque:

```text
Ambos nombres representan el mismo objeto.
```

---

# Visualización

Antes:

```text
edad
 │
 ▼
25
 ▲
 │
referencia_edad
```

---

Después:

```cpp
edad = 40;
```

---

Resultado:

```text
edad
 │
 ▼
40
 ▲
 │
referencia_edad
```

---

# Modificar la Referencia

También podemos modificar el objeto utilizando la referencia.

---

Ejemplo:

```cpp
int edad {25};

int& referencia_edad {edad};

referencia_edad = 50;
```

---

Ahora:

```cpp
std::cout
    << edad;
```

---

Salida:

```text
50
```

---

# Visualización

```text
referencia_edad = 50
         │
         ▼
        edad
         │
         ▼
         50
```

---

# Cambios Bidireccionales

Una modificación realizada mediante cualquiera de los nombres es visible desde ambos.

---

Ejemplo:

```cpp
int temperatura {20};

int& referencia_temperatura {temperatura};

temperatura = 30;

std::cout
    << referencia_temperatura
    << '\n';

referencia_temperatura = 40;

std::cout
    << temperatura
    << '\n';
```

Salida:

```text
30
40
```

---

# Múltiples Referencias

Una misma variable puede tener varias referencias.

---

Ejemplo:

```cpp
int edad {25};

int& referencia_1 {edad};
int& referencia_2 {edad};
```

---

Visualización:

```text
          referencia_1
                │
                ▼

edad ─────────► 25

                ▲
                │
          referencia_2
```

---

# Ejemplo

```cpp
int edad {25};

int& referencia_1 {edad};
int& referencia_2 {edad};

referencia_1 = 60;

std::cout
    << referencia_2
    << '\n';
```

Salida:

```text
60
```

---

Porque:

```text
Las dos referencias acceden al mismo objeto.
```

---

# Direcciones de Memoria

Aunque todavía no hemos estudiado punteros, podemos observar algo interesante.

---

Ejemplo:

```cpp
#include <iostream>

int main()
{
    int edad {25};

    int& referencia_edad {edad};

    std::cout
        << &edad
        << '\n';

    std::cout
        << &referencia_edad
        << '\n';

    return 0;
}
```

---

Salida aproximada:

```text
0x7ffeefbff58c
0x7ffeefbff58c
```

---

Las direcciones son iguales.

---

Porque:

```text
Variable y referencia son el mismo objeto.
```

---

# Referencia vs Copia

## Copia

```cpp
int edad {25};

int copia_edad {edad};
```

---

Visualización:

```text
edad        copia_edad
 │              │
 ▼              ▼
25             25
```

---

Modificar:

```cpp
copia_edad = 50;
```

---

Resultado:

```text
edad = 25
```

---

No existe relación entre ellas.

---

# Referencia

```cpp
int edad {25};

int& referencia_edad {edad};
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
```

---

Modificar:

```cpp
referencia_edad = 50;
```

---

Resultado:

```text
edad = 50
```

---

Porque no existe una copia.

---

# Scope y Lifetime

Las referencias siguen las reglas normales de alcance.

---

Ejemplo:

```cpp
if (true)
{
    int edad {25};

    int& referencia_edad {edad};
}
```

---

Fuera del bloque:

```cpp
referencia_edad
```

---

no existe.

---

Porque:

```text
La referencia tiene su propio scope.
```

---

# Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    int temperatura {20};

    int& referencia_temperatura {temperatura};

    std::cout
        << temperatura
        << '\n';

    referencia_temperatura = 35;

    std::cout
        << temperatura
        << '\n';

    temperatura = 50;

    std::cout
        << referencia_temperatura
        << '\n';

    return 0;
}
```

Salida:

```text
20
35
50
```

---

# Buenas Prácticas

## Recordar que No es una Copia

Correcto:

```cpp
int& referencia_temperatura {temperatura};
```

---

## Utilizar Nombres Claros

Correcto:

```cpp
int& referencia_temperatura {temperatura};
```

---

Evitar:

```cpp
int& r {temperatura};
```

---

## Tener Cuidado al Modificar

Cualquier modificación realizada mediante la referencia afecta a la variable original.

---

# Error Común

Pensar que:

```cpp
int& referencia_edad {edad};
```

crea una nueva variable.

---

Realidad:

```text
No crea una nueva variable.
```

---

Crea:

```text
Un alias para una variable existente.
```

---

# Visualización General

```text
Variable
    │
    ▼
 Referencia
    │
    ▼
Mismo objeto
    │
    ▼
Misma memoria
```

---

# Tabla Resumen

| Operación | Resultado |
|------------|------------|
| Modificar variable | Cambia la referencia |
| Modificar referencia | Cambia la variable |
| Crear una copia | Objeto independiente |
| Crear una referencia | Alias del mismo objeto |

---

## Resumen

- Una referencia y una variable representan el mismo objeto.
- Modificar cualquiera de ellas afecta al mismo valor.
- Una referencia no crea una copia.
- Es posible tener múltiples referencias para una misma variable.
- Variable y referencia comparten la misma dirección de memoria.
- Las referencias siguen las reglas normales de scope y lifetime.
- Comprender esta relación es fundamental para trabajar con funciones eficientes.
- Las referencias permiten acceder al mismo objeto mediante distintos nombres.
