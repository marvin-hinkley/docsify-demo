
      ---
      title: Order Processing
      ---

      Unless otherwise noted, all actions described in this article take place on the [Orders > Manage Orders](default.aspx?pageid=view_manage_orders) page in the \[Company Name\] admin console. These are the basic tasks necessary for handling orders once they have been placed on the site.

**Collecting Payment**
======================

Depending on the [payment methods](default.aspx?pageid=payment_method) you accept and your [transaction mode](default.aspx?pageid=transaction_modes), it may be necessary to take manual steps to collect payment on new orders. The steps are described below:   
  
​Are you spending hours processing your online orders? T-HUB is an easy to use multi-channel Order Manager solution to help integrate your ecommerce stores with QuickBooks and shipping services. If you are an ecommerce merchant selling on one or more websites and use QuickBooks to manage your operations, T-HUB will streamline your operations and save you lots of time to focus on growing your business.  

![](images/t-hub_pic-gr.png)

  

Automated Payment Methods
=========================

If using one of the supported payment gateways, or any method of [PayPal](default.aspx?pageid=paypal) alternate checkout, collecting payment is as simple as clicking the **Capture** button on a new order. The software will call the gateway and instruct it to transfer the authorized amount from the customer's account.  
  
 ![](images/1416249305300.png)  

Check or Purchase Order
=======================

For orders which are paid by check or purchase order, the majority of order processing must be handled outside of the software. Customers will be emailed a receipt with their order total, but there is usually going to be extra paperwork required to contact them, inform them of where to send payment, etc. \[Company Name\] does not handle any of that, it should be done manually or through your accounting package. Once payment has been received, click the **Capture** button on the order to indicate that.  
  
 ![](images/1416249364853.png)  

Delivery Details
================

If you are using [FedEx Shipping Manager](default.aspx?pageid=fedex_shipping_manager), [ShipWire](default.aspx?pageid=shipwire), or [any other supported label software](default.aspx?pageid=import_export_shipping_info), the shipping for orders is handled in bulk, through other pages of the admin console. Otherwise, each order needs to have the shipping information added manually to the Delivery Details section of the Order page.  
  
 ![](images/1416249915645.png)  

Once the carrier, tracking number, and shipping date are filled in, clicking the **Mark As Shipped** button sends the customer an email with their shipping information.   
  

  

Ad-hoc Transactions
===================

Ad-hoc transactions allow you to make partial refunds, or add to the cost of an order. The option is only available if the order's TransactionState is **Captured**, and the option appears in the Order Processing Actions dropdown menu.  
  
 ![](images/1416250141583.png)  

  
  

To perform a transaction, select  **Create Ad-Hoc Charge / Refund** from the Order Processing Actions dropdown within the Payment Details section on the Order page, and click the **Submit** button, then fill in the required fields on the window that opens (your screen may look slightly different depending on your gateway and the type of transaction):  
  
 ![](images/1416250236234.png)  

  

Void/Refunds
============

These are the 4 options for canceling an order, these are available from the Order Processing Actions dropdown in the Payment Details section on the Order page:

*   **Void** - Only orders that have not been captured may be voided. If the payment method went through a live gateway, the software notifies the gateway to cancel the transaction.   
      
    
*   **Refund** - Refunds are used on orders that have been captured. The payment gateway is notified to reverse the charges (if applicable).   
      
    
*   **Force Refund** - This button is only to be used if neither of the 2 options above will work. The force refund button ignores the payment method of the order and does not contact the gateway. The order is marked as refunded within the \[Company Name\] software only! If a payment gateway or other accounting package was used, the refund will need to be handled there separately. This is often used for 'paper' payment methods such as checks and purchase orders.  
      
    
*   **Force Void** - This allows Pending orders to be voided. It can be accessed from the admin console in the Order page. The force void button ignores the payment method of the order and does not contact the gateway. The order is marked as voided within the software only!! Once an order is force voided, the Transaction State will be "Force Voided". The Voided On date will also be populated. The Void, Force Void, Refund and Force Refund buttons will no longer be visible. And it unwinds the transaction at the same time restores the inventory.
      