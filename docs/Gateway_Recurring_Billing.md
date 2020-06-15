
      ---
      title: Gateway Recurring Billing
      ---

      The gateway recurring billing feature allows store admins who are using the **Authorize.net**, or **PayPal**  payment gateways and checkouts to handle recurring billing directly through the merchant gateway. This makes processing orders faster, and alleviates the need for the shopping cart to store the customer's credit card information.   
  

The recurring payment cannot be set to $0.00 and the minimum recurring period is 7 days.

Initial Configuration
=====================

To enable this feature, first make the following [Settings](default.aspx?pageid=settings) changes:

*   Set **Recurring.UseGatewayInternalBilling** to true 
*   Set **Recurring.SendOrderEMailToCustomer** to true (an email will be sent for each occurrence of a shipment)

To configure the product to be recurring, navigate to the Product Variant under [Products > Manage Products](default.aspx?pageid=manage_products) and set the “Is Recurring” attribute to Yes and select an interval frequency and interval type. Click Update. Click [here](default.aspx?pageid=recurring_orders1) for more information on recurring orders.  
  
Configuring your products should be done AFTER the gateway is set up, so that some values are stored properly for them in the database.

New Orders
==========

When a customer places a recurring item in their shopping cart, it will be indicated that it is an Auto-Ship item, and the interval is shown.   
  
When a customer places the original order, the initial charge is applied as an ordinary order and a recurring order subscription is created with the gateway using a start date of the next occurrence. The gateway will then automatically process the charge again on the recurring schedule. In order to create the corresponding orders in the storefront, you must do the following:   
  

Authorize.net:
--------------

To completely automate the process, configure your Silent Post URL in order to have the storefront automatically generate orders when Authorize.net performs the recurring charge. This is done by:

*   Logging into your Authorize.net account 
*   Going to the Account tab 
*   Selecting Settings in the navigation menu 
*   Under Transaction Format Settings/Transaction Response Settings, select Silent Post URL. Set the URL to the fully-qualified path to authnetpost.aspx on your site (i.e. http://www.yourstore.com/authnetpost.aspx )

If you are NOT using the Silent Post URL, you will need to set up Authorize.net to send you email ARB notices. These emails will contain 2 .csv files as attachments. You will need to open each attachment in notepad, and then copy/paste all the text into the box on the **Orders > Recurring Orders** > **Recurring Shipments** (to import the status from the gateway). You can process both the successful.csv and failed.csv files at the same time by pasting them into the text box one after the other.   
Once the text box is populated, click the **Process Records** button. If there are a large number of records, this may take some time, so be patient. You will see the results of each record that processes displayed in a new text box on the right hand side of the page. If the results show anything other than “1=OK” then you may need to follow up. It is recommended that you copy/paste the results to a document for future reference if there are orders that failed.   
  

PayPal Payments Advanced, PayPal Payflow Pro:
---------------------------------------------

To process recurring payments:

*   Go to **Orders > Recurring Orders** in the admin console, then click **Recurring Shipments**, then click the blue button for **Get Today's PayflowPro Autobill Status File** (to import the status from the Payflow gateway). Finally click the **Process Records** button. This is how the orders get created in the admin console for the recurring payments, which will be displayed in your Orders - Manage Orders menu now.  
    NOTE: Cancelled recurring profiles should not create new orders. Orders will only show up that have not been imported since the last import date up until yesterday.
*   You cannot currently checkout with products with different subscription intervals.
*   Orders cancelled in the PayPal Manager will not be reflected in the admin console, however the order can be cancelled by the customer at any time through their cart Account page and this will be reflected in PayPal and an email notification will be kicked off. If a merchant wants a recurring subscription to be cancelled and reflected in their admin console, they need to use the **Orders > Recurring Orders** page to cancel the order (this will cancel the recurring order on both the cart and the PayPal side).

  

PayPal Express and PayPal Payments Pro:
---------------------------------------

To process recurring payments:

*   IPN (Instant Payment Notification) must be enabled with site.com/paypalnotification.aspx set as the notification URL in the PayPal account. 
*   Admins and customers can cancel recurring profiles on PayPal's end and the storefront will be notified and cancel future billing. 
*   PayPal Express does not use **Recurring Shipments** (to import the status from the gateway)  in the admin console. When recurring orders are due they are handled via the IPN (Instant Payment Notification).

  

PayPal Standard:
----------------

To process recurring payments:

*   The **Use Instant Notification** field in the [Site Setup Wizard](default.aspx?pageid=site_setup_wizard) settings for PayPal Payments Standard must be set to **Yes** 
*   IPN must be enabled with site.com/paypalnotification.aspx set as the notification URL in the PayPal account. 
*   Admins and customers can cancel recurring profiles on PayPal's end and the storefront will be notified and cancel future billing.
*   PayPal Standard does not use **Recurring Shipments** (to import the status from the gateway)  in the admin console. When recurring orders are due they are handled via the IPN (Instant Payment Notification). 
*   With PayPal standard used for recurring, the recurring product is the only item that can be purchased. No other products can be in the shopping cart and purchased with the recurring item. The cart handles this by only allowing the user to have that item in the cart in order to proceed with purchasing that item.

Declined Transactions
=====================

If the recurring order instance results in a declined credit card transaction, a corresponding order will not get created in the storefront, but a row will be added to the Failed Transactions list for your review.   
  
The failed transaction record includes the original order number, the gateway’s subscription ID, and the gateway transaction ID for the decline.   
  
When a decline occurs for a recurring order, the customer is automatically emailed a notification requesting that they update their billing information on the account page. A store admin can also update the billing info. See the section “Updating Billing Details and Canceling Orders” below.

Updating Billing Details and Cancelling Orders
==============================================

The customer and store admin both have the ability to cancel future occurrences and update billing details on recurring orders. The billing details for a recurring order will have to be updated for expired cards or new billing addresses.   
  

Customer Changes
----------------

*   The customer may log into the storefront and go to their account page to update their recurring information. The account page displays the customer’s recurring orders, and each has a button to **Stop Future Billing** and **Update Billing Info**. 
*   If the **Update Billing Info** button is clicked, a form is displayed for the address and credit card details to be added and submitted to the gateway. 
*   If the **Stop Future Billing** button is clicked, a request is sent to the gateway to cancel all future occurrences of the order.

Store Admin Changes:
--------------------

*   The admin can view active recurring orders for a customer from that customer’s Order History page, where each one has a button to **Stop Future Billing**. If the Stop Future Billing button is clicked, a request is sent to the gateway to cancel all future occurrences of the order.
*   To EDIT the customer information for the recurring order such as Billing Address and Credit Card, access the recurring order in the **ORDERS - RECURRING ORDERS** menu. The customer information in the gateway will also be updated.
NOTE that this edit will overwrite the customer's billing address record.

Declined Transactions with PayPal PayFlow Pro
=============================================

When using the Payflow Pro gateway, the status of the subscription is retrieved from the gateway when the customer order history page is displayed. Depending on the status of the subscription there may be other buttons available. These include **Retry Payment** and **Restart Billing**. If the Payflow Pro subscription status is “TOO MANY FAILURES” then the Retry Payment button can be used to reattempt the payment and reactivate the subscription if the attempt is successful. If the subscription has been previously canceled by a **Stop Future Billing** button, then the Restart Billing button will be available for the subscription to be resumed. When the **Restart Billing** button is used, the recurring schedule will be altered with a starting date of the current date.
      