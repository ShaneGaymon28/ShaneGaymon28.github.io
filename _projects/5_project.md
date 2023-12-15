---
layout: page
title: Algorithm Visualizer
description: an algorithm visualizer project using Java and Java Swing
img: assets/img/proj5/algoViz.png
importance: 3
category: fun
github: https://github.com/ShaneGaymon28/Algorithm-Visualizer-using-Java-Swing
nav: true
toc:
    sidebar: left
---


<a href="https://github.com/ShaneGaymon28/Algorithm-Visualizer-using-Java-Swing">Link to this Github repository</a>

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

This project is an algorithm visualizer using Java Swing. I used the Model-View-Controller pattern to organize my code and make my GUI components reusable, preventing me from having to write a GUI for each algorithm.

<h4><strong><u>Algorithms</u></strong></h4>
The app supports both path finding and sorting algorithms. 

<h6><strong>Path Finding Algorithms</strong></h6>
The path finding algorithms are visualized by finding the shortest path through a maze from a selected starting position. When the path finding algorithm is running, squares that have been checked by the algorithm will turn green. Once the shortest path from start (red square) to the destination (blue square), the shortest path will be shown on the screen in yellow.

The list of supported path finding algorithms:
<ul>
    <li>Dijkstra's Algorithm</li>
    <li>A*</li>
    <li>Lee's Algorithm</li>
</ul>

Read more about these algorithms here: <a href="https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm">Dijkstra's Algorithm</a>, <a href="https://en.wikipedia.org/wiki/A*_search_algorithm">A*</a>, <a href="https://en.wikipedia.org/wiki/Lee_algorithm">Lee's Algorithm</a>

<h6><strong>Sorting Algorithms</strong></h6>
The sorting algorithms are visualized by sorting vertical rectanges by height from shortest to tallest. In the visualization, the yellow rectangles represent the values which are being currently compared by the algorithm and all others are blue. When running, the rectanges will be continuously compared and swapped until in order from least to greatest.

The list of supported sorting algorithms:
<ul>
    <li>Bubble Sort</li>
    <li>Quick Sort</li>
    <li>Selection Sort</li>
    <li>Merge Sort</li>
    <li>Insertion Sort</li>
    <li>Heap Sort</li>
</ul>

Read more about these algorithms here: <a href="https://en.wikipedia.org/wiki/Bubble_sort">Bubble Sort</a>, <a href="https://en.wikipedia.org/wiki/Quicksort">Quick Sort</a>, <a href="https://en.wikipedia.org/wiki/Selection_sort">Selection Sort</a>, <a href="https://en.wikipedia.org/wiki/Merge_sort">Merge Sort</a>, <a href="https://en.wikipedia.org/wiki/Insertion_sort">Insertion Sort</a>, <a href="https://en.wikipedia.org/wiki/Heapsort">Heap Sort</a>

<h4><strong><u>How to Run</u></strong></h4>
Once you have successfully downloaded the source code, open a terminal and navigate to the src directory.

To compile the code, copy and run the following command:  

`javac visualizer/SortAlgorithms/*.java visualizer/PathAlgorithms/*.java visualizer/*.java`

To run the code:
`java visualizer/Algo`

If you use an IDE like JetBrains Rider or Eclipse, there may be different steps to take.

After running the app, a screen will appear with some text and buttons for either path finding algorithms or sorting algorithms. When you make your selection by clicking the button, the visualization window will open. 

To begin the visualizer:
<ol>
    <li>Select the algorithm from the algorithm dropdown</li>
    <li>Change any options from the option menu (see Features section below)</li>
    <li>Click the start button to begin path finding</li>    
</ol>

<strong>NOTE:</strong> when using path finding algorithms, you need to choose the starting position and end/destination position. To do this, select the button for the corresponding position below the options menu then choose a square. The starting square will turn red when selected, and the destination square will turn blue when selected.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj5/pathScreen.png" title="Path Finding Screen" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig. 1 - Path Finding Screen
</div>


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj5/sortScreen.png" title="Sorting Screen" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig. 2 - Sorting Screen
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj5/finishedSort.png" title="Completed Sorting" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig. 3 - Completed Sorting Algorithm
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj5/finishedPath.png" title="Completed Path Finding" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig. 4 - Completed Path Finding Algorithm
</div>


<h4><strong><u>Features</u></strong></h4>
Options menu:
<ul>
    <li>Start - begins the visualization</li>
    <li>Reset - generates a new, random configuration</li>
    <li>Clear (path finding) - clears every obstacle from the board</li>
    <li>Algorithm dropdown - allows you to select the algorithm to visualize</li>
    <li>Size - number of elements to sort (sorting) or size of the board (path finding)</li>
    <li>Delay (ms) - time between iterations of the algorithm</li>
    <li>Density (path finding) - density of obstacles on board (higher values = more dense, lower values = less dense)</li>
</ul>

For sorting, the name of the current algorithm and number of swaps are displayed above the elements to be sorted.

<strong>NOTE:</strong> after selecting a new algorithm from the dropdown, you must reset the board by clicking the reset button for the changes to take affect.
