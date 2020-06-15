
      ---
      title: Customer Levels
      ---

      From the **Contacts** Menu, click **Customer Levels**.   
The customer level feature allows you to put your customers into groups, which can receive discounts, special prices, be tax exempt, etc. You can also use customer levels to determine which visitors on your site see which products.   
Customers that belong to these levels will see the level name next to their own name in the default skins, and will see any discounted prices they receive on product detail pages.

Customer level discounts, extended pricing, coupons, and quantity discounts can all end up combining to create the final price the customer pays.

This interaction can be very complex, and it is entirely possible for the cart to arrive at a final price that you cannot explain to your customers. Our advice is to keep your pricing schemes as simple as possible to avoid confusion.  
  
On this page, store administrators can create new levels, edit or delete the existing ones, or view a list of which customers are in each level.  
  
 ![](images/1415820641379.png) 

### **

Adding a Customer Level
=======================

**

To create a new customer level, click  **Create** and fill in the following fields:  
  
  ![](images/1415820779857.png) 

**Field Name**

**Description**

Name

This is the customer level name. This will be visible to customers who belong to this level. If your store uses mulitple [locales](default.aspx?pageid=locale_settings), you can create different names per locale.

Level Discount Percent

If you want this customer level to get a certain percentage off all products' base prices (Customer levels ignore sale prices entirely ) then put the percentage here.

Level Discount Amount

If you want this customer level to get a certain amount off all products' base prices (Customer levels ignore sale prices entirely ) then put that amount here.

Level Includes Free Shipping

If this is set to Yes, customers in this level will get free shipping on all orders, regardless of what they purchase. If set to No, normal shipping prices are added.

Level Allows Quantity Discounts

If this is set to Yes, customers in this level can take advantage of whatever quantity discount tables are assigned to the products they purchase. If it's set to No, these customers will not get quantity discounts.

Level Allows Purchase Orders

If this is set to Yes, and purchase orders are set up as an allowed [payment method](default.aspx?pageid=payment_method), customers in this level will be allowed to use POs to pay. If set to No, they will not be able to even if other customers can.

Level has no Tax on Orders

If this is set to Yes, customers in this level do not pay taxes on orders. If set to No, tax is charged normally.

Level Allows Coupons on Orders

If this is set to Yes, customers in this level can use coupons normally. If it is set to No, the coupon pane will not even appear for them on the shopping cart page.

Level Discounts Also Apply to Extended Prices

If this is set to Yes, and you have set up [extended prices](default.aspx?pageid=extended_prices), customers will receive the discount percentage/amount off of those extended prices. If this is set to No, they will get whatever extended prices were set up with no further discount.

### **

Managing Customer Level Membership
==================================

**

On this page, you can view the list of customers that belong to a certain customer level. You get here by clicking the **View Customers Of This Level** button on the main customer levels page. You can view customers by clicking on one of the letters to view them alphabetically, or search for a specific email address.   
  
Customers are also added to or removed from levels through this page. To add a customer, enter their email address in the text field and click **Add Customer to This Level**. To remove one, click the **Clear Level** button.  
  
 ![](images/1415821089840.png)  
  

Auto-Assigning Customer Levels
==============================

[Wholesale](default.aspx?pageid=wholesale_store_setup) stores may want all new customers to be in a non-zero customer level. To set that up, simply set the **DefaultCustomerLevelID** [Setting](default.aspx?pageid=settings) to the ID of the customer level you wish customers to be assigned to by default.  
  
The level you set **DefaultCustomerLevelID** to will essentially be a 'new registrant' level which will not see pricing yet, and your managed levels (all other non-zero levels) will be your Wholesaler levels which you assign manually to the new registrants.  

### **

Other Information
=================

**

*   Customer levels ignore sale prices. Any customer belonging to a non-0 customer level will not see sale prices, even if they have no other discounts/extended pricing set up. 
*   For details on setting up extended pricing (special customer level pricing aside from fixed amounts off), see [here](default.aspx?pageid=extended_prices).
*   For information on filtering which products your customers see based on customer level, see [this page](default.aspx?pageid=product_filtering).
      