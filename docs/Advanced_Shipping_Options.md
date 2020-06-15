
      ---
      title: Advanced Shipping Options
      ---

      This is an example of a knowledgebase article. If this is an article that describes a common error or problem that may occur with your product, provide an overview of why the error occurred and how to fix or work around it. Your readers will want a quick solution, so the cause and solution should be as clear and easy to understand as possible. Use screenshots to illustrate symptoms and solution where possible.  
  
  
![](images/related_files_msg.png) ** Related Files**  
none..  
  
**Related Pages**  
none..
      arriers return (for example, your products may not qualify for Media Mail but USPS will return it anyway based on weight). To do this, simply enter the names of the shipping methods you wish to hide _exactly as they appear on your shipping methods page_ in the **RTShipping.ShippingMethodsToPrevent** [Setting](default.aspx?pageid=settings), as a comma separated list (do not include IDs).   

### **

Free Shipping
=============

**

The software can be configured to grant free shipping on some orders, for customer levels, coupons, large orders, etc. The following AppConfigs must be set for this to work properly:

**Setting Name**

**Description**

FreeShippingThreshold

If you want to grant free shipping on orders over a certain dollar amount, put that amount here (no formatting, just the numeric value). All orders over that amount will automatically get free shipping.

FreeShippingAllowsRateSelection

Store administrators will generally want to use the cheapest (and therefore slowest) shipping method for their free shipping orders. Customers are sometimes willing to pay for shipping that would normally be free if it means getting their purchase faster. If you want to allow this, set this Setting to **Yes** and customers will be able to choose whether to use the free method, or pay for one of the faster methods you offer.

ShippingMethodIDIfFreeShippingIsOn

If you are granting free shipping on some orders, the shipping method ID must be in this Setting to tell the software what to give the customers. To locate shipping method ID's, go to **Configuration > Shipping Calculation** and click **View Shipping  Methods** in the Custom Shipping Calculations section. 

Restricting Free Shipping to Geographic Locations
=================================================

If you wish to restrict Free Shipping to specific geographic regions (such as the United States), you just need to set the Setting: **ShippingMethodIDIfFreeShippingIsOn** to shipping methods that are only available to the specific geographic region, and then set the Setting: **FreeShippingAllowsRateSelection** to **Yes**.  

### **

Shipping and Handling Fees
==========================

**

If you want to add an extra fee to the shipping costs generally charged on your store, enter a fee value in the **ShippingHandlingExtraFee** Setting. The value entered here will be added to the normal shipping costs on your store. This should be a simple numeric value, no $ or other special characters. Keep in mind that this fee is charged on ALL orders, it cannot be selectively applied.

### **

Renaming Real Time Shipping Methods
===================================

**

Store administrators can [rename all real time shipping rate methods](default.aspx?pageid=renaming___reordering_real_time_shipping_methods) returned from the carriers.  
  

### **

UPS2
====

**

UPS has a new API that allows more flexibility and features than the standard Real-time rates API. Store administrators must get a special account from UPS, and beyond the standard [setup directions](http://manual.aspdotnetstorefront.com/p-980-realtime-shipping-rates.aspx), the **RTShipping.UPS.AccountNumber** [Setting](default.aspx?pageid=settings) will have to be populated.   
  

**Negotiated Rates** 
---------------------

See [here](default.aspx?pageid=ups_negotiated_rates) for information on offering special discounted shipping rates.   
  

**Default Address Types** 
--------------------------

By editing the **RTShipping.UPS.AddressTypeBehavior** [Setting](default.aspx?pageid=settings), store administrators can force a certain address type for all orders.  
Allowed values are:

*   blank (default) - Customer selection is used. 'Unknown' is treated as 'Residential'
*   ForceAllResidential - All customer addresses are sent to UPS as 'Residential'
*   UnknownsAreCommercial - Customer selection is used. 'Unknown' is treated as 'Commercial'
*   ForceAllCommercial - All customer addresses are sent to UPS as 'Commercial'

**Delivery Confirmation 
----------------------** With the **RTShipping.UPS.DeliveryConfirmation** [](http://manual.aspdotnetstorefront.com/p-978-appconfig-parameters.aspx)[Setting](default.aspx?pageid=settings), store administrators can specify that their orders should require delivery confirmation.  
Allowed values are:

*   blank (default) - no confirmation required
*   DeliveryConfirmation 
*   SignatureRequired 
*   AdultSignatureRequired
      