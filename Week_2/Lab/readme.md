# Lab 2: Hello World (of HTML, Javascript, CSS, and Leaflet mapping!)


>### Objectives:
> - Create a basic webpage 
> - Add a Leaflet map
> - Add data to the map

This lab will walk you through the process of creating a static web page in HTML with some additional style elements using CSS. Then you will be tasked to add a map using the Leaflet JS library and host it using GitHub pages.

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
In coding, boiler plate code is ready to use code that people can freely copy and use with no changes. Think of them as ready-to-eat microwave dinners.
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

Here is our with a template code:

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Hello World with Leaflet</title>
        <meta charset="utf-8" />
        <link rel="shortcut icon" href="#">
        <!-- I'd add some style if here if I had any -->
        <link rel="stylesheet" href="styles/style.css">

    </head>
    
    <body>
        <header>
            Hello World!
        </header>
        
        <div class="main">
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

Hint: Right click on your `index.html` file and `reveal in file explorer`. Then, double click on the file.


## Cool Stylin' Sheets
Let's add some Cascading Style Sheets (CSS) to visualize our page better.

Insert the following code in the `<head>` right before the closing tag (i.e. `</head>`):

```html
<style>
    html {
        background-color: azure
    }
</style>
```
What happened to the page?

That's cool! But this way of using CSS, called inline CSS can make your HTML file long and cumbersome. So it's usually better a seperate file for CSS and bring that whole file in as a linked source.

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
     grid-template-rows: .1fr .90fr .05fr;
     grid-template-columns: 1fr;
     grid-template-areas: "header" "main" "footer";
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
    height: 80vh;
    /* grid-template-columns: 1fr;
    grid-template-rows: 1fr; */
    background-color: aqua;
}
#footer {
    grid-area: footer;
}
```
Remember to save the `style.css`!

Next go back to the `index.html` file and replace your entire `<style> </style>` content and tags with this code:
```
<link rel="stylesheet" href="css/style.css">
```

What this code does is that it tells the HTML file to use all of the css in the `href` attribute.

#### Note: You can have as many external references as you'd like, as long as you link them in this way.

We will go into CSS in more detail later, but what you need to know is that CSS has `selectors` which are then followed by the styles in `{ }`.

## JavaScript
JavaScript makes sure our page knows how to function and react. There are different frameworks for JavaScript, like React.js and vue.js, but this class will be focusing on vanilla JavaScript with ES7+ standards. All JavaScript must be contained within a script tag. In our `<head>` tag, let's add a `<script></script>` tag.

Sometimes it also becomes important to put JavaScript in the footer tag, why is that? It is because if you have JavaScript functions where the page needs to load first, then putting after the `</body>` becomes necessary. This will be relevant when we bring in Leaflet.js.

### Let's a variable go!
We'll discuss more next week, but JavaScript starts introducing the concept of variables and delcarations

This is an example of a declaration:
```html
var name = "Albert"
```
With JavaScript ES7, we no longer use `var`, but instead `let` and `const` to declar variables. They get declared in the same way, despite their differences:

```html
let location = "SF"
const name = "Albert"
```
A `let` declaration allows a variable to change, while `const` means a variable is constant and will never change.

`var` was problematic because it coule be BOTH!!!

Meaning `var` can be never changing and changing (mutable) at the same time. Hence, it was broken off into two variable types, `let` and `const`. So, bye bye `var` and `LET` us welcome our new `CONST` to the programming world.

### Console.log()
By itself, the script tag does nothing. So, one VERY important JavaScript functions that we should familarize ourself with is `console.log()`, because it allows us to test our code without things showing up in the webpage.

Add the following script:
```html
<script>
    console.log('Hello Asian Am 191! :)')
</script>
```

#### Nothing happened?! What!?
Actually, you are about to unlock your full web developer potential! In Firefox, right click anywhere on the page and the click `Inspect Element`:

This opens the `Developer Toolbar`!! You can find it by going to the Menu and going to `Web Developer` and then `Web Developer Tools`.

Click on the Console button:

Yay! Our message is there!

### Linking to another JavaScript file
Similar to the CSS files, we can move the JavaScript file into its own folder to avoid cluttering the HTML file. 

BUT!!! Instead of `<link>` we must include the JavaScript with the `<script>` tag and `src` attribute follows: 

```html
 <script src="YOUR_SCRIPT_NAME.js"></script> 
```

The `src` is location of your file.

### In-class Exercise #2
>#### Task:
>- Create a new folder called `js`
>- Add our script in there
>- Get our message to show up in the console. 

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

In our `<div id="main"></div>` add a new `<div></div>` tag, and give it an ID attribute of "map":

```html
<div id="map"></map>
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
- Looking at the code above a little bit, we can see some latitude/longitude pairs. Copy the marker code add more makers of your choosing. To find latitude/longitude of coordinates, please use this website:
   - [https://www.latlong.net/](https://www.latlong.net/)

- Optional: Not happy with the basemap?
See if you can switch the basemap out by visiting here: 
   - [https://leaflet-extras.github.io/leaflet-providers/preview/](https://leaflet-extras.github.io/leaflet-providers/preview/)


## Using GitHub Pages
Save and commit your project to GitHub.

Then visit your repository link on GitHub.

Click on Settings:
![](media/gitHubPages_0.png)


Scroll down to "GitHub pages" and then choose source: 
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
`https://albertkun.github.io/21S-ASIAAM-191A-Assignments` plus `/Week_02/index.html`

## Adding our GeoJSON file
Copy `lab1.geojson` from last week into this lab's folder. If you changed the name of it, please use your name or rename it to lab1.geojson.

Go into the `lab1.geojson` file and add the following:

```javascript
const california_counties = 
```

Rename the file to lab1.js.

Next, open the html file and add the following line:
```html
<script src="./js/lab1.js"></script>
```

Finally, go into the init.js file and then add this line at the end:
```javascript
L.geoJSON(ca_counties).addTo(map);
```

Optional:
If you want to get fancy, you can add this line of code which allows you to click on the polygons:

```javascript
function onEachFeature(feature, layer) {
    // checks to make sure feature exists with properties
    if (feature.properties) {
        layer.bindPopup("<h3>Name: "+feature.properties.name+"</h3>");
		console.log(feature.properties)
    }
}

L.geoJSON(ca_counties, {
    onEachFeature: onEachFeature
}).addTo(map);
```

## Lab Assignment - Map Portfolio:
Create a home page for the individual maps that you will be making this quarter. Describe some of your interests and include a map with some markers. 

- Use the `<h1>` tag for your title
- Add at least 2-3 markers to the map with a common theme, for example organizations you've volunteered for or places you've traveled.
- Use the `<h2>` or `<h3>` tag to create a title for your map. 
- Add a `<p>` tag for a paragraph describing yourself and your goals as a critical digital map maker.
- Style CSS by changing the background color, font, or anything else.
- Use an ordered list `<ol>` tag and an unordered list `<ul>` tag to list things.
- Include an `<img>` tag with a photo of yourself or an avatar. Feel free to add other images too to give some flavor to your page, like food or desserts.
- Use the `<a>` tag to add a link to 2 other web pages.
- Set up GitHub pages for your repo
- Submission: In the `week_02` folder, add a `readme.md` that links to your GitHub pages, it should look something like this:

  - https://albertkun.github.io/21S-ASIAAM-191A-Assignments/Week_02/index.html

- Extra Credit: Add the `lab1.geojson` to a completely different map and HTML page.
