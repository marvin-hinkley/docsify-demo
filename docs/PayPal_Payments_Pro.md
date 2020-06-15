
      ---
      title: PayPal Payments Pro
      ---

      Enabling this payment gateway automatically enables [PayPal Express](default.aspx?pageid=paypal_express_checkout).  
  
In order to complete this payment gateway setup, you will need to obtain an API Signature from PayPal. Log into your PayPal account and go to the Profile page. Click the **API Access** link, then click **Request API Credentials** link. Choose the **API Signature** method then agree to the terms and click Submit.   
  
To set up the PayPal Website Payments Pro payment gateway:

1.  In the \[Company Name\] admin console, go to **Configuration > Settings  
    **
2.  In the Filter section, enter "PayPal" in the **Search All Fields** box, then click **Apply Filter  
    **
3.  The following Settings will need to be populated with your personal account information, obtained [here](https://www.paypal.com/us/cgi-bin/webscr?cmd=_get-api-signature&generic-flow=true) from PayPal. Do not change the other Settings unless instructed to do so!  
    \- PayPal.API.Password  
    \- PayPal.API.Signature\*  
    \- PayPal.API.Username  
    \- PayPal.BusinessID  
      
    
4.  Finally, go to **Configuration > Site Setup Wizard** in the \[Company Name\] admin console and select **PayPal Payments Pro** from the Payment Gateways section. Click the **Save** button, and your gateway setup is complete.

PayPal Standard, Express and Advanced options now include the [PayPal Credit](default.aspx?pageid=promote_paypal_credit) feature.
      