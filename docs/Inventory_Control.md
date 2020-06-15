
      ---
      title: Inventory Control
      ---

      _**Compunix, taking inventory management a step further.**_  
Having accurate cart inventory and grasp on inventory to purchase is key to a healthy store. The Cart provides inventory overview via the Variant's Inventory management page, however the following additional reports help with viewing and managing inventory in bulk, [Inventory Report](http://www.ecommercecartmods.com/p-34-inventory-report-for-aspdotnetstorefront.aspx), [Low Stock/Inventory Report](http://www.ecommercecartmods.com/p-30-low-stockinventory-report-for-aspdotnetstorefront.aspx),  and [Back In Stock Notification](http://www.ecommercecartmods.com/p-101-item-back-in-stock-notification.aspx) for extra out of stock inventory handling when item is not in stock allowing users to signup up to be notified.  
From the **Configuration** menu, click **Inventory Control**.   
  
This page allows store administrators to configure how the software handles inventory tracking and display of products that are out of stock. See [this page](default.aspx?pageid=hiding_products_based_on_inventory) for more information.   
  
The first 2 options control how products that are in stock (or have at least one variant in stock) are handled:  
  
 ![](images/1416243240429.png)  

**Limit cart to quantity on hand** \- If this option is checked, customers will only be able to add the maximum amount on hand to the cart. If they try to purchase too many of a product, they will see a warning message and the cart quantity will be adjusted to the quantity on hand.

**Show inventory table** \- If this option is checked, an inventory table will display on product detail pages for products that have multiple size/color attributes and are using the **Track Inventory by Size and Color** option. (Note - not all product detail pages are built to display inventory table. \[Company Name\] is delivered with a selection of product detail pages. If you want to display the inventory table and it is not showing up, try switching your display page.)  
  

Store administrators will see an actual inventory count, customers will only see Yes/No in place of stock values.

The next group of options determine how to handle out-of-stock items:  
 ![](images/1416243261752.png)  

**Hide products with less than this inventory level** \- If this option is selected, products with an inventory less than the quantity specified will be hidden from all customers. _Set the quantity to -1 to disable the hiding of out-of-stock products_  
**  
Display out of stock products** - If this is selected, stock status messages will be displayed, using the following options: 

![](images/1416243331623.png)

**Option**

**Description**

Out of stock threshold

This number determines when the 'out of stock' messages will begin showing.

"Out of stock" message on product pages:

This message will display on product detail pages for products with less stock on hand than is specified in the threshold above.

"Out of stock" message on entity pages:

This message will display on entity pages for products with less stock on hand than is specified in the threshold above.

"In stock" message on product pages:

This message will display on product detail pages for products with more stock on hand than is specified in the threshold above.

"In stock" message on entity pages:

This message will display on entity pages for products with more stock on hand than is specified in the threshold above.

Show in product pages

Checking this will cause the messages specified above to display on product detail pages.

Show in entity pages

Checking this will cause the messages specified above to display on entity pages.

The final section controls how kit options that are tied to existing variants are handled. See [this page](default.aspx?pageid=kit_products) for details on how variants can be tied to kit options.  
 ![](images/1416243418458.png)

**Enable stock hints** \- If this option is checked, each kit item will show Yes/No next to it for in stock or out of stock status. Store administrators will see actual inventory counts.

**Option**

**Description**

Show Out of Stock Messages

If Yes, kit items that are out of stock won't appear in kit groups.

Allow sale, even if out-of-stock

If No, kit items that are out of stock will be visible in kit groups, but not selectable.

  

Inventory Tracking
==================

Inventory is tracked at the variant level by default, though it can be tracked at a lower level by setting the 'Track Inventory by Size and Color' [product attribute](default.aspx?pageid=manage_products) to true (Using this method will not work with Kits tied to the variant). Kit items can also [be linked to variant inventory](default.aspx?pageid=kit_products) so that items that you sell both individually and in kits are tracked correctly.  
  
The software deducts inventory when the order is [captured](default.aspx?pageid=transaction_states), not when it's initially placed, so it is possible for customers to add items to the cart that will be out of stock when the current orders are processed. To keep inventory from going into negatives, the software will make checks at each stage of checkout and send customers back to the shopping cart page with a notification if an item has since become out of stock. Customers can then start checkout again, or add other items to the cart and start over. There is a small (milliseconds) window of time where 2 customers could check out at the same time and push an item into negative inventory, but the odds of that happening are very small.  
  
Inventory is restored if an order is voided/refunded.
      