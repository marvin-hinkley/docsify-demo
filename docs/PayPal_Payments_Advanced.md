
      ---
      title: PayPal Payments Advanced
      ---

      PayPal Payments Advanced allows customers to pay using either a credit card or their PayPal account without leaving your site. Payment information is entered in a form hosted by PayPal and embedded on your checkout page. Your site never touches payment information, which simplifies PCI compliance, and your customers are able to use their PayPal accounts to pay without the extra steps of paying through another site.

This service is available for US and Canadian merchants. Click [here](http://www.aspdotnetstorefront.com/linkmanager.aspx?topic=paypalpaymentsadvanced&type=info) for more information regarding PayPal Payments Advanced.

[Sign up for PayPal Payments Advanced](http://www.aspdotnetstorefront.com/linkmanager.aspx?topic=paypalpaymentsadvanced&type=signup)

la

Before you can configure the storefront to use this new payment method, you’ll need to create an account for it. This can be done by contacting PayPal directly at 1-866-784-3640.   
  

Setting up PayPal Payments Advanced in PayPal Manager
=====================================================

Below are examples of typical setup, which should only require a few changes. Please consult with a knowledgeable PayPal Payments Advanced support technician for details.  
  
 ![](images/1415646619947.png)  
  
![](images/PPA%20setup.png)  
  
**The important items are:**

1.  Enter your storefront primary domain for the Cancel, Error and Return URL fields.
2.  Set Use Silent Post - YES and http://www.yourdomain.com/paypalembeddedcheckoutok.aspx
3.  Set Enable Secure Token - YES
4.  Select Layout C in the Hosted Checkout Pages - Customize menu (Layout C is the only properly supported Layout option.)

NOTE: Be sure to set the **Transaction Process Mode** appropriately for your site for either TEST mode (run test transactions) or LIVE (process real transactions).  
  

Enabling PayPal Payments Advanced in your storefront
====================================================

To turn on this feature, simply follow these steps:

1.  In the \[Company Name\] admin console, go to **Configuration > Site Setup Wizard**.
2.  In the Payment Processing Solutions section, click the **configure** link next to **PayPal Payments Advanced**.
3.  Enter the values you obtained when you created your PayPal account for Partner, Merchant Login, User, and Password.
4.  Click **Save and Close**.
5.  Select the radio button next to **PayPal Payments Advanced**.
6.  Finally, select the radio button next to **Credit Card** (verify the **configure** settings are set properly for this as well) and then click the **Save** button at the top or bottom of the page.

Enabling PayPal Express
=======================

1.  In your PayPal account, setup the PayPal Express Checkout section. If it does not appear within your setup, get an account set up with PayPal using the same business id email as your Advanced account.
2.  In the \[Company Name\] Site Setup Wizard, configure the PayPal Express with the credentials you obtain from PayPal for your [PayPal Express](default.aspx?pageid=paypal_express_checkout) checkout.

Checking out with PayPal Payments Advanced
==========================================

To pay through this payment method, customers add to the cart and go through the checkout process normally. On the final payment step, the payment form will be shown in an iFrame within your normal checkout page. Customers enter their payment information within that frame, and when payment is completed they’ll be directed to your normal order confirmation page.

Notes
-----

*   If PayPal Payments Advanced is enabled, PayPal Website Payments Standard and PayPal Express Checkout will not be displayed on your payment page. Since the PayPal Payments Advanced frame also contains a link to pay through PayPal Express, your customers will still be able to quickly and easily pay with their PayPal accounts.
*   PayPal Payments Advanced is supported on standard checkout and Smart One Page checkout only. Basic one page checkout is not supported.
*   See the document [here](https://cms.paypal.com/cms_content/US/en_US/files/developer/PayflowGateway_Guide.pdf) for a list of PayPal's error messages and what can be done if they're encountered on your site.
*   Turning on any PayPal PayFlow product (PayFlowPro, PayPal Payments Advanced, etc) also enables PayPal Express.
*   PayPal Standard, Express and Advanced options now include the [PayPal Credit](mailto:) feature. Navigate to [Configuration > Promote PayPal Credit](default.aspx?pageid=promote_paypal_credit) in your admin console to configure.
*   When using PayPal Payments Advanced with Smart One Page Checkout, Anonymous.AllowAlreadyRegisteredEmail or AllowCustomerDuplicateEMailAddresses have no affect on this scenario, and the [Setting](default.aspx?pageid=settings) PasswordIsOptionalDuringCheckout will provide the following behavior:
    *   PasswordIsOptionalDuringCheckout FALSE: This will force any customer making a purchase to have a registered account, but will force them to be registered without a password (need to use "Forgot Password?" next time), and the customer account will be blank (they will need to enter that info sometime in their account), but they will have Billing and Shipping addresses completed.
    *   PasswordIsOptionalDuringCheckout TRUE: This will allow any customers to make purchases without issue, but will not give them any option to register during the purchase, and their purchases will be as an anonymous customer (IsRegistered - NO), and they will not show up in the View/Edit Customer grid in admin. They can then sign up for an account manually on your site, although previous anonymous purchases will not be associated with the account automatically when created.
      