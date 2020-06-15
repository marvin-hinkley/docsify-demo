
      ---
      title: Paypal Standard Instant Notifications
      ---

      Your PayPal Standard account may list orders that do not appear in your \[Company Name\] admin console. PayPal orders generally require the customer to click a 'Return to Merchant' button at the end to complete checkout. Customers don't always do this, which can lead to lost orders. PayPal has created a service called 'Instant Payment Notification' that cuts down on the frequency of this.  
  
  
There are 2 ways this notification can take place:  
  

1.  You can enable PayPal’s forwarding service on your PayPal account. This will try to redirect customers back to your site once they are done with PayPal. This is configured on PayPal’s end. When prompted for a URL to direct customers to, you should use http://www.yoursite.com/paypalok.aspx  
      
    This redirect can sometimes fail. Customers can always decide to go to another site instead or close their browser before it can complete. If you are using this method, be sure to check your PayPal account regularly.  
      
    
2.  The preferred method to use is PayPal’s Instant Payment Notification service (IPN). This sends a notification of completed orders to your storefront, without redirecting the customer there. Once this service is enabled on PayPal’s end, set your **Paypal.UseInstantNotification** [Setting](default.aspx?pageid=settings) to **Yes**. You should also set the **PayPal.ReturnOKURL** Setting to 'default.aspx' once you have enabled the IPN service, or duplicate orders can get created.  
      
    To enable the IPN in PayPal, follow these steps:  
      
    ![](images/1415741221524.png)    
      
     ![](images/1415741300183.png)  
      
     ![](images/1415741386356.png)
      