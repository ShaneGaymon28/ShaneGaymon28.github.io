---
layout: page
title: Pizzeria Management System
description: a SQL database and Java application
img: assets/img/12.jpg
importance: 1
category: school
related_publications: einstein1956investigations, einstein1950meaning
---

<a href="https://github.com/ShaneGaymon28/Pizzeria-Management-System">Link to this Github Repository</a>


This project was done as part of my Database Management Systems class at Clemson University. This project included 3 parts:
<ul>
    <li>Part 1 - Database Design</li>
    <li>Part 2 - Database Implementation</li>
    <li>Part 3 - Adding the Java application</li>
</ul>




<h4>Project Requirements</h4>

The database system I created will be used to track the day-to-day operations of a small pizzeria.

The pizzeria's requirements for this system include:
<h6>Pizzas</h6>
<ul>
    <li>Crust Type (thin, original, pan, gluten free)</li>
    <li>Size (personal, medium, large, x-large)</li>
    <li>Price (selling price) and Cost (cost to produce) to the company, determined by size and toppings</li>
    <li>Can be in 2 states: completed by the kitched or still being processed</li>
    <li>Toppings on the pizza</li>
</ul>

<h6>Toppings</h6>
<ul>
    <li>Name of topping</li>
    <li>Price to customer and price to business</li>
    <li>Amount used for each pizza size</li>
    <li>Minimum inventory level</li>
    <li>Current Inventory level</li>
    <li>Can request extra</li>
</ul>

<h6>Orders</h6>
<ul>
    <li>Can be for dine in, pickup, or delivery</li>
    <li>Total cost to business</li>
    <li>Total price for customer</li>
    <li>Timestamp for when the order was placed</li>
    <li>Customer who placed order</li>
</ul>

<h6>Customers</h6>
<ul>
    <li>Dine in customers must provide table number</li>
    <li>Pickup customers must provide a name and phone number</li>
    <li>Delivery customers must provide a name, phone number, and address</li>
    <li>Customer information is saved for their next order</li>
    <li>A customer may only have one address</li>
</ul>

<h6>Discounts</h6>
<ul>
    <li>Can be applied to individual pizzas or an entire order</li>
    <li>Name of discount</li>
    <li>Either a dollar amount off or a percentage off</li>
</ul>



<h4>Part 1 - Database Design</h4>

In part 1 of this project we were asked to create an enhanced ER diagram (using an online tool like Lucid Chart) to base the database 
we created in part 2 on.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/db_design1.jpg" title="ER Diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig. 1 - The ER diagram created in part 1
</div>

The above screenshot (Fig. 1) shows the relationships, cardinality, and connectivity between different entities in the database.

The entities have the following relationships:
<ul>
    <li>A pizza can have multiple toppings</li>
    <li>The same topping can be on multiple pizzas</li>
    <li>Pizzas belong to orders</li>
    <li>An order can have multiple pizzas</li>
    <li>Each order must have an order type</li>
    <li>A customer can have many orders</li>
    <li>A pizza or order can have multiple discounts applied to it</li>
    <li>A discount can be applied to many pizzas or orders</li>
    <li>Each pizza needs a base pizza</li>
</ul>


There are a few entities in Fig. 1 that I did not mention in the project requirements section. BASE_PIZZA is meant to hold 
the crust type, size, price, and cost of all different combinations of those fields. PIZZA_TOPPINGS, DISCOUNT_PIZZA, and DISCOUNT_ORDER
are bridge entities that combine the primary and foreign keys of the entities.


<h4>Part 2 - Database Implementation</h4>
In part 2 of this project, we were asked to create 5 SQL scripts for the database. 

CreateTables.sql has the create statements necessary to build the tables for the database. 

PopulateData.sql has the insert statements necessary to populate the database with provided data.   

ViewTables.sql contains a "SELECT * FROM ..." for each table to display the table data.  

DropTables.sql drops each table in the database.  

CreateViews.sql creates the following views in the database: 
<ul>
    <li>ToppingPopularity - rank all toppings from most popular to least popular</li>
    <li>ProfitByPizza - a summary of the profit by pizza size and crust type from most profitable to least profitable</li>
    <li>ProfitByOrderType - a summary of the profit for each of the 3 types of orders</li>
</ul>


<h6>Part 3 - Adding the Java Application</h6>
In part 3 of this project, we were asked to create a Java application that interacts with the database through a command line interface.

The following features were required:
<ol>
    <li>Add a new order to the database</li>
    <li>View Customers</li>
    <li>Enter a new customer</li>
    <li>View Orders</li>
    <li>Mark an order as complete</li>
    <li>View inventory levels</li>
    <li>Add inventory</li>
    <li>View Reports</li>
</ol>

Upon running the application, the user is shown a menu with the required features as options.

To connect the Java application to the SQL database, we were required to use the JDBC API.


To give your project a background in the portfolio page, just add the img tag to the front matter like so:

    ---
    layout: page
    title: project
    description: a project with a background image
    img: /assets/img/12.jpg
    ---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images.
Say you wanted to write a little bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, *bled* for your project, and then... you reveal its glory in the next row of images.


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>


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
