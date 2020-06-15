
      ---
      title: Smart One Page Checkout
      ---

      Enabling Smart One Page Checkout
================================

1.  If you have not already done so, [purchase a license for the Smart One Page Checkout module](http://www.aspdotnetstorefront.com/p-188-smart-one-page-checkout.aspx?catid=163). You will receive a license key which will be used later on in this process.  
      
    These license keys are URL-specific and call to our license server so if you are using it on a development or staged site, we will need to set up SOPC license keys for those URLs as well.  
      
    Port numbers included in URLs do NOT work with Smart OPC licenses at this time.  
      
    
2.  Set the **Vortx.OnePageCheckout.LicenseKey** [Setting](default.aspx?pageid=settings) to the license key value you received from \[Company Name\] in step 1.  
      
    
3.  Search for **Vortx.OnePageCheckout.ShowEmailPreferencesOnCheckout** and set it true if you would like your customers to be asked if it is okay to email them. Set it to false if you do not want the option to show.  
      
    
4.  If you are configuring your site for use only in the UK, change the [Setting](default.aspx?pageid=settings) value for **Vortx.OnePageCheckout.AddressLocale** to **UK**. Otherwise, leave it set to **US**.  
      
    
5.  Set the **Checkout.Type** [Setting](default.aspx?pageid=settings) to SmartOPC.  
      
    
6.  Click the **Refresh Store button** in the top right of the admin console.

  
For custom skins, such as those from a previous version or add-on, you may need to add this jquery reference to the head of your template.master file that is used when the Smart OPC is operating:  
  

`<%-- jQuery is required` `in` `versions 9.4 and higher --%><br>`

`<script src=``"jscripts/jquery.min.js"` `type=``"text/javascript"``></script><br>`

`<script type=``"text/javascript"``><br>`

`adnsf$ = jQuery; <%-- to avoid conflicts` `with` `existing jQuery versions and other javascript frameworks, change` `this` `line to adnsf$ = jQuery.noConflict(); --%><br>`

`</script>`

  

Testing the one page checkout
=============================

1.  Open the front end of your website in a browser.  
      
    
2.  Add an item to your cart and proceed to checkout.  
      
    
3.  Test your new checkout process.  
    
4.  **You’re done!**

![](http://manual.aspdotnetstorefront.com/images/product/ML9/opcinstall7_9400.png)

Editing the Smart OPC Customer Service panel
============================================

You can edit the information in the Customer Service panel by modifying the [topic](default.aspx?pageid=topics) **OPC.CustomerServicePanel**  
  
All other text in the Smart OPC can be edited through the appropriate [Prompts](default.aspx?pageid=prompts). 

MultiStore Configuration
========================

To install the Smart One Page Checkout module on a Multi-Store site, simply set the store-specific version of the **Vortx.OnePageCheckout.LicenseKey** [Setting](default.aspx?pageid=settings) to the value of the key you got from \[Company Name\] for that store. Those keys are domain-specific, each can only be used for a single domain.

1.  Obtain a new license key for each store from \[Company Name\].  
      
    
2.  In the admin console, navigate to [Configuration > Settings](default.aspx?pageid=settings). Search for **Vortx.OnePageCheckout.LicenseKey**.  
      
    
3.  Set the value for the store you are enabling SmartOPC on to the new key you were given  
     ![](images/1415375016881.png)  
      
    
4.  Click **Save**.  
      
    
5.  Make sure that the **Checkout.Type** Setting is set to SmartOPC for the store you are enabling it on.

### Notes

*   SmartOPC makes extensive use of javascript and AJAX. Sites that have been customized to use these technologies beyond what the core software does should test SmartOPC extensively before 'going live' with it, to ensure there are no conflicts.
      