
      ---
      title: Moneris eSELECTplus
      ---

      Obtaining your credentials
==========================

Once you have received your activation letter/fax from Moneris, go to [https://esplus.moneris.com/usmpg/activate/](https://esplus.moneris.com/usmpg/activate/ ) as instructed. You will need to input the store ID and merchant ID provided in the email, then click on **Activate**. In this process you will need to create an administrator account that you will use to log into the Merchant Resource Centre to access and administer your eSELECTplus store. You will need to use the Store ID and API Token to send transactions through the API.   
  
Once you have created your first Merchant Resource Centre user, please log on to the Interface by clicking the “eSELECTplus” button. Once you have logged in please proceed to ADMIN and then STORE SETTINGS. At the top of the page you will locate your production API Token, which you will need to configure the store as directed below:   
  

Configuring the store
=====================

To enable the eSELECT Plus (Moneris) gateway:

1.  In the \[Company Name\] admin console, go to **Configuration > Site Setup Wizard**.  
      
    
2.  In the Payment Gateway section, click the **configure** link next to the eSELECT Plus (Moneris) entry.  
      
    
3.  Enter the values you obtained from eSELECT Plus (Moneris) for the **Live API Token** and **Live Store ID**.  
      
    
4.  Set the **Country** to either US or CA depending on the home country of your store. If you're going to use the Canada integration, you will also need to change your default locale and currency at the top of the Site Setup Wizard page.  
     ![](images/1415641353500.png)  
      
    
5.  Click **Save and Close**.  
      
    
6.  Finally, click the radio button next to **Moneris eSELECT plus** and then click the **Save** button.

Gateway Messages
================

Unlike most other gateways, with Moneris store admins can customize the transaction result messages that customers see when attempting to check out - things like "Authentication failed", "Card not accepted", etc through the [Prompts](default.aspx?pageid=prompts). This also allows these messages to be translated into other languages. See [here](default.aspx?pageid=locale_settings) for more information on doing that.

To review/edit these messages, go to **Content > Prompts** in the admin console and search for 'gw.moneris'.

Notes
-----

*   Moneris' test server uses a shared order number system. If an order number has ever been used by another customer on any other platform, the order will fail even if everything else about the request is valid. If you encounter unexpected errors during checkout testing, try another order number and it should go through.
*   The Moneris gateway differs from many gateways in that it does not allow voids on orders until they have been captured. Stores using delayed capture that need to cancel orders will have to do so through the Moneris terminal, or by capturing the order and then voiding/refunding it.
*   The \[Company Name\] Moneris integration does not currently support 3d secure transactions.
      