
      ---
      title: PayPal
      ---

      [![PayPal Logo](https://www.paypalobjects.com/webstatic/mktg/logo/pp_cc_mark_74x46.jpg)](https://www.paypal.com/webapps/mpp/paypal-popup "How PayPal Works")   
\[Company Name\] integrates with 5 PayPal services to provide customers different checkout options:

**PayPal Website Payment Standard** \- This is the original PayPal service. Customers are taken off of the store site to PayPal's site to complete payment, with order notification sent back to the cart. This method does not require customers to have a PayPal account.   
**PayPal Express Checkout** \- This service also takes customers off of the store site to pay, and brings them back for shipping and final order processing, providing notifications of new orders for store admins.   
**PayPal Payments Advanced** \- [This option](default.aspx?pageid=paypal_payments_advanced) allows customers to pay by credit card or with their PayPal account, without ever leaving your site. Payment is handled through a form on PayPal's site which is embedded on your checkout page. This means your site never 'touches' the credit card information, which is great for PCI compliance.   
**PayPal Website Payments Pro** \- This solution allows customers to pay by credit card directly through the store site and the funds will quickly and easily be posted to the named PayPal account. Note that if you enable PayPal Website Payments Pro, you also enable PayPal Express Checkout.   
**PayPal PayFlow Pro** \- Probably the #1 payment gateway among our user base. Payments are captured, transmitted and processed securely and funds will go directly to the merchant account of choice. Please see [this page](default.aspx?pageid=paypal_payflow_pro) for setup information for the PayPal PayFlow Pro gateway. Note that if you enable PayPal PayFlow Pro, you also enable PayPal Express Checkout.

PayPal Standard, Express and Advanced options now include the [PayPal Credit](https://www.paypal.com/webapps/mpp/billmelater-productoverview) feature.  
  
Only one non-gateway PayPal service can be enabled at one time on the checkout page. If multiple methods are enabled (PayPal Standard and PayPal Express Checkout, for example) only one will be shown. The options are shown in this order of precedence:

*   [PayPal Payments Advanced](default.aspx?pageid=paypal_payments_advanced)
*   PayPal Express Checkout
*   PayPal Website Payment Standard

PayPal Account Creation
=======================

These steps are required for all 3 PayPal services. Version-specific additional directions are provided below.

1.  Open a PayPal Business account by clicking the PayPal logo at the top of this page.  
      
    
2.  Log into your Paypal Account  
      
    
3.  Click on the Profile tab  
      
    
4.  Click the "View details" link in the API Access section  
      
    
5.  Click the “Request API Credentials” link. If you see information on this page about 'Certificates', the wrong integration method was chosen on a previous attempt. Click the 'Remove' button to clear out the certificate, and then move on to step 6 choosing the Signature method.  
      
    
6.  Choose the API Signature method  
      
    
7.  Agree to the terms and click submit  
      
    
8.  Click [this link](https://www.paypal.com/us/cgi-bin/webscr?cmd=_get-api-signature&generic-flow=true) and enter the username and password you created for your PayPal Business account. You will be provided with the 3 API values needed for further steps below.

PayPal Standard Setup
=====================

Once you have followed the steps in the 'PayPal Account Creation' section and have your PayPal account details, to enable PayPal Standard:

1.  In the \[Company Name\] admin console, go to **Configuration > Site Setup Wizard**.  
      
    
2.  In the Payment Methods section, click the **configure** link next to the **PayPal Payments Standard** entry.  
      
    
3.  Enter the email address associated with your PayPal account in the **Paypal Account Email Address** field.  
     ![](images/1415736063678.png)   
      
    
4.  Click **Save and Close**.  
      
    
5.  Finally, check the box next to PayPal Website Payments Standard and then click the **Save** button at the top or bottom of the page.  
    The following [Settings](default.aspx?pageid=settings) may also need to be adjusted, depending on your store's needs:
    
    **Setting**
    
    **Description**
    
    PayPal.DefaultLocaleCode
    
    Two-character locale code for pages displayed by PayPal (on Paypal's end, not your storefront). Supported values: AU, DE, FR, IT, GB, ES, US
    
    PayPal.ForceCapture
    
    If this is set to true, orders placed through PayPal will always be captured immediately, regardless of the [transaction mode](default.aspx?pageid=transaction_modes) in use for the rest of the site.
    
    PayPal.RequireConfirmedAddress
    
    If this is set to **Yes**, only customers who have verified their address through PayPal will be allowed to complete payment.
    
    PayPal.UseInstantNotification
    
    PayPal orders generally require the customer to click a 'Return to Merchant' button at the end to complete checkout. Customers don't always do this, which can lead to lost orders. PayPal has created a service called 'Instant Payment Notification' that cuts down on the frequency of this. If you are using that service (configured on PayPal's end), set this Setting to Yes. If this is set to Yes, you should also set the PayPal.ReturnOKURL Setting to 'default.aspx'.
    

PayPal Express Checkout
=======================

\[page:paypal\_express\_checkout\]  

PayPal Payments Pro
===================

\[page:paypal\_payments\_pro\]

Telephone Support
=================

*   If you have sales related questions about setting up NEW PayPal service and would like to speak directly to a PayPal Product Specialist, call 877-455-1484.
*   If you have customer service related questions regarding an EXISTING PayPal account and would like to speak directly to a PayPal Customer Service agent, call 888-221-1161.
      