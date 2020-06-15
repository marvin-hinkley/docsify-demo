
      ---
      title: Cardinal Commerce
      ---

      [Cardinal Commerce](http://www.cardinalcommerce.com/) is a 3rd-party service that provides secure integrations with many online payment brands (Google Checkout, BillMeLater, MyECheck, and others) and easy integration with the [Verified by Visa](http://www.visa.com/) and [MasterCard SecureCode](http://www.mastercard.com/index.html) services. \[Company Name\] uses Cardinal Commerce to enable the [eCheck](default.aspx?pageid=echecks) payment method and VBV support 'out of the box'. Cardinal's many other services would require customization to use.   
  
Supported Payment Gateways:

*   Authorize.net 
*   USAePay 
*   eProcessingNetwork 
*   Moneris eSELECT Plus
*   Sage Pay
*   SecureNet 
*   Cybersource 
*   PayPal Payflow Pro 
*   PayPal Payments Pro

Once VBV is enabled on your site, customers _may_ be taken off of the site briefly during checkout to the VBV/Securecode authentication page, _if_ they are enrolled in the program, or their merchant is a program participant, or they are invited to sign up during checkout. Once they have entered their information and verified their identity, they will be returned to your site to complete payment.  

Enabling Verified by Visa
=========================

Admin Console
-------------

1.  First, set the **CardinalCommerce.Centinel.Enabled** [Setting](default.aspx?pageid=settings) to **Yes**.  
      
    
2.  Configure the following Settings with your personal account information:  
    CardinalCommerce.Centinel.MerchantID (Note: leave this set to 100 while in testing)  
    CardinalCommerce.Centinel.ProcessorID (Note: leave this set to 800 while in testing)  
    CardinalCommerce.Centinel.TransactionPwd  
      
    
3.  Set the **CardinalCommerce.Centinel.IsLive** Setting to **Yes**. (Note: leave this set to No while in testing)

**Skin** 
---------

To display the Verified By Visa/SecureCode logo, add the [skin token](default.aspx?pageid=skinning_tokens) to your skin.  
 ![](images/1415735202488.png)   
In the Cardinal Commerce Profile settings (Cardinal Commerce account management), the \* CAVV/XID Format : should be set to "Hex"
      