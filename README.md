# Pygame_Foundations
Bases de pygame para desarrollo de videojuegos.
## Creación de ventana principal y estructura del juego.
```python
# Importamos la libreria para juegos y la libreria para cerrar la ventana del juego.
import pygame, sys

# iniciar la libreria pygame
pygame.init()

# tamanio de la ventaba (ancho, alto)
size = (800,500)

# creamos la ventana donde aparecera el juego
screen = pygame.display.set_mode(size)

# todos los juegos estan dentro de un bucle
while True:
    # aqui rastreamos todos los eventos que pasan en la pantalla
    for event in pygame.event.get():
        # si el tipo de evento/accion es "QUIT"
        if event.type == pygame.QUIT:
            # cierra la ventana del juego
            sys.exit()
```
## Dibujar figuras geométricas(linea, rectangulo, circulo) y colores en RGB
```python
# Importamos la libreria para juegos y la libreria para cerrar la ventana del juego.
import pygame, sys

# iniciar la libreria pygame
pygame.init()

# definimos colores
BLACK = (0,0,0)
WHITE = (255,255,255)
RED = (255,0,0)
GREEN = (0,255,0)
BLUE = (0,0,255)


# tamanio de la ventaba (ancho, alto)
size = (800,500)

# creamos la ventana donde aparecera el juego
screen = pygame.display.set_mode(size)

# todos los juegos estan dentro de un bucle
while True:
    # aqui rastreamos todos los eventos que pasan en la pantalla
    for event in pygame.event.get():
        # si el tipo de evento/accion es "QUIT"
        if event.type == pygame.QUIT:
            # cierra la ventana del juego
            sys.exit()

    # pintamos la pantalla de color blanco
    screen.fill(WHITE)
    
    # ----zona para dibujar

    # dibujar una linea (surface, color, (coordenada inicio x,y), (coordenada fin x,y), grosorLinea)
    pygame.draw.line(screen, GREEN,(0,100),(500,100),5)

    # dibujar un rectangulo (surface, color, (coordenada donde empieza(x,y),(tamanio x, tamanio y))
    pygame.draw.rect(screen, BLACK, (200,200,50,50))

    # dibujar un circulo (surface,color,center,radio)
    pygame.draw.circle(screen,BLUE,(300,300),20)

    # ----zona para dibujar

    # actualizamos los cambios
    pygame.display.flip()
```
## Dibujo de figuras con un bucle FOR
```python
# Importamos la libreria para juegos y la libreria para cerrar la ventana del juego.
import pygame, sys

# iniciar la libreria pygame
pygame.init()

# definimos colores
BLACK = (0,0,0)
WHITE = (255,255,255)
RED = (255,0,0)
GREEN = (0,255,0)
BLUE = (0,0,255)


# tamanio de la ventaba (ancho, alto)
size = (800,500)

# creamos la ventana donde aparecera el juego
screen = pygame.display.set_mode(size)

# todos los juegos estan dentro de un bucle
while True:
    # aqui rastreamos todos los eventos que pasan en la pantalla
    for event in pygame.event.get():
        # si el tipo de evento/accion es "QUIT"
        if event.type == pygame.QUIT:
            # cierra la ventana del juego
            sys.exit()

    # pintamos la pantalla de color blanco
    screen.fill(WHITE)
    
    # ----zona para dibujar

    # bucle de repeticion (inica, termina, salto)
    for x in range(100,700,100):
        # dibujamos varios rectangulos
        pygame.draw.rect(screen,BLACK,(x,100,50,50))

        # dibujamos varias lineas
        pygame.draw.line(screen,GREEN,(x,50),(x,80),8)

    # ----zona para dibujar

    # actualizamos los cambios
    pygame.display.flip()
```
## Animaciones(rebote en los bordes)/Control FPS/Estructura de un juego{Logica,pintar pantalla, zona de dibujos}
```python
# Importamos la libreria para juegos y la libreria para cerrar la ventana del juego.
import pygame, sys

# iniciar la libreria pygame
pygame.init()

# definimos colores
BLACK = (0,0,0)
WHITE = (255,255,255)
RED = (255,0,0)
GREEN = (0,255,0)
BLUE = (0,0,255)


# tamanio de la ventaba (ancho, alto)
size = (800,500)

# creamos la ventana donde aparecera el juego
screen = pygame.display.set_mode(size)

# Velocidad de frames por segundo
clock = pygame.time.Clock()

# coordenadas posicion inicial del cuadrado
cordenada_x = 400
cordenada_y = 250

# velocidad del cuadrado
speed_x = 3
speed_y = 3

# todos los juegos estan dentro de un bucle
while True:
    # aqui rastreamos todos los eventos que pasan en la pantalla
    for event in pygame.event.get():
        # si el tipo de evento/accion es "QUIT"
        if event.type == pygame.QUIT:
            # cierra la ventana del juego
            sys.exit()
    
    #-------LOGICA JUEGO--------------

    # efecto de rebote en los bordes en x
    if (cordenada_x > 720 or cordenada_x < 0):
        # si es > 720 se hacen valores negativos por el -1 y se mueve a la izquierda, 
        # si es < 0 los valores negativos *-1 ahora se hacen positivos y se mueve a la derecha
        speed_x *= -1 

    # efecto de rebote en los bordes en y
    if (cordenada_y >420 or cordenada_y < 0):
        speed_y *= -1

    # para incrementar la posicion en x, dando la ilusion de movimiento horizontal
    cordenada_x += speed_x

    # para incrementar la posicion en y, dando la ilusion de movimiento vertical
    cordenada_y += speed_y

    #-------LOGICA JUEGO--------------

    # pintamos la pantalla de color blanco
    screen.fill(WHITE)
    
    # ----zona para dibujar

    pygame.draw.rect(screen, RED, (cordenada_x, cordenada_y,80,80))

    # ----zona para dibujar

    # actualizamos los cambios
    pygame.display.flip()

    # controlamos los FPS
    clock.tick(60)
```
