# JavaScript FUNctions
>### Objectives:
> - Understand how JavaScript affects HTML and CSS
> - Understand how JavaScript variable, function, methods work together 
> - Use JavaScript to add data to a map
> - Add user interactivity with JavaScript functions

You can get the latest assignment by running in your assignments repository:
```
git pull upstream main
```

## Returning home to the HTML/CSS/JS analogy 
Recall from last week's [reading](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/The_web_and_web_standards#html_css_and_javascript) that a webpage is like a house:
- HTML is the scaffolding of the house
- CSS is the paint, carpets, etc. that makes the house look nice 
- JavaScript is the appliances that adds function to the house

Today we will be focusing on the appliances.

## Picking up from last week

We will start this lab off with this Leaflet template code:

> index.html
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Basic Leaflet Map</title>
        <meta charset="utf-8" />
        <link rel="shortcut icon" href="#">

        <style> #map{height:90vh}</style>

        <!-- Leaflet's css-->
        <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />

        <!-- Leaflet's JavaScript-->
        <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
    </head>
    
    <body>
        <div id="map"></div>
    </body>
    <script src="js/init.js"></script>
</html>
```

>js/init.js
```js
const map = L.map('map').setView([34.0709, -118.444], 5);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

// adding markers
let work = L.marker([34.0709, -118.444]).addTo(map)
		.bindPopup('Where I work on campus')

let home = L.marker([37.7409, -122.484]).addTo(map)
		.bindPopup('Where I currently am')

let random = L.marker([39.7409, -122.484]).addTo(map)
		.bindPopup('Third Point')
```

## What is `L.map` and `L.tile`?
`L.map` is Leaflet's lingo for its own mapping Application Programming Interface (API). Every API has its own unique language to utilize it. To learn more about Leaflet's API visit here:
[https://leafletjs.com/reference-1.7.1.html](https://leafletjs.com/reference-1.7.1.html)


## Some Variable Definitions
Last week I talked about `let` and `const` and `var`, but what we really need to understand about variables is that they act like **boxes** where you can **store** or **take** information out of. 
- `const` acts like a locked safe that will not let you put anything into it after you define it
- `let` is like a regular box.
-  `var` is `VARy` problematic because it can be both locked and unlocked 

Here are some of the types in JavaScript:
```js
//number
let box1 = 5;
let box2 = 5.0;

//string
let box3 = 'five';
let box4 = "five";

// string literal, uses backticks and ${variable} to bring in another variable
let box5 = `this is from box #4: ${box4}`;

// array
let box6 = [1,2,3,4,5]; 

// object, stores variables together, can be of different types!
let box7 = {"number": 'five', "value":5};

// boolean (true or false)
let box8 = true;

// null value
let emptyBox;
```

To declare a variable or give it a value you use the  `=` symbol, like so:
```js
let my_variable = "exist!";
```
> Notes:
> - `let` is the type of variable
> - `my_variable` is the variable's name
> - `"exist!"` is the value for this variable
> - `;` defines the end of a line in JavaScript 

**Remember:** 
- Use `let` to define variables you want to change,
- Use `const` to define unchangable variables

Let's practice using variables in our `init.js` file.

>js/init.js
```js
// original code
const map = L.map('map').setView([34.0709, -118.444], 5);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

// adding markers
let work = L.marker([34.0709, -118.444]).addTo(map)
		.bindPopup('Where I work on campus')

let home = L.marker([37.7409, -122.484]).addTo(map)
		.bindPopup('Where I currently am')

let random = L.marker([39.7409, -122.484]).addTo(map)
		.bindPopup('Third Point')

```
### Class Exercise #1

Replace the hard coded values of `const map = L.map('map').setView([34.0709, -118.444], 5);` with variables.

> Bonus: Try to use an object.

<details>
<summary><b>Answer</b></summary>

```js
// method 1
let zoomLevel = 5;
const mapCenter = [34.0709,-118.444];

const map = L.map('map').setView(mapCenter, zoomLevel);

// Bonus:
// let myMap = {'center': [34.0709,-118.444],'zoom':5}
// const map = L.map('map').setView(myMap.center, myMap.zoom);
```
</details>

> Note: You **cannot** use spaces in variable definitions like `let my map;`, so stick with `camelCase`.

#### Think about the benefits of having the variables sitting outside like that, is it easier to read for you? Harder?

### Checking our Dev Console

In VS Code, start Live Server.

After Firefox runs, open the **Console**:
- You can either right click anywhere on the page with the mouse and clicking on `Inspect` or press `F12` on the keyboard.

Think of the **Console** as the Command Line/Terminal for your browser.

- In the console, type `zoomLevel` then press `Enter`. 
- What gets outputted?

Knowing how to check the console will help us test our `functions`.

## Time for FUNctions
Programmers are often programming because they have to get something done, but a true programmer likes to automate (as well as copy and paste).

Look at our `init.js` file after the line `//adding markers`:
>js/init.js
```js
// original code
const map = L.map('map').setView([34.0709, -118.444], 5);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

// adding markers
let work = L.marker([34.0709, -118.444]).addTo(map)
		.bindPopup('Where I work on campus')

let home = L.marker([37.7409, -122.484]).addTo(map)
		.bindPopup('Where I currently am')

let random = L.marker([39.7409, -122.484]).addTo(map)
		.bindPopup('Third Point')

```

We can automate the marker creation by creating a function like this:

>js/init.js

```js
function addMarker(lat,lng,message){
    console.log(message)
    L.marker([lat,lng]).addTo(map).bindPopup(message)
    return message
}
```
> Notes:
> - `function` is the declaration of our function
>- `addMarker` is the name. 
>- `lat,lng,message` is the parameter, which are **passed in** to a function to be utilized. `Parameters` are optional, but parentheses `()` are not!!
>- `{` is the begining of the function.
>- Notice how the function accesses `lat`,`lng` in the `L.marker` and `message` in the `bindPopUp`. 
>- `return` tells the function to **return a variable**, it is also optional
>- `}` is the end of our function.

Note: Multiple parameters are seperated by a comma, `(lat,lng,message)` is 3 parameters. 

The `console.log` in the body will tell us if the function is working.

Go ahead and check the console!

WHAT?! Nothing has changed!

#### Using Functions

In order for a function to run, it needs to be "plugged-in". This is called "invoking" or "calling" the function. When a function has no parameters, you can call it like so:
```js
    function_name()
```

But since our function does have parameters (namely the `lat`,`lng`,and `message`), you must specify them. 

Add this to the end of our `init.js` file:
>js/init.js
```js
    addMaker(37,-122,'you are awesome! you automated a marker function')
```
**Important:** The order of the parameters (`lat`,`lng`,`message`) is the **SAME** order that the function reads them!! Try switching `37` and `-122` to see what I mean.

Now your console should return the "message" AND you should see a new marker on the map!

Inside `function` blocks you can create variables, change HTML, and do all sorts of things like play videos and even create games.

### Class Exercise #2 - Using the marker function
Create your own marker function that does the following:
- Utilizes at least `four parameters`
- Declare a `new variable` inside the function 
- `Returns` a value

Use your function to create 3 markers with it.
<details>
<summary><b>Answer</b></summary>

```js
    // create function
    function addMarker(lat,lng,title,message){
        console.log(message)
        L.marker([lat,lng]).addTo(map).bindPopup(`<h2>${title}</h2>`)
        return message
    }

    // use the function
    addMarker(37,-122,'home','home land!')
    addMarker(32,-118,'work','where i work land!')
    addMarker(39,-119,'location 1','random location')
    addMarker(36,-120,'location 2','another random location')

```
</details>

If you finished early, try these extra challenges:
- Try to style your pop-up with 2 attributes!
<details>

<summary><b>Bonus Exercise - Create your own function</b></summary>

Create your own function that does the following:
- Utilizes at least `two parameters`
- Declare a `new variable` inside the function 
- `Returns` a value
</details>

<details>
<summary><b>Bonus Answer</b></summary>

```js
    // create function
    function addNumbers(value1,value2){
        let result = value1 + value2
        return result
    }

    // use the function
    addNumbers(1,10)   // result: 11

```
</details>

### Sidenote: String Literals

```js
let popup = `${zoomLevel} + ${zoomLevel}`
```
Declaring a string with \` instead of `'` `'` or `" "`, allows you to convert `variables` to strings.  For example, the zoom level normally would be treated as a number, but when we brought it in with the `${}` combination it became a string so it could not be summed.

This technique will be helpful for our pop-ups.

## Functions and the DOM
### **The HTM-Elements: Avatag the last Airbender**

When you see tags in HTML, like `<body></body>`, they are referred to as elements, so for example:
```html
<water>Katara</water> 
<air>Aang</air> 
<earth>Toph</earth> 
<fire>Zuko</fire>
```
Above we have four elements. Each element has a `content`, for example, the `earth` element's content is `Toph`. Unfortunately, despite how exciting those elements are, the most common HTML element is the `<div></div>` element, which is a generic container.

The DOM is basically where HTML elements exists and it has an API that JavaScript can interact with with functions. 

### Objective: Make a button that we can click on to fly to a location for each of the markers you made.

> ### Steps:
> 1. Add a new function to our `addMarker` function
> 2. Create the function to add buttons
> 3. Add a function to toggle the zoom

To create HTML elements with JavaScript you need to use the [createElement](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement) method.
 
First, we will get our buttons ready by going to the `addMarker` function and adding a new function call for the function we haven't created yet.
>js/init.js
```js
// Step 1 adding to our addMarker function
function addMarker(lat,lng,title,message){
    console.log(message)
    L.marker([lat,lng]).addTo(map).bindPopup(`<h2>${title}</h2>`)
    createButtons(lat,lng,title); // new line!!!
    return message
}
```
Next we will add our new function. Notice how we are using the `lat`,`lng`,and `title` from the `addMarker` function? That's why it was helpful to do step one first.
>js/init.js
```js
// Step 2 adding our new function
function createButtons(lat,lng,title){
    const newButton = document.createElement("button"); // adds a new button
    newButton.id = "button"+title; // gives the button a unique id
    newButton.innerHTML = title; // gives the button a title
    newButton.setAttribute("lat",lat); // sets the latitude 
    newButton.setAttribute("lng",lng); // sets the longitude 
    newButton.addEventListener('click', function(){
        map.flyTo([lat,lng]); //this is the flyTo from Leaflet
    })
    document.body.appendChild(newButton); //this adds the button to our page.
}
```
Try clicking the button on the webpage and it should fly to the location of that marker!
### Congratulations on finishing the JavaScript FUNctions Lab!

### Final Code
> js/init.js
```js
// declare variables
let zoomLevel = 5;
const mapCenter = [34.0709,-118.444];

// use the variables
const map = L.map('map').setView(mapCenter, zoomLevel);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

// create a function to add markers
function addMarker(lat,lng,title,message){
    console.log(message)
    L.marker([lat,lng]).addTo(map).bindPopup(`<h2>${title}</h2>`)
    createButtons(lat,lng,title); // new line!!!
    return message
}

// create a function to add buttons with a fly to command
function createButtons(lat,lng,title){
    const newButton = document.createElement("button"); // adds a new button
    newButton.id = "button"+title; // gives the button a unique id
    newButton.innerHTML = title; // gives the button a title
    newButton.setAttribute("lat",lat); // sets the latitude 
    newButton.setAttribute("lng",lng); // sets the longitude 

    // attach an event listner to the button with Leaflet's map.flyTo
    newButton.addEventListener('click', function(){
        map.flyTo([lat,lng]); 
    })
    document.body.appendChild(newButton); //this adds the button to our page.
}

// use our marker functions
addMarker(37,-122,'home','home land!')
addMarker(32,-118,'work','where i work land!')
addMarker(39,-119,'location 1','random location')
addMarker(36,-120,'location 2','another random location')

```

> index.html
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Basic Leaflet Map</title>
        <meta charset="utf-8" />
        <link rel="shortcut icon" href="#">

        <style> #map{height:90vh}</style>

        <!-- Leaflet's css-->
        <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />

        <!-- Leaflet's JavaScript-->
        <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
    </head>
    
    <body>
        <div id="map"></div>
    </body>
    <script src="js/init.js"></script>
</html>
```
## Lab Assignment #3 - JavaScript FUNctions
### Due 4/22

In this lab, we learned how functions are helpful for automating tasks. Functions also form the basis of the programming we will be doing. Your assignment this week is to create a map that will pan to certain makers when a button is clicked. 

The requirements are:

- Add at least 3 markers to the map using a [JavaScript function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/Function)
- Use the [`<button>` element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button) to execute a JavaScript function to interact with your map 
- Add an [Event Listener](https://developer.mozilla.org/en-US/docs/Web/API/EventListener) that executes the JavaScript function to interact with your map 

### Extra Credit:
- Use something else like images or text to move the map.
- Try something new with the [Leaflet API](https://leafletjs.com/reference-1.7.1.html)
- 
## Submission
- Commit your changes to GitHub
- Commit and publish your file to [GitHub pages](https://guides.github.com/features/pages/)
- Find your `index.html` in the `Week_03` folder and copy the URL. It should look something like this:
  - https://albertkun.github.io/21S-ASIAAM-191A-Assignments/Week_03/index.html
- Paste your link as a comment in the Discussion forum for Lab Assignment #3
