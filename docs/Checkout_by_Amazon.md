
      ---
      title: Checkout by Amazon
      ---

      Checkout by Amazon is a payment method that combines your site's normal checkout process with Amazon's secure offsite payment information collection and verification. Customers initiate checkout on your site, and choose from your site's normal shipping methods on-site, but credit card information is entered on Amazon's site through a separate window that opens 'on top of' the store site.

[Click here](https://payments.amazon.com/sdui/sdui/business/cba?apaysccid=RPASPDNS) to sign up for a Checkout By Amazon (CBA) account.

**NOTE: [Checkout By Amazon](https://payments.amazon.com/help/81709) is no longer accepting new accounts, so this article is only valid if you are an existing CBA user.**

Enabling Checkout by Amazon
===========================

To enable the Checkout By Amazon payment method:

1.  In the \[Company Name\] admin console, go to **Configuration > Site Setup Wizard**.  
      
    
2.  Check the box next to **Checkout By Amazon** and then click the **Save** button at the top or bottom of the page.  
      
    
3.  In the Payment Methods Accepted section, click the **configure** link next to the **Checkout By Amazon** entry.  
      
    
4.  Enter the values you obtained from Checkout By Amazon for the **Access Key**, **Secret Key**, **Marketplace**, **Merchant ID**, **Marketplace Access Key**, and **Marketplace Secret Key**.  
      ![](images/1415721338606.png)  
      
      
    
5.  Set the **Order Fulfillment Type** to your desired setting. This controls when an order placed through Checkout By Amazon is marked as shipped on Amazon's end. The options are:  
      
    **Instant** - As soon as Amazon notifies the storefront that the order was successful (note that this can be up to several hours after the order is actually placed, as it takes time for payment to clear on Amazon's end). In this case, Amazon will notify the store that the order is ready to ship, and both the storefront and Amazon will automatically mark the order as shipped.  
      
    **MarkedAsShipped** - This will mark the order as shipped on Amazon's end when you do so in the admin console.  
      
    **Never** - The storefront will never notify Amazon's end of order shipping. All orders will have to be manually marked as shipped in Seller Central.  
      
    Currently this setting has no effect on the integration. Once the order is placed the cart does not call the Seller Central. All order updates must be set directly in Seller Central at this time.  
      
    
6.  Click **Save and Close**.  
      
    
7.  Finally, log into your [Seller Central](https://sellercentral.amazon.com/gp/homepage.html) account, go to **Settings > Checkout Pipeline Settings**, and click the **Edit** button on the top section of settings. Set your Merchant URL to https://www.yoursite.com/cbacallback.aspx

Notes
=====

*   The Checkout By Amazon integration currently does not support multiship orders.  
      
    
*   After you create your basic Checkout by Amazon account through Seller Central, you will need to get a Marketplace Access Key & Marketplace Secret Key (used in step 3 above). There is no charge for this and it can be done through your Seller Central account, but those values are not generated automatically when you register, you must request them manually.  
      
    
*   Order management actions such as Capture, Void, Refund, etc must be performed in both Seller Central and in the storefront admin console. They do not communicate with each other after the initial order is placed.  
      
    
*   Orders placed through Checkout By Amazon cannot be edited.  
      
    
*   Amazon has strict rules on how long they will allow each store to take to ship an item. If you do not mark orders as shipped within the time period they allow, Amazon will cancel the order and refund the customer. Make sure you are keeping up with orders in Seller Central!  
      
    
*   Amazon requires that your site use an SSL certificate from one of the certificate authorities on [this list](https://payments.amazon.com/sdui/sdui/helpTab/Checkout-by-Amazon/Technical-Resources/SSL-Certificates-and-the-Callback-API) for their callbacks. If you are using a cert from another CA, you will not be able to use Checkout by Amazon.  
      
    
*   CBA is not a valid checkout method at this time on the [Mobile version](default.aspx?pageid=mobile_skin).  
      
    
*   If you are using Checkout by Amazon in Europe, then please go to your admin console, and go to **Configuration > Settings**, and search for the word Amazon and update the parameters with the values below:
    *   CheckoutByAmazon.CBAServiceSandboxUrl : https://payments-sandbox.amazon.co.uk/cba/api/purchasecontract/
    *   CheckoutByAmazon.CBAServiceUrl : https://payments.amazon.co.uk/cba/api/purchasecontract/
    *   CheckoutByAmazon.WidgetSandboxUrl : https://static-eu.payments-amazon.com/cba/js/gb/sandbox/PaymentWidgets.js
    *   CheckoutByAmazon.WidgetUrl : https://static-eu.payments-amazon.com/cba/js/gb/PaymentWidgets.js
      