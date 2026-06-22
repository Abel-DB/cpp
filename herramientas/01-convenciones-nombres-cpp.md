# Convenciones de Nombres en C++

## ¿Qué son las convenciones de nombres?

Las convenciones de nombres son recomendaciones utilizadas para nombrar variables, funciones, clases, constantes y otros elementos de un programa.

Su objetivo es mejorar:

- La legibilidad del código.
- La organización de proyectos.
- El mantenimiento del software.
- El trabajo en equipo.

> **Importante:** Estas convenciones no son obligatorias. Lo más importante es mantener un criterio consistente en todo el proyecto.

---

# Convención utilizada en estos apuntes

| Elemento | Convención |
|-----------|------------|
| Variables | snake_case |
| Funciones | camelCase |
| Clases | PascalCase |
| Estructuras | PascalCase |
| Namespaces | snake_case |
| Enumeraciones | PascalCase |
| Valores enum | PascalCase |
| Templates | PascalCase |
| Constantes | UPPER_CASE |
| Macros | UPPER_CASE |
| Archivos | snake_case |

---

# Variables

Las variables almacenan información que puede cambiar durante la ejecución del programa.

Se utilizará **snake_case**.

### Ejemplos

```cpp
int edad_usuario;
double promedio_final;
std::string nombre_completo;
```

---

# Funciones

Las funciones realizan una tarea específica dentro del programa.

Se utilizará **camelCase**.

### Ejemplos

```cpp
void calcularPromedio();
int obtenerEdad();
void guardarArchivo();
```

---

# Clases

Las clases representan plantillas para la creación de objetos.

Se utilizará **PascalCase**.

### Ejemplos

```cpp
class Estudiante
{
};

class CuentaBancaria
{
};

class SistemaVentas
{
};
```

---

# Estructuras

Las estructuras permiten agrupar datos relacionados.

Se utilizará **PascalCase**.

### Ejemplos

```cpp
struct Producto
{
};

struct Cliente
{
};

struct Empleado
{
};
```

---

# Namespaces

Los namespaces permiten agrupar código relacionado y evitar conflictos de nombres.

Se utilizará **snake_case**.

### Ejemplos

```cpp
namespace sistema_ventas
{
}
```

```cpp
namespace utilidades_texto
{
}
```

```cpp
namespace calculos_financieros
{
}
```

---

# Enumeraciones

Las enumeraciones permiten representar conjuntos de valores relacionados.

Se utilizará **PascalCase**.

### Ejemplos

```cpp
enum class EstadoPedido
{
};
```

```cpp
enum class Color
{
};
```

```cpp
enum class TipoUsuario
{
};
```

---

# Valores de Enumeraciones

Los valores de una enumeración utilizarán **PascalCase**.

### Ejemplo

```cpp
enum class EstadoPedido
{
    Pendiente,
    Procesando,
    Completado
};
```

---

# Templates

Los parámetros de template utilizarán **PascalCase**.

### Ejemplos

```cpp
template<typename Tipo>
class Vector
{
};
```

```cpp
template<typename TValor>
void mostrar(TValor valor)
{
}
```

---

# Constantes

Las constantes almacenan valores que no cambian durante la ejecución del programa.

Se utilizará **UPPER_CASE**.

### Ejemplos

```cpp
const int MAX_ESTUDIANTES {100};
const double PI {3.141592};
const int LIMITE_INTENTOS {3};
```

---

# Macros

Las macros utilizarán **UPPER_CASE**.

### Ejemplos

```cpp
#define MAX_USUARIOS 100
```

```cpp
#define VERSION_APP "1.0"
```

---

# Archivos

Los nombres de archivos deben ser descriptivos y consistentes.

Se utilizará **snake_case**.

### Ejemplos

```text
variables_tipos_datos.cpp
operadores_basicos.cpp
sistema_notas.cpp
```

---

# Estilos de Nomenclatura

## snake_case

Las palabras se escriben en minúsculas y se separan mediante guiones bajos.

### Ejemplos

```text
edad_usuario
promedio_final
cantidad_estudiantes
```

---

## camelCase

La primera palabra comienza en minúscula y las siguientes en mayúscula.

### Ejemplos

```text
calcularPromedio
obtenerEdad
guardarArchivo
```

---

## PascalCase

Todas las palabras comienzan en mayúscula.

### Ejemplos

```text
Estudiante
CuentaBancaria
SistemaVentas
```

---

## UPPER_CASE

Todas las letras se escriben en mayúsculas y las palabras se separan mediante guiones bajos.

### Ejemplos

```text
MAX_ESTUDIANTES
PI
LIMITE_INTENTOS
```

---

# Buenas Prácticas Generales

| Recomendación | Ejemplo |
|--------------|----------|
| Utilizar nombres descriptivos | promedio_final |
| Mantener consistencia | usar siempre la misma convención |
| Evitar abreviaturas confusas | cantidad_estudiantes |
| Relacionar el nombre con el problema | salario_mensual |
| Evitar nombres excesivamente largos | nombre_usuario |

---

# Errores Comunes

| Error | Ejemplo |
|--------|----------|
| Nombres poco descriptivos | a, x, dato |
| Mezclar convenciones sin criterio | edad_usuario, Nombre, TOTAL |
| Utilizar palabras reservadas | int, while, class |
| Nombres excesivamente largos | nombre_del_usuario_registrado_en_la_aplicacion |

---

# Resumen

| Elemento | Convención |
|-----------|------------|
| Variables | snake_case |
| Funciones | camelCase |
| Clases | PascalCase |
| Estructuras | PascalCase |
| Namespaces | snake_case |
| Enumeraciones | PascalCase |
| Valores enum | PascalCase |
| Templates | PascalCase |
| Constantes | UPPER_CASE |
| Macros | UPPER_CASE |
| Archivos | snake_case |

---

## Resumen Final

- Las convenciones de nombres mejoran la legibilidad y el mantenimiento del código.
- En estos apuntes se utilizará una convención consistente para todos los ejemplos.
- Las variables usarán `snake_case`.
- Las funciones usarán `camelCase`.
- Las clases, estructuras y enumeraciones usarán `PascalCase`.
- Los namespaces usarán `snake_case`.
- Las constantes y macros usarán `UPPER_CASE`.
- Los archivos usarán `snake_case`.
- Mantener una convención uniforme facilita el desarrollo de proyectos grandes y el trabajo en equipo.
