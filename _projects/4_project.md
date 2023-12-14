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
        <h4><strong><u>Technologies</u></strong></h4>
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

<h6><strong>GUI.py</strong></h6>
This file controls the pygame GUI and handles much of the game logic. It displays and updates the pygame window, sets up the sudoku board from the Grid class,
and handles user input.

NOTE: To play the game, this is the file you want to run.


<h6><strong>Grid.py</strong></h6>
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

<h6><strong>Cube.py</strong></h6>
This file contains a class that represents a single square or space on the sudoku board. It handles highlighting a selected square, setting a value for the square, and displaying
the border around squares when the backtracking algorithm is called to solve the puzzle. The square is highlighted green when the algorithm thinks that value will work and red if the algorithm is backtracking. Squares that have been given to you through hints are highlighted blue.

<h6><strong>GridGenerator.py</strong></h6>
This file contains a class that handles generating a new, unique, and solvable puzzle. It handles the generation of new game boards by first generating a valid, completely filled 
board then removing random values off that board. The difficulty modifier in the GUI controls how many random values will be removed from the board (easy difficulty removes less and a harder difficulty removes more values). While removing values from the board, the algorithm does a check after each to ensure that the board is still solvable with the given starting values. The resulting board is a 9x9 2D array with 0 representing empty squares and non-zero values representing given squares.

This function generates new boards:

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


<h4><strong><u>How to Run the Game</u></strong></h4>
Once you have downloaded the files and have them in the same directory, you can run the game by typing the following command: 
{% raw %}
```python
python3 GUI.py
```
{% endraw %}


<h4><strong><u>How to Play</u></strong></h4>
If you are unfamiliar with the rules of sudoku, here is a link to <a href="https://masteringsudoku.com/sudoku-rules-beginners/">sudoku instructions</a>. Upon running the program for the first time, the game automatically generates a board (at normal difficulty) and starts the game. Clicking on an empty square will highlight it RED. Typing a number value in a selected square will place/sketch a TEMPORARY value for that square. Pressing RETURN on sketched square will attempt to add the temporary value in the square (NOTE: if the entered number is not part of the solution, it will not be added and you will gain a strike). Pressing the DELETE key on a sketched square will remove the value. If you select a square and press the SPACE BAR, the computer will begin attempting to solve the puzzle.

<h6><strong>Controls Summary</strong></h6>
<div class="container mb-5">
<table class="table">
    <thead>
        <tr>
            <th>Input</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Mouse Click (on empty square)</td>
            <td>Selects the square and turns border color red</td>
        </tr>
        <tr>
            <td>Mouse Click (on an option button)</td>
            <td>Toggle selected option</td>
        </tr>
        <tr>
            <td>Any Number (1-9)</td>
            <td>Sets the temporary/sketched value to the key pressed for a selected square</td>
        </tr>
        <tr>
            <td>Return / Enter</td>
            <td>Attempts to add the temporary value at that square to the solution</td>
        </tr>
        <tr>
            <td>Delete Key</td>
            <td>Removes a temporary/sketched value from the selected square</td>
        </tr>
        <tr>
            <td>Space Bar</td>
            <td>Tells the computer to begin solving the puzzle</td>
        </tr>
    </tbody>
</table>
</div>

<h6><strong>Menu Options</strong></h6>
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



