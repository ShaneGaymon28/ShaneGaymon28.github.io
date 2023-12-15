---
layout: page
title: Good Driver Incentive Program
description: a .NET MVC web application
img: assets/img/proj2/driveTime2.png
importance: 2
category: school
giscus_comments: false
github: https://github.com/ShaneGaymon28/Good-Driver-Incentive-Program
nav: true
toc:
    sidebar: left
---

<a href="https://github.com/ShaneGaymon28/Good-Driver-Incentive-Program">Link to this repository</a>

<div class="row justify-content-center">
    <h4><strong><u>Tech Stack</u></strong></h4>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>ASP.NET MVC</strong>
        </div>
        {% include figure.html path="assets/img/logos/dotnet.png" title=".NET" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>MySQL</strong>
        </div>
        {% include figure.html path="assets/img/logos/mysql1.png" title="MySQL" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>C#</strong>
        </div>
        {% include figure.html path="assets/img/logos/csharp.png" title="C#" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>Entity Framework Core</strong>
        </div>
        {% include figure.html path="assets/img/logos/efcore.png" title="EF Core" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>AWS Elastic Beanstalk</strong>
        </div>
        {% include figure.html path="assets/img/logos/beanstalk.png" title="AWS Elastic Beanstalk" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


<h4><strong><u>Introduction</u></strong></h4>
This project was completed as part of my senior software design class at Clemson University. The aim of the class 
is to allow students to gain experience working with a development team to develop a full stack web application over 
the course of a semester. We implemented the Agile Scrum process, with our professor acting as the client, to continually 
develop this application.

We used a wide range of tools and technologies including Azure Dev Ops (to host our repository), Git (to communicate with the repo), Amazon Web Services (to host our application), 
and Entity Framework Core (to serve as an O/RM). While teams were able to pick the framework and technologies to build the app, we chose to 
develop a C# ASP.NET Core MVC Application. The main reason we chose .NET over other popular frameworks (NodeJS, Django, etc.) was .NET's Entity Framework Core. 
This O/RM allowed us to create the entire MySQL database without writing any SQL. Another major reason for choosing .NET was for Identity, an API
that supports UI login functionality and manages users, passwords, profile data, roles, and email confirmations.

<h4><strong><u>Backstory</u></strong></h4>
The backstory we were given stated that our "company" (in this case, our class) has been given the contract to build a web application 
that can be used to incentivize the improvement of the on-road performance of commercial truck drivers. The main feature of this app 
is to allow sponsors to award points to drivers for behaviors they want to encourage and take away points for bad behaviors, similar to 
rewards programs you see at retail businesses. Drivers can then use their points in the sponsor's catalog of products.

<h4><strong><u>Project Requirements</u></strong></h4>
Each type of user in our project (drivers, sponsors, and admins) must do the following:
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
The application must be secure. At a minimum, the application must:
<ul>
    <li>Provide and enforce a password complexity system</li>
    <li>Encrypt the user's password at rest</li>
    <li>Encrypt any additional private information you add to the system</li>
    <li>Protect against SQL injection attacks</li>
    <li>Provide a secure password reset system for driver, sponsor, and admin users</li>
</ul>


<h4><strong><u>How to Run</u></strong></h4>
NOTE: having both <a href="https://dev.mysql.com/downloads/mysql/">MySQL</a> and <a href="https://dotnet.microsoft.com/en-us/apps/aspnet">ASP.NET Core</a> downloaded are prerequisites to be able to run the program. You are encouraged to download <a href="https://dev.mysql.com/downloads/workbench/">MySQL Workbench</a> as well, but it is not required.

The first step to getting this application is to clone the <a href="https://github.com/ShaneGaymon28/Good-Driver-Incentive-Program">github repository</a> to your local machine and open the terminal application. Once this is complete, navigate to the Team22.Web directory, then once again navigate into the directory called Team22.Web with the project's source code. (You know you're in the right place if when you type 'ls' to list directory contents, you will see a similar output to Fig. 1 below)

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj2/listOutput.png" title="LS output" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <strong>Fig. 1 - Output of 'ls' command within the source code directory</strong>
</div>


Once you are in the correct directory, you need to add the configuration info for the MySQL database. To do this type the following command:

    ---
    dotnet user-secrets set "Team22ConnectionString" "Server={host IP address};Port=3306;Database={database name};User Id={user name};Password={password}" 
    ---

where: 
<ul>
    <li>Host IP Address is the IP address where your MySQL server is being hosted</li>
    <li>Port is the port for the MySQL protocol (NOTE: the default port is 3306 and really shouldn't be changed)</li>
    <li>Database name is the name of the database to use </li>
    <li>User name is the name of the user to connect to MySQL with (default is root)</li>
    <li>Password is your MySQL password you set when downloading MySQL</li>
</ul>

The reason for this is that we are using .NET's Secret Manager (as opposed to using a json file) to store our database settings. To learn more about .NET's Secret Manager <a href="https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-6.0&tabs=linux">click here</a>

You can verify that the settings were updated by typing:

    ---
    dotnet user-secrets list
    ---

The output should reflect the values you set above.

To run the project in Microsoft Visual Studio, simply open the project solution and press the run button.

To run the project using .NET's CLI (Command Line Interface), navigate to the directory where you updated the user secrets setting and type `dotnet run`. If you're running this locally, open a web browser and type `localhost:7252` in the URL bar to be taken to the project's home page. Otherwise, open a web browser and navigate to where you're hosting it.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj2/landingPage.png" title="Project's Landing Page" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <strong>Fig. 2 - DriveTime home/landing page</strong>
</div>

<h4><strong><u>Using the Application</u></strong></h4>
Once you have everything setup and running, you can begin actually using the app. First, you need to create an account by clicking the green `Create Account` button on the home page. Then you'll be prompted to login using the credentials you created the account with. I recommend creating an account for all 3 user types (driver, sponsor, and admin) to use the different features. 






