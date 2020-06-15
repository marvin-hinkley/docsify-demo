
      ---
      title: URL Rewrite
      ---

      While the built-in URL formats are great for [SEO](default.aspx?pageid=seo), we have given store administrators the ability to modify the URL structure for [product](default.aspx?pageid=manage_products), [entity](default.aspx?pageid=product_groups), and [topic](default.aspx?pageid=topics) pages on their sites. This can sometimes be necessary to integrate with 3rd party applications, and can also help store owners who have migrated to \[Company Name\] from other applications keep the URL structures they had before.

Modifying URL structures
========================

Changing your site's URL format is done through modifications to the web.config. While this is a relatively simple process, it is very important to have this file backed up before making any changes!. Also, keep in mind that if you are working on the web.config for a live site (which we do **NOT** recommend), every time the file is saved the website will restart, which can impact any customers currently on the site.   
  
To modify the URL rewrite rules, open the web.config file in a text editor and search for 'Routing Rules'. The next 30 or so lines determine how the software generates URLs for different parts of the site.   
  
The first section is labeled 'AspDotNetStorefront Default Url Patterns'. This contains all of the standard URL rules. The most important ones are as follows:

`<``add` `name``=``"Product"` `url``=``"p-{ProductID}-{SEName}.aspx"` `virtualPath``=``"~/showproduct.aspx"` `checkPhysicalUrlAccess``=``"false"` `/>`

Format generated: p-##-product-name-with-dashes-for-spaces.aspx

`<``add` `name``=``"Category"` `url``=``"c-{CategoryID}-{SEName}.aspx"` `virtualPath``=``"~/showcategory.aspx"` `checkPhysicalUrlAccess``=``"false"` `/>`

Format generated: c-##-category-name-with-dashes-for-spaces.aspx

`<``add` `name``=``"Section"` `url``=``"s-{SectionID}-{SEName}.aspx"` `virtualPath``=``"~/showsection.aspx"` `checkPhysicalUrlAccess``=``"false"` `/>`

Format generated: s-##-department-name-with-dashes-for-spaces.aspx

`<``add` `name``=``"Manufacturer"` `url``=``"m-{ManufacturerID}-{SEName}.aspx"` `virtualPath``=``"~/showmanufacturer.aspx"` `checkPhysicalUrlAccess``=``"false"` `/>`

Format generated: m-##-manufacturer-name-with-dashes-for-spaces.aspx

`<``add` `name``=``"Topic"` `url``=``"t-{Topic}.aspx"` `virtualPath``=``"~/driver.aspx"` `checkPhysicalUrlAccess``=``"false"` `/>`

Format generated: t-topic-name-with-dashes-for-spaces.aspx

There are also several commented out lines in this area that give examples of how URLs can be changed. For example, commenting out the default product line and uncommenting this line:

`<!--<add name="Product" url="product/{ProductID}/{SEName}.aspx" virtualPath="~/showproduct.aspx" checkPhysicalUrlAccess="false" />-->`

Would generate a product URL in this format:

**product/##/product-name-with-spaces.aspx**

The same kind of change can be made to category URLs by commenting out the default line and uncommenting the second sample.   
  
A few things to remember when making changes:

1.  The label for the 'type' of URL (product, category, etc) does not have to be in the URL format, but the unique identifiers (ID and SENAME) do to ensure pages are indexed properly by search engines. If either of those components are left out of the URL structure, they will be added in as a querystring (ex: ?productid=78).  
      
    
2.  **Do not remove any lines entirely!** All of the formats can be changed, but all of the URL rules that are there by default should be left in place. We **highly** recommend that instead of removing lines you don't want, you simply comment them out so they can be recovered later if desired.  
      
    
3.  The links that the software generates automatically will change whenever you make changes to these rules, however any hard-coded links you have placed on your site (in topics, skins, etc) may need adjusting after any changes you make. Be sure to test your site thoroughly after making changes.  
      
    
4.  If you wish to change the file extensions on URLs (.aspx to .html, etc), your site must be running in IIS7 with Integrated Pipeline Mode enabled. Please speak with your host to verify that. On older versions of IIS, you will have to add a handler mapping in IIS to tell it to process the extension you changed pages to use through the ASP.NET handler.
      