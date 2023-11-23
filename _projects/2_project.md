---
layout: page
title: Good Driver Incentive Program
description: a .NET MVC web application
img: assets/img/3.jpg
importance: 2
category: school
giscus_comments: false
---

This project was completed as part of my senior software design class at Clemson University. The aim of the class 
is to allow students to gain experience working with a development team to develop a full stack web application over 
the course of a semester. We implemented the Agile Scrum process, with our professor acting as the client, to continually 
develop this application.

We used a wide range of tools and technologies including Azure (to host our repository), Amazon Web Services (to host our application), 
and Entity Framework Core (to serve as an O/RM). While teams were able to pick the framework and technologies to build the app, we chose to 
develop a C# .NET MVC Application. The main reason we chose .NET over other popular frameworks (NodeJS, Django, etc.) was .NET's Entity Framework Core. 
This O/RM allowed us to create the entire MySQL database without writing any SQL. Another major reason for choosing .NET was for Identity, an API
that supports UI login functionality and manages users, passwords, profile data, roles, and email confirmations.

The backstory we were given stated that our "company" (in this case, our class) has been given the contract to build a web application 
that can be used to incentivize the improvement of the on-road performance of commercial truck drivers. The main feature of this app 
is to allow sponsors to award points to drivers for behaviors they want to encourage and take away points for bad behaviors, similar to 
rewards programs you see at retail businesses. Drivers can then use their points in the sponsor's catalog of products.

<h4>Project Requirements</h4>
Each type of user in our project (driver, sponsors, and admins) must do the following:
<ul>
    <li>Sign up for an account</li>
    <li>Login to their account</li>
    <li>Review / update their user profile and password</li>
</ul>

<h6>Drivers</h6>
Driver users must be able to do the following:
<ul>
    <li>Browse products in their sponsor's company catalog</li>
    <li>"Purchse" products from the catalog</li>
    <li>Review their point status</li>
    <li>Cancel/update purchases</li>
    <li>Apply to different sponsor companies</li>
</ul>

<h6>Sponsors</h6>
<ul>
    <li>Review/update relevant sponsor information</li>
    <li>Review status of participating drivers</li>
    <li>Approve/reject driver applications</li>
    <li></li>
</ul>



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
