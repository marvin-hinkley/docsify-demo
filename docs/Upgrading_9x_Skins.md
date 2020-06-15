
      ---
      title: Upgrading 9x Skins
      ---

      This page would welcome a sponsor from the \[Company Name\] community.

General Considerations
======================

*   If you are upgrading to a 9400+ version, be aware that the MaxMenuLevel AppConfig is utilized differently in the new skins and may need to be increased for proper display in skins older than the 9400 skin (MaxMenuLevel is "0" by default in 9400+).

Moving from Versions between 9.0.1.3 and 9.3.1.1 and keeping your old skin
==========================================================================

*   Copy the file base.css from the new version's /App\_Themes/Skin\_1 folder to your /App\_Themes/Skin\_# containing your retained skin, as it contains necessary styles for the \[Current Version\] components.
*   Copy the folder /App\_Themes/Skin\_1/images from the new version to your /App\_Themes/Skin\_#/images folder containing your retained skin, but DO NOT OVERWRITE any files, just merge any new images that did not exist before in your old skin.
*   Other adjustments to the skin may be necessary. In particular, check your site to see if text like ( !BUYSAFEJSURL! ) or ( !BUYSAFESEAL! ) displays. Those strings come from old skin tokens that were removed in 9.1.0.0. If those display on your site, you'll need to edit the template.master file and remove references to the token
*   Copy the folder /Web/XmlPackages from the new version to your cloned site, overwriting all existing xml packages. If you have customized xml packages you wish to use, you will need to merge your changes with the appropriate new xml package versions. We highly recommend having a [knowledgeable developer](http://www.aspdotnetstorefront.com/c-270-development-partners.aspx) perform the modifications.
*   If you are using the [Smart One Page Checkout (SOPC)](http://manual.aspdotnetstorefront.com/p-1685-smart-one-page-checkout-instructions-for-multistore-9400.aspx), add this jQuery reference to the head of your template.master file :  
      
    
    `<%-- jQuery is required` `in` `versions 9.4 and higher --%>`
    
    `<script src=``"jscripts/jquery.min.js"` `type=``"text/javascript"``></script>`
    
    `<script type=``"text/javascript"``>`
    
    `adnsf$ = jQuery; <%-- to avoid conflicts` `with` `existing jQuery versions and other javascript frameworks, change` `this` `line to adnsf$ = jQuery.noConflict(); --%>`
    
    `</script>`
    
*   If you are using Google Remarketing, be sure to include the code from your live site template.master file. See [these instructions](default.aspx?pageid=google_remarketing) for more information.

Moving from version 9.4.0.0 and keeping your old skin
=====================================================

*   Copy the file base.css from the new version's /App\_Themes/Skin\_1 folder to your /App\_Themes/Skin\_# containing your 9.4.0.0 skin, as it contains necessary styles for the 9.4.1.0 components.
*   Copy the folder /App\_Themes/Skin\_1/images from the new version to your /App\_Themes/Skin\_#/images folder containing your 9.4.0.0 skin, but DO NOT OVERWRITE any files, just merge any new images that did not exist in your 9.4.0.0 skin.
*   Copy the folder /Web/XmlPackages from the new version to your cloned site, overwriting all existing XML packages. If you have customized XML packages you wish to use, you will need to merge your changes with the matching new XML package files. We highly recommend having a [knowledgeable developer](http://www.aspdotnetstorefront.com/c-270-development-partners.aspx) perform the modifications.

Moving from version 9.4.1.0 and keeping your old skin
=====================================================

*   If your old skin has a base.css file, you'll want to merge in changes from the newest version of that file.

For Customers with Customization
================================

The difficulty in moving customization varies from build to build. If you have customized code in the web folder, it MAY be possible just to copy over the files that you made modifications to. The further you are between builds, the more likely it is that this will not work however. Make sure you test thoroughly.  
  
If you have made changes to any of the compiled assemblies you must reapply those customizations and recompile in the new source files. The most efficient way to handle this in the future is to either add your code to custom classes or make sure you comment every single change with an easily searchable, highly descriptive comment. This will be invaluable if you have to change developers or wait months (or years) between upgrades.  
  
XML package customizations also vary in difficulty. There is a good chance that your recent XML packages will transfer between similar versions with little or no issues. If you do run into errors, most of the time it is simply due to parameters being changed that an extension function is expecting. Simply copying the specific call to the extension function from a new XML package will often resolve any of these issues. If there are significant changes, it may be easier just to apply your modifications to a new XML package.  
  
NOTE: [A developer's guide](default.aspx?pageid=upgrading_a_customized_store) has been created to assist with upgrading customized sites.  

Menus
=====

Starting in 9.5.0.0, a couple of the older ways of generating vertical menus in skins (namely asp:Menu controls and the EntityControl control) no longer work.  Upgraded skins that used one of those menus will need to replace them.  The recommended approach now is the using the XMLPackage skin token with the entitymenu.xml.config package.  As an example, the new 'out of the box' skins generate the vertical navigation with a topic called Template.VerticalNavigation that has multiple instances of that token:  
  

`<``div` `class``=``"nav-wrapper"``>`

`<``h6` `class``=``"bar"``>`

`(!stringresource name="appconfig.categorypromptplural"!)`

`</``h6``>`

`(!xmlpackage name="entitymenu.xml.config" entitytype="category" !)`

`</``div``>`

`<``div` `class``=``"nav-wrapper"``>`

`<``h6` `class``=``"bar"``>`

`(!stringresource name="appconfig.sectionpromptplural"!)`

`</``h6``>`

`(!xmlpackage name="entitymenu.xml.config" entitytype="section" !)`

`</``div``>`

`<``div` `class``=``"nav-wrapper"``>`

`<``h6` `class``=``"bar"``>`

`(!stringresource name="appconfig.manufacturerpromptplural"!)`

`</``h6``>`

`(!xmlpackage name="entitymenu.xml.config" entitytype="manufacturer" !)`

`</``div``>`

  

Troubleshooting Tips
====================

Please keep in mind that AspDotNetStorefront has many different versions, and some versions are very difficult to upgrade from (particularly versions prior to 6.1) while others are fairly simple. Our support Help Desk can provide you with troubleshooting tips and advice (be sure you have subscribed to [Year-Round Benefits](http://www.aspdotnetstorefront.com/p-917-year-round-benefits.aspx) before contacting the Help Desk), but it is not unlimited. If you are not comfortable performing some troubleshooting you should [contact us](mailto:sales@aspdotnetstorefront.com) to get a referral for someone that can help.  
  
Many of the common errors you will run into during an upgrade will be logged in our knowledge base already. Make sure you take a look in this manual for applicable entries to speed your installation process.
      