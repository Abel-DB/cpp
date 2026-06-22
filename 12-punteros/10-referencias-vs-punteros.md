# Referencias vs Punteros

## Introducción

Durante los últimos temas estudiamos dos mecanismos que permiten acceder indirectamente a un objeto:

```cpp
Referencias
```

---

y

```cpp
Punteros
```

---

Ambos permiten trabajar con una variable sin copiarla.

---

Ejemplo con referencia:

```cpp
int numero {10};

int& referencia_numero {numero};
```

---

Ejemplo con puntero:

```cpp
int numero {10};

int* puntero_numero {&numero};
```

---

Sin embargo:

```text
No son lo mismo.
```

---

Comprender sus diferencias es fundamental para escribir código correcto en C++.

---

# Objetivo Común

Tanto las referencias como los punteros permiten acceder a un objeto existente.

---

Visualización:

```text
numero
  │
  ▼
 10
```

---

Referencia:

```text
referencia_numero
      │
      ▼
    numero
```

---

Puntero:

```text
puntero_numero
      │
      ▼
    numero
```

---

# Sintaxis

## Referencia

```cpp
int numero {10};

int& referencia_numero {numero};
```

---

## Puntero

```cpp
int numero {10};

int* puntero_numero {&numero};
```

---

# Uso

## Referencia

Acceso directo:

```cpp
std::cout
    << referencia_numero;
```

---

Modificación:

```cpp
referencia_numero = 20;
```

---

# Puntero

Acceso mediante:

```cpp
*puntero_numero
```

---

Lectura:

```cpp
std::cout
    << *puntero_numero;
```

---

Modificación:

```cpp
*puntero_numero = 20;
```

---

# Inicialización

Una referencia:

```cpp
Debe inicializarse obligatoriamente.
```

---

Correcto:

```cpp
int numero {10};

int& referencia_numero {numero};
```

---

Incorrecto:

```cpp
int& referencia_numero;
```

---

Resultado:

```text
Error de compilación
```

---

# Punteros

Un puntero puede existir sin apuntar a nada.

---

Ejemplo:

```cpp
int* puntero_numero {};
```

---

o:

```cpp
int* puntero_numero {nullptr};
```

---

Correcto.

---

# ¿Puede Ser nullptr?

## Referencia

No.

---

Una referencia siempre debe referirse a un objeto válido.

---

Incorrecto:

```cpp
int& referencia_numero {nullptr};
```

---

Resultado:

```text
Error de compilación
```

---

# Puntero

Sí.

---

Correcto:

```cpp
int* puntero_numero {nullptr};
```

---

Visualización:

```text
No apunta a ningún objeto
```

---

# Reasignación

Una referencia no puede cambiar de objeto.

---

Ejemplo:

```cpp
int numero_1 {10};
int numero_2 {20};

int& referencia_numero {numero_1};
```

---

Intentar:

```cpp
referencia_numero = numero_2;
```

---

NO cambia la referencia.

---

Realmente hace:

```cpp
numero_1 = numero_2;
```

---

Resultado:

```text
numero_1 vale 20
```

---

La referencia sigue vinculada a:

```cpp
numero_1
```

---

# Punteros Sí Pueden Reasignarse

```cpp
int numero_1 {10};
int numero_2 {20};

int* puntero_numero {&numero_1};

puntero_numero = &numero_2;
```

---

Ahora apunta a:

```cpp
numero_2
```

---

Visualización:

```text
Antes

puntero_numero ──► numero_1

Después

puntero_numero ──► numero_2
```

---

# Seguridad

Las referencias suelen considerarse más seguras.

---

Porque:

```text
No pueden ser nulas.
No requieren desreferenciación.
No pueden reasignarse.
```

---

# Ejemplo

Referencia:

```cpp
int numero {10};

int& referencia_numero {numero};

std::cout
    << referencia_numero;
```

---

Puntero:

```cpp
int numero {10};

int* puntero_numero {&numero};

std::cout
    << *puntero_numero;
```

---

La referencia resulta más simple.

---

# Uso en Funciones

## Referencia

```cpp
void duplicar(int& numero)
{
    numero *= 2;
}
```

---

Uso:

```cpp
duplicar(numero);
```

---

# Puntero

```cpp
void duplicar(int* puntero_numero)
{
    *puntero_numero *= 2;
}
```

---

Uso:

```cpp
duplicar(&numero);
```

---

La versión con referencia suele ser más legible.

---

# ¿Cuándo Usar Referencias?

Cuando:

```text
Siempre debe existir un objeto válido.
```

---

Ejemplos:

```cpp
void mostrarValor(
    const int& numero)
{
}
```

---

```cpp
void duplicar(
    int& numero)
{
}
```

---

# ¿Cuándo Usar Punteros?

Cuando:

```text
nullptr es una posibilidad válida.
```

---

o cuando necesitamos:

```text
Reasignar direcciones.
Trabajar con arrays.
Gestionar memoria dinámica.
```

---

Ejemplos:

```cpp
int* puntero_numero {};
```

---

```cpp
procesar(nullptr);
```

---

# Ejemplo Comparativo

## Referencia

```cpp
int numero {10};

int& referencia_numero {numero};

referencia_numero = 20;
```

---

Resultado:

```cpp
numero == 20
```

---

# Puntero

```cpp
int numero {10};

int* puntero_numero {&numero};

*puntero_numero = 20;
```

---

Resultado:

```cpp
numero == 20
```

---

Ambos logran el mismo efecto.

---

# Diferencia Mental

Una referencia suele verse como:

```text
Otro nombre para el mismo objeto.
```

---

Visualización:

```text
numero
   ▲
   │
referencia_numero
```

---

Un puntero suele verse como:

```text
Una variable que almacena una dirección.
```

---

Visualización:

```text
puntero_numero
       │
       ▼
     numero
```

---

# Ejemplo Completo

```cpp
#include <iostream>

void duplicarReferencia(
    int& numero)
{
    numero *= 2;
}

void duplicarPuntero(
    int* puntero_numero)
{
    if (puntero_numero == nullptr)
    {
        return;
    }

    *puntero_numero *= 2;
}

int main()
{
    int numero_1 {10};
    int numero_2 {10};

    duplicarReferencia(numero_1);

    duplicarPuntero(&numero_2);

    std::cout
        << numero_1
        << '\n';

    std::cout
        << numero_2
        << '\n';

    return 0;
}
```

Salida:

```text
20
20
```

---

# Buenas Prácticas

## Preferir Referencias Cuando Sea Posible

Correcto:

```cpp
void actualizar(
    int& valor)
{
}
```

---

## Utilizar Punteros Cuando nullptr Sea Necesario

Correcto:

```cpp
void procesar(
    int* puntero_numero)
{
}
```

---

## Verificar nullptr

Siempre que exista la posibilidad.

---

```cpp
if (puntero_numero == nullptr)
{
    return;
}
```

---

# Error Común

Pensar que una referencia puede cambiar de objeto.

---

Incorrecto:

```cpp
int& referencia_numero {numero_1};

referencia_numero = numero_2;
```

---

Resultado:

```text
Copia el valor.
```

---

No:

```text
Cambia la referencia.
```

---

# Visualización General

```text
Referencia

Objeto
  ▲
  │
Alias
```

---

```text
Puntero

Puntero
   │
   ▼
 Objeto
```

---

# Tabla Comparativa

| Característica | Referencia | Puntero |
|---------------|------------|----------|
| Debe inicializarse | Sí | No |
| Puede ser `nullptr` | No | Sí |
| Puede reasignarse | No | Sí |
| Usa `*` para acceder | No | Sí |
| Sintaxis simple | Sí | No |
| Ideal para parámetros | Sí | Sí |

---

## Resumen

- Las referencias y los punteros permiten acceder indirectamente a objetos.
- Una referencia actúa como un alias de un objeto existente.
- Un puntero almacena una dirección de memoria.
- Las referencias deben inicializarse y no pueden ser nulas.
- Los punteros pueden ser `nullptr` y pueden cambiar de objeto.
- Las referencias suelen ser más simples y seguras.
- Los punteros ofrecen mayor flexibilidad.
- Elegir entre ambos depende del problema que se desea resolver.
