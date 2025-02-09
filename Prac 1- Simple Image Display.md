/* ACKNOWLEDGEMENT
Google Earth Engine Developers
Google Earth Engine Team
*/
/*
Please be sure you attempt this practical using the practical manual. The practical manual gives thorough explanations
to the concepts and scripts. Using the practical manual, the commands, arguments, or parameters used in the scripts will
make more sense to you.
*/
/*In this first prac, we will explore a single-band image. The goal of this task is to familiarise
ourselves with the basiic functionalities within GEE while utilisng the RS principles learnt
At the end of this prac you should be able to: 
1, bring your own data into GEE and visualise it
2, retrieve data from GEE data catalog and visualise it
3, make a single-band greyscale image colourful (i.e. create a pseudocolour image)
4, define and apply visualisation parameters 
*/

// upload an image from your computer
var prac1_img=ee.Image("users/richcrabbe/spa217_data_prac_1");

// print the prac1_img to view metadata
print(prac1_img); // be sure to click the console tab to see the metadata

// add image to interactive map. 
Map.addLayer(prac1_img); //Go to the map of Australia to find this image

/*
This is a Landsat 5 near-infrared image of Albury captured in day 309 (i.e. 5 November) of 2011.
The image has no meaningful name, so it will be difficult for other analysts to use.
To correct this, you will rename the band, set the range of DN possible DN values 
(0-255, as Landsat 5 was a 8 bit system), and display this in the interactive map.
*/

// Rename an image and load it to the interactive map
Map.addLayer(prac1_img, {min: 0, max: 255} ,'Landsat5_band_nir_20111105'); // check the name of the new layer created


/*pseudo-colour image- this is when you replace the greyscale of a single-band image with multiple colours based on the histogram of the pixel brightness values
 we do this because our eyes are more sensitive to colourful features than greyscale
to do this use the colour palette
*/

// pseudo-colour image 
Map.addLayer(prac1_img, {min: 0, max: 255, palette: ['white', 'cyan', 'red','blue', 'yellow']}, 'Landsat5_band_nir_20111105_pseudocolour');


/* In this session, load an image from the data catalog and create a pseudocolour display 
*/

// load an image from the repository. We will explore Landsat 8
var prac1_data_from_catalog=ee.Image("LANDSAT/LC08/C01/T1_SR/LC08_092085_20211203");

// print the image
print(prac1_data_from_catalog);


// let's select the NIR band (i.e., "B5") and print it to the console
var band_nir = prac1_data_from_catalog.select(["B5"]);

print (band_nir);

// add (display) the band layer to the interactive base layer
Map.addLayer(band_nir,  {bands:"B5"},'LANDSAT/LC08/C02/T1_TOA_092085_20220104_nir_band');

// create a pseudo image from the band
Map.addLayer(band_nir, {min: 0, max: 3000, palette: ['white', 'cyan', 'red','blue', 'yellow']}, 'Landsat8_band_nir_pseudocolour');


// Define the visualization parameters.
var vizParams = {
  bands: ['B5'],
  min: 0,
  max: 3000,
  palette: ['white', 'cyan', 'red','blue', 'yellow'] // you can choose your own combination
};

// Center the map and display the image.
Map.setCenter(146.904, -36.0700, 9); // Albury
var prac1_output_pseudocolourimage= Map.addLayer(band_nir, vizParams, 'pseudocolor image');

// print the final output image
print (prac1_output_pseudocolourimage);


/* export the final output image to your google drive, so you can add it to a report 
Export.image.toDrive({
  image:prac1_output_pseudocolourimage,
  folder: 'CSUHonoursProjects',
  description: 'Prac1_final_output',
  fileFormat: 'GeoTIFF',
  scale: 10
});
*/

