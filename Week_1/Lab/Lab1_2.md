# Lab 1.3 “Hello World!” – QGIS Bootcamp
  - [Adding spatial data](#adding-spatial-data)
  - [Exploring spatial data attributes](#exploring-spatial-data-attributes)
  - [Adding a field](#adding-a-field)
  - [Symbolizing our map](#symbolizing-our-map)
  - [Filtering our fields](#filtering-our-fields)
  - [Saving Our Map Layer for Web Mapping](#saving-our-map-layer-for-web-mapping)
  - [Adding non-spatial data](#adding-non-spatial-data)
  - [Lab Questions:](#lab-questions)

## Adding spatial data

>**Important:** Before starting this lab, you must have completed the pre-lab and part 1. This means you should have already installed QGIS and a local copy the lab.

1.  Click on “Layer”

<img src="media\image2.png" style="width:4.93798in;height:3.51357in" />

2.  “Add Layer” “Add vector layer”

<img src="media\image3.png" style="width:4.71318in;height:3.24806in" />

3.  Locate the file “**CA\_Counties.shp**”

<img src="media\image4.png" style="width:6.5in;height:4.28472in" />

4.  Click “Add” to add it to your QGIS project.

<img src="media\image5.png" style="width:6.5in;height:4.05972in" />

5.  Counties in California should now appear:

<img src="media\image6.png" style="width:6.5in;height:3.46667in" />

## Exploring spatial data attributes

6.  In the “Layers” panel, right click on the layer
    “**CA\_Counties\_TIGER2016**”

<img src="media\image7.png" style="width:6.5in;height:3.46667in" />

7.  Click on “Open Attribute Table”

<img src="media\image8.png" style="width:6.5in;height:3.46667in" />

8.  Now you can see the attributes of each of the spatial data shown in
    the map:

<img src="media\image9.png" style="width:6.5in;height:3.54306in" />

9.  You can click on the headers to sort, so let’s find the most
    populous country in the world by scrolling to “**TOTAL\_POP**” and
    clicking on it:

<img src="media\image10.png" style="width:6.5in;height:3.54306in" />

10. We can highlight the country by click on the number box with the
    number 1 next to it:

<img src="media\image11.png" style="width:5.98245in;height:3.49612in" />

Note: Shift + Click down to select multiple rows:  
<img src="media\image12.png" style="width:5.93798in;height:3.44147in" />

11. Return to the map to see the most populated counties according to
    the American Community Survey 2019 data in California highlighted:

<img src="media\image13.png" style="width:6.5in;height:3.45625in" />

12. Clear your selection in the following ways:

    1.  Clicking the deselect button in the general interface:

> <img src="media\image14.png" style="width:6.5in;height:3.45625in" />

2.  Or the deselect button in the attribute table:

> <img src="media\image15.png" style="width:6.5in;height:3.52986in" />

## Adding a field

Since bigger areas are most likely to have more people, we need to
factor that in to see where most people in the state are likely to be
found. We will do a population density calculation, which is simply
“number of people” divided by “total area.”

13. Click the “edit” tool to enable making changes:

<img src="media\image16.png" style="width:5.81989in;height:2.78295in" />

14. Warning! When you are in “editor” mode you can click on any cell to
    directly edit it:

<img src="media\image17.png" style="width:6.5in;height:2.20357in" />

1.  If you accidentally made edits, turn off editing mode by clicking
    the pencil
    again:<img src="media\image18.png" style="width:5.93023in;height:2.24849in" />

2.  Choose “Discard”:

> <img src="media\image19.png" style="width:6.45349in;height:3.49653in" />

15. Next click the “Field Calculator” button:

<img src="media\image20.png" style="width:5.63048in;height:2.52713in" />

16. The field calculator window will appear:

<img src="media\image21.png" style="width:6.5in;height:4.34583in" />

17. Click on “Output field name” and type in “AREA\_SQ\_KM” which will
    be “Area in square kilometers”.

<img src="media\image22.png" style="width:6.5in;height:4.34583in" />

18. Click on field type and choose “Decimal Number (real)”

<img src="media\image23.png" style="width:6.5in;height:4.34583in" />

19. In the Expression box type in the following:

**$area / 1000000**

<img src="media\image24.png" style="width:6.5in;height:4.34583in" />

20. If correctly done, you can see the preview will show the value:

<img src="media\image25.png" style="width:6.5in;height:4.34583in" />

21. Click OK:

<img src="media\image26.png" style="width:6.37209in;height:4.26372in" />

22. You can see our new field all the way on the right side:

<img src="media\image27.png" style="width:6.5in;height:3.49653in" />

23. Open the “Field Calculator” again and create a new field called
    “POP\_DENSIT” with Decimal number (real):

<img src="media\image28.png" style="width:6.5in;height:4.34583in" />

24. Locate the search box, this place is helpful for creating
    expressions.

<img src="media\image29.png" style="width:5.64341in;height:3.77313in" />

25. In the search box type in “total\_pop” and double click on the
    result:

<img src="media\image30.png" style="width:6.5in;height:4.34583in" />

1.  Note: The help on the right side explains more detail about what is
    being selected in the search box.

<!-- -->

26. Add a “/” for divide

27. Search for “area\_sq\_km” and add it to our expression:

<img src="media\image31.png" style="width:6.24031in;height:4.17221in" />

28. The final expression should be:

**"TOTAL\_POP" / "AREA\_SQ\_KM"**

<img src="media\image32.png" style="width:6.5in;height:4.34583in" />

29. Check the preview:

<img src="media\image33.png" style="width:6.5in;height:4.34583in" />

30. Hit OK:

<img src="media\image34.png" style="width:6.5in;height:4.34583in" />

31. Check to see if the POP\_DENSIT column is there:

<img src="media\image35.png" style="width:6.5in;height:3.56736in" />

32. If you have successfully calculated the population density for all
    the counties in California, then click the “save” button to save our
    edits:

<img src="media\image36.png" style="width:5.96899in;height:2.54375in" />

33. Turn off the editing tool as we are done with it:

<img src="media\image37.png" style="width:5.34109in;height:2.5417in" />

## Symbolizing our map

34. Right click on our layer and go to “Properties”:

<img src="media\image38.png" style="width:6.5in;height:3.46319in" />

35. Click on “Symbology”:

<img src="media\image39.png" style="width:6.5in;height:3.79375in" />

36. From there, click on “Single Symbol” to change which data fields are
    being used for map creation:

<img src="media\image40.png" style="width:6.5in;height:3.79375in" />

37. If we were working with qualitative data fields then we would use
    “categorized”, however we are going to be looking at our population
    density data field, so we should use “graduated”:

<img src="media\image41.png" style="width:6.5in;height:3.79375in" />

38. Click the dropdown arrow near “Value” to see the list of fields:

<img src="media\image42.png" style="width:6.5in;height:3.79375in" />

39. Choose “POP\_DENSIT”:

<img src="media\image43.png" style="width:6.5in;height:3.79375in" />

40. Change the “Mode” to “Equal Interval” which means that the breaks
    between values are evenly spaced apart (i.e. 0-5, 5-10,10-15):

<img src="media\image44.png" style="width:6.5in;height:3.79375in" />

41. You can click histogram to get a better sense of the data and which
    statistical mode you should use (but since this is not a stats
    class, I won’t spend much more time on this):

<img src="media\image45.png" style="width:6.5in;height:3.79375in" />

42. You can also change the number of “classes” (or breaks) by clicking
    here:

<img src="media\image46.png" style="width:6.5in;height:3.79375in" />

43. Click “OK” to apply our changes to the map:

44. You can change the colors by clicking on “Color ramp”:

<img src="media\image47.png" style="width:6.5in;height:3.79375in" />

45. Or individually by right clicking the square colored boxes:

<img src="media\image48.png" style="width:6.5in;height:3.79375in" />

46. Choose “change color” and adjust the color wheel:

<img src="media\image49.png" style="width:6.5in;height:3.79375in" />

47. When satisfied with your changes click “OK” to close the dialogue
    box:

<img src="media\image50.png" style="width:6.5in;height:3.79375in" />

48. You map should look like the following:

<img src="media\image51.png" style="width:6.5in;height:3.45347in" />

49. Tip: You can quickly change any color by right clicking on the
    colored box to the left of any layer:

<img src="media\image52.png" style="width:6.52713in;height:3.46789in" />

## Filtering our fields

50. Let’s do some advanced filtering to see places where more than
    100,000 Asians live.

51. Start by opening our attribute table again:

    1.  Right click on our layer

> <img src="media\image53.png" style="width:4.35659in;height:3.34481in" />

2.  Click “Open Attribute Table”:

> <img src="media\image54.png" style="width:3.96124in;height:4.76531in" />

52. Click the “Filter selection form”.

<img src="media\image55.png" style="width:5.1896in;height:2.32558in" />

53. We are finding places with “Asians” so locate the “ASIAN\_POP”
    field:

<img src="media\image56.png" style="width:6.5in;height:3.54792in" />

54. Click the “Exclude field” button to change it:

<img src="media\image57.png" style="width:6.5in;height:3.54792in" />

55. We will make it “Greater than or Equal to”:

<img src="media\image58.png" style="width:6.5in;height:3.23403in" />

56. Then type in 100000:

<img src="media\image59.png" style="width:6.5in;height:3.23403in" />

57. Click on “Select Features”

<img src="media\image60.png" style="width:6.15504in;height:3.40278in" />

58. Click the lower right icon to return to the table view:

<img src="media\image61.png" style="width:6.40278in;height:3.51319in" />

59. You can view only selected features by clicking here:

<img src="media\image62.png" style="width:6.5in;height:3.54722in" />

60. Then choosing “Show Selected Features”

<img src="media\image63.png" style="width:6.5in;height:3.54722in" />

61. Close the table when done exploring by clicking the X:

<img src="media\image64.png" style="width:6.5in;height:3.54722in" />

62. Congrats! Now you have filtered some features.

## Saving Our Map Layer for Web Mapping

63. With everything still selected, right click on the layer:

<img src="media\image65.png" style="width:6.24287in;height:3.43411in" />

64. Go to “Export” and then choose “Save Selected Features As…”:
    <img src="media\image66.png" style="width:5.7907in;height:4.44935in" />

65. Right Click on the layer

> <img src="media\image67.png" style="width:5.67945in;height:3.86822in" />

66. Going to Export Data Save Selected Features as…:

<img src="media\image68.png" style="width:5.63028in;height:4.39535in" />

67. The ESRI shapefile is the default, but it is very hard to use in our
    web applications because it is a proprietary data format..

<img src="media\image69.png" style="width:4.11827in;height:4.72247in" />

68. The preferred spatial format online is a GeoJSON file:

<img src="media\image70.png" style="width:3.72093in;height:4.3629in" />

69. Click the “…” next to “File Name” to find a nice new home for your
    GeoJSON file!

<img src="media\image71.png" style="width:2.83227in;height:3.24031in" />

70. Your final box should look like this:

    1.  Format: GeoJSON

    2.  File name: CA\_counties\_with\_over\_100k\_Asians.geojson

> <img src="media\image72.png" style="width:5.02109in;height:5.50723in" />

71. Congratulations! You have created your first “GeoJSON” file! We will
    revisit this file in next week’s lab, so keep it safe and sound!

## Adding non-spatial data

72. You can also add CSV files by clicking “Layer”

<img src="media\image73.png" style="width:6.5in;height:4.14931in" />

73. Click on “Add Layer” “Add Delimited Text Layer...”

<img src="media\image74.png" style="width:5.83073in;height:4.92248in" />

74. To the far right of “File Name”, click on the button with “…”:

<img src="media\image75.png" style="width:6.5in;height:4.32083in" />

75. Locate the file for California Asian American Hate Crimes,
    CA\_AAHC\_2021.csv and select it and choose “Open”:

<img src="media\image76.png" style="width:6.5in;height:4.27083in" />

76. Check to make sure “Point” coordinates and a coordinate reference
    system exists:

<img src="media\image77.png" style="width:6.5in;height:4.16389in" />

77. Click “Add” and then “Close”:

<img src="media\image78.png" style="width:6.5in;height:4.16389in" />

78. The data points should now show up:

<img src="media\image79.png" style="width:6.41651in;height:3.47287in" />

79. Note that you will not be able to edit CSV files, you will need to
    export them in a spatial data type format, such as shapefile or
    GeoJSON to do so.

80. Congratulations on finishing the spatial data management lab.

## Lab Questions: 

Please take some time to answer the following questions and include them
in your “Thinking Cap” response for the week.

1.  ## What changes did we make to the original data?

2.  ## How can the choices we made in changing the data be problematic?
