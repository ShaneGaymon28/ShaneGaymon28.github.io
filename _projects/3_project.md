---
layout: page
title: Web Application Programming
description: Web application projects
img: assets/img/proj3/webdev.jpg
importance: 3
category: school
github: https://github.com/ShaneGaymon28/Web-Application-Programming
nav: true
toc:
    sidebar: left
---

<a href="https://github.com/ShaneGaymon28/Web-Application-Programming">Link to this Github repository</a>

<div class="row justify-content-center">
    <h4><strong><u>Technologies</u></strong></h4>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>HTML</strong>
        </div>
        {% include figure.html path="assets/img/logos/html.png" title="Java" class="img-fluid rounded" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>CSS</strong>
        </div>
        {% include figure.html path="assets/img/logos/css.png" title="MySQL" class="img-fluid rounded" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>AWS EC2</strong>
        </div>
        {% include figure.html path="assets/img/logos/ec2.png" title="AWS RDS" class="img-fluid rounded" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>JavaScript</strong>
        </div>
        {% include figure.html path="assets/img/logos/jsLogo.png" title="AWS RDS" class="img-fluid rounded" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>NodeJs</strong>
        </div>
        {% include figure.html path="assets/img/logos/node.png" title="AWS RDS" class="img-fluid rounded" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>Nginx</strong>
        </div>
        {% include figure.html path="assets/img/logos/nginxLogo.png" title="AWS RDS" class="img-fluid rounded" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>Apache</strong>
        </div>
        {% include figure.html path="assets/img/logos/apache.png" title="AWS RDS" class="img-fluid rounded" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="caption">
            <strong>React</strong>
        </div>
        {% include figure.html path="assets/img/logos/react.png" title="AWS RDS" class="img-fluid rounded" %}
    </div>
</div>

<h4><strong><u>Introduction</u></strong></h4>
This collection of projects were completed at Clemson University as part of my Web Application Development class. In total there are 6 projects that increase in difficulty with each subsequent project. The aim of the class is to teach students how to build and host web applications and common programming languages used to do so. Each project was hosted on an AWS EC2 instance that was accessible by a public IP address (NOTE: the projects are no longer accessible by public IP address). The EC2 instance used Ubuntu Linux.

<h4><strong><u>Project 1</u></strong></h4>
<h6><strong>Description</strong></h6>
The first project was the basic setup of an AWS EC2 instance. I was asked to create and configure an EC2 instance that can be accessed with a public IP address, install apache (to host HTML files), and create a basic HTML page.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj3/p1.png" title="Project 1" class="img-fluid rounded z-depth-1 mx-auto d-block" %}
    </div>
</div>
<div class="caption">
    <strong>Fig. 1 - Project 1</strong>
</div>

<h4><strong><u>Project 2</u></strong></h4>
<h6><strong>Description</strong></h6>
Project 2 required us to complete a simple Tic Tac Toe game using HTML, JavaScript, and CSS. The project requirements are as follows:
<ul>
    <li>Show a 3x3 grid of buttons with innerHTML representing blank, x, or o</li>
    <li>Show a button that allows the AI to go first</li>
    <li>Show a button to refresh the game</li>
    <li>User plays against computer and player goes first unless otherwise specified</li>
    <li>User is always x</li>
    <li>Detect win conditions</li>
    <li>Detect cat game (no winner, no moves left)</li>
</ul>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj3/p2.png" title="Project 2" class="img-fluid rounded z-depth-1 mx-auto d-block" %}
    </div>
</div>
<div class="caption">
    <strong>Fig. 2 - Project 2 Tic Tac Toe</strong>
</div>

<h4><strong><u>A Note About Projects 3-6</u></strong></h4>
Beginning with project 3, we used nginx and NodeJs to host our projects. It was a bit complicated to setup, here's what we did:

<ol>
    <li>Install nginx and NodeJs on the AWS instance</li>
    <li>Disable apache (from previous projects) and enable nginx</li>
    <li>Modify the nginx config file to send dynamic requests to port 3000</li>
    <li>Create the following directories</li>
    <ul>
        <li>A project directory in the home folder</li>
        <li>A documentRoot folder within the project folder</li>
        <li>A server folder within the project folder</li>
    </ul>
    <li>Create a symlink between the documentRoot folder and /var/www/html/projectNumber</li>
    <li>Run `npm init` in the server folder and install the expressJs package with npm</li>
    <li>Create a service file for NodeJs</li>
    <li>Start the NodeJs service we created in the previous step</li>
</ol>

Projects 3 and 4 use this same folder structure, while project 5 only required us to use NodeJs to create a REST API. Project 6 uses the node server created in project 5 to build a React user interface.


<h4><strong><u>Project 3</u></strong></h4>
<h6><strong>Description</strong></h6>
The third project for this class involved transitioning from apache2 and static files to a combination of nginx and NodeJs. We installed and configured nginx and nodejs, hosted a static file through nginx and configured nginx to send certain requests to nodejs which will return dynamic content.

I was required to:
<ul>
    <li>Install nginx and NodeJs</li>
    <li>Modify the nginx config file to send requests that start with /dynamic/ to the NodeJs server</li>
    <li>Setup a NodeJs project</li>
    <li>Create an Index.html file shown at `http://yourip/project3/`</li>
    <li>The URL `http://yourip/project3/dynamic/` should return "Hello World"</li>
    <li>The URL `http://yourip/project3/dynamic/time` should return the current date and time</li>
    <li>Any other url that starts with `http://yourip/project3/dynamic/` besides what's listed above should return "The path was {path}</li>
</ul>

To do this, I edited the nginx configuration file to pass requests with the path `/project3/dynamic/` to port 3000, where our node server is running. 

This script handles the dynamic requests:
{% raw %}
```javascript
const express = require('express')
const app = express()
const port = 3000


app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.get('/time', (req, res) => {		
	res.send(new Date().toString())
})

app.get('*', (req, res) => {
	res.send(`path was ${req.path}`)
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```
{% endraw %}

<h4><strong><u>Project 4</u></strong></h4>
<h6><strong>Description</strong></h6>
Project 4 involved creating a set of files that allows users to register, authenticate, and view a protected resource. This was done using HTML, JavaScript, NodeJs, nginx, js promises, sessions, and JSON files. I was provided with starter code that had 8 spots where I had to fill in the required code, 4 pertaining to the NodeJs server and 4 in the HTML front-end. Since we need to keep track of different pieces of user info, a redis database was used to store the user data being passed to the server.

The server-side code I was required to complete (all in <strong>server/server.js</strong>):
<ul>
    <li>A function to compute the hash value given a password and a base64 encoded salt using sha256 </li>
    <li>The POST handler for /user/auth</li>
    <li>The GET handler for /user/exists</li>
    <li>The POST handler for /user</li>
</ul>

The front-end code I was required to complete:
<ul>
    <li><strong>documentRoot/login/index.html</strong> - A form that has 2 inputs, username and password</li>
    <li><strong>documentRoot/registration/index.js</strong> - A function to validate a user's information when registering for an account</li>
    <li><strong>documentRoot/registration/index.js</strong> - A function to get the value of the username field and validate that it is not empty, less than 25 characters, and that no users with that name already exist</li>
    <li><strong>documentRoot/registration/index.js</strong> - A function to get the value of the password field and determine how complex it is for the password strength indicator</li>
</ul>

Compute Hash function:

{% raw %}
```javascript
const computeHash = (password, salt)=>{	
	const hash = crypto.createHash('sha256');
	hash.update(password+salt);
	const value = hash.digest('base64');
	//returns an object with salt and hash value
	return value;
}

```
{% endraw %}

POST handler for /user/auth:
{% raw %}
```javascript
app.post('/user/auth', (req, res) => {
	const {userid, password} = req.body;
	if(!userid || userid == ""){
		res.redirect(`${proxy_path}/login/#${encodeURIComponent(errorMessages.NO_USER)}`);
		return;
	}
	else if(!password || password == ""){
		res.redirect(`${proxy_path}/login/#${encodeURIComponent(errorMessages.NO_PASSWORD)}`);
		return;
	}	

	if(userid == "admin"){
		return adminObj;
	}

	const user = getUser(userid);
	if(user == false){
		res.redirect(`${proxy_path}/login/#${encodeURIComponent(errorMessages.USER_NOT_FOUND)}`);	
		return;
	}

	if(computeHash(password, user.salt) != user.passwordHash){
		res.redirect(`${proxy_path}/login/#${encodeURIComponent(errorMessages.PASSWORD_NOT_MATCH)}`);		
		return;
	}
	console.log('auth passed');
	req.session.userid = userid;
	res.redirect(`${proxy_path}/dynamic/user/info`); 
})
```
{% endraw %}


GET handler for /user/exists:

{% raw %}
```javascript
app.get('/user/exists',(req,res)=>{
	userid = req.query.userid;

	if(!userid || userid == ""){
		console.log('userid is bad')
		res.json({"exists":false});
	}
	else if(getUser(userid) == false){
		console.log('user no exist')
		res.json({"exists":false});
	}
	else {
		console.log('user exists')
		res.json({"exists":true});		
	}
})
```
{% endraw %}

POST handler for /user:

{% raw %}
```javascript
app.post('/user', (req, res) => {
	const {userid, password, name} = req.body;
	if(!userid || userid == ""){
		res.redirect(`${proxy_path}/registration/#${encodeURIComponent(errorMessages.NO_USER)}`);
		return;
	}
	else if(userid.length > 25){
		res.redirect(`${proxy_path}/registration/#${encodeURIComponent(errorMessages.USER_TOO_LONG)}`);
		return;
	}
	else if(getUser(userid) != false){
		res.redirect(`${proxy_path}/registration/#${encodeURIComponent(errorMessages.USER_NOT_FOUND)}`);
		return;
	}
	else if(!password || password == ""){
		res.redirect(`${proxy_path}/registration/#${encodeURIComponent(errorMessages.NO_PASSWORD)}`);
		return;
	}
	else if(password.length > 100){
		res.redirect(`${proxy_path}/registration/#${encodeURIComponent(errorMessages.PASSWORD_TOO_LONG)}`);
		return;
	}
	else if(!name || name == ""){
		res.redirect(`${proxy_path}/registration/#${encodeURIComponent(errorMessages.NO_NAME)}`);
		return;
	}
	else if(name.length > 100){
		res.redirect(`${proxy_path}/registration/#${encodeURIComponent(errorMessages.NAME_TOO_LONG)}`);
		return;
	}
	else {
		const salt = (new Date()).valueOf().toString();
		const hash = computeHash(password, salt);
		const user = {userid:userid, name:name, salt:salt, passwordHash:hash};
		saveUser(user);
		res.redirect(`${proxy_path}/login/#${encodeURIComponent(errorMessages.REGISTRATION_SUCCESS)}`);
		return;
	}
})
```
{% endraw %}

Login form:

{% raw %}
```html
<h1>Login</h1>
<section>
	<form action="../dynamic/user/auth" method="post" id="form">
		<div><label>Username:<input type="text", id="username" name="userid"/></label></div>
		<div><label>Password:<input type="password" id="password" name="password"/></label></div>
		<button type="submit">Submit</button>
	</form>

</section>
```
{% endraw %}

Validate function:

{% raw %}
```javascript
const validate = () => {
	const userName = document.getElementById("username").value;
	const name = document.getElementById("name").value;
	const pw = document.getElementById("password").value;
	const confirmPw = document.getElementById("confirm_password").value;
	
	if(userName == ""){
		showError(errorMessages["NO_USER"]);
		return false;
	}
	else if(userName.length > 25){
		showError(errorMessages["USER_TOO_LONG"]);
		return false;
	}
	else if(pw == ""){
		showError(errorMessages["NO_PASSWORD"]);
		return false;
	}
	else if(pw.length > 100){
		showError(errorMessages["PASSWORD_TOO_LONG"]);	
		return false;
	}
	else if(confirmPw != pw){
		showError(errorMessages["PASSWORD_NOT_MATCH"]);
		return false;
	}
	else if(zxcvbn(pw).score < 2){
		showError(errorMessages["PASSWORD_TOO_WEAK"]);
		return false;
	}
	else if(name == ""){
		showError(errorMessages["NO_NAME"]);
		return false;
	}
	else if(name.length > 100){
		showError(errorMessages["NAME_TOO_LONG"]);
		return false;
	}
	else {
		showError(false);
		return true;
	}
};
```
{% endraw %}

Username:

{% raw %}
```javascript
//callback for username change and talks to server to see if username exists
//uses setUsernameStatus to change the icon based on result from server
const onUsernameChange = function(){
	const userName = document.getElementById("username").value;
	axios.get("../dynamic/user/exists?userid=" + userName).then(response => {
		setUsernameStatus(response.data.exists);
	});
}
```
{% endraw %}

Password:

{% raw %}
```javascript
//callback for password change, tests password against zxcvbn libs and
//uses setScore to display strength
const onPasswordChange = function(){
	const pw = document.getElementById("password").value;
	const sc = zxcvbn(pw).score;
	setScore(sc);
}
```
{% endraw %}


<h4><strong><u>Project 5</u></strong></h4>
<h6><strong>Description</strong></h6>
The next project I completed in this class was a RESTful API with endpoints surrounding students and grades. Once again redis was the database of choice due to its speed and ease of use. The API created in this project was used in the next project (project 6) to send data to the React front-end.

The project requirements:
<ul>
    <li>Handle HTTP Status Codes: 200, 400, 401, 404, and 500</li>
    <li>A function to:</li>
    <ul>
        <li>Filter results based on a given value</li>
        <li>Sort results based on a type</li>
        <li>Paginate results</li>
    </ul>
    <li>Endpoints:</li>
    <ul>
        <li><strong>POST /students -</strong> add a student</li>
        <li><strong>DELETE /students/:username -</strong> delete a student</li>
        <li><strong>PUT /students/:id -</strong> modify a student</li>
        <li><strong>GET /students/:id -</strong> get a student</li>
        <li><strong>GET /students -</strong> get all students</li>
        <li><strong>POST /grades -</strong> add a grade</li>
        <li><strong>GET /grades/:id -</strong> get a grade</li>
        <li><strong>PUT /grades/:id -</strong> modify a grade</li>
        <li><strong>DELETE /grades/:id -</strong> delete a grade</li>
        <li><strong>GET /grades -</strong> get all grades</li>
    </ul>
</ul>

Filter/Sort/Paginate function:

{% raw %}
```javascript
//this takes a set of items and filters, sorts and paginates the items.
//it gets it's commands from queryArgs and returns a new set of items
const filterSortPaginate = (type, queryArgs, items) => {
	let keys;
	//create an array of filterable/sortable keys
	if(type == 'student'){
		keys = ['id','name'];
	}else{
		keys = ['id','student_id','type','max','grade'];
	}

	//applied to each item in items
	//returning true keeps item
	const filterer = (item) =>{		
		for(let i = 0; i < keys.length; i++){
			const key = keys[i]
			if(!queryArgs[key]) continue;
			if(!item[key].toLowerCase().includes(queryArgs[key])) return false
		}
		return true;
	};

	//apply above function using Array.filterer
	items = items.filter(filterer);
	console.log('items after filter:',items)

	//always sort, default to sorting on id
	if(!queryArgs._sort){
		queryArgs._sort = 'id';
	}
	//make sure the column can be sorted
	let direction = 1;
	if(!queryArgs._order){
		queryArgs._order = 'asc';
	}
	if(queryArgs._order.toLowerCase() == 'desc'){
		direction = -1;
	}

	//used to sort items
	const sorter = (a,b)=>{
		const toSort = queryArgs._sort;
		if(a[toSort].toLowerCase() === b[toSort].toLowerCase()) return 0
		
		if(a[toSort].toLowerCase() > b[toSort].toLowerCase()) return 1 * direction	

		return -1 * direction;
	};

	//use apply the above comparator using Array.sort
	items.sort(sorter);
	if(queryArgs._start || queryArgs._end || queryArgs._limit){
		if(queryArgs._start){
			start = queryArgs._start
		}

		end = queryArgs._end ? queryArgs._end : items.length
		if(queryArgs._end){
			end = queryArgs._end
		}
		else if(queryArgs._limit){
			end = queryArgs._start + queryArgs._limit
		}

		items = items.slice(start, end);
	}
	return items;
};
```
{% endraw %}

For the sake of brevity, I won't include the endpoint functions but you can find them <a href="https://github.com/ShaneGaymon28/Web-Application-Programming/blob/main/project5/server/server.js">here</a>.

<h4><strong><u>Project 6</u></strong></h4>
<h6><strong>Description</strong></h6>
Project 6 involved using the REST API created in project 5 to create a front-end using React (more specifically <a href="https://marmelab.com/react-admin/">React-admin</a>).

The project required creating the following files (all in app/src/ directory):
<ul>
    <li><strong>Grades.js -</strong> file that handles creating, editing, and displaying all or a single grade entry for a student</li>
    <li><strong>Students.js -</strong> file that handles creating, editing, and displaying all or a single student</li>
    <li><strong>App.js -</strong> the main file that gets loaded by React</li>
</ul>

In both `Grades.js` and `Students.js`, the following functions were added:
<ul>
    <li><strong>List -</strong> returns a react-admin List component that on click goes to the show view and displays the fields in a TextField component </li>
    <li><strong>Show -</strong> returns a react-admin Show component containing either:</li>
    <ul>
        <li>Students - TextFields for id and name as well as a referenceMany field referencing the grades resource</li>
        <li>Grades - TextFields for id and type, NumberFields for the grade and max, and a ReferenceField for the associated student id</li>
    </ul>
    <li><strong>Edit -</strong> returns a react-admin Edit component to modify a resource</li>
    <li><strong>Create -</strong> returns a react-admin Create component to create a resource</li>
</ul>

