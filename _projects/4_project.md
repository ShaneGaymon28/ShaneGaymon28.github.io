---
layout: page
title: Sudoku Solver
description: a sudoku solving game using Python and Pygame
img: assets/img/sudoku_img.png
importance: 3
category: fun
github: https://github.com/ShaneGaymon28/sudoku_solver
nav: true
toc:
    sidebar: left
---

<a href="https://github.com/ShaneGaymon28/sudoku_solver">Link to this Github repository</a>

<div class="container">
    <div class="row justify-content-center">
        <h4><strong><u>Tech Stack</u></strong></h4>
    </div>
    <div class="row justify-content-center">
        <div class="col-sm mt-3 mt-md-0">
            <div><strong>Python</strong></div>
            <div class="mt-3">
                {% include figure.html path="assets/img/logos/pythonLogo.png" title="Python" class="img-fluid rounded z-depth-1" %}
            </div>
        </div>
    </div>
</div>

This project is a sudoku solver game that was implemented using Python and Pygame.

The game supports the following features:
<ul>
    <li>Difficulty selection (easy, medium, or hard)</li>
    <li>Generating a new puzzle</li>
    <li>Show the solution to the current board</li>
    <li>Ask the computer to solve the board using a backtracking algorithm</li>
    <li>Ask the computer for a hint (NOTE: you are only given 5 hints per board)</li>
    <li>View the time spent on the current puzzle</li>
    <li>View the number of incorrect tries for the current puzzle </li>
</ul>


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sudoku_solver_screenshot.png" title="Game Screenshot" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A screenshot of the sudoku solver
</div>

<h4><strong><u>Files</u></strong></h4>
<ul>
    <li>GUI.py</li>
    <li>Cube.py</li>
    <li>Grid.py</li>
    <li>GridGenerator.py</li>
</ul>

<h6>GUI.py</h6>
This file controls the pygame GUI and handles much of the game logic. It displays and updates the pygame window, sets up the sudoku board from the Grid class,
and handles user input.

NOTE: To play the game, this is the file you want to run.


<h6>Grid.py</h6>
This file contains a class that handles the ENTIRE sudoku board operations. It handles placing a value on the board, giving a hint to the user, sketching/pencil in a value, and 
provides the backtracking algorithm to solve the puzzle. Here is the recursive backtracking algorithm:
{% raw %}
```python
def solve_gui(self):
    self.update_model()
    find = self.find_empty(self.model)
    if not find:
        return True
    else:
        row, col = find

    for i in range(1, 10):
        if self.valid(self.model, i, (row, col)):
            self.model[row][col] = i
            self.cubes[row][col].set(i)
            self.cubes[row][col].draw_change(self.win, True)
            self.update_model()
            pygame.display.update()

            if self.solve_gui():
                return True

            self.model[row][col] = 0
            self.cubes[row][col].set(0)
            self.update_model()
            self.cubes[row][col].draw_change(self.win, False)
            pygame.display.update()

    return False
```
{% endraw %}

To explain this code snippet a little, the algorithm starts by updating the "model" which is the board we will send to the solving method to attempt to solve. Next, it tries to find an empty square on the model and sets the row and column values if it finds one. If not, the board has no more empty squares and is solved. The next step is to loop through possible values that can be placed in that square and determine if the proposed value can be placed in the square at the found position. If the value allows a valid solution, we place it on the board and recursively call the function again.

<h6>Cube.py</h6>
This file contains a class that represents a single square or space on the sudoku board. It handles highlighting a selected square, setting a value for the square, and displaying
the border around squares when the backtracking algorithm is called to solve the puzzle. The square is highlighted green when the algorithm thinks that value will work and red if teh algorithm is backtracking. Squares that have been given to you through hints are highlighted blue.

<h6>GridGenerator.py</h6>
This file contains a class that handles generating a new, unique, and solvable puzzle. It handles the generation of new game boards by first generating a valid, completely filled 
board then removing random values off that board. The difficulty modifier in the GUI controls how many random values will be removed from the board (easy difficulty removes less and a harder difficulty removes more values). While removing values from the board, the algorithm does a check after each to ensure that the board is still solvable with the given starting values. The resulting board is a 9x9 2D array with 0 representing empty squares and non-zero values representing given squares.


<h4><strong><u>How to Run the Game</u></strong></h4>
Once you have downloaded the files and have them in the same directory, you can run the game by typing the following command: 
{% raw %}
```python
python3 GUI.py
```
{% endraw %}


<h4><strong><u>How to Play</u></strong></h4>
If you are unfamiliar with the rules of sudoku, here is a link to <a href="https://masteringsudoku.com/sudoku-rules-beginners/">sudoku instructions</a>. Upon running the program for the first time, the game automatically generates a board (at normal difficulty) and starts the game. Clicking on an empty square will highlight it RED. Typing a number value in a selected square will place/sketch a TEMPORARY value for that square. Pressing RETURN on sketched square will attempt to add the temporary value in the square (NOTE: if the entered number is not part of the solution, it will not be added and you will gain a strike). Pressing the DELETE key on a sketched square will remove the value. If you select a square and press the SPACE BAR, the computer will begin attempting to solve the puzzle.



<h4><strong><u>Menu Options</u></strong></h4>
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        <ul>
            <li class="mt-3">Solve - solves the current puzzle using a backtracking algorithm</li>
            <li class="mt-3">New Puzzle - generates a new, unique puzzle with the selected difficulty</li>
            <li class="mt-3">Show/Hide Solution - shows or hides the COMPLETE solution of the board to the user (NOTE: you must hide the solution to continue entering values into the puzzle)</li>
            <li class="mt-3">Hint - randomly reveal one CORRECT square in the puzzle</li>
            <li class="mt-3">Difficulty - sets the difficulty (easy, medium, or hard) for the puzzle (NOTE: the currently selected difficulty is highlighted for you)</li>
        </ul> 
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/sudoku_options.png" title="Sudoku Options" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


<h4><strong><u>Methodology</u></strong></h4>
<h6>GUI.py</h6>
When you first run the program, a main function is called and begins to run. This function creates the pygame window (with options), initializes the Grid class, and starts a while loop to capture user input events. Here's a list of the different events I'm concerned with receiving from the user:
<ul>
    <li>QUIT - user quits the game / closes the window</li>
    <li>KEYDOWN - user enters a value (1-9 key), deletes a value (DEL key), asks the computer to solve (SPACE key), or places a value in the board (RETURN key)</li>
    <li>MOUSEBUTTONDOWN - user selected a square or one of the options</li>
    <li>MOUSEMOTION - user hovers over an option</li>
</ul>

When a user triggers a KEYDOWN event and the event key is a number from 1-9, we set a key value so that when the window is updated it knows to sketch the value into the square. If a user triggers a KEYDOWN event and the event key is the DEL key, we clear the sketched value at the selected square. If user triggers a KEYDOWN event and the event key is the RETURN key, we check that there is a value sketched and attempt to place it in the board. In the event that the value is wrong, you will gain a strike. After placing the value (or not), the board is checked for completion and is shown the game over screen if there are no more empty squares on the board.

When a user triggers a MOUSEBUTTONDOWN event, we first get the position of the mouse click. Then we check the click position against each option button's position to see if an option was selcted and call the corresponding action for that option. If an option button was not clicked, we know the user selected a square on the board and highlight the corresponding square.

If a user triggers a MOUSEMOTION event, we first loop through all of the option buttons and highlight the corresponding button.

After checking for the different events listed above, we call the redraw_window function and display the update to the window.

<h6>Grid.py</h6>
This class takes a few arguments in it's constructor: rows, cols, the GridGenerator class, height (of window), width, the window object, and difficulty level (as an int, 1 = easy, 3 = medium, 5 = hard). The board and solution properties are set through the GridGenerator class that was passed into the constructor. The methods are as follows:
<ul>
    <li>draw(self) - used to draw the grid lines and square values on the board</li>
    <li>update_model(self) - updates the model that is sent to solver method with values placed in the board</li>
    <li>generate_new_board(self, grid_gen, diff) - generate a new board with the grid_gen class and difficulty of diff</li>
    <li>place(self, val) - places val into the selected square if it's empty</li>
    <li>hint_user(self) - finds a random empty square on the board and display correct value to user</li>
    <li>sketch(self, val) - places a temporary value, val, on the board</li>
    <li>select(self, row, col) - sets the square at row, col to be selected, resets all other squares</li>
    <li>clear(self) - removes the sketched temporary value in the selected square</li>
    <li>click(self, pos) - determines the square a user clicked on based on pos</li>
    <li>is_finished(self) - determine if the board is complete</li>
    <li>solve(self) - determines if the board is solvable after entering a new value</li>
    <li>solve_gui(slef) - solves the board using backtracking algorithm and updates it to the window</li>
    <li>show_solution(self, solution_win) - draws the solution we got from the GridGenerator object to the solution_win window</li>
    <li>find_empty(self, bo) - finds an empty space on the board bo</li>
    <li>get_difficulty(self) - returns the current difficulty setting</li>
    <li>valid(self, bo, num, pos) - determines if placing num in square at pos in board bo, follows the rules of sudoku</li>
</ul>

<h6>GridGenerator.py</h6>
This class takes the number of rows, columns, and difficulty level as arguments to its constructor. The methods are as follows:
<ul>
    <li>solve(self, board) - determines if the board is solvable after entering a new value</li>
    <li>fill_board(self) - fills the board with values in positions that will leave the board in a solvable state</li>
    <li>generate_new(self) - generates a new board and returns it</li>
    <li>find_open(self, board) - searches for an open square in board argument</li>
    <li>check_grid(self, board) - checks that the grid is completely filled with values</li>
    <li>print_grid(self) - prints the grid to console</li>
    <li>print_solution(self) - prints the solution to console</li>
    <li>get_solution(self) - returns the solution array to current board</li>
    <li>set_counter(self, value) - sets the counter property to value</li>
    <li>set_solution(self, board) - sets the solution property to board</li>
</ul>

{% raw %}
```python
def generate_new(self):
    self.grid = [
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0]
    ]
    self.fill_board()
    self.set_solution(self.grid)

    attempts = self.difficulty
    while attempts > 0:
        # select random cell that isn't empty
        row = randint(0, 8)
        col = randint(0, 8)
        while self.grid[row][col] == 0:
            row = randint(0, 8)
            col = randint(0, 8)

        backup = self.grid[row][col]
        self.grid[row][col] = 0

        copy = []
        for i in range(0, 9):
            copy.append([])
            for j in range(0, 9):
                copy[i].append(self.grid[i][j])

        self.set_counter(0)
        self.solve(copy)
        if self.counter != 1:
            self.grid[row][col] = backup
            attempts -= 1

    return self.grid
```
{% endraw %}

When generate_new() is called, the grid property is first set to an empty 9x9 2D array then the fill_board() method is called. From there, we continuously select a random non-zero square, remove the value, and determine if removing it will lead to a solvable board. This is done until we have removed enough values to satisfy the difficulty level. 

fill_board() will search for an empty square and place a random number (values 1-9) and determine if placing the value in that square will lead to a solvable board. 

<h6>Cube.py</h6>
This class takes the following as arguments to its constructor: value, row, col, width, and height. Here are the methods:
<ul>
    <li>draw(self, win) - draws the value of this square on the board</li>
    <li>draw_change(self, win, g=TRUE) - draws the change from the backtracking solution</li>
    <li>set_temp(self, val) - sets the temporary value of the square to val</li>
    <li>set(self, val) - sets the value of the square to val</li>
    <li>set_hinted(self, val) - sets the boolean property hinted to TRUE</li>
</ul>

{% raw %}
```python
def draw(self, win):
    fnt = pygame.font.SysFont("comicsans", 30)

    gap = self.width / 9
    x = self.col * gap
    y = self.row * gap

    if self.temp != 0 and self.value == 0:
        text = fnt.render(str(self.temp), 1, (128, 128, 128))
        win.blit(text, (x + 5, y + 5))
    elif not(self.value == 0):
        text = fnt.render(str(self.value), 1, (0, 0, 0))
        win.blit(text, (x + (gap / 2 - text.get_width() / 2), y + (gap / 2 - text.get_height() / 2)))

    if self.hinted:
        pygame.draw.rect(win, (0, 0, 255), (x, y, gap, gap), 3)
    elif self.selected:
        pygame.draw.rect(win, (255, 0, 0), (x, y, gap, gap), 3)

```
{% endraw %}

When the draw() method is called, we start by determining the gap between squares as well as the x,y coordinates where the square will be drawn. It then draws either the temporary sketched value or the actual value on the window. If the square was given through a hint or is currently selected, it's border is highlighted with the corresponding color.


The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}
```html
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
```
{% endraw %}
