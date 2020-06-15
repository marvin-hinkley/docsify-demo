
      ---
      title: Products that vary by Size/Color
      ---

      Many stores sell products that have attributes like size or color that can change - for example dresses, shirts, car parts, etc. Sometimes these products will be set up as [variants](default.aspx?pageid=manage_products), so the price, SKU, weight, size, etc can be adjusted. If, however, there are only 2 attributes that change, that's often not necessary. Each variant can have 2 customer-selectable attributes (which can affect the price of the product) which can save store admins from having to create multiple variants.

Variants may only have 2 of these attributes. While these attributes can be renamed (see below), by default they are referred to as Size & Color, so that is how this guide will refer to them.

Naming the Attributes
=====================

To set up a product with customer-selectable attributes, first you have to decide what those attributes will be called. By default the software will use Size and Color, but these can be changed to whatever is required for your store - Make and Model, Weight and Height, etc.   
  
To change those values (if desired), go to **Products > Manage Products** in the \[Company Name\] admin console and navigate through the grid to the parent product of the variant you're setting up. On the **Main** tab, scroll to the bottom and set the **Color Option Prompt** and **Size Option Prompt** attributes. The values entered here will be what is used for the dropdown labels on the product detail page on your site, so set these to exactly what you want your customers to see. (e.g. Select Color OR Select Size).   

These attribute names cannot contain special characters such as &, !, etc.  
  
 ![](images/1416238832180.png)

Setting Selectable Values
=========================

Next, you need to define the options that customers can choose from in the attributes you named above. To do this, go to **Products > Manage Products** in the \[Company Name\] admin console and this time navigate to the variant level for the product you're editing. On the **Attributes** tab, fill in the following fields:  
  
 ![](images/1416239066939.png) 

  
  

**Attribute Name**

**Description**

Colors

This should be a list of the values customers can select from for this attribute. Note that this field will always be labeled 'Colors' in the admin console, regardless of what you set for the **Color Option Prompt**

Color SKU Modifiers

If desired, you can have a suffix added to the SKU when customers choose an attribute from the list defined on the line above. That suffix will display on the receipt.

Sizes

This should be a list of the values customers can select from for this attribute. Note that this field will always be labeled 'Sizes' in the admin console, regardless of what you set for the **Size Option Prompt**

Size SKU Modifiers

If desired, you can have a suffix added to the SKU when customers choose an attribute from the list defined on the line above. That suffix will display on the receipt.

Varying Price by Size and Color
===============================

Some products need to vary in price depending on the attributes the customer chooses. To do this, specify a price modifier in brackets next to each option as you define them on the **Attributes** tab. In the example below, the default variant price would be for the Medium size. Choosing Small would take $1 off the price, choosing Large would add $2 to the price.  
  
 ![](images/1416239491389.png) 

Tracking Inventory by Size and Color
====================================

If your store offers products that vary by attribute as described in this article, odds are you have different inventory levels of each size/color combination. If you need to be able to track those inventory levels through the software, it can be done with the **Track Inventory by Size and Color** feature (Using this method will not work with Kits tied to the variant).   
  
To enable this, go to **Products > Manage Products**, and navigate through the grid to the parent product of the variant you're working on. On the **Main** tab, scroll to the bottom and set the **Track Inventory by Size and Color** option to **Yes** and click **Save**.  
 ![](images/1416239703716.png)  
  
Then navigate to the variant for that product, and at the bottom of the **Main** tab there will be a new option labeled **Manage Inventory: Click Here**.  
 ![](images/1416239764436.png) 

  

Click on the **Click Here** link and you will be taken to a page where the inventory levels and other attributes can be set for every size/color combination you entered above:  
  
 ![](images/1416239797884.png) 

**Attribute Name**

**Description**

Inventory

Set this value to the quantity of that size/color combination that you have on-hand. When a customer makes a purchase, this quantity will be decremented accordingly.

Warehouse Location

This field is for internal use only, and is not used/displayed anywhere on the site. It can be used to specify which warehouse a product size/color combination is stored in if multiple locations are used.

Vendor ID

This field is for internal use only, and is not used/displayed anywhere on the site.

Vendor Full SKU

This field is for internal use only, and is not used/displayed anywhere on the site.

WeightDelta

If this size/color combination changes the weight of the product variant, the weight delta (change) can be specified here. For example, if the variant weight was specified as 3.5 which is for the medium size, a small version might have a weight delta of -.5 and an extra large version might have 2.0 (to add 2 to the weight).

Notes
=====

  
When using **Track Inventory by Size and Color**, all sizes and colors will be displayed to customers on the product detail pages. The software will not hide combinations that do not exist on-hand. For example, if no Small/Red shirts are in stock, customers will still be able to choose 'Red' after choosing 'Small'. However, when they attempt to add to the cart, they will be shown a message stating that the selected size/color combination is out of stock, and will be asked to choose another one.

This behavior can be disabled by setting the **Inventory.LimitCartToQuantityOnHand** [Setting](default.aspx?pageid=settings) to **No**. Customers will be able to purchase any size/color regardless of inventory levels.
      