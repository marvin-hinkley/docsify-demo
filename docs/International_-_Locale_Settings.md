
      ---
      title: International - Locale Settings
      ---

      ​Grow your International presence. Bongo gives you the best overseas shipping rates. Learn more [here](https://bongous.com/business/).                                                                                                                                                                                                        ![](images/bongologo.png)   
  
One of the software's key features is the ability to present all text on the site in multiple languages, to increase international sales. Customers visiting the site can choose which of the installed languages they'd like to view the content in, and their setting will be saved between visits.  
 ![](images/1415810956151.png)  

  

The software does not actually do live translations. Store admins must install 'language packs' with pre-translated versions of all of the text on the site (English comes pre-loaded of course), and the software displays the appropriate language pack depending on the customer's selection. 

### **

Installing a new Locale
=======================

**

IMPORTANT: Make sure you back up your existing /images,  /App\_Themes, and /App\_Templates folders before installing new language packs!

1.  Once you have purchased or created the language pack, copy the string file (xls file) to the **/Web/StringResources** folder  
      
    
2.  Copy the template file to the **/Web/App\_Templates/Skin\_#** folder  
      
    
3.  Copy the images to the **/Web/App\_Themes/Skin\_#/images** folder
4.  In the \[Company Name\] admin console, go to **Configuration > Locale Settings  
    **
5.  Click **Add New**  and fill in the fields below to create the new locale. If your locale is going to use a different currency than USD, make sure that the currency is published before creating the new locale. See [here](default.aspx?pageid=currencies) for details on doing that. When finished, click **Save**.  
     ![](images/1415811270669.png)  
      
    
    **Field Name**
    
    **Description**
    
    Name
    
    This is the locale's name for use within the admin site. This must be a valid .NET locale name, in the format of aa-AA.
    
    Description
    
    This is a label for the locale, which customers will see when choosing which language to view the site in (French, Spanish, etc).
    
    Default Currency
    
    If you have multiple [currencies](http://manual.aspdotnetstorefront.com/p-419-currencies.aspx) published on your site, you can associate one of them with this locale so that when customers change to this language, they see prices in the associated currency.
    
    Display Order
    
    This controls the order languages will be listed in the pulldown menu customers use to change languages.
    
6.  A confirmation message will display indicating that the new locale has been added. In the Prompts column, click the **Edit/Upload** link to upload the new string file.
    
7.  Select the new locale from the dropdown list on the left, then click **Reload from Excel File on Server**
    
8.  If you have loaded strings for this language in the past, choose to **Replace Existing** or **Leave my modified** strings based on personal preference. Replace existing will overwrite all existing strings with new values. Leaving modified strings will skip over values that you have edited.
    
9.  Click the **Reload Preview** button, then click **Begin Reload Processing** 
    
10.  Verify that the upload process completes successfully and displays a **Done** message (scroll to the bottom to check). The new locale is complete!
    

Creating a Language Pack
========================

Before you can install a new locale, you have to create the translated files. There are 3 parts to this:   
  

**Strings** 
------------

The strings resource file (which is just a simple Excel spreadsheet) contains almost all of the text that is seen on the site, both on the admin site and the front-end. Translating these values allows the software to display that text in other languages than English. Within the root folder (/Web, by default), there is a **StringResources** folder, which contains these strings files.  

To create a new language, make a copy of the strings.en-US.xls file and rename it for your new language (for example strings.es-MX.xls for the Spanish language). The values in the file then all need to be translated to the new language.

**Images** 
-----------

If any of the images on your site contain text, you'll want to make translated versions of those as well, and the software will use those if a customer changes locales. 

**Template** 
-------------

The final step is translating any text in the template.master file, so that when the customer changes locales your links, headlines, etc will change as well. The modified template should be named with the locale as images were:

template.master → template.es-MX.master  
  
Set the Global Config (**Configuration > Global Config Parameters**): **AllowTemplateSwitchingByLocale** to **Yes**

  

Switching to a single non-US Locale
===================================

While the storefront can be configured to use multiple locales very easily, there are times when a site may need to simply set the storefront to a single locale other than en-US.   
  
This section will explain how to do so, using French (fr-FR) as an example.

1.  Create a new string resources file (and entire language pack if desired) as explained in the **Creating a language pack** section on this page.  
      
    
2.  Open the [Currencies](default.aspx?pageid=currencies) page in the admin console and check the box in the **Published** column for the French Franc. The display locale will be fr-FR. Do not unpublish USD yet!  
    If the currency you wish to display is not listed, you may add it at this time. Visit [http://en.wikipedia.org/wiki/ISO\_4217](http://en.wikipedia.org/wiki/ISO_4217) for applicable currency codes.  
      
    
3.  Open the [Locales](default.aspx?pageid=locale_settings) page in the admin console. Click **Create Locale** and enter fr-FR as the name. Enter a Description and set the currency to EUR. Click **Save**.  
      
    
4.  Once you have saved your new locale, click the **Edit/Upload** link in the **Prompts** column, then click the **Reload From Excel File on Server** button. This will load your new string resources from the file created in Step 1. Follow the on-screen directions to upload all of the strings (don't forget to hit the Begin Reload Processing link after all the strings show on the page). Then click the **Refresh Store** button to complete the upload.  
      
    
5.  From the root of your website, open the web.config file in Visual Studio or a text editor and look for the GLOBALIZATION section. Change the "en-US" references to "fr-FR". You may also need to change the database locale in the web.config file ( DBSQLServerLocaleSetting ) which is within the appSettings section. This section is encrypted if you have the web.config encrypted in the admin console of your website, and would require decrypting it first before you have access to that setting. You will need Read/Write/Modify permissions given to the .NET user account temporarily on the web folder that contains the web.config file in order to decrypt/encrypt it.  
      
    
6.  Go to [the locale page](default.aspx?pageid=locale_settings) in the admin console and delete the en-US locale. Then from [the currencies page](default.aspx?pageid=currencies), uncheck **Published** next to USD.  
      
    
7.  Go to the [Settings](default.aspx?pageid=settings) page and search for 'Localization'. Set the **Localization.StoreCurrency** Setting to FRF, and **Localization.StoreCurrencyNumericCode** to 250. (remember to change these values for your locale)
      