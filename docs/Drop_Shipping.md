
      ---
      title: Drop Shipping
      ---

      Many store owners will not handle shipping themselves. If you are using 'drop shippers' to handle your order fulfillment, the software can be set up to easily notify them (via email only) of new orders. To do this, follow the steps below.

### **

Enabling Drop Shipping
======================

**

1.  Create one ore more distributors through the admin console, under the [Distributors](default.aspx?pageid=manage_distributors) menu  
      
    
2.  Assign the products you want to drop ship to a distributor by selecting the appropriate entry from the “Distributor:” dropdown menu in [Product Manager](default.aspx?pageid=manage_products).  
      
    
3.  Configure your email Settings (if not already done). Information on doing so can be found [here](default.aspx?pageid=email_setup).  
      
    
4.  Notify the Distributor of new orders. This can be done either manually for each order, or automatically:  
      
    Manually: Set the **DelayedDropShipNotifications** [Setting](default.aspx?pageid=settings) to true and click the **Send Distributor Email(s)** button on the order in the admin console.  
    Automatically: Set the **DelayedDropShipNotifications** [Setting](default.aspx?pageid=settings) to **No**.  
      
    For orders containing products with different distributors, multiple emails will be sent. Each distributor sees only their own portion of the order.

### **

Realtime Rates and Drop Shipping
================================

**

When using [realtime shipping rates](default.aspx?pageid=real_time_shipping_rates), the software generally uses the values of the RTShipping.Origin\* Settings (the store's home location) as the origin for calculating shipping rates. When using drop-shipping, this can result in the customer seeing prices that are not actually what the shipping carrier will be charged. To account for this, the software can be configured to use the drop shippers' addresses as origins when requesting realtime rates.   
  
To enable this feature, simply set the **RTShipping.MultiDistributorCalculation** [Setting](default.aspx?pageid=settings) to **Yes**, and be sure that all of your [Distributors](default.aspx?pageid=manage_distributors) have valid addresses set.   

This feature only works with UPS, the other shipping carriers will continue to calculate all shipping costs from the Origin Settings.

**Shipping Calls** 
-------------------

When this feature is being used, the software breaks the cart contents into groups and sends (up to) 4 requests to UPS. Those requests are:

*   IsShipSeparately products with distributors (rates determined by distributor zip code) 
*   Non-IsShipSeparately products grouped by distributors (rate determined by distributor zip code) 
*   IsShipSeparately products without a distributor (rates determined by RTShipping.OriginZip value) 
*   Non-IsShipSeparately products without a distributor (rate determined by RTShipping.OriginZip value)
      