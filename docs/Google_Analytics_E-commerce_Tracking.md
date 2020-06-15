
      ---
      title: Google Analytics E-commerce Tracking
      ---

      \[Company Name\] supports asynchronous e-commerce tracking using Universal Analytics (analytics.js). This version of Google Analytics in \[Company Name\] allows you to make modifications to the Google Analytics code without modifying core source code.

To use this latest analytics code, your Google account will need to be set for **Universal Analytics**. To check the status of your GA account (Universal or Classic), you can check which JavaScript Library your tracking code is referencing. To do so, login to your Google Analytics account and click **Tracking Code** to see the tracking code snippet for a specific property. Look for ga.js or analytics.js referenced somewhere in the code. Classic Google Analytics properties reference ga.js and Universal Analytics properties reference analytics.js.  
  
 If your account requires upgrading, [follow Step 1 in this guide.](https://developers.google.com/analytics/devguides/collection/upgrade/guide#overview)  
If you do not see the upgrade option, [review this information.](https://developers.google.com/analytics/devguides/collection/upgrade/faq#no-option)  
  

Google Analytics
================

Configuration
-------------

First you will need your Google Analytics account number. You can find this code by logging into your Google Analytics account. The interface on Google Analytics changes frequently but you should find the number on the page where you get your tracking script. Copy the UA-xxxxxxxx-x number from this page.

 ![](images/1415914397899.png)  
  
Once you've got the UA number, navigate to your admin console  and add the account number to the [Setting](default.aspx?pageid=settings): **Google.AnalyticsAccount**.  
  
 ![](images/1415914513937.png)

Lastly, make sure that the [Setting](default.aspx?pageid=settings): **UseLiveTansactions** is set to **Yes**. This setting assures that Google Analytics only runs on your live website.

At this point you have completed the installation of Google Analytics. You should be able to view page source on the front end of your website and see the Google Analytics code.

 ![](images/1415914575032.png)   
  

Google Analytics Ecommerce Tracking
===================================

If you would like to enable ecommerce tracking you just have two more steps to complete.

First, login to your Google Analytics account and enable e-commerce tracking. The interface tends to change, but look under **View(Profile) > View Settings**.

 ![](images/1415914632784.png)  
  
Next,  log in to the admin console and set the [Setting](default.aspx?pageid=settings): **Google.EcomOrderTrackingEnabled** to **Yes**.

That's it! At this point your site will send order data up to Google Analytics when your customers check out.

Google Display Advertising
==========================

To enable [Google Display Advertising](https://support.google.com/analytics/answer/3450482?hl=en) in the tracking code, set [Setting](default.aspx?pageid=settings): **Google.AnalyticsDisplayAdvertising.Enabled** to **Yes**.  
  
When this is set to **Yes**, it will include the following line in your analytics javascript: ga('require', 'displayfeatures');
      