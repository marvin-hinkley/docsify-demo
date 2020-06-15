
      ---
      title: Google Remarketing
      ---

      This page would welcome a sponsor from the \[Company Name\] community.  

Google remarketing is a service offered by Google to help return your customers to your website after they've abandoned your shopping funnel. For more information about this service please see [Google's documentation.](https://support.google.com/adwords/answer/2476688?hl=en)

Adding the remarketing tag
==========================

1.  Login to your adwords account click on the **Shared library** link in the left navigation. Then click on **Audiences**.  
     ![](images/1415374030063.png)  
      
    
2.  Click **Setup dynamic remarketing** if you would like to, or **Setup remarketing**, whichever you'd prefer. Dynamic Remarketing requires that you have your products in Google Merchant Center.  
      
    
3.  Follow the prompts until you get back to the main Audiences page. You should get the remarketing tag code emailed to you during this process.  
     ![](images/1415374057987.png)  
      
      
    You can also copy your tag code from the **View tag details** button.  
      
     ![](images/1415374086664.png)  
      
    
4.  Click **Setup** and you can copy your tag code from here.  
     ![](images/1415374122169.png)  
      
    
5.  If you chose **Dynamic Remarketing** in step 2, you will see a section near the top of the code that look likes the highlighted section in the image below. You will want to remove this section of code before adding it to \[Company Name\] because there is code in \[Company Name\] that generates this part for you.  
     ![](images/1415374154392.png)  
      
      
    
6.  Now add your remarketing tag code to the topic titled **Script.Google.Remarketing**. Make sure to add the code to the **HTML** view of the topic editor not the design view.  
     ![](images/1415374330542.png)  
      
    
7.  Next set the Value of the **Google.Remarketing.Enabled** [Setting](default.aspx?pageid=settings) to **Yes**. Installation is complete.  
      
    

Notes
=====

For custom skins, such as those from a previous version or add-on, you will need to add two lines of code to your template.master file:  
  
Add this above the <head> section:  

`<%@ Register TagPrefix="aspdnsf" TagName="XmlPackage" Src="~/Controls/XmlPackageControl.ascx" %>`

Add this above the closing </body> tag:

`<``aspdnsf:XmlPackage` `runat``=``"server"` `PackageName``=``"script.bodyclose"` `/>`

  
It may take some time to see Google acknowledge your tag installation on the audiences page. If you would like to setup Dynamic Remarketing please read on.

![Tag Not Detected](http://manual.aspdotnetstorefront.com/images/tagNotDetected.jpg) ![Tag Detected](http://manual.aspdotnetstorefront.com/images/tagDetected.jpg)

Dynamic Remarketing
===================

To enable Dynamic Remarketing, set the Value for the **Google.DynamicRemarketing.Enabled** [Setting](default.aspx?pageid=settings) to true.

In order for Google to know what product a user is looking at they need to match the product id to the product id used up in your Google Merchant Center. You can adjust the output format of your product identifiers in your dynamic remarketing tag so that they match the identifiers you've used in Google Merchant Center.

There are three different tokens you can use to build up your product identifiers. You can use just one, or any combination of these.

*   ProductID
*   VariantID
*   FullSKU (ProductSKU + SKUSuffix from the product variant)

These tokens are case sensitive, and must be surrounded with the curly braces.

The default format is "{ProductID}-{VariantID}--". This matches the default product identifier format from DotFeed. This outputs code that looks something like this.

    	<script type="text/javascript">        var google_tag_params = {            ecomm_prodid: '31-37--',            ecomm_pagetype: 'product',            ecomm_totalvalue: 189.99        };    </script>
    	

Once you've got your product identifiers matching the format used up in your Google Merchant Center your installation is complete. The Dynamic remarketing code will be ouput on all pages of the website.
      