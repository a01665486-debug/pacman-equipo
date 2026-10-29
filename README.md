# Pacman - Proyecto colaborativo

## Descripción

Adaptación del videojuego Pacman de Free Python Games, desarrollado
en Python con Turtle Graphics.

El objetivo es mejorar las decisiones de los fantasmas, modificar
la distribución del tablero y aumentar la velocidad de los fantasmas,
utilizando Git y GitHub para registrar las contribuciones del equipo.

## Fuente original

Autor del código base: Grant Jenks.

https://grantjenks.com/docs/freegames/pacman.html

El archivo original se obtuvo con:

```bash
python -m freegames copy pacman
```

El primer commit conserva el código sin modificaciones.

## Integrantes

| Integrante | Matrícula | GitHub | Rol |
|---|---|---|---|
| Diego Lemus Mejía | A01665486 | a01665486-debug | Dueño / Main |
| Yerik Escobar Asprón | Por completar | Por completar | Fork |

Cada integrante utiliza su propia cuenta. Yerik contribuye desde
un fork, sin acceso de colaborador al repositorio original.

## Instalación

Se requiere Python 3 con soporte para Turtle y Tkinter.

Después de descargar el repositorio, entrar a su carpeta y ejecutar:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Cada integrante crea su propio ambiente virtual. La carpeta `.venv/`
no se sube al repositorio.

## Ejecución

Con el ambiente activado:

```bash
python pacman.py
```

Para otra sesión, entrar a la carpeta del proyecto y activar:

```bash
source .venv/bin/activate
```

Para salir del ambiente:

```bash
deactivate
```

## Controles

| Tecla | Acción |
|---|---|
| Flecha arriba | Subir |
| Flecha abajo | Bajar |
| Flecha izquierda | Moverse a la izquierda |
| Flecha derecha | Moverse a la derecha |

Se debe recoger comida y evitar a los fantasmas. La partida
se detiene cuando un fantasma alcanza a Pacman.

Para reiniciar, cerrar la ventana y ejecutar nuevamente el programa.

## Reparto y plan de trabajo

| Responsable | Funcionalidad | Rama |
|---|---|---|
| Diego | Mejorar las decisiones de los fantasmas | feat/fantasmas-inteligentes |
| Yerik | Cambiar el tablero | Rama propia en su fork |
| Yerik | Aumentar la velocidad de los fantasmas | Rama propia en su fork |

Ambos trabajan simultáneamente desde una base común.
Cada funcionalidad se registra en un commit separado, se documenta
y se propone mediante un pull request hacia `main`.

Los cambios se revisan antes de integrarse. Se utiliza un merge
que conserve los commits individuales y sus autores.

## Acuerdos para integrar el código

- La velocidad de los fantasmas se configura mediante `GHOST_SPEED`.
- Diego implementa la función que selecciona sus direcciones.
- Yerik modifica el tablero y configura la velocidad.
- Pacman conserva su desplazamiento original de 5 unidades.
- El tablero debe conservar 400 elementos y sus bordes cerrados.
- Las posiciones iniciales deben estar sobre caminos.
- Después del merge se prueban las tres funcionalidades juntas.

## Estado de las funcionalidades

| Funcionalidad | Estado |
|---|---|
| Fantasmas inteligentes | Implementado |
| Nuevo tablero | Pendiente |
| Fantasmas más rápidos | Pendiente |

## Pruebas

| Prueba | Resultado esperado | Resultado observado |
|---|---|---|
| Inicio | El juego abre sin errores | Pendiente |
| Controles | Pacman responde a las flechas | Pendiente |
| Puntuación | Aumenta al recoger comida | Pendiente |
| Inteligencia | Los fantasmas consideran la posición de Pacman | Pendiente |
| Paredes | Los personajes permanecen en caminos válidos | Pendiente |
| Tablero | Caminos conectados y comida accesible | Pendiente |
| Velocidad | Los fantasmas avanzan más rápido que antes | Pendiente |
| Colisión | La partida se detiene al alcanzar a Pacman | Pendiente |

Los resultados se actualizarán después de realizar cada prueba.

## Problemas encontrados

Pendiente de documentar durante el desarrollo.

Cada problema registrado incluirá el síntoma, la solución aplicada
y la prueba utilizada para comprobar la corrección.

## Evidencias

La entrega incluye el código final, el historial de commits y
las evidencias de pull requests y merges en GitHub.

Para consultar el historial:

```bash
git --no-pager log --graph --oneline --all
```

Para exportar los commits de la versión integrada:

```bash
git log main --date=iso --pretty=fuller > historial_commits.txt
```
## Fork - Yerik

### Modificación del laberinto
Se agregaron 4 caminos nuevos al mapa original de Pacman.

### Velocidad de los fantasmas
Se aumentó la velocidad de los fantasmas de 5 a 10 unidades, manteniendo la velocidad de Pacman y el temporizador original.

### Colores de los fantasmas
Se agregaron 4 colores nuevos: rojo, rosa, cyan y naranja.

### Pruebas
Se verificó el funcionamiento de los nuevos caminos, el movimiento de los fantasmas, las colisiones con las paredes y los controles de Pacman.
## Implementación de Diego: fantasmas inteligentes

Se añadió `choose_direction(point, course)` para revisar las
cuatro direcciones al alinearse el fantasma con una casilla.

Se descartan movimientos bloqueados y se elige el destino más
cercano a la posición actual de Pacman. Entre casillas, el fantasma
mantiene su dirección.

La función utiliza `GHOST_SPEED`, por lo que puede integrarse
con el cambio de velocidad sin fijar el desplazamiento en 5.

La estrategia busca acercarse a Pacman, pero no garantiza
encontrar la ruta más corta alrededor de las paredes.
