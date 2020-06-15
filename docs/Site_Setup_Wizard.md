
      ---
      title: Site Setup Wizard
      ---

      From the **Configuration** Menu, click **Site Setup Wizard**. 

The Site Setup Wizard can be used to make changes to multiple site-wide settings at once. It is also the easiest place to set up your store's basic information, set up payment methods and gateways, etc. 

Only Super Admin accounts can make changes in the config wizard. Please see [here](default.aspx?pageid=manage_admin_users) for information on creating super admin accounts.  
  
After changing settings on this page, click the **Save** button at the top or bottom of the page to apply your changes.

The wizard is broken into several sections, explained below. There are several elements that appear throughout the page that provide additional functionality or information:

*    ![](images/1415824582769.png)   
    This button is used to edit values for multiple stores at once. When clicked, store-specific copies of the setting you're working on will be displayed, and can all be edited at once. Note that you can edit multiple values and save them all with a single **Save** click. For more information on how Settings can vary by store, see [this page](default.aspx?pageid=varying_settings_by_store).  
      
    
*    ![](images/1415824803109.png)   
    Where it appears, the **Toggle Advanced** button will expand the current window and show additional options for the item being configured. The options shown by clicking that link generally do not have to be changed for basic functionality to work.

General Settings
================

Here you configure some general settings for your site(s). Several of these settings affect almost every page on the site, so be careful with any changes made here.  
  ![](images/1415825241376.png)

  

**Setting**

**Description**

Store Name

This is the name of your store. This will appear on browser page titles, receipts, etc, so format it exactly as you want your name to look in those places.

Live Server Domain

This is your store's URL, without the 'www'.

Store Origin Zip Code

This will be used as the 'origin' zip code when calculating shipping costs (if your site uses [realtime shipping rates](default.aspx?pageid=real_time_shipping_rates)).

Store Currency

This is the master currency your store will use (in ISO 4217 Standard Code format). Please see [here](default.aspx?pageid=currencies) for more information.

Store Currency Numeric Code

This should be the ISO 4217 Standard Code for the currency your store will use (from above). Please see [here](default.aspx?pageid=currencies) for more information.

Use Live Transactions

This setting determines whether your store will try to call the live version of your payment gateway, or the test version.

Use SSL

This controls whether your site will switch to secure mode (https) on some pages throughout the site - shopping cart, signing pages, etc. See [here](default.aspx?pageid=ssl) for more information on enabling SSL.

Set Static Machine Key

Sets a random, static machine key in the web.config file. This will allow the site to function properly on server farms, and can also resolve issues with users being logged out and/or losing their shoppingcart after an application reset.  
NOTE: The {root} folder where the web.config file is located requires Read/Write/Modify permissions for the .NET user account in order to make this change (typically ASPNET for WindowsXP or NETWORK SERVICE for Windows Server 2003/Vista or IIS\_IUSRS for Windows Server 2008/Windows7).

Encrypt the Web.config

This setting determines whether or not the web.config file (which controls several very important elements of your site) is encrypted or not. This is generally not done until development and testing of a site is complete and it is time to [go live](default.aspx?pageid=go_live_checklist). Please see [here](default.aspx?pageid=encryptkey) for more information on encrypting the web.config file.  
NOTE: The {root} folder where the web.config file is located requires Read/Write/Modify permissions for the .NET user account in order to make this change (typically ASPNET for WindowsXP or NETWORK SERVICE for Windows Server 2003/Vista or IIS\_IUSRS for Windows Server 2008/Windows7).

Email

Click the 'Configure Email' link to set up the outgoing mail settings for your site. See [here](default.aspx?pageid=email_setup) for more information.

SEO

Click the 'Configure SEO' link to set up the store-wide meta tags for your store. See [this page](default.aspx?pageid=seo) for more details.

Configure Fraud Solutions
=========================

Maxmind is a built-in fraud prevention service. Click [here](default.aspx?pageid=maxmind) for more information.

Choose Your Country
===================

Choose your country from the dropdown menu. This is set to United States by default.  
  

Configure Wallets
=================

Wallets are 3rd party alternative payment methods where customers might already have established accounts with (and saved credit card information in). [PayPal Express](default.aspx?pageid=paypal_express_checkout) & [Checkout By Amazon](default.aspx?pageid=checkout_by_amazon) can be configured here.

Credit Cards & Other Payment Methods
====================================

In this section, you set up the payment options that customers will have on your site. Note that these settings will apply to customers shopping on your site, as well as to admin users placing [phone orders](default.aspx?pageid=phone_orders).  
  
These checkboxes allow you to select the payment method(s) you will accept on your site. You can select multiple options. See [here](default.aspx?pageid=payment_method) for an explanation of the different payment methods.   
  
The more complicated payment methods require some extra setup to enable. Clicking the **configure** link to the right of the individual options allows you to set those methods up without leaving the page.   
  
If you choose the Credit Card option, you'll also need to configure a Payment Processing Solution to accept payment. See the next section for more information.  
  
 ![](images/1415825834123.png)

Payment Processing Solutions
============================

Payment Processing Solutions are 3rd-party services that the store runs credit card transactions through. You may only select one option. To enable a gateway, click the **configure** link to the right of its individual entry and fill in the required fields. Once you click Save and Close, the radio button for that gateway will enable, allowing you to select it. Click that option, then click **Save** at the bottom of the page to enable the gateway. _The gateway will not be enabled until you select it and click Save._ Click [here](default.aspx?pageid=payment_gateways) for more information about payment gateways.  
 _![](images/1415826001719.png)_ 

  

Payment Gateway Updater
=======================

\[Company Name\] has the capability to download gateway updates through the admin console. This allows \[Company Name\] to release updates to gateways or even add support for new gateways in between major version releases, and eliminates the need for those updates be applied through patches or support requests.

The admin console checks your current gateway version against the latest version available from AspDotNetStorefront each time the Site Setup Wizard page is loaded. When an update is available for a gateway, a link to download it will appear in the Payment Gateways section of this page:  
  
 ![](images/1415826144561.png)

To apply an update, click the link as shown above, and a .zip file will be downloaded to your computer. The .zip file should contain a single .DLL file. Extract that and upload it to the /bin folder on your site. Note that _doing so will force your site to restart_, so it's best to do this during low traffic hours.
      