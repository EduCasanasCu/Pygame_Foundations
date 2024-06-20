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
