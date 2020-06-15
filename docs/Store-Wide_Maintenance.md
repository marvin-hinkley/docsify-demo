
      ---
      title: Store-Wide Maintenance
      ---

      From the **Configuration** Menu, click **Store Wide Maintenance**.  
  
This page enables you to perform some bulk actions that will probably very rarely need to be done, but would be difficult to do product-by-product. 

Setting the [On Sale](default.aspx?pageid=sales_prompts) prompt
===============================================================

1.  Select the **'On Sale' Prompt** from the drop-down list
2.  Select a Category, Department, or Manufacturer (If you wish to use this prompt for all entities, leave all three set to 'All...')
3.  Click the **Submit** button

If you select only one specific entity name, the other two fields need to be set to 'All...'

Setting a global [](http://manual.aspdotnetstorefront.com/p-390-quantity-discounts.aspx)[Quantity Discount Table](default.aspx?pageid=quantity_discounts)
=========================================================================================================================================================

1.  Select from the drop-down list the [](http://manual.aspdotnetstorefront.com/p-390-quantity-discounts.aspx)[Quantity Discount Table](default.aspx?pageid=quantity_discounts) you want to use.
2.  Click Submit

If you want to remove ALL Quantity Discount Tables for ALL products, leave the drop-down set to - select -, then  click Submit.  
This overrides any previous 'Quantity Discount Table' selections for all products.

Resetting all default variants
==============================

The default variant is what is used for search results, the name and price displayed on product grouping pages (categories, manufacturers, etc) and so on. Over time, as products change, you can end up with products whose default variants aren't the ones that you really want to 'take priority' in those areas. Clicking this button will go through every product on the site and set the default variant to the first one on each product ordered by display order and then name. This should almost never need to be done.

Resetting all SENames
=====================

SENames are modified versions of product names, used for generating the product URL. Special characters are removed from the name, all letters become lower case, and spaces are replaced by dashes. For example a product named "Bob's Favorite BBQ Sauce' would get an SEName of "bobs-favorite-bbq-sauce". Normally speaking when you change a product name through the admin console, the SEName is updated as well. If product names are being updated externally through DB queries or another custom integration, those may eventually not match. Clicking this button will regenerate the SEName for every product. This should almost never need to be done.
      