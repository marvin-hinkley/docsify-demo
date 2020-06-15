
      ---
      title: In-Store Pickup for Real-time Shipping
      ---

      From **Configuration** Menu, click **Shipping Calculation**.  
  
In the **Real-time Rates** section, click **Configure in-store pickup**.  
  
Using this feature, store administrators for stores that also have physical locations can give their local customers the option to pick up their purchases at the shop.   
  
This only functions when the store uses [Real-time Shipping rates](default.aspx?pageid=real_time_shipping_rates). If using fixed shipping methods, this feature must be disabled. You can create another fixed method for your local pickup option.   
  
To enable this option, check the **Allow In-Store Pickup box** and give the option the desired price.  
  
 ![](images/1416416230852.png)  

The name of the In-Store Pickup shipping method can be changed by modifying the **RTShipping.LocalPickupMethodName** [Prompt](default.aspx?pageid=prompts).

This option can be limited by geographic region if desired, based on the following restrictions:    
 ![](images/1416416442488.png)  
  
**Unrestricted**   
All customers can choose the in-store pickup option.

**By State**   
Only customers in the allowed state(s) will be able to choose this option.

**By Zip Code**   
Only customers in the allowed zip code(s) will be able to choose this option. The entire 5-digit zip code should be listed. 

**By Zone**   
Only customers in the allowed zone(s) will be able to choose this option. See [here](default.aspx?pageid=shipping_zones) for information on creating zones.  
  
The In-Store Pickup settings affect all stores. If you wish to have different settings per store, you will need to modify the Settings directly per store. Access the [Settings](default.aspx?pageid=settings) page and search for "pickup".
      