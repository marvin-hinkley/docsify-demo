
      ---
      title: Shipping to Multiple Addresses (Multiship)
      ---

      By default, all products in an order ship to the same address - whichever address is currently set as the default shipping address on the customer's account. Store owners can change this however, to allow customers to ship to multiple addresses. This is especially popular around the holidays, for gift shopping.

Enabling Multiship
==================

To enable this feature, simply set the **AllowMultipleShippingAddressPerOrder** [Setting](default.aspx?pageid=settings) to Yes, and set the **MultiShipMaxItemsAllowed** [](p-978-appconfig-parameters.aspx)[Setting](default.aspx?pageid=settings) to the highest number of addresses you want to allow customers to ship to.

Each address represents another call to the shipping carrier API if you are using [realtime shipping](default.aspx?pageid=real_time_shipping_rates). Page load times can become very slow for customers with large orders. Also, please note that if you are using a [free shipping threshold](default.aspx?pageid=advanced_shipping_options), the threshold is calculated per address on multiship orders.

Using Multiship
===============

If Multiship orders are enabled, customers will see the following text on Step 2 of checkout:  
  
 ![](images/1420562147035.png)  
  

This will only appear if customers have more than one item in their cart.

When a shopper clicks the **click here** link, they will be sent to this page. For each product in the cart they can choose from existing addresses on record in the dropdown menu, or click **Add New Address** to create a new address for each item if necessary.  
  
 ![](images/1420562356103.png)  

After choosing the shipping address, shoppers will click **Continue Checkout** and arrive at the page pictured below. Each package will display the shipping methods and rates that apply to it based on the package size, weight, and destination. Shoppers can choose different methods for each package, then click **Continue Checkout** again to go to step 3 (Payment) of checkout. The prices for shipping for all of their packages will be combined into one line item on the payment page.  
  
 ![](images/1420562565780.png)
      