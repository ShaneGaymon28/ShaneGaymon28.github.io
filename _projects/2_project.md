---
layout: page
title: Good Driver Incentive Program
description: a .NET MVC web application
img: assets/img/3.jpg
importance: 2
category: school
giscus_comments: false
github: https://github.com/ShaneGaymon28/Good-Driver-Incentive-Program
nav: true
toc:
    sidebar: left
---

<a href="https://github.com/ShaneGaymon28/Good-Driver-Incentive-Program">Link to this repository</a>


<h4><strong><u>Introduction</u></strong></h4>
This project was completed as part of my senior software design class at Clemson University. The aim of the class 
is to allow students to gain experience working with a development team to develop a full stack web application over 
the course of a semester. We implemented the Agile Scrum process, with our professor acting as the client, to continually 
develop this application.

We used a wide range of tools and technologies including Azure Dev Ops (to host our repository), Git (to communicate with the repo), Amazon Web Services (to host our application), 
and Entity Framework Core (to serve as an O/RM). While teams were able to pick the framework and technologies to build the app, we chose to 
develop a C# .NET MVC Application. The main reason we chose .NET over other popular frameworks (NodeJS, Django, etc.) was .NET's Entity Framework Core. 
This O/RM allowed us to create the entire MySQL database without writing any SQL. Another major reason for choosing .NET was for Identity, an API
that supports UI login functionality and manages users, passwords, profile data, roles, and email confirmations.

<h4><strong><u>Backstory</u></strong></h4>
The backstory we were given stated that our "company" (in this case, our class) has been given the contract to build a web application 
that can be used to incentivize the improvement of the on-road performance of commercial truck drivers. The main feature of this app 
is to allow sponsors to award points to drivers for behaviors they want to encourage and take away points for bad behaviors, similar to 
rewards programs you see at retail businesses. Drivers can then use their points in the sponsor's catalog of products.

<h4><strong><u>Project Requirements</u></strong></h4>
Each type of user in our project (driver, sponsors, and admins) must do the following:
<ul>
    <li>Sign up for an account</li>
    <li>Login to their account</li>
    <li>Review / update their user profile and password</li>
</ul>

<h6><strong>Drivers</strong></h6>
Driver users must be able to do the following:
<ul>
    <li>Browse products in their sponsor's company catalog</li>
    <li>"Purchse" products from the catalog</li>
    <li>Review their point status</li>
    <li>Cancel/update purchases</li>
    <li>Apply to different sponsor companies</li>
</ul>

<h6><strong>Sponsors</strong></h6>
Sponsor users must be able to do the following:
<ul>
    <li>Review/update relevant sponsor information</li>
    <li>Review status of participating drivers</li>
    <li>Approve/reject driver applications</li>
    <li>Add/review/update driver information</li>
    <li>Add/deduct points from a driver (and provide a reason)</li>
    <li>Review/update the product catalog</li>
    <li>Purchase items on behalf of a driver</li>
    <li>Create new sponsor users, there can be multiple logins per sponsor</li>
    <li>Generate sponsor reports</li>
</ul>

<h6><strong>Admins</strong></h6>
Admin users must be able to do the following:
<ul>
    <li>Review/update any sponsor user, driver user, or admin user</li>
    <li>Add new admins, drivers, and sponsor users</li>
    <li>Generate admin reports</li>
</ul>

<h6><strong>Sponsor Product Catalog</strong></h6>
The sponsor product catalog must:
<ul>
    <li>Be unique to the sponsor (i.e. different sponsors have different catalogs)</li>
    <li>Use a public, online API to produce the catalog of incentive products</li>
    <li>Uses the API to obtain the current product price and availability of a product upon "purchase"</li>
    <li>Be updated in real time via the web API</li>
</ul>

<h6><strong>Sponsor Reports</strong></h6>
The system must include the following reports to be available to sponsors:
<ul>
    <li>Driver Point Tracking</li>
    <ul>
        <li>Select all drivers or an individual driver</li>
        <li>Select by date range</li>
        <li>Display driver name, total points, point changes, date of point change, name of sponsor, reason for point change</li>
    </ul>
    <li>Audit Log report</li>
    <ul>
        <li>Select by date range</li>
        <li>Select by audit log category (below)</li>
    </ul>
</ul>


<h6><strong>Admin Reports</strong></h6>
The system must include the following reports to be available to admins:
<ul>
    <li>Sales by Sponsor</li>
    <ul>
        <li>Select by All sponsors or individual sponsor</li>
        <li>Select by date range</li>
        <li>Detailed or summary views</li>
    </ul>
    <li>Sales by driver</li>
    <ul>
        <li>Select by all sponsors or individual sponsor</li>
        <li>Select by date range</li>
        <li>Detailed or summary views</li>
    </ul>
    <li>Invoice, one per sponsor</li>
    <ul>
        <li>Select by all sponsors or individual sponsor</li>
        <li>Select by date range</li>
        <li>Summarizes purchases by driver over date range (fee generated by driver)</li>
        <li>Total fee due per sponsor</li>
    </ul>
    <li>Audit log reports</li>
    <ul>
        <li>Select by date range</li>
        <li>Select by audit log category (below)</li>
    </ul>
</ul>

<h6><strong>Audit Logging</strong></h6>
The system needs to maintain information on significant state changes:
<ul>
    <li>Driver applications: date, sponsor, driver, status (accept/reject), reason</li>
    <li>Point changes: date, sponsor, driver, # of points, reason</li>
    <li>Password changes: date, user, type of change</li>
    <li>Login attempts: date, username, success/failure</li>
</ul>

<h6><strong>Application Security</strong></h6>
The application must be secure. At a minimum, your application must:
<ul>
    <li>Provide and enforce a password complexity system</li>
    <li>Encrypt the user's password at rest</li>
    <li>Encrypt any additional private information you add to the system</li>
    <li>Protect against SQL injection attacks</li>
    <li>Provide a secure password reset system for driver, sponsor, and admin users</li>
</ul>


<h4><strong><u>Part 1 - User Stories, Backlogs, and Setup</u></strong></h4>
As I said previously, we used Agile Project Management via Azure Dev Ops and Git to manage our project. We were involded in "sprints" 
that were typically 1 week in length and changed from week to week. For the sake of brevity, I will not go through each sprint but instead
break the project up into major sections.

This part of the project included setup of the various technologies, brainstorming user stories, and populating the planning out the prjoect 
in Azure Dev Ops.

<h6><strong>User Stories</strong></h6>
We started by brainstorming different user stories based on the project requirements listed above. More specifically, we broke it down to the different
database tables we may need based on the features required. The user stories we came up with followed the form: "As a [type of user], I can [feature], so that [reason]". ...

<h6><strong>Backlogs</strong></h6>
After deciding on the relevant user stories and features required, our next step was to add all this information to Azure Dev Ops and begin planning the project. This
included populating the product backlog, estimating story points for user stories, and populating the sprint backlog for each sprint. Our main focus here was to accurately estimate
story points for the user stories so the group could reasonably split work up for each sprint.

<h6><strong>Setup</strong></h6>
Once we identified specifically what information we will need, we began to decide on what web framework and database system to use. As stated in an above section, we chose
Microsoft's .NET framework (using the MVC pattern) with a MySQL database. 

Upon deciding on a web framework, we were able to begin developing the project. This process included configuring the repository, creating and pushing the initial project files 
to the repo, and ensuring that every member of the group could access the project files.


<h4><strong><u>Part 2 - Development</u></strong></h4>


<h4><strong><u>Part 3 - Issues and Class Demo</u></strong></h4>


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
