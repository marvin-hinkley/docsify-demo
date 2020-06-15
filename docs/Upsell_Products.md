
      ---
      title: Upsell Products
      ---

      The upsell feature gives store administrators the ability to cross-sell or recommend additional products to their customers.

### **

Setup
=====

**

1.  First, list the IDs of the products you would like to upsell (this must be done for each product) on the [Manage Products](default.aspx?pageid=manage_products) page in the admin console, under the **Options** tab. You can also specify a discount for upsell products if desired. This discount will only be applied if the product is added to the cart through the upsell window on another product page. Adding that product directly to the cart from its own product page will not apply the discount.  
     ![](images/1416421033956.png)  
      
    If you don't know the ID's of the products offhand, click on the **Upsell Products Helper** bar to the right and you'll be shown a search box, enter the name of a product you are searching for, and all matching products will be displayed. Check the ones you want, and they will be added to the list of upsell products.  
      
    
2.  Configure these [Settings](default.aspx?pageid=settings) as desired for your site:
    
    **Setting Name**
    
    **Description**
    
    UpsellProductsGridColWidth
    
    This controls how many upsell products to display per row.
    
    ShowUpsellProductsOnCartPage
    
    If this is set to true, upsell products will also be displayed on the shopping cart page (based on the products already in the cart).
    
    UpsellProductsLimitNumberOnCart
    
    If ShowUpsellProductsOnCartPage is set to true, this determines how many upsell products to display.
    

Display
=======

Upsell products configured this way will display at the bottom of product detail pages and the shopping cart:  
  
![](images/1416421210110.png)

Restrictions
============

Upsell products must meet the following criteria or they will not display:

*   Cannot have sizes
*   Cannot have colors
*   Cannot require a text option
*   Cannot be kits
*   Must be published
*   Cannot be deleted
*   Cannot already be in the shopping cart
*   The default product variant of the Upsell product will be added to the cart
      