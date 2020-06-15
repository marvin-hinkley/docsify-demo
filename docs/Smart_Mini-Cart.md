
      ---
      title: Smart Mini-Cart
      ---

      Introduction
============

Thank you for your purchase of the Vortx Mini-Cart for AspDotNetStorefront. This guide will take you through the process of installing the Mini-Cart on AspDotNetStorefront. The process will include:

1\. Run SQL  
2\. Merge source  
3\. Test Mini-Cart  
4\. Merge animation  
5\. Configuration

Before You Begin
----------------

This installation process requires a level of technical expertise. Please read through the entire installation guide and make sure you understand the installation process before you begin an installation on your live site. If there are any steps of this installation process that are unclear, please contact the\[Help Desk\]to request assistance before making the installation attempt.  
In order to safely complete this installation on a live website you need to be able to backup your site files and database, and have a plan and permission to restore them should you encounter a problem during the installation process. Different hosting providers and environments will have different methods of backing up and restoring databases. Please work with your hosting company to discuss the backup and restore tools that are available to you.  
  
Before you begin please ensure that:

• You have file access to the root of your website (FTP or RDC are the most common).  
• You have Super Admin Access to your AspDotNetStorefront site.  
• You have the ability to use a text editor to modify an existing Xml Package.  
• You have basic knowledge of HTML and CSS.

Installation
============

Throughout this installation guide, the Mini-Cart deployment package will be referred to as **source** folders and files. The website files and folders will be referred to as the **target** files and folders.  
  
**Run SQL  
  
**This procedure will install the new MiniCart settings (AppConfigs) and prompts (String Resources).

1\. Log in to the admin console of your website.  
2\. Navigate to Configuration > Advanced > Run SQL.  
3\. In source files, navigate to the Schema/VortxMiniCart.sql file and open it in your text editor. Copy the text from VortxMiniCart.sql and paste it into the textbox on the Run SQL admin screen. Click Submit.  
4\. Close the text editor and click the Reset Cache button in the admin console.

**Merge Source**  
  
Using your FTP program, open the Source(Web)/App\_Themes/Skin\_1 folder that is found in the source files on your desktop. Connect to your site files over FTP, and navigate to the App\_Themes/Skin\_{your skinID} folder of the target site.  

1\. From the source (install) files, move the following files to the target site:

a. Move the Source(Web)/App\_Themes/Skin\_1/CustomImages folder to the App\_Themes/Skin\_{your skinID} folder on your website.  
  
b. Move the Source(Web)/App\_Themes/Skin\_1/js folder to the App\_Themes/Skin\_{your skinID} folder on the target site.  
  
c. Move the Source(Web)/App\_Themes/Skin\_1/MiniCart-style.css file to the App\_Themes/Skin\_{your skinID} folder on the target site.  
  
d. Move the contents of the Source(Web)/App\_Templates/Skin\_1/XmlPackages folder to the App\_Templates/Skin\_{your skinID} /XmlPackages folder on the target site.  
  
e. Move Source(Web)/App\_Templates/Skin\_1/deletefromcart.aspx and deletefromcart.aspx.cs to the App\_Templates/Skin\_{your skinID} folder on the target site.

f. App\_Code/ASPDNSFHandlers.cs

Pull a copy of the App\_Code/ASPDNSFHandlers.cs file down from the target site.  
Open the copy of App\_Code/ASPDNSFHandlers.cs that you pulled down from the live site and locate the following lines of code:

`public` `void` `ProcessRequest(HttpContext context) {` `string` `pn = XMLPackage; Customer ThisCustomer = ((AspDotNetStorefrontPrincipal)context.User).ThisCustomer;` `try` `{`

  
Paste the code from the deployment package(Source/App\_Code/ASPDNSFHandlers.cs) into the copy of the target site's App\_Code/ASPDNSFHandlers.cs. This code goes in the _second_ ProcessRequest method in that file, within the 'try' statement, before 'using'. It should look like this:

`public` `void` `ProcessRequest(HttpContext context) {` `string` `pn = XMLPackage; Customer ThisCustomer = ((AspDotNetStorefrontPrincipal)context.User).ThisCustomer;` `try` `{` `#region Vortx - MiniCart SkinId Fix` `int` `StoreID = AppLogic.StoreID();` `int` `SkinID = AppLogic.GetStoreSkinID(StoreID);` `if` `(CommonLogic.IsInteger(HttpContext.Current.Profile.GetPropertyValue(``"SkinID"``).ToString())) {` `int` `skinFromProfile =` `int``.Parse(HttpContext.Current.Profile.GetPropertyValue(``"SkinID"``).ToString());` `if` `(skinFromProfile >` `0``) { SkinID = skinFromProfile; } }` `if` `(CommonLogic.QueryStringUSInt(``"skinid"``) > 0) { SkinID = CommonLogic.QueryStringUSInt(``"skinid"``); } ThisCustomer.SkinID = SkinID;` `#endregion`

  
upload the modified file up to the target site overwriting the existing file.

2\. Download a copy of the template.master file from the target App\_Templates/Skin\_{your skinID} folder to your local computer. Keep one file as a backup, and modify the other, this will be uploaded to the target site when the steps below are complete.  
  
3\. Open both the MiniCart-template.master and the template.master just downloaded in your text editor for merging.  
  
4\. Copy the Mini-Cart JavaScript reference code from MiniCart-template.master and add it to the <head> section of the template.master file below your jQuery reference.  
  

`<script type=``"text/javascript"` `language=``"javascript"` `src=``"App_Themes/Skin_{your skinID}/js/newminicart.js"``></script>`

5\. There are two options for placing the Mini-Cart on your website.

a. You can copy the Mini-Cart Xml Package reference from the source MiniCart-template.master file and add it to the template.master file where you want the Mini-Cart to display on the page. Position the Mini-Cart using HTML and CSS.

`<asp:Literal ID="litMiniCart" runat="server" Text='<%$ Tokens:XmlPackage, minicartdriver.xml.config %>' />`

b. The other option is to modify your Topic: Template.Header and add this token:

`(!XMLPACKAGE name="minicartdriver"!)`

6\. Upload the modified template.master file to the target site.

**Test Mini-Cart**  
  
Depending on your placement of the Mini-Cart in your template, you should now be able to see the Mini-Cart on each page that displays. Go to a product and add the product to your cart and you should see the Mini-Cart Update with the new product. That will mean the Mini-Cart is set up correctly.  
  
To test the JavaScript installation, open 2 browser windows, the first with a product page on your site, and the second with the same product’s editing screen in the admin console:  

 [![](images/product.minicartplain9.jpg)](images/product.minicartplain9.jpg) [![](images/product.minicartplain.admin9.jpg)](images/product.minicartplain.admin9.jpg) 

In the admin console, make note of what Page Display is set to because you will want to set it back after this test. We will also use that information in the next steps of the installation.  
  
Change the selected Page Display to Mini Cart Plain and click Update.  
  

![](images/minicart_install2.png)

  
Now refresh the product page on your site, and click the add to cart button. You will see the animation working to put the product into your Mini-Cart. If you see the animation, the Mini-Cart JavaScript is set up correctly.  
  
Set the product back to the original Page Display and update your product.  
  
**Merge Animation**

1\. Find the Xml package used to display your products by going into the product editing screen in the admin console of your site.

![](images/minicart_install3.png)

2\. Find the Xml package listed on the product editing screen on your website by going to the XmlPackages folder on the target site and matching the file name. Download it to your computer and open it using your text editor.  
3\. Verify that **<xsl:value-of select="aspdnsf:AddtoCartForm(ProductID, VariantID, 1)" disable-output-escaping="yes"/>** is included on the page.  
4\. Find **<xsl:template match="Product"> (and <xsl:template name="Variant"> if the package is multi variant)** and the corresponding **</xsl:template>** tag(s). Add the following just before the closing **</xsl:template>** tag:

`<script type="text/javascript"> $window_addLoad(function(){ ajaxifyAddToCartForm(document.getElementById("AddToCartForm_<xsl:value-of select="ProductID"/>_<xsl:value-of select="VariantID"/>"), "ProductPic<xsl:value-of select="ProductID"/>", <xsl:value-of select="ProductID"/>, <xsl:value-of select="VariantID"/>); }); </script>`

  
  
The the second parameter in the ajaxifyAddToCartForm is the ID of the image that the JS 'animates' to move to the cart. If you are using 3rd party image viewers/tools that change the image ID, you will need to change this - **ProductPic<xsl:value-of select="ProductID"/>** - to be the new image ID.  
  
**For customers using the Advanced Product Image Viewer sold [here](http://www.aspdotnetstorefront.com/p-209-advanced-product-image-display.aspx?catid=156)**, change **ProductPic<xsl:value-of select="ProductID"/>** to empty quotes, for example "".

5\. Save the XmlPackage and upload it back to your site.

**Configuration**  
  

1\. From the admin console of your site, navigate to Configuration > Advanced > AppConfig Parameters  
2\. Set AppConfig: Vortx.MiniCart.UseDropDown to false if you want the Mini-Cart to always show (not be a dropdown).  
3\. We also recommend setting the appconfig titled 'AddToCartAction' to 'STAY'. This will help prevent javascript errors for cross domain scripting when you have ssl enabled.

**Clean up**  

1\. product.minicartplain.Xml.config is for testing and reference only. Remove it after everything is working properly.

Options
=======

The latest versions of the Mini-Cart plugin (1.2.0 and beyond) contain several configurable options:

**MiniCartMaxIconHeight** - Sets the maximum height of the icon image that displays for each product in the cart (if minicart pics are enabled).  
  
**MiniCartMaxIconWidth** - Sets the maximum width of the icon image that displays for each product in the cart (if minicart pics are enabled).  
  
**ShowPicsInMiniCart** - Determines whether or not an icon image will be displayed next to each item in the minicart.  
  
**Vortx.MiniCart.HideContentsOnCheckout** - If this is set to true, the minicart will not be interactive during the checkout process. This simplifies the page, as all of the cart contents will be visible during checkout anyway.  
  
**Vortx.MiniCart.UseDropDown** - If this is set to true, customers can expand/collapse the minicart by clicking an arrow icon at the top of the minicart. If this is false, the minicart will always be fully expanded.
      