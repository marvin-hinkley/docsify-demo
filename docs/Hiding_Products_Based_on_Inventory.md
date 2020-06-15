
      ---
      title: Hiding Products Based on Inventory
      ---

      Many store administrators will want to inform customers ahead of time of whether or not products are in stock. This can help prevent back-order situations, which can lead to frustrated customers and refunds.   
  
There are 3 ways of doing this: hiding the product entirely so the customer never sees it, showing the product but informing the customer up front of whether or not it is in stock, or showing the product but forcibly preventing customers from adding more than is on hand to their cart.

Hiding Out of Stock Products
============================

1.  Go to **Configuration > Settings**  
      
    
2.  Search for the “HideProductsWithLessThanThisInventoryLevel” Setting, and put in a value. This will prevent products with an inventory less than that value from showing up on entity pages.  
      
    If you wish for all products to show, regardless of inventory levels, leave that Setting set to -1. If you need to reset it back to -1, you first need to access _advanced_ and set the Setting to String type. Modify the value to -1, save, and reset type back to Integer.  
      
    
3.  Click **Save**.

For multi-variant products, the inventory level for the default variant is used to determine if a product is shown. If the default variant has less than N, the product won’t be shown, even if other variants have inventory greater than N.

Displaying In-Stock Status
==========================

1.  Go to **Configuration > Settings  
    **
2.  Search for the “ShowInventoryTable” Setting, and set it to Yes. Customers will now see Yes/No for “In Stock” on each product page.  
    Store administrators will see exact inventory quantities when viewing product pages, customers will only see Yes/No.  
      
    
3.  Click Update.

Setting Limitations On Adding Products To Cart
==============================================

1.  Go to **Configuration > Settings  
    **
2.  Search for the “Inventory.LimitCartToQuantityOnHand” Setting, and set it to Yes. This allows customers to add products to the cart as long as the quantity purchased does exceed the quantity on hand. If they try to purchase too many they will see a popup message, and the quantity will be adjusted to the max in stock.
      