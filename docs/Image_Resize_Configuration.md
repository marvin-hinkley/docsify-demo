
      ---
      title: Image Resize Configuration
      ---

      The Image Resize features involve several Settings, all in the IMAGERESIZE setting group. Those Settings are:  
  

UseImageResize

CategoryImg\_icon

CategoryImg\_medium

CategoryImg\_large

DistributorImg\_icon

DistributorImg\_medium

DistributorImg\_large

ManufacturerImg\_icon

ManufacturerImg\_medium

ManufacturerImg\_large

ProductImg\_icon

ProductImg\_medium

ProductImg\_large

ProductImg\_swatch

SectionImg\_icon

SectionImg\_medium

SectionImg\_large

VariantImg\_icon

VariantImg\_medium

VariantImg\_large

DefaultWidth\_icon

DefaultHeight\_icon

DefaultWidth\_medium

DefaultHeight\_medium

DefaultWidth\_large

DefaultHeight\_large

DefaultQuality

DefaultStretch

DefaultCrop

DefaultCropHorizontal

DefaultCropVertical

DefaultFillColor

LargeCreatesOthers

LargeOverwritesOthers

UseImagesForMultiNav  

MultiMakesMicros

MicroStyle

UseRolloverForMultiNav  

  

**The “DefaultXXXX” Settings**
==============================

These Settings are the defaults for all of the resizing functions. If a value is not set for one of the other specific Settings, these default values are used. These should never be left blank, but they can be changed if the majority of your images are going to need different default values. These values are explained in more detail later for specific Settings.  
  

**Setting Name**

**Default Value**

DefaultWidth\_icon

Default icon width (150)

DefaultHeight\_icon

Default icon height (150)

DefaultWidth\_medium

Default medium width (250)

DefaultHeight\_medium

Default medium height (250)

DefaultWidth\_large

Default large width (500)

DefaultHeight\_large

Default large height (500)

DefaultQuality

Default quality (100)

DefaultStretch

Default stretch (true)

DefaultCrop

Default crop (true)

DefaultCropHorizontal

Default crop horizontal (center)

DefaultCropVertical

Default crop vertical (middle)

DefaultFillColor

Default fill color (#FFFFFF)

**The Sizing Settings (icon and medium)** 
==========================================

All of the sizing “\_icon” and “\_medium” Settings can control some, all, or none of the following properties of the icon/medium images:

*   width – a number representing the width (in pixels) 
*   height – a number representing the height (in pixels) 
*   quality – a number from 1 to 100 representing the percentage of the original quality to retain in the resized image 
*   resize – this value will override the value in the UseImageResize Setting. If you have a specific image group you don’t want resizing, add resize:false to its Setting to disable it for that group (true/false) 
*   crop – this value will override the value in the DefaultCrop Setting. If you have a specific image group you don’t want cropped, add crop:false to its Setting to disable it for that group (true/false) 
*   cropv – this will override the value in the DefaultCropVertical Setting(top/bottom/middle) 
*   croph – this will override the value in the DefaultFill Setting (left/right/center) 
*   fill – this will override the value in the DefaultFill Setting (any 6-digit hex color value with a preceding “#” - #00FF00, etc) 
*   stretch – determines whether an image will stretch to fill the resized width and height specified (true/false – see below for example)  
     ![](images/1415979820141.png)  
      
      
    

Example values:

*   CategoryImg\_icon – width:150;height:150;crop:false;quality:100; 
*   CategoryImg\_medium – crop:true;width:250;croph:left;height:250;quality:80; 
*   ProductImg\_icon – resize:false; 
*   ProductImg\_medium – quality:100;height:250;stretch:true;width250;

**The Sizing Settings (large)** 
================================

The “\_large” Settings have all of the same properties as the “\_small” and “\_medium” Settings, along with 2 additional properties (more on what these do later):

*   largecreates – overrides whatever value is in the LargeCreatesOthers Setting (true/false) 
*   largeoverwrites – overrides whatever value is in the LargeOverwritesOthers Setting (true/false)

Example Values:

*   CategoryImg\_large – width:500;height:100;largecreates:true;largeoverwrites:false; 
*   ProductImg\_large – crop:true;croph:center;quality:100;width:500;height:100; 
*   ManufacturerImg\_large – resize:false;

  
**

AutoOthers Settings
===================

**

*   LargeCreatesOthers 
*   LargeOverwritesOthers 

  
These 2 Settings control the creation of icon and medium images when a large image is uploaded. If LargeCreatesOthers is set to Yes, then icon and medium images will be created according to the respective “\_icon” and “\_medium” Settings. If LargeOverwritesOthers is set to Yes, or the attribute largeoverwrites:true is specified for a particular large image group, then even if an icon or medium image already exist, they will be over-written with the images created when the large image is uploaded. If this is set to true and you are uploading in the [multi-image manager](default.aspx?pageid=multi_image_manager), the medium multi images and the icon multi images will also be created. If LargeOverwritesOthers is set to No or the attribute largeoverwrites:false is specified, then medium and icon images will only be created if medium and icon images do not already exist.   
  
  

**Additional Resizing Settings**
================================

These additional Settings will add some time saving functionality and some user-friendly features to the store front-end.   
  
MultiMakesMicros – if set to Yes, the micro images are created for images uploaded into the first row (no-color) of the medium multi image manager. These micros are created according to the width and height specified in the MicroStyle Setting and are stored in the newly created /images/product/micros directory. These micro images can then be used instead of the number icons when viewing a product through use of the UseImagesForMultiNav Setting (Yes/No). Even if MultiMakesMicros is set to No, deleting a medium multi-image will result in the micro image related to it being deleted as well.   
  
UseImagesForMultiNav – if set to Yes, micro images will replace the number icons on the product detail page for products with multiple images. If a micro image does not exist then the “no picture” image will be shown sized on the fly to match the width and height specified in MicroStyle (Yes/No).   
  
UseRolloverForMultiNav – if set to Yes then on a product page with multiple images, the images will change on rollover rather than on click (Yes/No)   
  
MicroStyle – width and height parameters to use for creating the micro images if MultiMakesMicros is set to Yes. MicroStyle can also have the “cols,” “colspacing,” and “rowspacing” attributes that specify the number of micros in a row, the spacing between each image in the row, and the spacing between each row. (width:40;height:40;cols:4;colspacing:10;rowspacing:10;)  
  
 ![](images/1415980225607.png)
      