
      ---
      title: UPS Negotiated Rates
      ---

      [UPS](http://www.ups.com/) offers special 'negotiated' rates to many of its customers. \[Company Name\] is able to request these special rates through the Real-time shipping rates API, which allows store owners to offer discounted shipping prices to their customers.

For directions on setting up standard realtime UPS rates, or realtime rates from the other major carriers, please see [this page](default.aspx?pageid=real_time_shipping_rates).

### **

Setup
=====

**

To enable this feature, first follow these basic steps to enable [Real-time rates](default.aspx?pageid=real_time_shipping_rates):

1.  In the \[Company Name\] admin console, go to **Configuration > Settings**.  
      
    
2.  In the **Search All Fields** box, enter 'Origin', then click **Apply Filter**.  
      
    
3.  Each of these RTShipping.Origin Settings needs to be populated. These make up the origin address that is used for shipping calculations, so set them to the address you wish to use for that purpose. Note the following rules:  
    Be sure that RTShipping.OriginState is a 2-letter abbreviation, do not use the full state name  
    RTShipping.OriginZip should only be 5 digits  
      
    
4.  Go to **Configuration > Shipping Calculation**, and select the radio button next to **Use Real Time Rates**, then click **Save**.  
      
    
5.  Once Real-time shipping is enabled, configure the software to use UPS' special API for negotiated rates:
    *   Set the **RTShipping.UPS.AccountNumber** [Setting](default.aspx?pageid=settings) to the 6-digit account number you obtained from UPS.
    *   Set the **RTShipping.ActiveCarrier** [Setting](default.aspx?pageid=settings) to UPS2 (in addition to other carriers used, comma separated)
    *   Set the **RTShipping.DomesticCarriers** [Setting](default.aspx?pageid=settings) to UPS2 if desired for United States rates (in addition to other carriers used, comma separated).
    *   Set the **RTShipping.InternationalCarriers** [Setting](default.aspx?pageid=settings) to UPS2 if desired for International rates (in addition to other carriers used, comma separated).
    *   Set the **RTShipping.UPS.GetNegotiatedRates** [Setting](default.aspx?pageid=settings) to true.
    *   Set the **RTShipping.UPS.UserName** [Setting](default.aspx?pageid=settings) to your UPS account user name.
    *   Set the **RTShipping.UPS.Password** [Setting](default.aspx?pageid=settings) to your UPS account password.
    *   Set the **RTShipping.UPS.License** [Setting](default.aspx?pageid=settings) to your UPS account license.
      