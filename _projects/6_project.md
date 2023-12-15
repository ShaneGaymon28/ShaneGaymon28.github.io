---
layout: page
title: Conway's Game of Life Simulator
description: a Conway's game of life simulator using Java and Java Swing
img: assets/img/proj6/conwaygol.png
importance: 4
category: fun
github: https://github.com/ShaneGaymon28/Conways-GameOfLife-Simulator-using-Java-Swing
nav: true
toc:
    sidebar: left
---

<a href="https://github.com/ShaneGaymon28/Conways-GameOfLife-Simulator-using-Java-Swing">Link to this Github repository</a>

<div class="row justify-content-center">
    <h4><strong><u>Technologies</u></strong></h4>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>Java</strong>
        </div>
        {% include figure.html path="assets/img/logos/javaLogo2.png" title="Java" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


This project is a Conway's Game of Life simulator using Java Swing. Conway's Game of Life is a cellular automaton represented by an "infinite" (in our case max board size is 100 x 100) 2D grid of squares, called a cells. Each cell has one of two states, alive or dead. The state is determined by the cell's 8 neighbors (horizontally, vertically, or diagonally adjacent). See the RULES section for rules determining the state for the next generation of cells.


<h4><strong><u>Rules</u></strong></h4>
While it's named "Conway's Game of Life", it is a zero player game. This means that its initial state determines how it evolves. Once you start the "game", there is no further input required. 

Rules for determining state for next generation:
<ol>
    <li>Any live cell with fewer than two live neighbors dies, as if by <strong>underpopulation</strong></li>
    <li>Any live cell with two or three live neighbors <strong>lives</strong> on to the next generation</li>
    <li>Any live cell with more than three live neighbors dies, as if by <strong>overpopulation</strong></li>
    <li>Any dead cell with exactly three live neighbors becomes a live cell, as if by <strong>reproduction</strong></li>
</ol>

The initial state is randomly generated. The first generation is created by applying the above rules to every cell in the intial state and is then updated to the GUI. Each subsequent generation is created by applying the rules to the previous generation.

There is no "finished" state, and once the game begins it will continually run until you stop it.

You can read more about Conway's Game of Life <a href="https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life">here</a>

<h4><strong><u>How to Run</u></strong></h4>
Once you have successfully downloaded the source code, open a terminal and navigate to the src directory.

To compile the program, copy and run the following command:

`javac game/gameOfLife/*.java`

To run:
`java game/gameOfLife/ConwaysGameOfLifeGUI`

If you use an IDE like JetBrains Rider or Eclipse, there may be different steps to take.

Once you run the app, a welcome screen will appear with some options (see Features section) and instructions. Once you select the board size and click the start simulation button, the simulation screen will appear with the generated initial state. Simply press the start button to begin the simulation. 


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj6/welcome.png" title="Welcome Window" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig. 1 - Welcome Window
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj6/simulationScreen.png" title="Simulation Window" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig. 2 - Simulation Window
</div>


<h4><strong><u>Features</u></strong></h4>
<ul>
    <li>Rules - button that opens a window with the four state generation rules.</li>
    <li>SG - button that opens a window with information about the author (me!)</li>
    <li>Board Size - dropdown for changing the size of the simulation board</li>
    <li>Start Simulation - button that opens the simulation window</li>
</ul>

<strong>NOTE:</strong> I recommend changing the board size to at a minimum 25. You can't really see the different repeating patterns with the smaller boards, but I wanted to leave the option there. 
