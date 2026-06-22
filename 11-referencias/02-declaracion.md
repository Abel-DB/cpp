# Declaración de Referencias

## Introducción

En el tema anterior aprendimos que una referencia es un alias para una variable existente.

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

Ahora estudiaremos cómo se declaran las referencias y las reglas que deben cumplirse.

---

# Sintaxis

La sintaxis general es:

```cpp
tipo& nombre_referencia {variable};
```

---

Ejemplo:

```cpp
int edad {25};

int& referencia_edad {edad};
```

---

Visualización:

```text
tipo  &
 │     │
 ▼     ▼
int& referencia_edad {edad};
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

# El Operador &

En una declaración de referencia:

```cpp
int& referencia_edad {edad};
```

el símbolo:

```cpp
&
```

significa:

```text
Referencia a
```

---

No debe confundirse con otros usos de:

```cpp
&
```

que veremos más adelante.

---

# Inicialización Obligatoria

Una referencia debe inicializarse al momento de declararse.

---

Correcto:

```cpp
int edad {25};

int& referencia_edad {edad};
```

---

Incorrecto:

```cpp
int& referencia_edad;
```

---

Resultado:

```text
Error de compilación
```

---

Porque una referencia siempre debe estar asociada a una variable.

---

# ¿Por Qué?

Una referencia no puede existir sola.

---

Visualización:

```text
Referencia
    │
    ▼
¿Referencia a qué?
```

---

Debe existir una variable asociada.

---

# Asociar a una Variable Existente

```cpp
int temperatura {20};

int& referencia_temperatura {temperatura};
```

---

Ahora:

```text
temperatura
```

y

```text
referencia_temperatura
```

representan el mismo objeto.

---

# Diferentes Tipos

Las referencias utilizan el mismo tipo que la variable referenciada.

---

## int

```cpp
int edad {25};

int& referencia_edad {edad};
```

---

## double

```cpp
double precio {99.99};

double& referencia_precio {precio};
```

---

## bool

```cpp
bool activo {true};

bool& referencia_activo {activo};
```

---

## std::string

```cpp
std::string nombre {"Juan"};

std::string& referencia_nombre {nombre};
```

---

# Múltiples Referencias

Es posible crear varias referencias para la misma variable.

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

Todas representan el mismo objeto.

---

# Ejemplo

```cpp
int edad {25};

int& referencia_1 {edad};
int& referencia_2 {edad};

referencia_1 = 40;

std::cout
    << referencia_2
    << '\n';
```

Salida:

```text
40
```

---

# Referencias y Asignación

Observa:

```cpp
int edad {25};

int& referencia_edad {edad};
```

---

Después:

```cpp
referencia_edad = 30;
```

---

Esto NO significa:

```text
Cambiar la referencia
```

---

Significa:

```text
Modificar el valor referenciado
```

---

Resultado:

```cpp
edad == 30
```

---

# Una Referencia No Puede Reasignarse

Observa:

```cpp
int edad {25};
int temperatura {20};

int& referencia_dato {edad};
```

---

Luego:

```cpp
referencia_dato = temperatura;
```

---

Muchos principiantes creen que ahora:

```cpp
referencia_dato
```

apunta a:

```cpp
temperatura
```

---

Pero eso es incorrecto.

---

Lo que realmente ocurre es:

```cpp
edad = temperatura;
```

---

Resultado:

```text
edad = 20
```

---

La referencia sigue asociada a:

```cpp
edad
```

---

# Visualización

Antes:

```text
referencia_dato
       │
       ▼
      edad
       │
       ▼
      25
```

---

Después:

```cpp
referencia_dato = temperatura;
```

---

Resultado:

```text
referencia_dato
       │
       ▼
      edad
       │
       ▼
      20
```

---

La asociación no cambia.

---

# Referencias y Literales

Una referencia no constante no puede asociarse directamente a un literal.

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

Porque:

```cpp
10
```

no es una variable.

---

Más adelante veremos cómo las referencias constantes permiten otros casos.

---

# Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    int temperatura {20};

    int& referencia_temperatura {temperatura};

    referencia_temperatura = 35;

    std::cout
        << temperatura
        << '\n';

    std::cout
        << referencia_temperatura
        << '\n';

    return 0;
}
```

Salida:

```text
35
35
```

---

# Buenas Prácticas

## Inicializar Siempre la Referencia

Correcto:

```cpp
int& referencia_edad {edad};
```

---

## Utilizar Nombres Descriptivos

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

## Recordar que No Puede Reasignarse

Una vez creada:

```cpp
referencia_temperatura
```

siempre estará asociada a la misma variable.

---

# Error Común

Pensar que:

```cpp
referencia_dato = temperatura;
```

cambia la variable referenciada.

---

Realidad:

```text
Modifica el contenido de la variable original.
```

---

La referencia continúa asociada al mismo objeto.

---

# Visualización General

```text
Declaración
      │
      ▼
tipo& referencia {variable}
      │
      ▼
Alias creado
      │
      ▼
Mismo objeto
```

---

# Tabla Resumen

| Regla | Descripción |
|---------|-------------|
| Debe inicializarse | Sí |
| Puede quedar vacía | No |
| Puede reasignarse | No |
| Puede modificar la variable | Sí |
| Es una copia | No |

---

## Resumen

- Una referencia se declara utilizando `&`.
- Debe inicializarse en el momento de su declaración.
- Siempre está asociada a una variable existente.
- Una referencia no puede quedar sin inicializar.
- Una referencia no puede reasignarse a otra variable.
- Modificar la referencia modifica el objeto referenciado.
- Es posible crear múltiples referencias para la misma variable.
- Comprender estas reglas es fundamental antes de trabajar con referencias constantes y punteros.
```**``**
