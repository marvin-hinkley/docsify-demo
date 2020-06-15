
      ---
      title: Kit Products
      ---

      Kit products allow store administrators to offer highly-customizable products to customers. Prices and weights can vary by the choices customers make, and you can even have the software use products sold separately on your site as components of the kit, for inventory tracking purposes. This guide walks through the process of setting up a kit product.  
  
A few notes on kits:

*   Kit products can only have one variant
*   If a customer adds multiple identical kits to the cart they'll be listed as a single line item with a quantity >1. If multiple kits with different options are added, they'll be listed individually.
*   The **Page Display** setting has no effect on kit products.
*   The **File Upload** kit group type allows customers to upload an image file.
    
    By default, the files are uploaded to the site's /images/orders folder.  The filename starts with the customer ID number and is printed on the receipt (you will want to specify a maximum size such as 500x500 pixels).  Please note that only .jpg, .gif, and .png files are supported. Your receipt may require custom developer modifications to accommodate the image acceptably.
    

Creating a Kit Product
======================

1.  In the \[Company Name\] admin console, go to **Products > Create Product**. Make sure that the **Product Type** dropdown is set to Kit and the **Is a Kit** attribute is set to **Yes**. The price you set will be used as the base price, before customers choose any custom options. This price should include the cost of the default kit group options. See below for more information.  
     ![](images/1416236810969.png)  
      
     ![](images/1416236857193.png)  
      
    
2.  Click **Save**, and you will see an **Edit Kit** link next to the **Is a Kit** option. Click that link to create the kit options.  
     ![](images/1416236958175.png)  
      
    
3.  The first thing to do to set up your customer-selectable options is to create a new kit group. Each kit group contains related items that customers choose from.  
      
    The Name and Summary fields show when a customer first loads the product page. The Description field is used for additional information that customers can view by expanding a kit group.  
      
    Check the Required box if you want to force shoppers to select an option from this group.  
      
    Check the Read Only box if you want to prevent shoppers from selecting/deselecting options from this group.  
      
    You also need to select the type of kit group this is going to be, from the dropdown list. This determines how customers choose options (dropdown list, radio button, etc) and even how many options they can choose (multi-select checkbox types allow for multiple selections).  
      
    Submit your changes with the **Create** link at the bottom of the window.   
      ![](images/1416237265532.png)  
      
      
      
      
    
4.  Within each kit group are the kit items. These are the choices that customers have within that group.  
     ![](images/1416237369031.png)  
      
     ![](images/1416237395748.png)  
      
     ![](images/1416237420799.png)  
      
    
5.  There are areas involved in setting up kit items:
    
    *   **General**: On the General tab, you can enter the name and description of the kit items, as well as set the order they appear in and which item is selected by default.
    *   **Inventory Variant**: On this tab, you can click the Select link to be shown a list of all of the variants that currently exist in your store. You can choose one of those variants from the list and the name, price, and weight for that kit item will be taken from that variant. This also ties the kit item to that variant for inventory purposes so if a customer purchases a kit with that item chosen, the separate variant's inventory will be reduced (this is not valid for products using **[Track Inventory by Size and Color](default.aspx?pageid=products_that_vary_by_size_color)**).
    *   **Pricing**: On this tab, you can set how much the kit price and weight will change if a kit item is chosen. The price values entered here will be added to the base price on the Variant.
6.  **Manage Images** allows you to add images to each kit item, which are then accessible by clicking on the item on the kit product page.

Purchasing a Kit Product
========================

As shoppers choose the options they want, the price and description shown on the product detail page will change. Once the kit is configured the way they want, shoppers can click **Add to Cart** to purchase it.
      