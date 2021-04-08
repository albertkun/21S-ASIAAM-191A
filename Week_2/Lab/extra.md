
### Exploration:

If you'd rather use icons then a circular color, then try to see if you can implement this code, be sure to have a custom icon ready!

#### Customizing Icons
```javascript
function createCustomIcon (feature, latlng) {
  let myIcon = L.icon({
    iconUrl: 'my-icon.png',
    shadowUrl: 'my-icon.png',
    iconSize:     [25, 25], // width and height of the image in pixels
    shadowSize:   [35, 20], // width, height of optional shadow image
    iconAnchor:   [12, 12], // point of the icon which will correspond to marker's location
    shadowAnchor: [12, 6],  // anchor point of the shadow. should be offset
    popupAnchor:  [0, 0] // point from which the popup should open relative to the iconAnchor
  })
  return L.marker(latlng, { icon: myIcon })
}
```

The following code will turn your geojson from lab1 into a choropleth map:
```javascript
// this is a function to get the color, notice how the numbers are hard coded, who decides that?
function getColor(d) {
    return d > 1000000 ? '#800026' :
           d > 500000  ? '#BD0026' :
           d > 200000   ? '#FEB24C' :
           d > 10000   ? '#FED976' :
                      '#FFEDA0';
}

// this is the generation function for the style, notice it uses the getColor function
function style(feature) {
    return {
        fillColor: getColor(feature.properties.TOTAL_POP),
        weight: 2,
        opacity: 1,
        color: 'white',
        dashArray: '3',
        fillOpacity: 0.7
    };
}

fetch("js/lab1.geojson")
    .then(response => {
        return response.json()
    })
    .then(ca_counties =>{
        // Basic Leaflet method to add GeoJSON data
        L.geoJSON(ca_counties, {
            style: style
        }).bindPopup(function (layer) {
            return layer.feature.properties.name;
        }).addTo(map);
    })

```

