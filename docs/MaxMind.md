
      ---
      title: MaxMind
      ---

      MaxMind is a 3rd-party service that uses geolocation tools and other tests to check online orders for fraud. MaxMind does not actually verify cardholder information (this is left to the payment gateway), it instead focuses on verifying that the cardholder is actually the person making the online transaction. It is completely separate from the payment gateway, and serves as an extra level of security above your gateway's standard checks.   
  
See [http://www.maxmind.com](http://www.maxmind.com/app/ccv_buynow?rId=aspdnsf) for more information on how the service works and pricing.   
  

**Thresholds** 
===============

MaxMind's service works by assigning each transaction a fraud score, with 0.0 being very low risk and 100.0 being the highest risk. Store admins must set several 'threshold' Settings (explained below) to determine how the software should handle orders based on that score. The default values for those Settings are simply recommendations based on information from MaxMind, store admins should feel free to adjust the values based on their business model and fraud rates.   

Enabling MaxMind
================

1.  First, visit [http://www.maxmind.com](http://www.maxmind.com/app/ccv_buynow?rId=aspdnsf) and register an account for the MaxMind services.  
      
    
2.  Once you have your account information, go to the [Site Setup Wizard](default.aspx?pageid=site_setup_wizard) page and click the **Configure Maxmind** link. In the window that opens, set the following values the way you want for your site:  
      
     ![](images/1415916148189.png)

**Setting Name**

**Description**

MaxMind.Enabled

Set this to **Yes** to enable the MaxMind service.

MaxMind.DelayDownloadThreshold

If your business sells [downloadable products](default.aspx?pageid=downloadable_products) and sends the download emails automatically, the value in this Setting determines when the software will hold off on that email until a store admin can review the order.

MaxMind.DelayDropShipThreshold

If you use [drop shipping](default.aspx?pageid=drop_shipping), the value in this Setting determines when the software will hold off on sending the distributor email until a store admin can review the order.

MaxMind.FailScoreThreshold

The value in this Setting determines when the software will mark an order as fraud. Store administrators can review these orders at **[Orders > Manage Orders > Fraudulent Transactions](default.aspx?pageid=fraudulent_transactions)**

MaxMind.LicenseKey

This key is obtained from MaxMind. The service will not work until this is populated.
      