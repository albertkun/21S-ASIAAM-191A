# Lab 2: Hello World (of HTML, Javascript, CSS, and Leaflet mapping!)


### Objectives:
 - Create a basic webpage 
 - Add a Leaflet map
 - Add GeoJSON data to the map
 - Create a GeoJSON online

This lab will walk you through the process of creating a static web page in HTML with some additional style elements using CSS. Then you will be tasked to add a map using the [Leaflet JS library](leafletjs.com/) and host it using GitHub pages.

>Note: I highly recommend checking out the [Leaflet  documentation](https://leafletjs.com/reference-1.7.1.html). Looking at any documentation before choosing any software is important, because badly documented libraries can make tools difficult to use. 


## Let's get VS Coding!

Start up VS Code and open your Assignments repo:
![](media/assignments_open.png)

Remember to select the correct folder!
![](media/assignments_folder.png)

Make sure Explorer is open in the activity bar by clicking on it:

![](media/explorer_open.png)

Click on `Week_02` <span style="background-color:red">**(1)**</span> and then the `new file` button <span style="background-color:red">**(2)**</span>:
  ![](media/new_file.png) 
   
## HTML?! Oh what `tag`gony!

HTML is what makes up the house for websites to be able to  talk to the server. Everything in HTML is surrounded by tags which look like this:
`<tag> Look Ma'! I'm in a tag! </tag>`

### 2.1 Attributes in tags
If we can only use tags, the web would be a pretty boring place. So in order to make each tag unique, we can add attributes to them. To do so, you add an `attribute="some value"`

For example, we can name a tag something:
`<tag name="Albert"></tag>`

Wow, that's my name tag!

### 2.2 Boilerplate vs. Template Code
In coding, boilerplate code is ready to use code that people can freely copy and use with no changes. Think of them as ready-to-eat microwave dinners.
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <title></title>
</head>
<body>

</body>
</html>
```

Template code refers to sample code that can be copied and pasted, but requires modifications in order for it to work.

Here is our template code:

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Hello World with Leaflet</title>
        <meta charset="utf-8" />
        <link rel="shortcut icon" href="#">

        <!-- I'd add some style if here if I had any -->

    </head>
    
    <body>
        <header>
            Hello World!
        </header>
        
        <div class="main">
        <!-- hint: majority of your lab assignment can go here     -->
        
        </div>


        <div id="footer">
Copyright(2021)
        </div>
        
    </body>
</html>
```

> What do you observe in the code? 
> 1. How does this code differ from the boilerplate code?
> 2. Why should everything be enclosed in the `html` tag?
> 3. Do empty spaces matter in HTML?
> 4. What is a comment and how do you write one?
> 5. Is there a difference between the `class` and `id` attributes?

### In-Class Exercise #1
Let's fix our code so that it actually looks presentable. Look for the errors in the template code.

Save the file and name it `index.html` and open it in Firefox.

### Preview our file
Make sure you have the Live Server extension installed:
[https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

Click on Go Live!
![](media/go_live.png)

Your default browser should automatically pop-up, if it is not Firefox, you will need to copy and paste the link over.

![](media/live_preview.png)

Alternatively: Right click on your `index.html` file and `reveal in file explorer`. Then, double click on the file.


## Cool Stylin' Sheets
Let's add some Cascading Style Sheets (CSS) to visualize our page better.

Insert the following code in the `<head>` right before the closing tag (i.e. `</head>`):

```html
<style>
    html {
        background-color: azure;
    }
</style>
```
What happened to the page?

That's cool! But this way of using CSS, called inline CSS, can make your HTML file long and cumbersome. So it's usually better to have a separate file for CSS and bring that whole file in as a linked source.

### Adding linked CSS
Click the new folder button:

![](media/new_folder.png)

Highlight the `style` folder by clicking on it:

![](media/new_file_2.png)

Then click on the `new file` button file:

![](media/new_file_3.png)

Name the file `style.css`:

![](media/style_css.png)

Double click to open the new file. Then copy and paste the following CSS:

```
html, body {
    padding: 5px;
 }

 body {
     display: grid;
     grid-template-rows: .1fr .30fr .60fr .05fr;
     grid-template-columns: 1fr;
     grid-template-areas: "header" "main" "map"  "footer";
     justify-content: center;
 }

 header {
    grid-area: header;
    display: grid;
    grid-template-columns: .2fr .6fr .2fr;
    justify-content: center;
 }

.main {
    display: grid;
    grid-area: main;
    background-color: aqua;
}

#map {
    grid-area: map;
    height: 40vh;
}

#footer {
    grid-area: footer;
}
```
Remember to save the `style.css`!

Next go back to the `index.html` file and replace your entire `<style> </style>` content and tags with this code:
```
<link rel="stylesheet" href="style/style.css">
```

What this code does is that it tells the HTML file to use all of the css in the `href` attribute.

#### Note: You can have as many external references as you'd like, as long as you link them in this way.

We will go into CSS in more detail later, but what you need to know is that CSS has `selectors` which are then followed by the styles in `{ }`.

## JavaScript
JavaScript makes sure our page knows how to function and react. There are different frameworks for JavaScript, like React.js and vue.js, but this class will be focusing on vanilla JavaScript with ES7+ standards. All JavaScript must be contained within a script tag. In our `<head>` tag, let's add a `<script></script>` tag.

Sometimes it also becomes important to put JavaScript in the footer tag, why is that? Sometimes you need JavaScript functions to run after the body loads, so putting `<script>` after the `</body>` becomes necessary. This will be relevant when we bring in Leaflet.js.

### Let's a-(variable)-go!
Remember how we had field types in QGIS? Like, double, float and string? In programming languages we call those "types." With JavaScript, variables are automatically assigned types based on their declaration. We'll discuss more next week, but is a quick introducing the concept of variables and declarations.

This is an example of a declaration:
```js
var day = 8;
var name = "Albert";
```
Here `day` is a **number** type and `name` is a **string** type. Each type has certain properties with them, for example you can add **numbers** together using something like `day + day`, but you adding strings will simply concatenate and not total them.

Important note, that with JavaScript ES7, we no longer use `var`, but instead `let` and `const` to declare variables. They get declared in the same way:

```js
let day = 8;
const name = "Albert";
```

### Let vs Const vs Var
What is the difference? 

1. `let` declaration allows a variable to change
2.  `const` means a variable is constant and will never change.
3. `var` can be both changed and never changed depending on where it was declared! VERY PROBLEMATIC!

Because `var` can be changing (mutable) and unchanging at the same time, so it was broken off into two variable types, `let` and `const`. 

So, bye bye `var` and `LET` us welcome our new `CONST` variables to the programming world.

To recap: NEVER USE `var` unless you have to code for old browsers.

### Console.log()
By itself, our script tag does nothing. So, one VERY important JavaScript method that we should familarize ourself with is `console.log()`, because it allows us to test our code without things showing up in the webpage.

Add the following script:
```html
<script>
    console.log('Hello Asian Am 191! :)');
</script>
```

#### Nothing happened?! What!?
Actually, you are about to unlock your full web developer potential! 

In Firefox, right click anywhere on the page and the click `Inspect Element`:
![](media/click_anywhere.png)
This opens the `Developer Toolbar`!! You can find it by going to the Menu and going to `Web Developer` and then `Web Developer Tools`.

Click on the Console button:

![](media/console.png)

Yay! Our message is there!

![](media/console_log_worked.png)

### Linking to another JavaScript file
Similar to the CSS files, we can move the JavaScript file into its own folder to avoid cluttering the HTML file. Importing libraries is the main way we level up our webpage.

BUT!!! Instead of `<link>` we use the `<script>` tag:

```html
 <script src="YOUR_SCRIPT_NAME.js"></script> 
```

The `src` attribute is location of your file.

### In-class Exercise #2
>#### Task:
>- Create a new folder called `js`
>- Add our script in there
>- Get our message to show up in the console 

## Hello Leaflet... Finally..
OK, why did we do ALL of that? Well, when we use Leaflet, we actually need to bring in Leaflet's external CSS and JavaScript files!

So, in our header, let's add the following:
```html
<!-- Leaflet's css-->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />

<!-- Leaflet's JavaScript-->
<script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
```

Now, let's go ahead and add a container for our map. 

After `<div id="main"></div>` add a new `<div></div>` tag, and give it an ID attribute of "map":

```html
<div id="map"></div>
```

With our container ready to go, open up the JavaScript file again and add the following Leaflet code template:

```javascript

// JavaScript const variable declaration
const map = L.map('map').setView([34.0709, -118.444], 15);

// Leaflet tile layer, i.e. the base map
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
	attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

//JavaScript let variable declaration to create a marker
let marker = L.marker([34.0709, -118.444]).addTo(map)
		.bindPopup('Math Sciences 4328 aka the Technology Sandbox<br> is the lab where I work in ')
		.openPopup();

```
#### Class Exercise #3 - Adding more markers
- Looking at the code above a little bit, we can see some latitude/longitude pairs. Copy the marker code add more markers of your choosing. **Note**: Be sure give the marker variable a new name, like `marker2`.  
- To find latitude/longitude of coordinates, please use this website:
   - [https://www.latlong.net/](https://www.latlong.net/)

- Optional: Not happy with the basemap?
See if you can switch the basemap out by visiting here: 
   - [https://leaflet-extras.github.io/leaflet-providers/preview/](https://leaflet-extras.github.io/leaflet-providers/preview/)


## Using GitHub Pages
Save and commit your project to GitHub.

Then visit your repository link on GitHub.

Click on Settings:
![](media/gitHubPages_0.png)


Scroll down to "GitHub pages" and under source click here: 
![](media/gitHubPages_1.png)

Click on the "main" branch:
![](media/gitHubPages_2.png)


Choose "root":
![](media/gitHubPages_3a.png)

Click on Save:
![](media/gitHubPages_4a.png)


Copy the link and put it in your `readme.md` file in the `week 2` folder.
![](media/gitHubPages_5.png)

You can see the `html` file if you go to 
`https://YOUR_GITHUB_ACCOUNT.github.io/21S-ASIAAM-191A-Assignments/Week_02/index.html`

## Adding a GeoJSON file
Copy `lab1.geojson` from last week into this lab's folder. If you changed the name of it, please use  your filename to follow along or rename the file to lab1.geojson.

### FETCH and THEN
We will use the JavaScript [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) to get our geojson file and then add it to our map. In JavaScript whenever you see a `.` after a parenthesis, it means you are **chaining** a command to follow it. In this case we are chaining a `then` method. In the `then` method we will have a 

```javascript
fetch("js/lab1.geojson")
    .then(response => {
        return response.json();
    })
    .then(data =>{
        // Basic Leaflet method to add GeoJSON data
        L.geoJSON(data).addTo(map)
    });
```
The map should now have a blue tint over it and you cannot interact with it. Not really useful.

Add the basic Leaflet method for a geojson:
```javascript
// the leaflet method for adding a geojson
L.geoJSON(data, {
    style: function (feature) {
        return {color: 'red'};
    }
}).bindPopup(function (layer) {
    return layer.feature.properties.name;
}).addTo(map);
```

The completed `fetch` code should look like this:
```javascript
fetch("js/lab1.geojson")
	.then(response => {
		return response.json();
		})
    .then(data =>{
        // Basic Leaflet method to add GeoJSON data
                        // the leaflet method for adding a geojson
            L.geoJSON(data, {
                style: function (feature) {
                    return {color: 'red'};
                }
            }).bindPopup(function (layer) {
                return layer.feature.properties.name;
            }).addTo(map);
        });
```
Notice now that when you click on the map, the name of the counties show up.

## The power of web mapping

The boundary that we added from last week doesn't really seem to add much. Let's put to practice what web development and GIS can do for power.

Head over to this website:
[http://www.geojson.io/](http://www.geojson.io/)

Click on the marker tool:

![](./media/geojson1.png)

Click on a location of interest to you:

![](./media/geojson2.png)

Add a data column:

![](./media/geojson3.png)

Call it place and click "OK":

![](./media/geojson4.png)

Click inside the place column

![](./media/geojson6.png)

Type in a description for the place, in this case I called it "home".

![](./media/geojson7a.png)

Zoom out:
![](./media/geojson8.png)

Click the edit button:

![](./media/geojson9.png)

Click the move the marker to the adjust the location:

![](./media/geojson9a.png)

Save your edit:

![](./media/geojson10.png)

Repeat these steps until you have a few points.

Add another column called "color", to put some color to your map later.

![](./media/geojson10.png)

Save your file:

![](./media/geojson11.png)

Click geoJSON:

![](./media/geojson12.png)

Download the file to your computer:

![](./media/geojson13.png)

Copy the file into your project folder:

![](./media/geojson15.png)

Change `lab1.geojson` to `map.geojson` (the name of the file we downloaded) in the `fetch` code:

```javascript
fetch("js/map.geojson")
    .then(response => {
        return response.json()
    })
    .then(data =>{
        // Basic Leaflet method to add GeoJSON data
        L.geoJSON(data, myLayerOptions)
        .bindPopup(function (layer) {
            return layer.feature.properties.place;
        }).addTo(map);
    })
```
Bam! It updated!

Utilize our color property:

```javascript
function customMarker (feature, latlng) {
    return L.circleMarker(latlng, { color: feature.properties.color })
  }
  
  // create an options object
  let myLayerOptions = {
    pointToLayer: customMarker
  }
```
Now think about how empowering it was for you to be able to add data to the map yourselves. Whether you were clicking random spots or trying to find your old favorite places to visit, the ability to mark things is a reclaiming of mapping for yourself. This sense of staking a claim is what I mean when I refer to "empowering community voices".

### Final Template Code:

`index.html`
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Hello World with Leaflet</title>
        <meta charset="utf-8" />
        <link rel="shortcut icon" href="#">
        <!-- I'd add some style if here if I had any -->
        <link rel="stylesheet" href="style/style.css">
        <script>
            console.log('Hello Asian Am 191! :)')
        </script>
        <!-- Leaflet's css-->
        <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />

        <!-- Leaflet's JavaScript-->
        <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
        <script src="./js/lab1.js"></script>
    </head>
    
    <body>
        <header>
            My Map
        </header>
        
        <div class="main">
            
        </div>
        <div id="map"></div>
        <div id="footer">
            Copyright(2021)
        </div>
        
    </body>

    <script src="./js/init.js"></script>
</html>
```

`init.js`
```js
const map = L.map('map').setView([34.0709, -118.444], 5);

// Leaflet tile layer, i.e. the base map
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
	attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

//JavaScript let variable declaration to create a marker
let marker = L.marker([34.0709, -118.444]).addTo(map)
		.bindPopup('Math Sciences 4328 aka the Technology Sandbox<br> is the lab where I work in ')
		// .openPopup();

fetch("js/map.geojson")
	.then(response => {
		return response.json();
		})
    .then(data =>{
        // Basic Leaflet method to add GeoJSON data
                        // the leaflet method for adding a geojson
            L.geoJSON(data, {
                style: function (feature) {
                    return {color: 'red'};
                }
            }).bindPopup(function (layer) {
                return layer.feature.properties.place;
            }).addTo(map);
        });
    

```

`style/style.css`
```css

html, body {
    padding: 5px;
 }

 body {
     display: grid;
     grid-template-rows: .1fr .30fr .60fr .05fr;
     grid-template-columns: 1fr;
     grid-template-areas: "header" "main" "map"  "footer";
     justify-content: center;
 }

 header {
    grid-area: header;
    display: grid;
    grid-template-columns: .2fr .6fr .2fr;
    justify-content: center;
 }

.main {
    display: grid;
    grid-area: main;
    background-color: aqua;
}

#map {
    grid-area: map;
    height: 40vh;
}

#footer {
    grid-area: footer;
}

```
## Lab Assignment - Map Portfolio:
### Due 4/15
Time to put your skills to the test and create a home page for the individual maps that you will be making this quarter. Describe some of your interests and include a map with some markers. This is your portfolio, so feel free to delete or add anything. If you made multiple HTML pages, please link them all to the `index.html` using the `<a href=""></a>` tag>.

Your map portfolio must contain the following:

- A [`<h1>` tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements) for your title
- Add at least 2-3 markers to the map with a common theme, for example organizations you've volunteered for or places you've traveled.
- A `<h2>` or [`<h3>` tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements) to create a title for your map. 
- A [`<p>` tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p) for a paragraph describing yourself and your goals as a critical digital map maker.
- Style CSS by changing the background color, font, or anything else.
- Use an ordered list [`<ol>` tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ol) and an unordered list [`<ul>` tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ul) to list things.
- Include an [`<img>` tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img) with a photo of yourself or an avatar. Feel free to add other images too to give some flavor to your page, like food or desserts.
- Use the [`<a>` tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a) to add a link to 2 other web pages.
- Set up GitHub pages for your repo

###  Submission: 
- Commit and publish your file to your repo's [GitHub pages](https://guides.github.com/features/pages/)
- Find your `index.html` in the `Week_02` folder and copy the URL. It should look something like this:

  - https://albertkun.github.io/21S-ASIAAM-191A-Assignments/Week_02/index.html

- Paste your link as a comment in the [Discussion forum for Lab Assignment #2](https://github.com/albertkun/21S-ASIAAM-191A/discussions/89)


### Extra Credit: (any of these) 
   - Add another `geojson` (it can be `lab1.geojson` or anything else) to a completely different HTML page not `index.html`. (Be sure to link it to your `index.html` and describe what you are showing)
   - Add some Leaflet features that we did not discuss in class.
   - Check out the [Extra](extra.md) or [Leaflet documentation](http://www.leafletjs.com/) and try something there.

### HTML Resources to help with your assignment:
- Short MDN HTML Syntax (good recap): 
https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started

- Long overview and explanation of HTML:
https://geobgu.xyz/web-mapping2/html.html
