
      ---
      title: Real Time Shipping Rates
      ---

      With Real Time Shipping (RTS), your website connects to one or more of the major shipping carriers (UPS, USPS, FedEx, Australia Post, and Canada Post) and gets the price that the carrier would charge to ship that order based on the weight and/or size of the products ordered, and the origin and destination of the package. This requires an account with one or more of the 3rd-party carriers, and incurs additional monthly fees through those companies.

More than one carrier can be used at the same time, to give your customers a wider array of shipping choices.

Calculations
============

When using Real Time Shipping rates, the software sends the total weight of all of the products, the dimensions (if the product is set as [is ship separately](default.aspx?pageid=manage_products)), the customer's shipping address, and the origin address. The origin address is taken either from the storefront address (see below) or the [drop shipper's](default.aspx?pageid=drop_shipping) address if using drop shipping (UPS only). The carrier then calculates the rates based on this information and returns it to the site for display.   
  

Rate Restrictions
=================

By default, the software will display all rates that the shipping carrier returns. This means that the shipping carrier determines which methods are applicable to the customer, and the customer can choose from any of them. Some store owners may want to restrict these choices. This can be done by [preventing shipping methods from appearing](default.aspx?pageid=advanced_shipping_options) .  
  
To restrict where customers can ship to, store administrators must delete the [States/Provinces](default.aspx?pageid=edit_states_provinces) from \[Company Name\].   
  

**General Setup** 
==================

To set up Real Time Shipping (regardless of the carrier you choose to use), the following steps must first be performed:

1.  In the \[Company Name\] admin console, go to **Configuration > Settings**.  
      
    
2.  In the **Search All Fields** box, enter 'Origin', then click **Apply Filter**.  
      
    
3.  Each of these RTShipping.Origin Settings needs to be populated. These make up the origin address that is used for shipping calculations, so set them to the address you wish to use for that purpose. Note the following rules:  
    Be sure that RTShipping.OriginState is a 2-letter abbreviation, do not use the full state name  
    RTShipping.OriginZip should only be 5 digits  
      
    
4.  Go to **Configuration > Shipping Calculation**, and select the radio button next to **Use Real Time Rates**, then click **Save**.
5.  There are three Settings that control which carriers are offered:  
      
    **RTShipping.ActiveCarrier**  
    **RTShipping.DomesticCarriers**  
    **RTShipping.InternationalCarriers**
  
All carriers used must be set in the **RTShipping.ActiveCarrier**.  
If all carriers are allowed to display for both Domestic (United States) and International (Other non-US), then the two specific settings should be left blank.  
If you want to limit the carriers Domestically or Internationally, select and save the carriers that you wish to allow within each setting.

UPS
---

 Once the General Real Time Shipping setup steps have been completed, follow the steps below to enable UPS shipping:

1.  In the \[Company Name\] admin console, go to **Configuration > Settings**.  
      
    
2.  In the **Search All Fields** box, enter 'RTShipping.ups', then click **Apply Filter**.  
      
    
3.  The following Settings will need to be populated with your personal account information, obtained from UPS. Do not change the other Settings unless instructed to do so!  
    RTShipping.UPS.License (UPS refers to this as an Access Key)  
    RTShipping.UPS.Password  
    RTShipping.UPS.UserName  
      
    
4.  Finally, search for the **RTShipping.ActiveCarrier** Setting, and set the value to UPS.

**For UPS2 negotiated rates, see [this article](default.aspx?pageid=ups_negotiated_rates).**

USPS
----

 Once the General Real Time Shipping setup steps have been completed, follow the steps below to enable USPS shipping:

1.  Obtain access to the [USPS Web Tools](https://www.usps.com/business/web-tools-apis/welcome.htm) by clicking the "Register Now" link, and submitting your information.
2.  You should receive an email from USPS with your username and password for the API. These credentials should be valid for the USPS production and test servers.
    
3.  In the \[Company Name\] admin console, go to **Configuration > Settings  
      
    **
4.  In the **Search All Fields** box, enter 'RTShipping.usps', then click **Apply Filter**.  
      
    
5.  The following Setting will need to be populated with your personal account information, obtained from USPS. Do not change the other Settings unless instructed to do so!  
    RTShipping.USPS.UserName: This is the username assigned to you by USPS.  
      
    
6.  Finally, search for the **RTShipping.ActiveCarrier** Setting, and set the value to USPS.

USPS has a maximum shipping weight of 70 lbs. Store administrators should make sure that their **RTShipping.USPS.MaxWeight** Setting is set to 70 or less.

FedEx
-----

 Once the General Real Time Shipping setup steps have been completed, follow the steps below to enable FedEx shipping:

1.  In the \[Company Name\] admin console, go to **Configuration > Settings**.  
    
2.  In the **Search All Fields** box, enter 'RTShipping.Fedex', then click **Apply Filter**. 
3.  The following Settings will need to be populated with your personal account information, obtained from FedEx. Do not change the other Settings unless instructed to do so!  
    RTShipping.FedEx.AccountNumber  
    RTShipping.FedEx.Meter \*  
    RTShipping.FedEx.Key  
    RTShipping.FedEx.Password  
      
    
4.  Finally, search for the **RTShipping.ActiveCarrier** Setting, and set the value to FedEx.

FedEx's API does not accept product dimensions with decimal places (ie 3.5). Remember that when entering dimensions for your products, they will be rounded up to whole numbers if you're using FedEx Real Time Shipping rates.

**\* To obtain your FedEx Web Services Meter Number, follow this procedure:**

1.  Go to the [FedEx developer website](http://www.fedex.com/us/developer/index.html)
2.  Login to FedEx and select **Web Services for Shipping** from the drop down selector
3.  Select **FedEx Web Services** on the left side navigation, then **Move to Production**
4.  Click the button called **Get Production Key**
5.  Fill out the required information and you will be given your meter number and credentials

**Australia Post** 
-------------------

  
Once the General Real Time Shipping setup steps have been completed, follow the steps below to enable AusPost shipping:

1.  In the \[Company Name\] admin console, go to **Configuration > Settings**.  
      
    
2.  In the **Search All Fields** box, enter 'RTShipping.AusPost', then click **Apply Filter**.  
    
3.  Verify that the following Settings are configured as desired for your site. Note that AusPost does not require any username/password information to return live rates.  
    RTShipping.AusPost.DefaultPackageSize  
    RTShipping.AusPost.DomesticServices  
    RTShipping.AusPost.IntlServices  
    RTShipping.AusPost.MaxWeight  
      
    
4.  Change the **Localization.StoreCurrency** Setting to **AUD** (see [this page](default.aspx?pageid=locale_settings) for more information on changing locales).  
      
    
5.  Change the **Localization.WeightUnits** Setting to **kg** (see [this page](default.aspx?pageid=locale_settings) for more information on changing locales).  
      
    
6.  Finally, search for the **RTShipping.ActiveCarrier** Setting, and set the value to AusPost.

**Canada Post** 
----------------

Once the General Real Time Shipping setup steps have been completed, follow the steps below to enable Canada Post shipping:  
  

1.  In the \[Company Name\] admin console, go to **Configuration > Settings**.  
      
    
2.  In the **Search All Fields** box, enter 'RTShipping.CanadaPost', then click **Apply Filter**.  
    
3.  Verify that the following Setting is configured with your account information from Canada Post.  
    RTShipping.CanadaPost.MerchantID  
      
    
4.  Change the **Localization.StoreCurrency** Setting to **CAD** (see [this page](default.aspx?pageid=locale_settings) for more information on changing locales).  
      
    
5.  Change the **Localization.WeightUnits** Setting to **kg** (see [this page](default.aspx?pageid=locale_settings) for more information on changing locales).  
      
    
6.  Finally, search for the **RTShipping.ActiveCarrier** Setting, and set the value to CanadaPost.
      