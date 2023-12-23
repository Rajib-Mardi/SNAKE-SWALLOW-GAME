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
---------------------------------------------------------------------------------------


Checking for Self-Collision:

for x in snake_List[:-1]:: Iterates through the elements of snake_List excluding the last element.
if x == snake_Head:: Checks if any element of the snake's body is equal to the current position of the snake's head (snake_Head).
If a match is found, it sets game_close to True, indicating that the game is in a closed (game over) state due to self-collision.
Drawing the Snake:

our_snake(snake_block, snake_List): Calls the our_snake function to draw the snake on the game display. The function takes the size of each snake block (snake_block) and the list of coordinates representing the snake's body (snake_List).
Displaying the Score:

Your_score(Length_of_snake - 1): Calls the Your_score function to display the player's score on the game display. The score is calculated as the length of the snake minus 1.
Updating the Display:

pygame.display.update(): Updates the game display with the drawn snake and score.
Food Consumption Check:

if x1 == foodx and y1 == foody:: Checks if the snake's head has reached the position of the food.
If true:
Loads a crunch sound effect ('crunch.wav') using mixer.music.load.
Plays the crunch sound effect using mixer.music.play().
Generates new random positions for the food within the game window, rounded to multiples of 10.
Increases the length of the snake (Length_of_snake) by 1.
Controlling Game Speed:

clock.tick(snake_speed): Limits the frame rate of the game loop to the specified snake_speed. This helps control the speed of the snake.
Quitting Pygame:

Once the game loop exits, it reaches pygame.quit() and quit(), which close the Pygame module and exit the program.
Initial Game Launch:

gameLoop(): Calls the gameLoop function to initiate the game loop and start the game.
