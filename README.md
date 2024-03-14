import pygame
import sys

# Inicializar pygame
pygame.init()

# Definir colores
BLANCO = (255, 255, 255)
NEGRO = (0, 0, 0)

# Definir dimensiones de la pantalla
ANCHO = 800
ALTO = 600

# Crear la pantalla
pantalla = pygame.display.set_mode((ANCHO, ALTO))
pygame.display.set_caption("Movimiento del personaje")

# Cargar la imagen del personaje
personaje_img = pygame.image.load("personaje.png")
personaje_rect = personaje_img.get_rect()
personaje_rect.center = (ANCHO // 2, ALTO // 2)

# Definir ángulo inicial de la mano
angulo = 0

# Bucle principal del juego
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # Limpiar la pantalla
    pantalla.fill(BLANCO)

    # Dibujar el personaje
    pantalla.blit(personaje_img, personaje_rect)

    # Girar la mano del personaje 90 grados
    angulo += 90
    if angulo >= 360:
        angulo = 0

    # Rotar la imagen de la mano
    mano_rotada = pygame.transform.rotate(personaje_img, angulo)

    # Obtener el rectángulo de la mano rotada y centrarlo en el personaje
    mano_rect = mano_rotada.get_rect(center=personaje_rect.center)

    # Dibujar la mano rotada en la pantalla
    pantalla.blit(mano_rotada, mano_rect)

    # Actualizar la pantalla
    pygame.display.flip()
