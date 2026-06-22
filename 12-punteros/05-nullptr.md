# nullptr

## Introducción

En los temas anteriores aprendimos que un puntero almacena una dirección de memoria.

Ejemplo:

```cpp
int edad {25};

int* puntero_edad {&edad};
```

---

También vimos que para utilizar el valor apuntado usamos:

```cpp
*puntero_edad
```

---

Sin embargo, aparece una pregunta importante:

```text
¿Qué ocurre si todavía no tenemos
una dirección válida para almacenar?
```

---

Por ejemplo:

```text
Un puntero recién creado.
Una búsqueda que no encontró resultados.
Un objeto que aún no existe.
```

---

Necesitamos una forma de indicar:

```text
Este puntero no apunta a nada.
```

---

Para ello C++ proporciona:

```cpp
nullptr
```

---

# ¿Qué es nullptr?

`nullptr` representa la ausencia de una dirección válida.

---

Visualización:

```text
puntero_edad
      │
      ▼
   nullptr
```

---

Significa:

```text
No apunta a ningún objeto.
```

---

# Sintaxis

```cpp
int* puntero_numero {nullptr};
```

---

Ejemplo:

```cpp
double* puntero_precio {nullptr};
```

---

```cpp
char* puntero_letra {nullptr};
```

---

Todos son válidos.

---

# Primer Ejemplo

```cpp
#include <iostream>

int main()
{
    int* puntero_numero {nullptr};

    return 0;
}
```

---

Aquí:

```cpp
puntero_numero
```

no apunta a ninguna variable.

---

# ¿Por Qué Usar nullptr?

Observa:

```cpp
int* puntero_numero;
```

---

Problema:

```text
No está inicializado.
```

---

Su contenido es desconocido.

---

Visualización:

```text
puntero_numero
      │
      ▼
 Dirección basura
```

---

Esto es peligroso.

---

# Forma Correcta

```cpp
int* puntero_numero {nullptr};
```

---

Ahora sabemos exactamente que:

```text
No apunta a nada.
```

---

Visualización:

```text
puntero_numero
      │
      ▼
   nullptr
```

---

# Comprobar si un Puntero es Nulo

Podemos verificarlo mediante:

```cpp
if (puntero_numero == nullptr)
{
}
```

---

Ejemplo:

```cpp
if (puntero_numero == nullptr)
{
    std::cout
        << "Sin direccion\n";
}
```

---

Salida:

```text
Sin direccion
```

---

# Forma Más Habitual

También es común escribir:

```cpp
if (!puntero_numero)
{
}
```

---

Porque un puntero nulo se interpreta como:

```text
false
```

---

Ejemplo:

```cpp
if (!puntero_numero)
{
    std::cout
        << "Sin direccion\n";
}
```

---

Resultado:

```text
Sin direccion
```

---

# Asignar una Dirección Más Tarde

Un puntero puede comenzar como:

```cpp
nullptr
```

---

y posteriormente apuntar a un objeto.

---

Ejemplo:

```cpp
int edad {25};

int* puntero_edad {nullptr};

puntero_edad = &edad;
```

---

Visualización:

Antes:

```text
puntero_edad
      │
      ▼
   nullptr
```

---

Después:

```text
puntero_edad
      │
      ▼
     edad
```

---

# Comprobar Antes de Desreferenciar

Recordemos:

```cpp
*puntero_edad
```

---

solo es seguro cuando existe una dirección válida.

---

Por ello es habitual:

```cpp
if (puntero_edad)
{
    std::cout
        << *puntero_edad;
}
```

---

Visualización:

```text
¿Es nullptr?
      │
   Sí ▼ No
      │
      ▼
Desreferenciar
```

---

# Error Grave

Observa:

```cpp
int* puntero_numero {nullptr};

std::cout
    << *puntero_numero;
```

---

Resultado:

```text
Comportamiento indefinido
```

---

Porque:

```text
No existe ningún objeto válido.
```

---

# Visualización

```text
nullptr
   │
   ▼
Nada
```

---

Intentar:

```cpp
*puntero_numero
```

equivale a:

```text
Acceder a algo que no existe.
```

---

# Ejemplo Completo

```cpp
#include <iostream>

int main()
{
    int* puntero_numero {nullptr};

    if (!puntero_numero)
    {
        std::cout
            << "Puntero vacio\n";
    }

    int numero {42};

    puntero_numero = &numero;

    if (puntero_numero)
    {
        std::cout
            << *puntero_numero
            << '\n';
    }

    return 0;
}
```

Salida:

```text
Puntero vacio
42
```

---

# nullptr vs NULL

Antes de C++11 era común utilizar:

```cpp
NULL
```

---

Ejemplo:

```cpp
int* puntero_numero {NULL};
```

---

Actualmente se recomienda:

```cpp
nullptr
```

---

Porque:

```text
Es específico para punteros.
Es más seguro.
Evita ambigüedades.
```

---

# Comparación

## Antiguo

```cpp
NULL
```

---

## Moderno

```cpp
nullptr
```

---

Preferir siempre:

```cpp
nullptr
```

---

# Uso Habitual

Es frecuente encontrar:

```cpp
int* puntero_numero {nullptr};
```

---

en:

```text
Inicializaciones
Búsquedas
Recursos opcionales
Objetos aún no creados
```

---

# Buenas Prácticas

## Inicializar Siempre los Punteros

Correcto:

```cpp
int* puntero_numero {nullptr};
```

---

Evitar:

```cpp
int* puntero_numero;
```

---

## Verificar Antes de Desreferenciar

Correcto:

```cpp
if (puntero_numero)
{
}
```

---

## Utilizar nullptr

Correcto:

```cpp
nullptr
```

---

Evitar:

```cpp
NULL
```

---

# Error Común

Pensar que:

```cpp
nullptr
```

es una dirección real.

---

Realidad:

```text
Representa la ausencia de una dirección válida.
```

---

Otro error común:

```cpp
int* puntero_numero {nullptr};

*puntero_numero = 10;
```

---

Resultado:

```text
Comportamiento indefinido
```

---

# Visualización General

```text
Puntero
   │
   ▼
nullptr

No apunta a nada
```

---

```text
Puntero
   │
   ▼
Dirección válida
   │
   ▼
Objeto
```

---

# Tabla Resumen

| Estado | Significado |
|----------|-------------|
| `nullptr` | No apunta a ningún objeto |
| `&variable` | Dirección válida |
| Sin inicializar | Valor desconocido |

---

## Resumen

- `nullptr` representa la ausencia de una dirección válida.
- Se utiliza para indicar que un puntero no apunta a ningún objeto.
- Es recomendable inicializar los punteros con `nullptr`.
- Nunca debe desreferenciarse un puntero nulo.
- Los punteros pueden verificarse antes de utilizarse.
- Desde C++11 se prefiere `nullptr` frente a `NULL`.
- Mejora la seguridad y claridad del código.
- Es una herramienta fundamental al trabajar con punteros.
