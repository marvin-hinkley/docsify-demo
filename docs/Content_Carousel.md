
      ---
      title: Content Carousel
      ---

      Introduction
============

The content carousel consists of JPG images and some code, done with javascript, which creates the fading from one image to the next. Below are instructions on how to install the necessary code and creating the topic so that the content carousel will work. These instructions assume some basic information, so references to file names and lines of code may not be accurately described, but should be close enough to follow. These instructions also assumes some knowledge of things like basic HTML structure and uploading files via FTP to a website hosting server.

Before You Begin
----------------

Please read through the entire installation guide and make sure you understand the installation process before you begin an installation on your live site. If there are any steps of this installation process that are unclear, please contact our\[Help Desk\]to request assistance.

Installation
============

### Step 1: Images (Slides)

Images that make up the "slides" for the content carousel can be named what you would like and then simply be uploaded via FTP. The content carousel "container" is specifically designed to have images all the same dimensions. For best results when creating new images, please be sure the new images are exactly the same size as each other. For the sake of these instructions, we'll assume that there are 3 slides in the content carousel. The file names of these slides may be; "slide1.jpg", "slide2.jpg" and "slide3.jpg". File name is case sensitive, so "slide1.jpg" is not the same as "Slide1.jpg" or "slide1.jpg", so be careful what the new files are named.

Now that you have some information about carousel slides, upload your images to your skin's "images" folder.

### Step 2: JavaScript File

Copy the included ContentCarousel.js file to the "js" folder that contains your skin level javascript files within the appropriate skin folder. If your skin does not have a "js" folder, you will need to create one.

### Step 3: Topic Code

The following is the most basic code necessary to create the content carousel. The code in this section contains images that are referencing the carousel images that were uploaded via step 1.

To get an idea of how to add controls and customize your content carousel, double-click the index.html file found in the "Documentation" folder of the installation files. The div container id shown as "FaderContainer" below must match the id name and the parameter value in the content carousel initiation code shown in step 4. The names that must match are highlighted in green. You can leave this id as-is or rename it as long as it is updated in all of the locations that are highlighted.

#### ASPDOTNETSTOREFRONT TOPIC CODE

`<div` `id``="FaderContainer"``>` `<div>` `<img` `src``=``"app_themes/Skin_(!SKINID!)/images/slide1.jpg"` `alt``=``"slide1"``/>` `</div>` `<div>` `<img` `src``=``"app_themes/Skin_(!SKINID!)/images/slide2.jpg"` `alt``=``"slide2"``/>` `</div>` `<div>` `<img` `src``=``"app_themes/Skin_(!SKINID!)/images/slide3.jpg"` `alt``=``"slide3"``/>` `</div>` `</div>` `<div` `class``=``"cleared"``></div>`

#### YOU MAY ALSO HAVE THESE CONTENT CAROUSEL SLIDES LINK TO OTHER PAGES

Add <a> tags around the images to have them link to other pages. Example:

`<div` `id``=``"FaderContainer"``> <div> <a href="link1.aspx"> <img src="app_themes/Skin_(!SKINID!)/images/slide1.jpg" alt="slide1"/> </a> </div> <div> <a href="link2.aspx"> <img src="app_themes/Skin_(!SKINID!)/images/slide2.jpg" alt="slide2"/> </a> </div> <div> <a href="link3.aspx"> <img src="app_themes/Skin_(!SKINID!)/images/slide3.jpg" alt="slide3"/> </a> </div> </div> <div class="cleared"></div>`

This code is typically put into a unique topic (usually named "contentCarousel"). Then add a token where you'd like the content carousel to display: (For example, placing this token code in the topic "hometopintro" will place the content carousel on the site's homepage.)

`(!Topic Name="contentCarousel"!)`

### Step 4: Template Code

#### TEMPLATE.MASTER CODE

Copy the code below and place it between the opening <head> tag and the closing </head> tag on your skin's template.master file which is located here {Root}/App\_Templates/Skin\_X/template.master. This will add the necessary reference to the ContentCarousel.js file. If the code below is left as-is, it will look for the ContentCarousel.js file in {Root}/App\_Templates/Skin\_X/js/ContentCarousel.js

`<script type=``"text/javascript"` `src=``"App_Templates/Skin_<asp:Literal runat='server' Text='<%$Tokens:SkinId %>'/>/js/ContentCarousel.js"``></script>`

Copy the code below and place it in the same file as referenced above, but add it just above the closing </body> tag. This will initiate the Content Carousel.

Timing of the slides can be adjusted within the "fader.setDisplayTime" variable. 4000 is equal to 4 seconds. The amount of time it takes to fade from one slide to another can be adjusted within the "fader.setFadeTime" variable. 750 is equal to three fourths of a second (1000 is equal to 1 second). You can see where to change these variables in the code block below. This is a reminder that the names highlighted in green below must match the id on the content carousel's container div shown in step 3.

`<script type=``"text/javascript"``>` `if` `(document.getElementById(``'FaderContainer'``) != null) {` `var` `fader =` `new` `ContentCarousel(``"FaderContainer"``); fader.setDisplayTime(``4000``); fader.setFadeTime(``750``); fader.start(); } </script>`

Final Notes
===========

Once each part of the code is added to the appropriate site files, load the site in a browser and the content carousel slides should load, one at a time and fade from one to the next and then loop.
      