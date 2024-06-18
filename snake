import pygame
import time
import random


pygame.init()


white = (255, 255, 255)
pink = (255, 50, 200)
red = (255, 0, 0)


width = 800
height = 600
block_size = 20
snake_speed = 15


game_display = pygame.display.set_mode((width, height))
pygame.display.set_caption('Snake Game')


def our_snake(block_size, snake_list):
    for x in snake_list:
        pygame.draw.rect(game_display, white, [x[0], x[1], block_size, block_size])


def game_loop():
    game_over = False
    game_close = False

    
    lead_x = width / 2
    lead_y = height / 2

    
    lead_x_change = 0
    lead_y_change = 0

    
    snake_list = []
    length_of_snake = 1

    
    foodx = round(random.randrange(0, width - block_size) / 10.0) * 10.0
    foody = round(random.randrange(0, height - block_size) / 10.0) * 10.0

    
    while not game_over:

        
        while game_close:
            game_display.fill(pink)
            pygame.display.update()

            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        game_over = True
                        game_close = False
                    if event.key == pygame.K_c:
                        game_loop()

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    lead_x_change = -block_size
                    lead_y_change = 0
                elif event.key == pygame.K_RIGHT:
                    lead_x_change = block_size
                    lead_y_change = 0
                elif event.key == pygame.K_UP:
                    lead_y_change = -block_size
                    lead_x_change = 0
                elif event.key == pygame.K_DOWN:
                    lead_y_change = block_size
                    lead_x_change = 0

        
        lead_x += lead_x_change
        lead_y += lead_y_change

        
        if lead_x >= width or lead_x < 0 or lead_y >= height or lead_y < 0:
            game_close = True

        
        if lead_x == foodx and lead_y == foody:
            foodx = round(random.randrange(0, width - block_size) / 10.0) * 10.0
            foody = round(random.randrange(0, height - block_size) / 10.0) * 10.0
            length_of_snake += 1

        
        game_display.fill(pink)
        pygame.draw.rect(game_display, red, [foodx, foody, block_size, block_size])
        snake_head = []
        snake_head.append(lead_x)
        snake_head.append(lead_y)
        snake_list.append(snake_head)
        if len(snake_list) > length_of_snake:
            del snake_list[0]

        for segment in snake_list[:-1]:
            if segment == snake_head:
                game_close = True

        our_snake(block_size, snake_list)

        pygame.display.update()

        
        pygame.time.Clock().tick(snake_speed)

    pygame.quit()
    quit()


game_loop()
