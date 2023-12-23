pygame.init(): Initializes the Pygame library.

Color Definitions:

white, yellow, black, red, green, and blue are tuples representing RGB color values.
Display Dimensions:

dis_width is set to 800, representing the width of the game window.
dis_height is set to 600, representing the height of the game window


---------------------------------------------------------------



Creating a Game Window:

pygame.display.set_mode((dis_width, dis_height)) creates a game window with the specified dimensions (dis_width and dis_height).
Setting the Window Caption:

pygame.display.set_caption('Python Snake Swallow Game!') sets the title or caption of the game window to 'Python Snake Swallow Game!'.
Clock Initialization:

clock = pygame.time.Clock() creates a Pygame clock object. This clock is often used to control the speed of the game loop, ensuring consistent frame rates and controlling the overall flow of the game.


 -----------------------------------------------------------------------


 snake_block = 10:

This variable sets the size of the snake blocks in the game. It seems that the snake in the game will consist of blocks, and each block will have a size of 10 pixels.
snake_speed = 15:

This variable determines the speed of the snake in the game. It appears to be the number of frames per second at which the game updates.
font_style = pygame.font.SysFont("bahnschrift", 25):

This line sets the font style and size for rendering text in the game. The chosen font is "bahnschrift," and the font size is 25.
score_font = pygame.font.SysFont("comicsansms", 35):

Similarly, this line sets another font style and size specifically for rendering the game score. The chosen font is "comicsansms," and the font size is 35.
def Your_score(score)::

This line defines a function named Your_score that takes a parameter score. The purpose of this function is to display the player's score in the game.




----------------------------------------------------------------------------


value = score_font.render("Your Score: " + str(score), True, yellow):

This line creates a text surface (value) using the score_font previously defined. The text rendered is "Your Score: " followed by the actual score converted to a string (str(score)).
The True argument indicates that anti-aliasing should be used for smoother text rendering.
The yellow color is used for the text.
dis.blit(value, [0, 0]):

This line blits or draws the rendered text (value) onto the game display (dis) at the specified coordinates [0, 0]. These coordinates determine where the top-left corner of the text will be positioned on the game screen.


---------------------------------------------------


for x in snake_list::

This loop iterates over each element (x) in the snake_list. Each element is expected to be a pair of coordinates representing the position of a snake segment.
pygame.draw.rect(dis, red, [x[0], x[1], snake_block, snake_block]):

Within the loop, this line draws a rectangle representing a snake segment on the game display (dis).
The rectangle is drawn with the Pygame draw.rect method, using the red color.
The rectangle's position and size are determined by the list [x[0], x[1], snake_block, snake_block]. x[0] and x[1] represent the x and y coordinates of the snake segment, and snake_block is used as the width and height of the rectangle.


-----------------------------------------------------------


mesg = font_style.render(msg, True, color):

This line creates a text surface (mesg) using the specified font_style. The text content is given by the msg parameter.
The True argument indicates the use of anti-aliasing for smoother text rendering.
The color parameter determines the color of the text.
dis.blit(mesg, [dis_width / 6, dis_height / 3]):

This line blits or draws the rendered text (mesg) onto the game display (dis) at a specific position.
The position is determined by the list [dis_width / 6, dis_height / 3], which sets the x and y coordinates for the top-left corner of the text. These coordinates are calculated based on fractions of the game window dimensions.




-----------------------------------------------------


Background Music:

The game includes background music. The mixer.music.load('BGM.wav') line loads a background music file named 'BGM.wav,' and mixer.music.play() starts playing the background music.
Game State Flags:

Two boolean variables are used to manage the game state:
game_over: Indicates whether the game is over.
game_close: Indicates whether the game is in a closed state.
Initial Snake Position and Movement:

x1 and y1: Initialize the coordinates of the snake head at the center of the game window (dis_width / 2, dis_height / 2).
x1_change and y1_change: Variables to store the change in coordinates for the snake's movement. They are initially set to 0, indicating that the snake is stationary.
Snake Properties:

snake_List: An empty list that will be used to store the coordinates of the snake segments.
Length_of_snake: Initialized to 1, representing the initial length of the snake.
Food Position:

foodx and foody: Initialize the position of the food within the game window. The random.randrange function is used to generate random positions, and the positions are rounded to multiples of 10 to align with the snake block size.



--------------------------------------------------------



Outer Game Loop:

while not game_over:: This is the main game loop. It continues running as long as the game is not over.
Inner Game Over Loop:

while game_close == True:: This loop is entered when the game is in a closed (game over) state.
Display Setup:

dis.fill(black): Fills the game display with a black color.
Display Messages:

message("You Lost! Press C-Play Again or Q-Quit", red): Displays a message on the game screen indicating that the player has lost and providing instructions to either play again or quit. The text is colored red.
Display Score:

Your_score(Length_of_snake - 1): Calls the Your_score function to display the player's score on the game screen. The score is calculated as the length of the snake minus 1.
Update Display:

pygame.display.update(): Updates the game display to show the messages and score.
Event Handling:

for event in pygame.event.get():: Iterates through the events in the Pygame event queue.
Inside the loop, it checks for key presses:
If the 'Q' key is pressed (if event.key == pygame.K_q:), it sets game_over to True, indicating that the game should end.
If the 'C' key is pressed (if event.key == pygame.K_c:), it calls the gameLoop() function to restart the game.



-----------------------------------------------------





----------------------------------------------------------------------------------


Event Loop:

for event in pygame.event.get():: Iterates through the events in the Pygame event queue.
QUIT Event:

if event.type == pygame.QUIT:: Checks if the event type is a QUIT event, indicating that the user closed the game window.
If the window is closed (pygame.QUIT), it sets game_over to True, signaling that the game should end.
KEYDOWN Events:

if event.type == pygame.KEYDOWN:: Checks if the event type is a KEYDOWN event, indicating that a key was pressed.
Key Press Handling:

Inside the KEYDOWN event block, the code checks which key was pressed using event.key.

If the left arrow key (pygame.K_LEFT) is pressed, it sets x1_change to a negative value, indicating that the snake should move left. It also sets y1_change to 0 to prevent diagonal movement.

If the right arrow key (pygame.K_RIGHT) is pressed, it sets x1_change to a positive value, indicating that the snake should move right. It also sets y1_change to 0.

If the up arrow key (pygame.K_UP) is pressed, it sets y1_change to a negative value, indicating that the snake should move up. It also sets x1_change to 0.

If the down arrow key (pygame.K_DOWN) is pressed, it sets y1_change to a positive value, indicating that the snake should move down. It also sets x1_change to 0.



---------------------------------------------------------------------------------------------------



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
