import pygame
import sys

# Pygame boshlash
pygame.init()

# Ekran sozlamalari
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("O'zbek Avtomobillari O'yini")

# Ranglar
WHITE = (255, 255, 255)

# Avtomobil tasvirlari
car_images = [
    pygame.image.load("damas.png"),      # 1-mashina
    pygame.image.load("lacetti.png"),    # 2-mashina
    pygame.image.load("jiguli.png"),     # 3-mashina
    pygame.image.load("cobalt.png")      # 4-mashina
]

# Tasvirlar o'lchamini moslashtirish
car_images = [pygame.transform.scale(img, (150, 90)) for img in car_images]

# Avtomobil parametrlari
current_car_index = 0
car_x, car_y = WIDTH // 2 - 75, HEIGHT // 2 - 45

# O'yin tsikli
running = True
while running:
    screen.fill(WHITE)  # Fonni tozalash

    # Hozirgi avtomobilni chizish
    screen.blit(car_images[current_car_index], (car_x, car_y))

    # Hodisalarni tekshirish
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

        # Klaviatura boshqaruvi
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_RIGHT:  # Mashinani almashtirish
                current_car_index = (current_car_index + 1) % len(car_images)
            elif event.key == pygame.K_LEFT:  # Orqaga o'tish
                current_car_index = (current_car_index - 1) % len(car_images)

    # Ekranni yangilash
    pygame.display.flip()
