/**** Start of imports. If edited, may not auto-convert in the playground. ****/
var cropping = 
    /* color: #d63000 */
    /* shown: false */
    /* displayProperties: [
      {
        "type": "rectangle"
      }
    ] */
    ee.Feature(
        ee.Geometry.Polygon(
            [[[145.8276330011747, -35.489857499262214],
              [145.8276330011747, -35.573117127452],
              [145.94195947822547, -35.573117127452],
              [145.94195947822547, -35.489857499262214]]], null, false),
        {
          "surface_type": "cropping",
          "system:index": "0"
        }),
    water = 
    /* color: #98ff00 */
    /* shown: false */
    /* displayProperties: [
      {
        "type": "rectangle"
      }
    ] */
    ee.Feature(
        ee.Geometry.Polygon(
            [[[147.1311453555224, -36.018990228670575],
              [147.1311453555224, -36.04467209360513],
              [147.15595042449212, -36.04467209360513],
              [147.15595042449212, -36.018990228670575]]], null, false),
        {
          "surface_type": "water",
          "system:index": "0"
        }),
    urban = 
    /* color: #0b4a8b */
    /* shown: false */
    /* displayProperties: [
      {
        "type": "rectangle"
      }
    ] */
    ee.Feature(
        ee.Geometry.Polygon(
            [[[146.94405726612783, -36.06397057502037],
              [146.94405726612783, -36.06670244836888],
              [146.94717935742116, -36.06670244836888],
              [146.94717935742116, -36.06397057502037]]], null, false),
        {
          "surface_type": "urban",
          "system:index": "0"
        }),
    forest = 
    /* color: #ffc82d */
    /* shown: false */
    /* displayProperties: [
      {
        "type": "rectangle"
      }
    ] */
    ee.Feature(
        ee.Geometry.Polygon(
            [[[146.637326742355, -36.14946876091917],
              [146.637326742355, -36.169842265836756],
              [146.66565086955225, -36.169842265836756],
              [146.66565086955225, -36.14946876091917]]], null, false),
        {
          "surface_type": "forest",
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
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
/*
Practical 3- Basic image Statistics:
In Prac 2 we computed mean spectral values to generate a spectral profile for different
surface types. In this prac, we will build on the prac 2 by computing other statistics,
including min, max, median, standard deviation, and correlation.In GEE, reducers are used to compute
these statistics. Also, you will explore stacked images.
At the end of this prac, you should be able to compute and interpret band statistics for a single image and 
time series images (image collection)
*/

/*
 1, Compute statistics of a multiband image using 'image.reduce()' function
*/

// load the Landsat data used in previous pracs and select the first seven bands
var prac3_data = ee.Image("LANDSAT/LC08/C01/T1_SR/LC08_092085_20211203")
    .select ('B[1-7]');

// Now display the metadata of the image for more details
print('All metadata:', prac3_data);

// add a true colour composite of the image to the base layer
Map.addLayer(prac3_data, {bands: ['B4', 'B3', 'B2'],min:0, max: 3000}, 'True colour image'); 

/*
compute stats over the whole image using 'image.reduce()'
*/
// compute the maximum reflectance 
var data_meanValue= prac3_data.reduce(ee.Reducer.mean());

// display the result
Map.centerObject(data_meanValue, 7);
Map.addLayer(data_meanValue,  {max:6000},'Mean value');


// Compute the mean and standard deviation stats at the same time Use the 'combine ()' command.
var mean_plus_sd = ee.Reducer.mean().combine({
  reducer2: ee.Reducer.stdDev(),
  sharedInputs: true
});

// Use the combined reducer to get the mean and SD of the image.
var stats = prac3_data.reduceRegion({
  reducer: mean_plus_sd,
  bestEffort: true,
});

// Display the dictionary of band means and SDs.
print(stats);


// Stats for regions of interest
/*
Statistics for a region of interest; use image.reduceRegion().This reduces all the pixels 
in the region(s) to a statistic or other compact representation of the pixel data 
in the region (e.g. histogram).
*/

/*
We will create a feature collection. A feature collection is a vector data type in GEE in that it contains a
number of geometry data, including points,lines and polygons. Through the geometry data we can compute statistics 
for a region of interest (and not necessarily the whole image). Follow prac manual to create the feature collection.
*/

// create a feature collection from the features created for surface types
var feature_collection = ee.FeatureCollection([cropping,urban,water,forest]);

// display a feature collection
Map.addLayer(feature_collection, {}, 'default display'); // default display
Map.addLayer(feature_collection, {color: 'FF0000'}, 'user defined');  // customised

// compute mean value for each ROI. Print the result to a dictionary.
var meanDictionary = prac3_data.reduceRegion({
  reducer: ee.Reducer.mean(),//The statistic or reducer (in GEE parlance) to compute
  geometry: forest.geometry(), //The region over which to reduce data
  scale: 30, // A nominal scale in meters of the projection to work in.
  maxPixels: 1e9, // maximum number of pixels to reduce
  bestEffort: true // If the polygon would contain too many pixels at the given scale, compute and use a larger scale which would allow the operation to succeed.
});

// Export the table as a csv file to my google drive
//Export.table.toDrive({
//  collection: feature_collection,
//  description: 'SPA217_Prac3_Mean_Stat',
//  folder: 'CSUHonoursProjects',
//  fileFormat: 'CSV'
//});


// print the output
print(meanDictionary);


// Statistic of image regions
/*
To get image statistics in multiple regions stored in a FeatureCollection, you can use image use
reduceRegions() to reduce multiple regions at once. The input to reduceRegions() is an Image and a FeatureCollection. 
The output is another FeatureCollection with the reduceRegions() output set as properties on each Feature. 
*/
// Add reducer output to the features in the collection.
var meansFeatures = prac3_data.reduceRegions({
  collection: feature_collection,
  reducer: ee.Reducer.mean(),
  scale: 30,
});

// Print the first feature, to illustrate the result.
print(ee.Feature(meansFeatures.first()).select(prac3_data.bandNames()));

//Image Collection

/*
We can also apply stats to an image collection. Image collection is a stack of images; for example, a time series image 
where you have multiple images collected between two dates. While in ee.Image you compute stats over individual bands, 
the ee.ImageCollection has an image as the input.
*/

// ImageCollection Reductions
/*
To reduce (i.e. compute a stat) an ImageCollection, use imageCollection.reduce(). This reduces the collection of images to an individual image
Specifically, the output is computed pixel-wise, such that each pixel in the output is composed of the statistic
of all the images in the collection at that location.
/*

/*
compute the mean of an image collection
*/

// load an image collection data(Landsat 8 collection 1 tier 1), filter using dacquisition date,
//and path and row ID to reduce the file size
var collection = ee.ImageCollection("LANDSAT/LC08/C01/T1")
  .filterDate('2020-11-01', '2022-03-31')
  .filter(ee.Filter.eq('WRS_PATH', 92))
  .filter(ee.Filter.eq('WRS_ROW', 85))
  .select('B[1-7]');

print (collection);
// Compute the median in each band, each pixel.
// Band names are B1_median, B2_median, etc.
var median = collection.reduce(ee.Reducer.median());

print(median); // to view the output in the console

// The output is an Image.  Add it to the map.
var vis_param = {bands: ['B5_median', 'B4_median', 'B3_median'], gamma: 1.2};

//Map.setCenter(146.904, -36.0700,  9);
Map.addLayer(median, vis_param, 'median_stat_imageCollection');



