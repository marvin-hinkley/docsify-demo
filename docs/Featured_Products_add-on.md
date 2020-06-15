
      ---
      title: Featured Products (add-on)
      ---

      Before You Begin
----------------

Please read through the entire installation guide and make sure you understand the installation process before you begin an installation on your live site. If there are any steps of this installation process that are unclear, please contact our\[Help Desk\]to request assistance.

*   You will need a basic knowledge of the following concepts:
*   You will also need admin access to your website
*   You will need FTP access to your website.

Installation
============

Follow these instructions to install your Featured Products.

Make sure you download the appropriate version of your featured products add-on. There are currently 3 different installation packages. The differences in the version numbers for the 3 packages are (9.4.0.0 and earlier), (9.4.1.0 and above non-responsive skin) and (9.4.1.0 and above responsive skin). While the 9x and above installation process is the same for all packages, the files in them are different. The 9.4.1.0 responsive skin install package does not include the featuredstyles.css file and is intentionally left out as it is not needed for that package. Also, it is based off of the Bootstrap framework.

1.  Use FTP to connect to your website.
2.  Place featured.xml.config in the XmlPackage folder of your skin.
    *   Example: {root}/App\_Templates/Skin\_X/XmlPackages/featured.xml.config.
3.  Place simpleaddtocartform.xml.config in the XmlPackage folder of your skin.
    *   Example: {root}/App\_Templates/Skin\_X/XmlPackages/simpleaddtocartform.xml.config.
4.  If your install package includes the featuredstyles.css file in it, add it to your Skin folder.
    *   Example: {root}/App\_Themes/Skin\_X/featuredstyles.css
5.  That's it! The XML Package is installed. Now let's go over how it is used.

Using the featured products package
===================================

This XML Package is very versatile. You can feature products on your home page, category page, or topic page. You can call the XML Package from a topic or the template or even another XML Package. You can list products from a category or department or manufacturer or you can specify by product ID exactly which products you would like displayed. This guide will cover featuring products from a featured category on the home page as well as displaying specific products in a category page description.  
  

Displaying products from a category on the homepage
---------------------------------------------------

1.  Login to the admin console of your website and create a featured products category if you don't already have one. Make a note of the Category ID as you create this category. Map the products that you would like to display as featured products to this category. If you do not want this category to show in your site's navigation I would recommend unpublishing this category once you've finished mapping products.
2.  Navigate to your topic editing screen and make a backup of the home page topic (usually called "hometopintro"). Make a backup by putting the editor into HTML mode (hit the <> button) and copying all of the HTML out of the topic into a text file on your computer. This way you can restore your home page if anything goes wrong.
3.  With the editor in HTML mode, add the following XML Package token to your home page topic where you would like to display your featured products.  
    
    `(!XMLPackage Name="featured.xml.config" featuredentityid="REPLACEME" featuredentitytype="category" headertext="Featured Products" numberofitems="4" columns="4" showprice="true" !)`
    
4.  Replace the REPLACEME text with the Category ID of the category that you created in step 1 for the featuredentityid parameter.
5.  Enter the number of items and the number of columns you would like them to display in.
6.  Save the home page topic.
7.  Have a look at your home page to see your featured products. See all the configuration options in the Configuration Settings section.

Displaying specific products on a category page description
-----------------------------------------------------------

1.  Gather a list of products that you would like to display, and make note of their product IDs.
2.  Navigate to the category editing screen and open up the description tab.
3.  Make sure that the HTML Editor is in HTML mode (hit the <> button).
4.  If you have a complicated HTML description I recommend making a backup of the HTML that's in there by copying and pasting the HTML into a text file on your computer.
5.  With the editor in HTML mode, add the following XML Package token to your category description where you would like to display your featured products.  
    
    `(!XMLPackage Name="featured.xml.config" usecommadelimitedproductlist="true" commadelimitedproductlist="1,2,3,4" headertext="Featured Products" numberofitems="4" columns="4" showprice="true" !)`
    
6.  Modify the commadelimitedproductlist parameter to include the product IDs of the products you would like to feature.
7.  Save the category description.
8.  That's it, you're done. Have a look at the category description on the front end of your website.

Configuration
=============

Configuration Option

Description

Default

featuredentityid

This is the entityid of your featured products entity. For example "33". This parameter is required unless you use the comma delimited product list.

N/A

featuredentitytype

The type of entity to use. Example: "category" or "section" or "manufacturer".

category

usecommadelimitedproductlist

Whether or not to use the comma delimited product list. If this is set to true featuredentity settings are ignored. Accepted values are "true" or "false".

false

commadelimitedproductlist

The specific products you want to feature. These override the entity products. You can't do both. For Example "1,2,3,4,5"

N/A

headertext

The text that shows up in the header.

Featured Products

numberofitems

This is the number of items to show

4

columns

This is the number of columns in the featured products grid.

4

showprice

Can be true or false. Determines whether the product's price is shown.

false

showcartform

Determines whether the add to cart form is shown. If shown, the quantity text field, add to cart button and add to wish list button will display. The wish list button will not display if the appconfig parameter ShowWishButtons is set to false. If a products inventory is zero, the cart form will not display for that item. Also, if the product is a kit, pack or has colors or sizes, a Details button will display instead taking the user to the product page. Accepted values are "true" or "false".

false

randomorder

Whether or not to randomize the order of products. "true" or "false"

false

mininventorylevel

If you would like to show only featured products that have and inventory of 10 or more you could set this value to 10.

1

**NOTE: mininventorylevel - The software will not display any product with a variant inventory less than -1 regardless of the value set in this parameter.**
============================================================================================================================================================

Appendix
========

Calling the Featured Products xmlpackage from the template in version 9x
------------------------------------------------------------------------

Copy the example code below and replace the "REPLACEME" text with the value you want to specify for the featuredentityid parameter.  
  

`<asp:Literal ID="FeaturedProducts" runat="server" Text='<%$ Tokens``:``XMLPACKAGE``,` `featured.xml.config``,` `featuredentityid``=``REPLACEME``&``featuredentitytype``=``category``&``headertext``=``Featured Products``&``numberofitems``=``4``&``columns``=``4``&``showprice``=``true %>' />`

  
  

Calling the featured products package from another Xml Package
--------------------------------------------------------------

Copy the example code below and replace the "REPLACEME" text with the value you want to specify for the featuredentityid parameter.  
  

`<``**xsl:value-of**` `select``=``"aspdnsf:XmlPackage('featured.xml.config', 'featuredid=REPLACEME&featuredentitytype=category&headertext=Featured Products&numberofitems=4&columns=4')"` `disable-output-escaping``=``"yes"` `/>`

Support
=======

If you have further questions or comments, please feel free to contact [our help desk](https://support.aspdotnetstorefront.com/index.php?_m=tickets&departmentid=27&_a=submit&step=1).
      