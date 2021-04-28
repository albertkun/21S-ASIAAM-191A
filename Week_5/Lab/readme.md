# Loops and APIs

>### Objectives:
> - Be able to use loops and conditional statements in JavaScript 
> - Understand what an API is 
> - Add data from a Google Sheet into a website
> - Implement a trigger for geocoding "location" data in Google Sheets

Start by creating a `week5` folder in your lab assignments repo.

### Note: If you finished last week's lab, then you can copy the contents of your `week4` folder and skip the following setup section.

## Setup


Create a new html page called `index.html` and add this code:
> index.html
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Basic Leaflet Map</title>
        <meta charset="utf-8" />
        <link rel="shortcut icon" href="#">
        <link rel="stylesheet" href="style/style.css">

        <!-- Leaflet's css-->
        <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />

        <!-- Leaflet's JavaScript-->
        <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
    </head>
    
    <body>
        <div id="map"></div>
        <div id="survey">
        <!-- put the survey in here! -->
        </div>
        <script src="js/init.js"></script>
    </body>
</html>
```