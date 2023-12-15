---
layout: page
title: Pizzeria Management System
description: a SQL database and Java application
img: assets/img/proj1/pizzeria.jpg
importance: 1
category: school
github: https://github.com/ShaneGaymon28/Pizzeria-Management-System
nav: true
toc:
    sidebar: left
---

<a href="https://github.com/ShaneGaymon28/Pizzeria-Management-System">Link to this Github repository</a>

<div class="row justify-content-center">
    <h4><strong><u>Tech Stack</u></strong></h4>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>Java</strong>
        </div>
        {% include figure.html path="assets/img/logos/javaLogo2.png" title="Java" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>MySQL</strong>
        </div>
        {% include figure.html path="assets/img/logos/mysql1.png" title="MySQL" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>AWS RDS</strong>
        </div>
        {% include figure.html path="assets/img/logos/rds.png" title="AWS RDS" class="img-fluid rounded z-depth-1" %}
    </div>
</div>



This project was done as part of my Database Management Systems class at Clemson University. This project included 3 parts:
<ul>
    <li><strong>Part 1 - Database Design</strong></li>
    <li><strong>Part 2 - Database Implementation</strong></li>
    <li><strong>Part 3 - Adding the Java application</strong></li>
</ul>

<h4><strong><u>Project Requirements</u></strong></h4>

The database system I created will be used to track the day-to-day operations of a small pizzeria.

The pizzeria's requirements for this system include the following entities:
<h6><strong>Pizzas</strong></h6>
<ul>
    <li>Crust Type (thin, original, pan, gluten free)</li>
    <li>Size (personal, medium, large, x-large)</li>
    <li>Price (selling price) and Cost (cost to produce) to the company, determined by size and toppings</li>
    <li>Can be in 2 states: completed by the kitched or still being processed</li>
    <li>Toppings on the pizza</li>
</ul>

<h6><strong>Toppings</strong></h6>
<ul>
    <li>Name of topping</li>
    <li>Price to customer and price to business</li>
    <li>Amount used for each pizza size</li>
    <li>Minimum inventory level</li>
    <li>Current Inventory level</li>
    <li>Can request extra</li>
</ul>

<h6><strong>Orders</strong></h6>
<ul>
    <li>Can be for dine in, pickup, or delivery</li>
    <li>Total cost to business</li>
    <li>Total price for customer</li>
    <li>Timestamp for when the order was placed</li>
    <li>Customer who placed order</li>
</ul>

<h6><strong>Customers</strong></h6>
<ul>
    <li>Dine in customers must provide table number</li>
    <li>Pickup customers must provide a name and phone number</li>
    <li>Delivery customers must provide a name, phone number, and address</li>
    <li>Customer information is saved for their next order</li>
    <li>A customer may only have one address</li>
</ul>

<h6><strong>Discounts</strong></h6>
<ul>
    <li>Can be applied to individual pizzas or an entire order</li>
    <li>Name of discount</li>
    <li>Either a dollar amount off or a percentage off</li>
</ul>



<h4><strong><u>Part 1 - Database Design</u></strong></h4>

In part 1 of this project we were asked to create an enhanced ER diagram (using an online tool like Lucid Chart) to base the database 
we created in part 2 on.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj1/db_design1.jpg" title="ER Diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <strong>Fig. 1 - The ER diagram created in part 1</strong>
</div>

The above screenshot (Fig. 1) shows the relationships, cardinality, and connectivity between different entities in the database. <strong>BASE_PIZZA</strong> is meant to hold the crust type, size, price, and cost of all different combinations of those fields. <strong>PIZZA_TOPPINGS, DISCOUNT_PIZZA, and DISCOUNT_ORDER</strong> are bridge entities that combine the primary and foreign keys of the entities.

The different relationship classifications between entities are as follows:
<h6><strong>One to many (1:M)</strong></h6>
This represents two entities where a single occurrence of the first participant can refer to many occurrences of the second.

<h6><strong>Many to many (M:M)</strong></h6>
This represents two entities where many occurrences of the first participant can refer to many different references to the second.

<h6><strong>One to one (1:1)</strong></h6>
This represents two entities where a single occurrence of the first participant can only refer to one occurrence of the second. 

<div class="container m-5">
    <table class="table">
        <thead>
            <tr>
                <th>Entity 1</th>
                <th>Connectivity</th>
                <th>Entity 2</th>
                <th>Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>PIZZA</td>
                <td>1:M</td>
                <td>TOPPINGS</td>
                <td>A pizza can have multiple toppings</td>
            </tr>
            <tr>
                <td>ORDER</td>
                <td>1:M</td>
                <td>PIZZA</td>
                <td>An order can have multiple pizzas</td>
            </tr>
            <tr>
                <td>PIZZA</td>
                <td>1:1</td>
                <td>ORDER</td>
                <td>Each pizza belongs to one order</td>
            </tr>
            <tr>
                <td>ORDER</td>
                <td>1:1</td>
                <td>ORDER_TYPE</td>
                <td>Each order must have one order type</td>
            </tr>
            <tr>
                <td>CUSTOMER</td>
                <td>1:M</td>
                <td>ORDER</td>
                <td>A customer can have multiple orders</td>
            </tr>
            <tr>
                <td>PIZZA</td>
                <td>1:M</td>
                <td>DISCOUNTS</td>
                <td>A pizza can have multiple discounts applied to it</td>
            </tr>
            <tr>
                <td>ORDER</td>
                <td>1:M</td>
                <td>DISCOUNTS</td>
                <td>An order can have multiple discounts applied to it</td>
            </tr>
            <tr>
                <td>PIZZA</td>
                <td>1:1</td>
                <td>BASE_PIZZA</td>
                <td>Each pizza must have a base pizza</td>
            </tr>
        </tbody>
    </table>  
</div>
  
  
<h4><strong><u>Part 2 - Database Implementation</u></strong></h4>
In part 2 of this project, we were asked to create 5 SQL scripts for the database. 

<strong>CreateTables.sql</strong> has the create statements necessary to build the tables for the database. 

<strong>PopulateData.sql</strong> has the insert statements necessary to populate the database with provided data.   

<strong>ViewTables.sql</strong> contains a "SELECT * FROM ..." for each table to display the table data.  

<strong>DropTables.sql</strong> drops each table in the database.  

<strong>CreateViews.sql</strong> creates the following views in the database: 
<ul>
    <li><strong>ToppingPopularity</strong> - rank all toppings from most popular to least popular</li>
    <li><strong>ProfitByPizza</strong> - a summary of the profit by pizza size and crust type from most profitable to least profitable</li>
    <li><strong>ProfitByOrderType</strong> - a summary of the profit for each of the 3 types of orders</li>
</ul>


<h4><strong><u>Part 3 - Adding the Java Application</u></strong></h4>
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

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj1/menu.png" title="Application Menu" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <strong>Fig. 2 - The menu displayed to users upon running the app</strong>
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj1/viewOrders.png" title="ER Diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <strong>Fig. 3 - Output to user upon selecting option 4 (View Orders)</strong>
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj1/viewInventory.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj1/viewTopByPop.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <strong>Fig. 4 - The image on the left shows the output to user upon selecting option 6 (View Inventory), the right image shows the output upon selecting option 8, then option 1 (View Reports --> Topping Popularity)</strong>
</div>

To connect the Java application to the SQL database, we were required to use the JDBC API. It did require some configuration in the IDE I was using (IntelliJ), but overall was very easy to setup and run.

In the src folder of the project files, you can find the project package which includes the files required to run the program. Each database entity that was created has a corresponding class with different get/set functions to manipulate the data. The main method is in the Menu.java file and is the entry point into the application. This file controls the selection menu and handles a user's request for data. DBConnector.java holds the MySQL server credentials for the database and is called when the application wants to make a connection to the database. DBNinja.java is a utility class to help add and retrieve information from the database. This file is the one that talks to the database.

Here's an example of the Customer class in the Java code:

{% raw %}
```java
package cpsc4620;

public class Customer 
{
	private int CustID;
	private String FName;
	private String LName;
	private String Phone;
	private String Address;
	
	
	public Customer(int custID, String fName, String lName, String phone) {
		CustID = custID;
		FName = fName;
		LName = lName;
		Phone = phone;
	}

	public int getCustID() {
		return CustID;
	}

	public String getFName() {
		return FName;
	}

	public String getLName() {
		return LName;
	}

	public String getPhone() {
		return Phone;
	}

	public void setCustID(int custID) {
		CustID = custID;
	}

	public void setFName(String fName) {
		FName = fName;
	}

	public void setLName(String lName) {
		LName = lName;
	}

	public void setPhone(String phone) {
		Phone = phone;
	}
	
	@Override
	public String toString() {
		return "CustID=" + CustID + " | Name= " + FName +  " " + LName + ", Phone= " + Phone;
	}
	
}
```
{% endraw %}

In addition to creating the Java application, we were asked to host the database in the cloud using Amazon Web Service's Relational Database Service (RDS).


<h4><strong><u>How to Run (IntelliJ)</u></strong></h4>
There are a few steps to setup the JDBC in IntelliJ, I used <a href="https://www.youtube.com/watch?v=e8g9eNnFpHQ&t=293s">this youtube tutorial</a> to do so.

Once this is done, you need to connect to the database in MySQL Workbench and run the following scripts IN ORDER:
<ol>
    <li>CreateTables.sql</li>
    <li>PopulateData.sql</li>
    <li>CreateViews.sql</li>
    <li>ViewTables.sql (optional, but will run a 'select * from' on each table)</li>
</ol>

NOTE: you can find these files within the SQL folder in the Github repository. 

After running the necessary SQL scripts, add a Run/Debug configuration (beside the green 'run' arrow on top right of screen) to run the Menu class, click apply then you can close that screen.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj1/runConfig.png" title="Run Configuration Settings" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <strong>Fig. 5 - Run/Debug configuration settings</strong>
</div>

Once this is done, you can manipulate the database as you'd like!

NOTE: Per the project requirements, we did not add any error checks for the input format. This means that when you are interacting with the menu, you should follow the format given by the output prompt.