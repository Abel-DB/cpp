# Neovim + NvChad Cheat Sheet (Versión Realmente Útil)

## Regla de Oro

Vim funciona con:

operador + movimiento

Ejemplos:

dw   -> borrar palabra
cw   -> cambiar palabra
yw   -> copiar palabra

---

# MODOS

| Comando | Acción                      |
| ------- | --------------------------- |
| Esc     | Volver a modo Normal        |
| i       | Insertar antes del cursor   |
| a       | Insertar después del cursor |
| I       | Insertar al inicio de línea |
| A       | Insertar al final de línea  |
| o       | Nueva línea debajo          |
| O       | Nueva línea encima          |

---

# NAVEGACIÓN

## Básica

| Comando | Acción    |
| ------- | --------- |
| h       | Izquierda |
| j       | Abajo     |
| k       | Arriba    |
| l       | Derecha   |

## Por palabras

| Comando | Acción            |
| ------- | ----------------- |
| w       | Siguiente palabra |
| e       | Final de palabra  |
| b       | Palabra anterior  |

## Por línea

| Comando | Acción          |
| ------- | --------------- |
| 0       | Inicio de línea |
| ^       | Primer carácter |
| $       | Final de línea  |

## Por archivo

| Comando | Acción             |
| ------- | ------------------ |
| gg      | Inicio del archivo |
| G       | Final del archivo  |
| 10G     | Ir a línea 10      |
| :10     | Ir a línea 10      |

## Scroll

| Comando | Acción              |
| ------- | ------------------- |
| Ctrl+d  | Media página abajo  |
| Ctrl+u  | Media página arriba |
| Ctrl+f  | Página abajo        |
| Ctrl+b  | Página arriba       |

---

# SELECCIÓN

| Comando | Acción             |
| ------- | ------------------ |
| v       | Visual             |
| V       | Visual por líneas  |
| Ctrl+v  | Visual por bloques |

---

# TEXT OBJECTS (MUY IMPORTANTES)

## Palabras

| Comando | Acción            |
| ------- | ----------------- |
| iw      | Dentro de palabra |
| aw      | Palabra completa  |
| ciw     | Cambiar palabra   |
| diw     | Borrar palabra    |
| yiw     | Copiar palabra    |

## Comillas

| Comando | Acción            |
| ------- | ----------------- |
| ci"     | Cambiar contenido |
| di"     | Borrar contenido  |
| yi"     | Copiar contenido  |

## Paréntesis

| Comando | Acción            |
| ------- | ----------------- |
| ci(     | Cambiar contenido |
| di(     | Borrar contenido  |
| yi(     | Copiar contenido  |

## Llaves

| Comando | Acción         |
| ------- | -------------- |
| ci{     | Cambiar bloque |
| di{     | Borrar bloque  |
| yi{     | Copiar bloque  |

---

# COPIAR Y PEGAR

| Comando | Acción           |
| ------- | ---------------- |
| yy      | Copiar línea     |
| y       | Copiar selección |
| p       | Pegar después    |
| P       | Pegar antes      |

---

# BORRAR

| Comando | Acción                      |
| ------- | --------------------------- |
| x       | Borrar carácter             |
| dd      | Borrar línea                |
| dw      | Borrar palabra              |
| diw     | Borrar palabra actual       |
| d$      | Borrar hasta final de línea |

---

# CAMBIAR

| Comando | Acción                       |
| ------- | ---------------------------- |
| cw      | Cambiar palabra              |
| ciw     | Cambiar palabra actual       |
| cc      | Cambiar línea                |
| c$      | Cambiar hasta final de línea |

---

# DESHACER

| Comando | Acción |
| ------- | ------ |
| u       | Undo   |
| Ctrl+r  | Redo   |

---

# BÚSQUEDA

| Comando | Acción                     |
| ------- | -------------------------- |
| /texto  | Buscar                     |
| n       | Siguiente coincidencia     |
| N       | Coincidencia anterior      |
| *       | Buscar palabra bajo cursor |

---

# COMENTARIOS (Comment.nvim)

| Comando | Acción             |
| ------- | ------------------ |
| gcc     | Comentar línea     |
| gc      | Comentar selección |
| 3gcc    | Comentar 3 líneas  |

---

# INDENTACIÓN

| Comando | Acción                         |
| ------- | ------------------------------ |
| >>      | Indentar                       |
| <<      | Desindentar                    |
| gg=G    | Formatear indentación completa |

---

# VENTANAS

## Crear

| Comando | Acción              |
| ------- | ------------------- |
| :sp     | División horizontal |
| :vsp    | División vertical   |

## Moverse

### Vim

| Comando  | Acción    |
| -------- | --------- |
| Ctrl+w h | Izquierda |
| Ctrl+w j | Abajo     |
| Ctrl+w k | Arriba    |
| Ctrl+w l | Derecha   |

### NvChad

| Comando | Acción    |
| ------- | --------- |
| Ctrl+h  | Izquierda |
| Ctrl+j  | Abajo     |
| Ctrl+k  | Arriba    |
| Ctrl+l  | Derecha   |

---

# BUFFERS

## Vim

| Comando | Acción           |
| ------- | ---------------- |
| :ls     | Listar buffers   |
| :bnext  | Siguiente buffer |
| :bprev  | Buffer anterior  |
| :bd     | Cerrar buffer    |

## NvChad

| Comando   | Acción           |
| --------- | ---------------- |
| Tab       | Siguiente buffer |
| Shift+Tab | Buffer anterior  |
| Space x   | Cerrar buffer    |

---

# GUARDAR

| Comando | Acción            |
| ------- | ----------------- |
| :w      | Guardar           |
| :wq     | Guardar y salir   |
| :q!     | Salir sin guardar |
| :qa     | Salir de todo     |

---

# MARCAS

| Comando | Acción                    |
| ------- | ------------------------- |
| ma      | Crear marca a             |
| 'a      | Ir a la línea de la marca |
| `a      | Ir a posición exacta      |

---

# TELESCOPE (NvChad)

| Comando  | Acción             |
| -------- | ------------------ |
| Space ff | Buscar archivos    |
| Space fw | Buscar texto       |
| Space fb | Buffers            |
| Space fo | Archivos recientes |
| Space fh | Ayuda              |

---

# EXPLORADOR DE ARCHIVOS

| Comando | Acción          |
| ------- | --------------- |
| Space e | Abrir NvimTree  |
| Ctrl+n  | Toggle NvimTree |

---

# LSP

## Navegación

| Comando | Acción          |
| ------- | --------------- |
| gd      | Ir a definición |
| gr      | Referencias     |
| gi      | Implementación  |
| K       | Documentación   |

## Refactorización

| Comando  | Acción      |
| -------- | ----------- |
| Space ca | Code Action |
| Space rn | Rename      |

## Formato

| Comando  | Acción            |
| -------- | ----------------- |
| Space fm | Formatear archivo |

---

# TERMINAL (NvChad)

| Comando | Acción              |
| ------- | ------------------- |
| Alt+i   | Terminal flotante   |
| Space h | Terminal horizontal |
| Space v | Terminal vertical   |

---

# GIT

## Terminal

git status
git add .
git commit -m "mensaje"
git push
git pull

## Telescope Git

| Comando  | Acción     |
| -------- | ---------- |
| Space gt | Git status |
| Space cm | Commits    |

---

# C++

| Comando  | Acción                  |
| -------- | ----------------------- |
| %        | Saltar entre (), {}, [] |
| gd       | Ir a definición         |
| gr       | Ver referencias         |
| K        | Documentación           |
| Space fm | Formatear               |

---

# MACROS

| Comando | Acción                     |
| ------- | -------------------------- |
| qa      | Grabar macro en registro a |
| q       | Detener grabación          |
| @a      | Ejecutar macro             |
| @@      | Repetir última macro       |

---

# LOS 15 COMANDOS MÁS IMPORTANTES

```text
Esc
i
o
w
b
0
$
gg
G
yy
dd
p
ciw
/
n
```

# LOS 15 MÁS IMPORTANTES DE NVCHAD

```text
Space ff
Space fw
Space fb
Space e
gd
gr
K
Space fm
Tab
Shift+Tab
Space x
Ctrl+h
Ctrl+j
Ctrl+k
Ctrl+l
```
