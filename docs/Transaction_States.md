
      ---
      title: Transaction States
      ---

      The different transaction states depend on the payment method and transaction mode of an order. These can be viewed on the **[Orders > Manage Orders](default.aspx?pageid=view_manage_orders)** page in the \[Company Name\] admin console. The different transaction states are described below:   

Authorized
==========

*   This state means that the credit card of the customer has been verified, but payment has not been processed yet. The **Capture** button must be clicked in order for payment to be collected. 
*   If the [transaction mode](default.aspx?pageid=transaction_modes) is auth, then this will be the default state after the order has been placed. 
*   The order cannot be marked as fraud if it is still in the authorized state. 
*   Ad Hoc Charge/Refund cannot be created while in this state. 
*   It can only be voided or captured.

Captured
========

*   The payment has been processed in this state, wherein the payment has been transferred from the customer's account to the merchant's account. 
*   If the [transaction mode](default.aspx?pageid=transaction_modes) is auth capture, then this is the state the order will default to after being placed. 
*   The order can be [voided, refunded or force refunded](default.aspx?pageid=order_processing). 
*   It can also be marked as fraud. 
*   An [Ad-Hoc Charge/Refund](default.aspx?pageid=order_processing) can also be made. 
*   It can be marked as Ready To Ship, Shipped and/or Printed.

Voided
======

*   A [](http://manual.aspdotnetstorefront.com/p-1056-order-processing.aspx)[voided](default.aspx?pageid=order_processing) order is cancelled. 
*   Once an order is voided, it can only be marked as Shipped and/or Printed.

Force Voided
============

*   This allows pending orders to be voided. 
*   It also unwinds the transaction at the same time restores the inventory. 
*   It can only be marked as Shipped and/or Printed.

Refunded
========

*   The payment of the customer will be returned or repaid. 
*   This can only be marked as Shipped and/or Printed.

Fraud
=====

*   This state is the result of clicking the **Mark As Fraud** button in a captured transaction. 
*   Once an order is marked as fraud, the IP address of the customer will automatically be blocked. That is why there is an **Allow This IP** button, to enable the admin to grant the customer access to the store. 
*   The fraud state can still be lifted by clicking the **Clear Fraud Flag**. 
*   The **Mark As Fraud** button will not function on orders entered by admin users. 
*   It can also be marked as Shipped and/or Printed.

Pending
=======

*   These orders are still awaiting approval. 
*   This is similar to the authorized transaction state except that the [payment method](default.aspx?pageid=payment_method) here is not credit card, it is either by [check](default.aspx?pageid=checks), [cod](default.aspx?pageid=cods), [purchase order](default.aspx?pageid=purchase_orders), or [request for quote](default.aspx?pageid=request_for_quote).
*   The **Capture** button must be clicked for payment to be processed otherwise it can be voided to cancel the order. 
*   Other than that, it can only be marked as Ready to Ship, Shipped and/or Printed.
      