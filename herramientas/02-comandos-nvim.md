# Atajos de Neovim

## ¿Qué es Neovim?

Neovim es un editor de texto orientado al desarrollo de software que permite trabajar de forma eficiente utilizando principalmente el teclado.

Su filosofía consiste en minimizar el uso del mouse y maximizar la productividad mediante comandos.

---

# Modos de trabajo

| Modo    | Descripción                        |
| ------- | ---------------------------------- |
| Normal  | Navegación y ejecución de comandos |
| Insert  | Escritura de texto                 |
| Visual  | Selección de texto                 |
| Command | Comandos avanzados                 |

---

# Entrar en modo inserción

| Comando | Acción                         |
| ------- | ------------------------------ |
| i       | Insertar antes del cursor      |
| a       | Insertar después del cursor    |
| I       | Insertar al inicio de la línea |
| A       | Insertar al final de la línea  |
| o       | Crear línea debajo e insertar  |
| O       | Crear línea arriba e insertar  |

---

# Salir del modo inserción

| Comando | Acción                |
| ------- | --------------------- |
| Esc     | Volver al modo normal |

---

# Navegación básica

| Comando | Acción    |
| ------- | --------- |
| h       | Izquierda |
| j       | Abajo     |
| k       | Arriba    |
| l       | Derecha   |

---

# Navegación por palabras

| Comando | Acción                     |
| ------- | -------------------------- |
| w       | Siguiente palabra          |
| e       | Final de palabra           |
| b       | Inicio de palabra anterior |

---

# Navegación por líneas

| Comando | Acción                      |
| ------- | --------------------------- |
| 0       | Inicio de línea             |
| ^       | Primer carácter de la línea |
| $       | Final de línea              |

---

# Navegación por archivo

| Comando | Acción             |
| ------- | ------------------ |
| gg      | Inicio del archivo |
| G       | Final del archivo  |
| 10G     | Ir a línea 10      |
| :10     | Ir a línea 10      |

---

# Selección de texto

## Visual Mode

| Comando | Acción                   |
| ------- | ------------------------ |
| v       | Selección por caracteres |
| V       | Selección por líneas     |
| Ctrl+v  | Selección por bloques    |

---

## Selecciones rápidas

| Comando | Acción                              |
| ------- | ----------------------------------- |
| viw     | Seleccionar palabra                 |
| vip     | Seleccionar párrafo                 |
| vap     | Seleccionar párrafo completo        |
| vw      | Seleccionar hasta siguiente palabra |
| ve      | Seleccionar hasta final de palabra  |
| v0      | Seleccionar hasta inicio de línea   |
| v$      | Seleccionar hasta final de línea    |

---

# Copiar y pegar

| Comando | Acción       |
| ------- | ------------ |
| y       | Copiar       |
| yy      | Copiar línea |
| p       | Pegar debajo |
| P       | Pegar encima |

---

# Eliminar texto

| Comando | Acción                        |
| ------- | ----------------------------- |
| x       | Eliminar carácter             |
| dd      | Eliminar línea                |
| diw     | Eliminar contenido de palabra |
| daw     | Eliminar palabra completa     |

---

# Edición rápida

| Comando | Acción                           |
| ------- | -------------------------------- |
| ciw     | Cambiar palabra                  |
| ci"     | Cambiar contenido entre comillas |
| cc      | Cambiar línea completa           |
| .       | Repetir último comando           |

---

# Deshacer y rehacer

| Comando | Acción   |
| ------- | -------- |
| u       | Deshacer |
| Ctrl+r  | Rehacer  |

---

# Búsqueda

| Comando | Acción                     |
| ------- | -------------------------- |
| /texto  | Buscar texto               |
| n       | Siguiente coincidencia     |
| N       | Coincidencia anterior      |
| *       | Buscar palabra bajo cursor |

---

# Comentarios

## Comment.nvim

| Comando | Acción                    |
| ------- | ------------------------- |
| gcc     | Comentar línea            |
| Ngcc    | Comentar N líneas         |
| gc      | Comentar selección visual |

### Ejemplos

```text
gcc
3gcc
5gcc
```

---

# Indentación

| Comando | Acción               |
| ------- | -------------------- |
| >>      | Indentar línea       |
| <<      | Desindentar línea    |
| gg=G    | Autoindentar archivo |

---

# Ventanas

## Crear ventanas

| Comando | Acción              |
| ------- | ------------------- |
| :sp     | División horizontal |
| :vsp    | División vertical   |

---

## Moverse entre ventanas

| Comando  | Acción    |
| -------- | --------- |
| Ctrl+w h | Izquierda |
| Ctrl+w j | Abajo     |
| Ctrl+w k | Arriba    |
| Ctrl+w l | Derecha   |

---

## Redimensionar ventanas

| Comando  | Acción          |
| -------- | --------------- |
| Ctrl+w < | Reducir ancho   |
| Ctrl+w > | Aumentar ancho  |
| Ctrl+w - | Reducir altura  |
| Ctrl+w + | Aumentar altura |

---

## Cerrar

| Comando | Acción         |
| ------- | -------------- |
| :q      | Cerrar ventana |
| :qa     | Cerrar todas   |

---

# Buffers

| Comando | Acción           |
| ------- | ---------------- |
| :ls     | Listar buffers   |
| :bnext  | Buffer siguiente |
| :bprev  | Buffer anterior  |
| :bd     | Cerrar buffer    |

---

# Guardar archivos

| Comando | Acción            |
| ------- | ----------------- |
| :w      | Guardar           |
| :wq     | Guardar y salir   |
| :q!     | Salir sin guardar |

---

# Telescope (NvChad)

## Búsquedas

| Comando  | Acción                   |
| -------- | ------------------------ |
| Space ff | Buscar archivos          |
| Space fb | Buscar buffers abiertos  |
| Space fw | Buscar texto en proyecto |
| Space fo | Archivos recientes       |

---

## Edición

| Comando  | Acción           |
| -------- | ---------------- |
| Space fm | Formatear código |

---

# LSP (Clangd)

## Navegación

| Comando | Acción              |
| ------- | ------------------- |
| gd      | Ir a definición     |
| gr      | Ver referencias     |
| gi      | Ir a implementación |
| K       | Ver documentación   |

---

## Refactorización

| Comando  | Acción            |
| -------- | ----------------- |
| Space ca | Code Action       |
| Space rn | Renombrar símbolo |

---

# Programación en C++

## Navegación entre bloques

| Comando | Acción                                      |
| ------- | ------------------------------------------- |
| %       | Saltar entre llaves, paréntesis o corchetes |

---

## Utilidades

| Comando  | Acción             |
| -------- | ------------------ |
| gd       | Ir a definición    |
| gr       | Buscar referencias |
| K        | Documentación      |
| Space fm | Formatear código   |
| gg=G     | Reindentar archivo |

---

# Macros

## Grabar macro

| Comando | Acción                     |
| ------- | -------------------------- |
| qa      | Grabar macro en registro a |
| q       | Detener grabación          |

---

## Ejecutar macro

| Comando | Acción               |
| ------- | -------------------- |
| @a      | Ejecutar macro a     |
| @@      | Repetir última macro |

---

# Cheat Sheet Personal

## Uso diario

```text
i
a
o
Esc

h j k l

w
e
b

0
$

gg
G

yy
dd
p

u
Ctrl+r

/texto
n

gcc

:w
:wq

:bd

gd
gr
K

Space ff
Space fw

Space fm

%
```

---

# Relación con otras herramientas

Neovim se integra con:

* Clangd
* GCC / G++
* Clang / Clang++
* Git
* GitHub
* Make
* CMake
* GDB
* Kitty
* Zsh

---

# Conclusión

Neovim es una herramienta extremadamente potente para el desarrollo de software. Dominar estos atajos permite navegar, editar y mantener proyectos de forma rápida y eficiente, incrementando significativamente la productividad.

---

# Resumen

| Categoría  | Contenido           |
| ---------- | ------------------- |
| Navegación | h, j, k, l, w, e, b |
| Inserción  | i, a, o, I, A, O    |
| Selección  | v, V, Ctrl+v        |
| Edición    | ciw, diw, yy, dd    |
| Búsqueda   | /, n, N, *          |
| Ventanas   | :sp, :vsp           |
| Buffers    | :ls, :bd            |
| Telescope  | Space ff, fw, fb    |
| LSP        | gd, gr, gi, K       |
| C++        | %, Space fm         |
| Macros     | qa, @a              |
