
      ---
      title: Advanced Product Image Display
      ---

      Installation Guide
==================

Before You Begin
----------------

Please read through the entire installation guide and make sure you understand the installation process before you begin an installation on your live site. If there are any steps of this installation process that are unclear, please contact our\[Help Desk\]to request assistance.

*   In order to safely complete this installation on a live website you need to be able to backup your site files and database, and have a plan and permission to restore them should you encounter a problem during the installation process.
*   This installation process requires a level of technical expertise.
*   Please ensure that:
    *   You have file access to the root of your website (FTP or RDC are the most common).
    *   You have SuperAdmin Access to your \[Company Name\] site.

Simple Installation
-------------------

This installation package contains a **Web** directory that contains all of the files necessary to install this package. Please note that it is always a good idea to make a backup of your website before deploying files to your website.

To install the Advanced Product Image Display, follow these directions:

1.  Connect to your \[Company Name\] site using your favorite FTP program.
2.  Upload the contents of the **App\_Code** folder from this package to the **App\_Code** folder on your website.
3.  Upload the contents of the **jscripts** folder from this package to your website's **jscripts** folder.
4.  Upload the contents of the **Skin\_X** folder to your website **App\_Themes** folder. For example: **/App\_Themes/Skin\_1/**
5.  Upload the contents of the **XmlPackages** folder from this package to your website **XmlPackages** folder.
6.  Log in to the admin console of your site, and navigate to **Products > Manage Products**.
7.  Select a product, then choose **Advanced Product Image Display** from the **Page Display** dropdown, then **Save and Close** the product editing.
8.  Navigate to the product page on the front end of your website, and add **?install=true** to the end of the URL.
    *   For example http://www.yourdomain.com/p-1-my-product.aspx?install=true
    *   Make sure to hit enter or the go button on your navigation bar (This step will create new configuration options documented below).
9.  Back in the admin console, click **Refresh Store**.
10.  Congratulations! Your installation is complete. Refresh your product page to see the Advanced Product Image Display in action. Use the options section below to configure it just the way you want.

Options:
--------

#### [Setting](default.aspx?pageid=settings): 

#### 

*   **ImageViewer.UseVariantImages:** Set this to Yes to have the product page display variant images rather than product images.

#### [Prompts](default.aspx?pageid=prompts):  

*   **ImageViewer.ViewsLabel:** The label text above the view icons.
*   **ImageViewer.ColorsLabel:** The label text above the color icons.
*   **ImageViewer.VariantsLabel:** The label text above the variant icons if you use variant images instead of product images.

Image Setup
-----------

#### Dimensions

All of the alternate views and color images need to have the same height and width dimensions.

#### Multi-Image Manager

The multi-image manager grid needs to be complete. See the examples below.

#### Good Examples:

![](./images/goodexample1.jpg)

![](./images/goodexample2.jpg)

![](./images/goodexample3.jpg)

#### Bad Example:

![](./images/badexample.jpg)

#### Default Image

It's best to put the same image in the first view slot as you put for the default image.

![](./images/defaultimage.jpg)

Variant Image Setup
-------------------

It is also possible to setup your product page to display variant images rather than product images. To do this, change the [Setting](default.aspx?pageid=settings): ImageViewer.UseVariantImages to **Yes**. Variant images do not support multiple views so they are easier to setup. Simply upload Large, Medium, and Icon images to each of your variants and each will be represented on the product page by its image.

Adding the Advanced Product Image Display to your Custom Product XmlPackage
---------------------------------------------------------------------------

The installation package for the Advanced Product Image Display comes with a product XmlPackage that already includes the feature. If you already have a custom XmlPackage that you would like to add the Advanced Product Image Display to, you can follow the instructions below to help you through this process. Please note that this process is much more advanced than the initial installation process and you may want to enlist the help of an \[Company Name\] developer if you are unfamiliar with XmlPackages.

#### Skills Required

*   XSLT
*   HTML

#### Before you get started

Please note that the image viewer and color options should only be displayed once on the product page. The Advanced Product Image Display was not designed to work with product pages that have multiple add to cart forms.  
We recommend making a copy of your original XmlPackage so you can get back to what you started with.  
  

#### Instructions

1.  Open up the XmlPackage that you would like to add the Advanced Product Image Display to.  
      
    
2.  Find the place where the product image is being displayed. There may be several places depending on the XmlPackage. It should look something link this:  
    
    `aspdnsf:LookupProductImage(ProductID, ImageFilenameOverride, SKU, 'medium', 1, $AltText)`
    
      
    
3.  Replace the code above with the following code for the main image viewer. If there are several places you can replace each of them:  
    
    `aspdnsf:XmlPackage('vortxmultiimage.xml.config', concat('productid=', ProductID))`
    
      
    That will get you the image viewer and the view images. Now we need to add the color icons to the product page. You can place the code where ever you want on your product page, but we recommend placing it just above your add to cart form.  
      
    
4.  Search for the following line of code:  
    
    `<``xsl:value-of` `select``=``"aspdnsf:AddtoCartForm(ProductID, VariantID, 1)"` `disable-output-escaping``=``"yes"``/>`
    
      
      
    
5.  Add the color icons code just above it like this: 
    
    `<``xsl:value-of` `select``=``"aspdnsf:XmlPackage('vortxmultiimage.xml.config', concat('productid=', ProductID, '&#38;widgettodisplay=coloricons' ))"` `disable-output-escaping``=``"yes"` `/>`  
    `<``xsl:value-of` `select``=``"aspdnsf:AddtoCartForm(ProductID, VariantID, 1)"` `disable-output-escaping``=``"yes"``/>`
    
6.  Test out the modified page to make sure it is working. If you see errors you may need to modify the values of the names of the parameters being passed into the Advanced Product Image Display to the names of XSLT parameters available in your custom XmlPackage.  
      
    
7.  If you need to create the [Settings](default.aspx?pageid=settings), [Prompts](default.aspx?pageid=prompts), and [Topics](default.aspx?pageid=topics) that go along with the Advanced Product Image Display, simply navigate to your product page URL and add the "?install=true" query string.
      