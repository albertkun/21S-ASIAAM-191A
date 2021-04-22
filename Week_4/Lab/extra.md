
## Automatic Geocoding for "Free"
Now we will perform a geocode (putting Latitude and Longitude to named places) on the location after each time it is run. To make things easier, we will need to install an add-on for this.

Click on Add-ons:
![](media/googleForms26a.png)
Click on Get add-ons:
![](media/googleForms26b.png)
Search for `Geocode by Awesome Table`
![](media/googleForms27.png)
Click the the button to open the add-on installation:
![](media/googleForms28.png)
Click install:
![](media/googleForms29.png)
Click continue to sign-in with Google:
![](media/googleForms30.png)
Choose the account to give access to the geocoder add-on:
![](media/googleForms31.png)
Allow the permissions (be sure to read what it allows first):
![](media/googleForms32.png)
After the installation is done, go to `Add-ons` in the menu:
![](media/googleFormsAddon.png)
Click on the `Geocode by AwesomeTable` and select `Start Geocoding`
![](media/googleForms34.png)
Click the column under the `address` column, it defaults to the first column:
![](media/googleForms34a.png)
Choose the `location` column:
![](media/googleForms34b.png)
Click the `Geocode!` button:
![](media/googleForms34c.png)
In the add-on menu for Geocode by Awesome Table, choose `Geocode on Form Submit`
![](media/googleForms34d.png)
Activate the trigger: 
![](media/googleForms34e.png)
Close the window:
![](media/googleForms34f.png)


## Publishing the survey
Now that our data is able to be geocoding, we can bring it into our HTML file through JavaScript. But first we have to publish the spreadsheet:

Go to file:
![](media/googleForms35.png)
Click on `Publish to web`:
![](media/googleForms36.png)
Click on `Publish`:
![](media/googleForms37.png)
Copy the URL in the address bar:
![](media/googleForms38.png)

Go to this website:
[https://sandbox.idre.ucla.edu/tools/gsJson/](https://sandbox.idre.ucla.edu/tools/gsJson/)
Paste the URL in:
![](media/googleForms39.png)
Click the button, `Get Spreadsheets`:
![](media/googleForms40.png)
Click the button, `Get Spreadsheets JSON`:
![](media/googleForms41.png)
Copy the results:
![](media/googleForms42.png)

In the `init.js` file paste the entire result into the `URL` variable:

> js/init.js
```js
let url = "https://spreadsheets.google.com/feeds/list/1j3a2do9HIS6xvpBsKMjmI4soNaqGdlnIkwYQHktmp1U/oua1awz/public/values?alt=json"
fetch(url)
	.then(response => {
		return response.json();
		})
    .then(data =>{
        console.log(data)
    }
```
In your console, you should now see the Google Spreadsheet data when some one enters information.