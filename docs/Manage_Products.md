
      ---
      title: Manage Products
      ---

      From the **Products** Menu, click **Manage Products**.   
  
This is the preferred place to make product changes within the admin console. While there are other bulk edit pages discussed elsewhere in this manual, this page gives quick, easy access to all of your product properties from one screen. 

**Finding your product**
========================

1.  Use the **Filters** section to locate a product by **Product ID**, **Name**, or **SKU**. Optionally, use the dropdown menu to display (or hide) products which have been deleted.  
     ![](images/1415043196316.png)  
      
    
2.  From the product grid, you can click the column headers to sort by **ID**, **Name**, or **SKU**. You can also check/uncheck boxes to publish or delete products.  
      
    
3.  To copy a product, click the **Clone** button. This will create a copy of an existing product that can be modified independently from the original.  
      
    
4.  Click the **Variants** button to manage a product's variants.

Adding a product
================

1.  From the Products page, click **Add New Product**.  
     ![](images/1415043504861.png)  
      
    
2.  Fill out the form fields with information about your new product. At a minimum, there are a few required fields that must have information in order to save the product, these are marked with a red asterisk (\*) next to the required fields on the **Main** tab. See below for more information about each field.  
      
    
    ### Main
    
    \*Name 
    
    The product's name. This is visible to all shoppers. 
    
    \*Product Type
    
    General type or classification of product.
    
    \*Manufacturer
    
    Choose from a list of Manufacturers. Create new Manufacturers in your admin console on the **Products > Brands/Manufacturer** page.
    
    Distributor
    
    Choose from a list of Distributors. Create new Distributors in your admin console on the **Contacts > Manage Distributors** page.
    
    SKU
    
    The product's SKU. This is visible to all shoppers.
    
    Manufacturer Part #
    
    This value will be sent in distributor emails if populated (optional)
    
    \*Published
    
    Determines whether or not the product appears on the front end of the site.
    
    \*Page Display
    
    Choose from a list of page layouts. This setting will adjust the layout of the product detail page.
    
    Column Width
    
    Determines the number of columns that variants are displayed in (this field is only used by Page Displays that are designed for multiple product variants)
    
    Tax Class
    
    Determines the tax % that will be calculated for this product. Learn more about Taxes [here](default.aspx?pageid=taxes).
    
    Quantity Discount Table
    
    If a discount table is selected here, shoppers will get a discount based on the quantity of the product purchased.
    
    \*Show Buy Button
    
    If this is set to No, the Add to Cart/Wishlist buttons will not be displayed on the site.
    
    \*Requires Registration to View
    
    If this is set to Yes, the product will only be displayed on the site after shoppers have created an account and logged in.
    
    \*Is Call To Order
    
    If this is set to Yes, Add to Cart/Wishlist buttons are hidden, and a "Call to Order" prompt is displayed to customers.
    
    \*Hide Price Until Cart
    
    If this is set to Yes, the product price will not be displayed on the site. The price can only be seen after the product is added to the cart.
    
    \*Exclude from Product Feeds
    
    Prevents DotFeed from exporting the product details to Comparison Shopping Engine feeds.
    
    \*Is a Kit
    
    If this is set to Yes, additional product configuration options will be made available.
    
    \*Track Inventory by Size and Color
    
    If this is set to Yes,  inventory will be tracked individually for every size/color combination set up on the product variant(s)  
    (Using this method will not work with Kits tied to the variant)
    
    Color Option Prompt
    
    Text to display to shoppers for attributes they may choose instead of "Color:"
    
    Size Option Prompt
    
    Text to display to shoppers for attributes they may choose instead of "Size:"
    
    Requires Text Field
    
    If this is set to Yes, a text field will be displayed on the product detail page for shoppers to enter personalization details or other custom information, using the field prompt: "Customization Text" (see [Prompt](default.aspx?pageid=prompts): common.cs.70 ), unless a different value is entered in the "Field Prompt" box. If this is set to "No" and a value has been entered for the "Field Prompt", then the text box displayed will not be required (optional).
    
    Field Prompt
    
    How to label the text box if "Requires Text Field" is set to Yes. See "Requires Text Field" for more information.
    
    Max Length
    
    Maximum number of characters allowed in the text field.
    
      
      
    **Default Variant Information**  
      
    
    Price 
    
    The price that will be displayed to shoppers
    
    Sale Price
    
    If this field is populated, the product detail page will list the normal price with the sale price underneath
    
    Weight
    
    Variant weight, used for shipping calculations
    
    Dimensions
    
    Size (height x width x depth) of the package the item ships in (in the format N x N x N or NxNxN)
    
    Current Inventory
    
    Number of this item on hand
    
    Colors
    
    You can use the Color/Size fields to define user-selectable attributes that change the product variant (for example the size and color of a t-shirt). Values defined here will be listed as dropdown menus on the product detail page. You can also specify SKU suffixes that will be added to the product SKU on receipts to indicate which attributes were chosen.  
      
    You can also specify price modifiers for these attributes by enclosing them in brackets immediately after the attribute name. Example: a shirt with a base price of $12 for the medium size would be $10 for small, or $15 for large:  
    Sizes: Small \[-2.00\], Medium, Large \[3.00\]  
      
    These fields can be called something other than Color and Size, using the “Color Option Prompt” and “Size Option Prompt” attributes on the product.  
      
    Note: Avoid using quote marks (") in the attributes as they can cause Add To Cart to fail when using the Limit cart to quantity on hand feature.
    
    Color SKU Modifiers
    
    Sizes
    
    Size SKU Modifiers
    
      
    
    ### Images
    
    On the images tab, you can upload images to display for your products. Icon images display in category-level views (where many products are shown at once) and a few other places if the store is configured to do so. Medium images show on the main product detail page, and large images show in a separate window if customers click the View Larger Image link on the product detail page.  
      
    By default, the software will resize images uploaded through this page to the standard sizes – 150x150 for icons, 250x250 for mediums, and 500x500 for larges. To change these sizes or other Image Resize settings, go to Settings in the admin console and choose “IMAGERESIZE” from the **Setting Group** dropdown.  
     ![](images/1415123531560.png)  
      
    The [Multi-Image Manager](default.aspx?pageid=multi_image_manager) links allow you to upload multiple images of a certain size. On the product detail page, customers will be able to cycle through the multiple images.  
      
    The top field on this page, labeled “Image Filename Override” allows you to specify a filename for the software to use for this product's images (by default, images are saved as productID.jpg). This is useful for bulk-uploading images, which can be faster than loading them individually through the admin site. You can specify a filename in this field (with extension), and then FTP your images to the following folders:  
    
    *   /images/product/icon/filename.jpg
    *   /images/product/medium/filename.jpg
    *   /images/product/large/filename.jpg
    
      
    See [here](default.aspx?pageid=image_resize_configuration) for information on configuring the software's image resize tools.
    
    ### Summary
    
    This field can contain a short description of the product. It it used on some of \[Company Name\]'s product & entity page layouts.
    
    ### Description
    
    This field stores your product description and is displayed to shoppers on the product detail page. 
    
    ### SEO
    
    The fields on the SEO tab are used to generate the meta information for your product pages. This information is part of what most search engines use to index your site's pages, so you should take the time to put good information here.  
    Available fields are:   
    
    *   Page Title
    *   Keywords
    *   Description
    *   Alt Text
    
    ### Product Feeds
    
    This field is used to store product descriptions in plain-text format. Some Comparison Shopping Engines do not permit rich text or HTML product descriptions. If you are using DotFeed, the DotFeed engine will automatically use a description stored in the Product Feed description field.
    
    ### Mappings
    
    On this tab, you control where each product appears on your site and (if desired) who can see it. In the Category and Department columns, simply check the box(es) for the entities you'd like your product to appear in. Any shopper who navigates to those areas of the site will find this product.  
      
    In the Affiliates and Customer Level columns, you can set whether or not members of each of these groups will be able to view this product (see [here](default.aspx?pageid=product_filtering) for more information on product filtering). 
    
    ### Store Mapping
    
    This section appears when you have configured multiple stores on \[Company Name\]. Simply check the box next to each store that should advertise the product.
    
    ### Options
    
      
     ![](images/1415125621070.png)  
    
    Related Products
    
    Insert Product IDs (not names) here. These products will be displayed in a special box at the bottom of the main product's page
    
    Upsell Products
    
    Insert Product Ids (not names) here. These products will be displayed in a special box at the bottom of the main product's page and can also be displayed on the shopping cart page
    
    Upsell Product Discount Percent
    
    If a customer adds an upsell product to the cart from the parent product's detail page, the discount here will be applied. If they add this product from its own page, the discount will not apply
    
    Requires Products
    
    Insert Product IDs (not names) here. If a customer adds this product to the cart, the required product(s) will be added as well
    
    On Sale Prompt
    
    If your product has a sale price set, this dropdown determines which prompt precedes that sale price. New sale prompts can be created at Products > Manage Products > Sales Prompts
    
    ### Custom Fields
    
    This section contains 7 unique fields that accept HTML and can be used to store additional information about your product. By default, these fields are not displayed on the store, but could be optionally used in a custom skin design.
    

Variant Properties
==================

### Main

  
 ![](images/1415992419244.png)

**Property Name**

**Description**

Variant Name

Name of this product variant (optional). This value will be appended to the parent product name if filled in

SKU Suffix

This value will be appended to the parent product SKU on receipts and during checkout )optional)

Manufacturer Part #

This value will be sent in distributor emails if populated (optional)

GTIN

Used for unique product identification. This field holds up to 14 characters and can be used for EAN, UPC, ISBN, etc.

Published

Determines whether or not the variant appears on the front end of the site

Restricted Quantities

If your variant can only be purchased in certain quantities, list them here (ie: If you sell by the dozen – 12, 24, 36, etc)

Minimum Quantity

Smallest quantity customers are allowed to add to the cart

Price

The price that will be displayed to customers

Sale Price

If this field is populated, the product detail page will list the normal price with the sale price underneath

Customer Enters Price

If this is set to true, customers can set their own price for the product (often used for donation or gift card products). NOTE: This option does not work for kit or pack products!

Customer Enters Price Prompt

Label for the text box customers enter their price in on the product detail page. NOTE: This option does not work for kit or pack products!

MSRP

For internal use only

Actual Cost

For internal use only

Is Taxable

Determines whether or not this variant is taxed under the class set for the parent product

Shipping

**Has a cost** is set by default, shipping charges will be determined based on the store's configured [shipping calculation](default.aspx?pageid=shipping_calculation). To override the store shipping calculation, select **Is free**, or **Is not required**.

Is Ship Separately

If using realtime shipping, this instructs the carrier to calculate the cost of shipping this item in its own box. This is done by sending the product dimensions, instead of just the weight that is usually sent to the carrier

Is Free Shipping

Set whether or not the item gets free shipping, or if it doesn't even need shipping at all (such as a service or digital product)

Is Download

If the product is downloadable, select **Yes**. See [here](default.aspx?pageid=downloadable_products) for more information on downloadable products.

Download is Valid for Number of Days

Number of days the product will be available for download. 

Download Location

The relative path to the download file (only applicable if Is Download is set to **Yes**)

Condition

Available options are: New, Used, Refurbished.

Weight

Variant weight, used for shipping calculations

Dimensions

Size (height x width x depth) of the package the item ships in (in the format N x N x N or NxNxN)

Manage Inventory

Click Manage Inventory to adjust the quantity on hand.

### Images

  ![](images/1415993370928.png)  
  
See Images section under Parent Product Properties above for full details. Variant images will only show when using certain XmlPackages for display (Page Display attribute on the parent product).   
  

### Description

 ![](images/1415993588482.png)  
The Description tab is where product variant information is entered. This information will only show when using certain XmlPackages for display (Page Display attribute on the parent product). This tab uses the Telerik RAD editor, and can accept HTML code. To insert HTML, click the “<>” button at the bottom of the editor. 

### HTML-Free Description

  ![](images/1415993743559.png)  
  
The plain text (no HTML allowed here) in this box will be used for descriptions in product feeds.  

### Attributes

 ![](images/1415993778339.png)  
On the Attributes tab, you can define user-selectable attributes that change the variant (for example the size and color of a t-shirt). Values defined here will be listed as dropdown menus on the product detail page. You can also specify SKU suffixes that will be appended to the base SKU on receipts to indicate which attributes were chosen.   
  
You can also specify price modifiers for these attributes by enclosing them in [](http://manual.aspdotnetstorefront.com/p-296-product-attributes.aspx#)brackets immediately after the attribute name. In the example below, a shirt with a base price of $12 for the medium size would be $10 for small, or $15 for large:

Sizes: Small \[-2.00\], Medium, Large \[3.00\]

Note: These fields can be called something other than Color and Size, using the **Color Option Prompt** and **Size Option Prompt** attributes on the parent product (see above).

### Recurring

 ![](images/1415993849036.png)  
The Recurring tab allows you to define a product that customers can automatically re-order on a recurring basis. See [this page](default.aspx?pageid=recurring_orders1) for more information about recurring orders.
      