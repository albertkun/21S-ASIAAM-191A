# Lab 1.2 "Hello World!" QGIS Bootcamp
  - [Adding spatial data](#adding-spatial-data)
  - [Exploring spatial data attributes](#exploring-spatial-data-attributes)
  - [Adding a field](#adding-a-field)
  - [Symbolizing our map](#symbolizing-our-map)
  - [Filtering our fields](#filtering-our-fields)
  - [Saving Our Map Layer for Web Mapping](#saving-our-map-layer-for-web-mapping)
  - [Adding non-spatial data](#adding-non-spatial-data)
  - [Lab Questions](#lab-questions)

## Adding spatial data

>**Important:** Before starting this lab, you must have completed the pre-lab and part 1. This means you should have already installed QGIS and a local copy the lab.

1.  Click on `Layer`

<img src="media\image2.png" style="" />

2.  `Add Layer` `Add vector layer`

<img src="media\image3.png" style="" />

3.  Locate the file `**CA_Counties.shp**`

<img src="media\image4.png" style="" />

4.  Click `Add` to add it to your QGIS project.

<img src="media\image5.png" style="" />

5.  Counties in California should now appear:

<img src="media\image6.png" style="" />

## Exploring spatial data attributes

6.  In the `Layers` panel, right click on the layer
    `**CA_Counties_TIGER2016**`

<img src="media\image7.png" style="" />

7.  Click on `Open Attribute Table`

<img src="media\image8.png" style="" />

8.  Now you can see the attributes of each of the spatial data shown in
    the map:

<img src="media\image9.png" style="" />

1.  You can click on the headers to sort, so let’s find the most populous county in  California by scrolling to `**TOTAL_POP**` and clicking on it:

<img src="media\image10.png" style="" />

10. We can highlight the county by click on the number box with the
    number 1 next to it:

<img src="media\image11.png" style="" />

Note: Shift + Click down to select multiple rows:  
<img src="media\image12.png" style="" />

11. Return to the map to see the most populated counties according to
    the American Community Survey 2019 data in California highlighted:

<img src="media\image13.png" style="" />

12. Clear your selection in the following ways:

    1.  Clicking the deselect button in the general interface:

<img src="media\image14.png" style="" />

2.  Or the deselect button in the attribute table:

<img src="media\image15.png" style="" />

## Adding a field

Since bigger areas are most likely to have more people, we need to factor that in to see where most people in the state are likely to be found. We will do a population density calculation, which is simply
`number of people` divided by `total area.`

13. Click the `edit` tool to enable making changes:

<img src="media\image16.png" style="" />

14. Warning! When you are in `editor` mode you can click on any cell to
    directly edit it:

<img src="media\image17.png" style="" />

1.  If you accidentally made edits, turn off editing mode by clicking
    the pencil
    again:<img src="media\image18.png" style="" />

2.  Choose `Discard`:

<img src="media\image19.png" style="" />

15. Next click the `Field Calculator` button:

<img src="media\image20.png" style="" />

16. The field calculator window will appear:

<img src="media\image21.png" style="" />

17. Click on `Output field name` and type in `AREA_SQ_KM` which will
    be `Area in square kilometers`.

<img src="media\image22.png" style="" />

18. Click on field type and choose `Decimal Number (real)`

<img src="media\image23.png" style="" />

19. In the Expression box type in the following:

- `$area / 1000000`

<img src="media\image24.png" style="" />

20. If correctly done, you can see the preview will show the value:

<img src="media\image25.png" style="" />

21. Click `OK`:

<img src="media\image26.png" style="" />

22. You can see our new field all the way on the right side:

<img src="media\image27.png" style="" />

23. Open the `Field Calculator` again and create a new field called
    `POP_DENSIT` with `Decimal number (real)`:

<img src="media\image28.png" style="" />

24. Locate the search box, this place is helpful for creating
    expressions.

<img src="media\image29.png" style="" />

- In the search box type in `total_pop` and double click on the result:

<img src="media\image30.png" style="" />
 
- Note: The help on the right side explains more detail about what is
    being selected in the search box.

<!-- -->

1.  Add a `/` for divide

2.  Search for `area_sq_km` and add it to our expression:

<img src="media\image31.png" style="" />

28. The final expression should be:

`"TOTAL_POP" / "AREA_SQ_KM"`

<img src="media\image32.png" style="" />

29. Check the preview:

<img src="media\image33.png" style="" />

30. Hit OK:

<img src="media\image34.png" style="" />

31. Check to see if the `POP \ DENSIT` column is there:

<img src="media\image35.png" style="" />

32. If you have successfully calculated the population density for all
    the counties in California, then click the `save` button to save our
    edits:

<img src="media\image36.png" style="" />

33. Turn off the editing tool as we are done with it:

<img src="media\image37.png" style="" />

## Symbolizing our map

34. Right click on our layer and go to `Properties`:

<img src="media\image38.png" style="" />

35. Click on `Symbology`:

<img src="media\image39.png" style="" />

36. From there, click on `Single Symbol` to change which data fields are
    being used for map creation:

<img src="media\image40.png" style="" />

37. If we were working with qualitative data fields then we would use
    `categorized`, however we are going to be looking at our population
    density data field, so we should use `graduated`:

<img src="media\image41.png" style="" />

38. Click the dropdown arrow near `Value` to see the list of fields:

<img src="media\image42.png" style="" />

1.  Choose `POP_DENSIT`:

<img src="media\image43.png" style="" />

40. Change the `Mode` to `Equal Interval` which means that the breaks
    between values are evenly spaced apart (i.e. 0-5, 5-10,10-15):

<img src="media\image44.png" style="" />

41. You can click histogram to get a better sense of the data and which
    statistical mode you should use (but since this is not a stats
    class, I won’t spend much more time on this):

<img src="media\image45.png" style="" />

42. You can also change the number of `classes` (or breaks) by clicking
    here:

<img src="media\image46.png" style="" />

43. Click `OK` to apply our changes to the map:

44. You can change the colors by clicking on `Color ramp`:

<img src="media\image47.png" style="" />

45. Or individually by right clicking the square colored boxes:

<img src="media\image48.png" style="" />

46. Choose `change color` and adjust the color wheel:

<img src="media\image49.png" style="" />

47. When satisfied with your changes click `OK` to close the dialogue box:

<img src="media\image50.png" style="" />

48. You map should look like the following:

<img src="media\image51.png" style="" />

49. Tip: You can quickly change any color by right clicking on the colored box to the left of any layer:

<img src="media\image52.png" style="" />

## Filtering our fields

50. Let’s do some advanced filtering to see places where more than 100,000 Asians live.

51. Start by opening our attribute table again:
    -  Right click on our layer
<img src="media\image53.png" style="" />
    - Click `Open Attribute Table`:

 <img src="media\image54.png" style="" />

1.  Click the `Filter selection form`.

<img src="media\image55.png" style="" />

53. We are finding places with `Asians` so locate the `ASIAN_POP`
    field:

<img src="media\image56.png" style="" />

54. Click the `Exclude field` button to change it:

<img src="media\image57.png" style="" />

55. We will make it `Greater than or Equal to`:

<img src="media\image58.png" style="" />

56. Then type in 100000:

<img src="media\image59.png" style="" />

57. Click on `Select Features`

<img src="media\image60.png" style="" />

58. Click the lower right icon to return to the table view:

<img src="media\image61.png" style="" />

59. You can view only selected features by clicking here:

<img src="media\image62.png" style="" />

60. Then choosing `Show Selected Features`

<img src="media\image63.png" style="" />

61. Close the table when done exploring by clicking the X:

<img src="media\image64.png" style="" />

62. Congrats! Now you have filtered some features.

## Saving Our Map Layer for Web Mapping

63. With everything still selected, right click on the layer:

<img src="media\image65.png" style="" />

64. Go to `Export` and then choose `Save Selected Features As…`:
    <img src="media\image66.png" style="" />

65. The ESRI shapefile is the default, but it is very hard to use in our
    web applications because it is a proprietary data format..

<img src="media\image69.png" style="" />

66. The preferred spatial format online is a GeoJSON file:

<img src="media\image70.png" style="" />

67. Click the `…` next to `File Name` to find a nice new home for your GeoJSON file!

<img src="media\image71.png" style="" />

68. Your final box should look like this:

- Format: GeoJSON

- File name: CA_counties_with_over_100k_Asians.geojson

<img src="media\image72.png" style="" />

69.  Congratulations! You have created your first `GeoJSON` file! We will revisit this file in next week’s lab, so keep it safe and sound!

## Adding non-spatial data

70. You can also add CSV files by clicking `Layer`

<img src="media\image73.png" style="" />

71. Click on `Add Layer` `Add Delimited Text Layer...`

<img src="media\image74.png" style="" />

72. To the far right of `File Name`, click on the button with `…`:

<img src="media\image75.png" style="" />

73. Locate the file for California Asian American Hate Crimes,
    CA_AAHC_2021.csv and select it and choose `Open`:

<img src="media\image76.png" style="" />

74. Check to make sure `Point` coordinates and a coordinate reference
    system exists:

<img src="media\image77.png" style="" />

75. Click `Add` and then `Close`:

<img src="media\image78.png" style="" />

76. The data points should now show up:

<img src="media\image79.png" style="" />

77. Note that you will not be able to edit CSV files, you will need to
    export them in a spatial data type format, such as shapefile or GeoJSON to do so.

78. Congratulations on finishing the spatial data management QGIS bootcamp.

## Lab Questions

Please take some time to think about the following questions, they may be helpful when you are posting your Thinking Cap response for this week.  

1.  What changes did we make to the original data?

2.  How can the choices we made in changing the data be problematic?
