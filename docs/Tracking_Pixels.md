
      ---
      title: Tracking Pixels
      ---

      The storefront software has built-in support for [Google Analytics E-commerce Tracking](default.aspx?pageid=google_analytics_e_commerce_tracking) , but many sites will want to use other services instead. These services are often referred to as 'tracking pixels', and require store owners to insert special javascript code on the orderconfirmation.aspx page. This can easily be done with the following steps:  
  
While the values mentioned here are named 'Google', the steps will work for almost any 3rd party tracking pixel that requires a simple code snippet on the order confirmation page. Multiple snippets may be added to the topic for different services requiring injection on the order confirmation page.

1.  Set the **IncludeGoogleTrackingCode** [Setting](default.aspx?pageid=settings)  to **Yes**.  
      
    
2.  Modify the **GoogleTrackingCode** [Topic](default.aspx?pageid=topics) in HTML mode (<>). Insert the code provided by your tracking system that should be inserted on the order confirmation page. This will be inserted into the code on that page automatically for each new order.

If the tracking code includes javascript, you may have to follow [these steps](default.aspx?pageid=allow_scripts_in_html_editor) before the script will save.

### Tracking Code Tokens

The orderconfirmation page has support for 3 special 'tokens' that can be used to insert important values into your tracking code. These tokens are:

(!ORDERTOTAL!) - This will be replaced by the current order total.

(!ORDERNUMBER!) - This will be replaced by the current order number.

(!CUSTOMERID!) - This will be replaced by the current customer's ID.

  
**For Example**: If the **GoogleTrackingCode** topic contained this code when a customer checked out with a $125.67 total:

`<``noscript``> <``img` `height``=``"1"` `width``=``"1"` `border``=``"0"` `src``=``"[https://www.googleadservices.com/pagead/conversion/123456789/?value=](https://www.googleadservices.com/pagead/conversion/123456789/?value=)(!ORDERTOTAL!)&label=Purchase&script=0"``/> </``noscript``>`

The software would actually output this code on the page, which would insert the order total:

`<``noscript``> <``img` `height``=``"1"` `width``=``"1"` `border``=``"0"` `src``=``"[https://www.googleadservices.com/pagead/conversion/123456789/?value=125.67&label=Purchase&script=0](https://www.googleadservices.com/pagead/conversion/123456789/?value=125.67&label=Purchase&script=0)"``/> </``noscript``>`
      