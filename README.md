Collision Check with Game Window Boundaries:

if x1 >= dis_width or x1 < 0 or y1 >= dis_height or y1 < 0:: Checks if the snake's head (x1, y1) has collided with the boundaries of the game window. If so:
It loads a crash sound effect ('crash.wav') using Pygame's mixer.music.load.
It plays the crash sound effect using mixer.music.play().
Sets game_close to True, indicating that the game is in a closed (game over) state.
Updating Snake's Position:

x1 += x1_change and y1 += y1_change: Updates the position of the snake's head based on the changes calculated from user input.
Filling the Display with Background Color:

dis.fill(black): Fills the game display with a black color, effectively clearing the previous frame.
Drawing the Food:

pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block]): Draws the food on the game display. The food is represented by a green rectangle at the position specified by foodx and foody.
Updating Snake's Body:

snake_Head = []: Creates an empty list to represent the head of the snake.
snake_Head.append(x1) and snake_Head.append(y1): Appends the current position of the snake's head to the snake_Head list.
snake_List.append(snake_Head): Appends the snake_Head list to the snake_List, representing the entire snake's body.
Managing Snake's Length:

if len(snake_List) > Length_of_snake:: Checks if the length of the snake has exceeded the desired length (Length_of_snake).
del snake_List[0]: If so, removes the first element from snake_List, effectively shortening the snake to maintain the desired length.
