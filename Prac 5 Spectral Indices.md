/* ACKNOWLEDGEMENT
Google Earth Engine Developers
Google Earth Engine Team
*/
/*
Please be sure you attempt this practical using the practical manual. The practical manual gives thorough explanations
to the concepts and scripts. Using the practical manual, the commands, arguments, or parameters used in the scripts will
make more sense to you.Also, you will test your understanding of the remote sensing principles as you work through challenge tasks
and revision questions.
*/
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
/*Prac 5: Spectral Indices 
In this prac, we will compute spectral vegetation indices, including normalised difference vegetation
index (NDVI) from a Sentinel-2 BOA collection. Also you will write an NDVI function and apply it to every image 
in the collection. This means that you will compute NDVI for each image in an image collection.
Thus, at the end of this prac you should be able to:
1, compute NDVI from a single image and visualise it
2, create NDVI function and apply it to an individual image within an image collection
*/

// Define a point geometry for Albury as it is our area of interest.
/*We have two ways to do this:
a,use the UI Drawing Tools to import a point geometry and name it "point" 
b, set the point coordinates with the ee.Geometry.Point() function. We will use this approach 

*/

var point = ee.Geometry.Point([146.94,-36.08]);

// Import the Sentinel-2 BOA image collection.
var s2BOA = ee.ImageCollection('COPERNICUS/S2_SR').filter(ee.Filter.lt('CLOUDY_PIXEL_PERCENTAGE', 1));

// Get the least cloudy image in 2021.
var s2BOA_leastCloudy = ee.Image(
  s2BOA.filterBounds(point)
    .filterDate('2021-01-01', '2021-12-31')
    .sort('CLOUD_COVER')
    .first()
);
print(s2BOA_leastCloudy);

// visualise a standard false colour composite
// create a visualisation parameter to use
var visualization = {
  min: 0,
  max: 10000,
  bands: ['B8', 'B4', 'B3']
};

// set the point location of Albury and display the layer
Map.setCenter(146.94,-36.08, 8);
Map.addLayer(s2BOA_leastCloudy, visualization, 'False colour composite');

// compute the Normalised Difference Vegetation Index (NDVI).
var nir = s2BOA_leastCloudy.select('B8'); // retrieves the NIR band
var red = s2BOA_leastCloudy.select('B4'); // retrieves the RED band
var ndvi = nir.subtract(red).divide(nir.add(red)).rename('NDVI'); // computes NDVI

// visualise the single-band NDVI layer as a pseudocolour
Map.centerObject(s2BOA_leastCloudy, 9);
var ndviParams = {min: -1, max: 1, palette: ['blue', 'brown', 'green']}; // pixels with higher NDVI values will be green while blue pixels will have low NDVI values
Map.addLayer(ndvi, ndviParams, 'NDVI image');

/*Mapping a Function over a Collection
Suppose now that you want to add NDVI to every image in an image collection.
The way to do that in Earth Engine is to map() a function over the collection. 
The function defines the operations that will be applied to every element in the collection. 
*/
var addNDVI = function(image) {
  var ndvi_2 = image.normalizedDifference(['B8', 'B4']).rename('NDVI_2');
  return image.addBands(ndvi_2);
};

// Test the addNDVI function on a single image.
var ndvi_2 = addNDVI(s2BOA_leastCloudy).select('NDVI_2');

/*This code might not be as efficient for computing NDVI for a single image, but this function 
can be used as an argument to map() in order to add an NDVI band to every image in the collection. 
It's often useful to first test a function on a single image, to make sure the function is behaving as you expect. 
Once you've tested the function on an individual image and have determined that it does what you want, 
you can map it over the collection:
*/

var withNDVI = s2BOA.map(addNDVI);

/*
To verify that this is indeed putting an NDVI band in every image in this collection, 
you can add the 'withNDVI' collection to the map and query a random location with the Inspector tab. 
You should notice that each image in the collection now has a band called NDVI.
*/
