
      ---
      title: Quantity Discounts
      ---

      From the **Products** Menu, click **Manage Products**, then click **Quantity Discounts**.  
  
Quantity discounts allow store administrators to grant customers discounts for buying in bulk. These discounts are taken off before [customer level discounts](default.aspx?pageid=customer_levels) and [promotions](default.aspx?pageid=promotions) are deducted. On the main quantity discount page, store administrators can select an existing discount from the list to view/edit it, or click **Add New** to create a new discount table.

 ![](images/qd1.jpg)  
  
  

### **

Creating a Quantity Discount Table
==================================

**

To create a new discount table, click the **Add New** button, fill in the fields below, then click **Save**.

 ![](images/1415990516024.png)

  

The **Name** will not be displayed to customers, this is used only in the admin console as an identifier when assigning products to a Quantity Discount Table.  
**Discount type** can be either percentage, or a flat dollar (or other currency) off. Note that this is a per-item discount.  
  
Once the table has been created with the basic information, a **Quantity Discount Table Rows** section will appear and you can create Low/High ranges and associated discounts.  
  
Enter values for the first Low/High range, and click Save. Additional rows will appear each time the Quantity Discount Table is saved.  
  
 ![](images/1415990741402.png)  
  

  

Editing a Quantity Discount Table
=================================

To edit an existing table, click its name from the list on the Quantity Discounts page. Use the **Delete** button to delete a Low/High discount range, or use the **New** fields to create a new discount.

 ![](images/1415990856699.png)

  

Quantity Discount Display
=========================

Quantity discounts display on product detail pages on the site's front-end. These discounts will appear one of two ways, depending on the ShowQuantityDiscountTablesInline [Setting](default.aspx?pageid=settings).

ShowQuantityDiscountTablesInline = **Yes**

 ![](images/1416326926143.png)

  

ShowQuantityDiscountTablesInline = **No**(customers see the table when they mouse-over the 'what's this' link)  
  
 ![](images/1416326977164.png)

Also note that the **QuantityDiscount.PercentDecimalPlaces** [Setting](default.aspx?pageid=settings) can be used to set how many decimal places to display in your quantity discount tables, when using percent-type discounts.

Qualifying for a Quantity Discount
==================================

Quantity discounts are calculated per product, not for an entire order. If a discount requires a minimum purchase of 10, customers must purchase 10+ of each product to get the discount, they cannot combine multiple products to reach that minimum.

For products that have sizes or colors, the quantity discount handling can vary, and depends on the **QuantityDiscount.CombineQuantityByProduct** [Setting](default.aspx?pageid=settings):

**Yes:** All line items of a specific product will be combined when determining whether an order qualifies for a quantity discount. For example, if product 14 comes in red, green, and blue, all instances of product 14 will be counted towards the quantity discount, regardless of color chosen.  
**No:** Each line item of a specific product will be considered individually when determining whether an order qualifies for quantity discounts. For example, if product 14 comes in red, green, and blue and a customer orders some green and some blue, the quantity of the blue items will be checked to see if it qualifies for a quantity discount, and then green will be checked separately.

Assigning Quantity Discount
===========================

Quantity discounts can be assigned to individual [products](default.aspx?pageid=manage_products), or entire [entities](default.aspx?pageid=product_groups). If assigned to an entity, all products mapped to that entity will get the quantity discount.   
  
To assign a discount to an entity, edit that entity and select a discount table from the **Quantity Discount Table** dropdown menu:  
  
 ![](images/1415992129358.png) 

  

To assign a discount to a product, edit that product and select a discount table from the **Quantity Discount Table** dropdown menu:  
  
 ![](images/1415992211482.png)
      