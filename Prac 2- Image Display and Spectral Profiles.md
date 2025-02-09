/**** Start of imports. If edited, may not auto-convert in the playground. ****/
var albury_polygon = 
    /* color: #999900 */
    /* shown: false */
    /* displayProperties: [
      {
        "type": "rectangle"
      }
    ] */
    ee.Geometry.Polygon(
        [[[146.8218914939389, -35.92194325436896],
          [146.8218914939389, -36.24047525744386],
          [147.23799867167327, -36.24047525744386],
          [147.23799867167327, -35.92194325436896]]], null, false),
    water = 
    /* color: #ffc82d */
    /* displayProperties: [
      {
        "type": "rectangle"
      }
    ] */
    ee.Feature(
        ee.Geometry.Polygon(
            [[[147.08841785940214, -36.003970569847645],
              [147.08841785940214, -36.01507938544943],
              [147.1061848119168, -36.01507938544943],
              [147.1061848119168, -36.003970569847645]]], null, false),
        {
          "surface_type": "water",
          "system:index": "0"
        }),
    urban = 
    /* color: #3ce5d6 */
    /* displayProperties: [
      {
        "type": "rectangle"
      }
    ] */
    ee.Feature(
        ee.Geometry.Polygon(
            [[[146.9257570710496, -36.089616771441776],
              [146.9257570710496, -36.09081754846549],
              [146.92722155717172, -36.09081754846549],
              [146.92722155717172, -36.089616771441776]]], null, false),
        {
          "surface_type": "urban",
          "system:index": "0"
        }),
    forest = 
    /* color: #00ff00 */
    /* displayProperties: [
      {
        "type": "rectangle"
      }
    ] */
    ee.Feature(
        ee.Geometry.Polygon(
            [[[147.17489599940853, -36.110615973160996],
              [147.17489599940853, -36.119352447755034],
              [147.18888640163024, -36.119352447755034],
              [147.18888640163024, -36.110615973160996]]], null, false),
        {
          "surface_type": "forest",
          "system:index": "0"
        }),
    cropping = 
    /* color: #009999 */
    /* displayProperties: [
      {
        "type": "rectangle"
      }
    ] */
    ee.Feature(
        ee.Geometry.Polygon(
            [[[146.84592962682498, -35.95037696139978],
              [146.84592962682498, -35.96114596112333],
              [146.8597483676697, -35.96114596112333],
              [146.8597483676697, -35.95037696139978]]], null, false),
        {
          "surface_type": "cropping",
          "system:index": "0"
        });
/***** End of imports. If edited, may not auto-convert in the playground. *****/
/* ACKNOWLEDGEMENT
Google Earth Engine Developers
Google Earth Engine Team
*/
/*
Please be sure you attempt this practical using the practical manual. The practical manual gives thorough explanations
to the concepts and scripts. Using the practical manual, the commands, arguments, or parameters used in the scripts will
make more sense to you.
*/

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
/*
Practical 2- Multispectral Image Display and Spectral Profiles
In this prac, you will further explore the Landsat 8 image used in prac 1. 
At the end of the prac you should be able to:
a, display a true colour composite
b, display a standard false colour composite
c, create spectral profiles for different surface types
*/

// use 'ee.Image' to retrieve the Landsat data from the repository
var prac2_data=ee.Image("LANDSAT/LC08/C01/T1_SR/LC08_092085_20211203");

// print the image to console
print (prac2_data);

//define a region of interest to spatially subset the image
/*
To do this, we will use the 'draw a rectangle'in the interactive base map. 
Click and draw a rectangle around 'Albury'. Re-name the geometry as 'albury-polygon' and save as feature collection
Notice that this variable is add to the 'Imports' (this is the bar just above the code editor). 
Go to 'Geometry Imports' and uncheck the feature collection.
This means that you can now call this variable. The name of the variable is 'albury_polygon'. It is a polygon with 4 vertices.
Best to follow the detailed instructions in the prac manual to complete the task
*/

// clip the image using 'albury_polygon' feature
var prac2_data_clipped_to_albury=prac2_data.clip(albury_polygon);

// print the clipped image to console. 
print (prac2_data_clipped_to_albury);

// display the true colour composite. (band 4 = red; band 3=green; and band 2=blue)
Map.setCenter(146.904, -36.0700, 10); // to zoom in to a specific coordinate
Map.addLayer(prac2_data_clipped_to_albury, {bands: ['B4', 'B3', 'B2'],min:0, max: 3000}, 'True colour image'); 

// click 'Layers' in the GUI to see the new layer created. If you add a new layer this will be updated.
// display a standard false colour image (band 5 = red; band 4=green; and band 3=blue) to enhance vegetation pixels
Map.setCenter(146.904, -36.0700, 10); // to zoom in to a specific coordinate
Map.addLayer(prac2_data_clipped_to_albury, {bands: ['B5', 'B4', 'B3'],min:0, max: 3000}, 'Standard false colour image'); 

/*
1, See if this new layer is added to 'Layers'.
2, display the other false colour composites in prac manual
*/

/*
We will now create spectral profiles for urban surface, water surface, cropping surface, and forest surface
Spectral profile means to plot the wavelengths or bands against the surface reflectance (or brightness values)
It is a pixel-based analysis, so a point geometry for a pixel can be used. Alternatively you can create a region of interest
for a homogenous surface type, compute the mean value for the whole ROI, and plot the mean values. We will use this approach. 
First create a feature for each surface type. In this case we will have four feature classes.
Second, spectrally resize the image since not all the bands are useful for this task. In this case, let's use
bands 2 to 7.

*/

/*
Choose the relevant bands and define a feature collection to use. 
This will help create the mean reflectance for each spectral band
*/

// spectral resize i.e. select the relevant bands
var spectral_resize = prac2_data_clipped_to_albury.select('B[2-7]');

// group the features into a feature collection
var surface_type_features = ee.FeatureCollection([cropping,urban,water,forest]);

// Create a line chart (i.e. spectral profile) for the surface types
var spectral_profile = ui.Chart.image.regions(
    spectral_resize, surface_type_features, ee.Reducer.mean(), 30,'surface_type')
        .setChartType('LineChart');
print(spectral_profile);

// Set chart style properties.
var moreAesthetics = {
  title: 'Spectral profiles for different surface types',
  hAxis: {title: 'Selected spectral bands',
  titleTextStyle: {italic: false, bold: true},
    gridlines: {color: 'FFFFFF'}
  },
  vAxis: {title: 'Surface reflectance',
    titleTextStyle: {italic: false, bold: true},
    gridlines: {color: 'FFFFFF'},
    //format: 'short',
    baselineColor: 'FFFFFF'
  },
  series: {
    0: {lineWidth: 3, color: 'lime', pointSize: 5}, //cropping
    1: {lineWidth: 3, color: 'purple', pointSize: 5}, // urban
    2: {lineWidth: 3, color: 'aqua', pointSize: 5}, // water
    3: {lineWidth: 3, color: 'green', pointSize: 5} // forest
  },
  chartArea: {backgroundColor: 'silver'}
};


var spectral_profile_2= ui.Chart.image.regions(
    spectral_resize, surface_type_features, ee.Reducer.mean(), 30,'surface_type')
        .setChartType('LineChart').setOptions(moreAesthetics);
print(spectral_profile_2);

/*
clip the breadcrumb by the chart in the console. This opens the chart up in a new window.
Download the chart and save it to your working folder or report.
*/
