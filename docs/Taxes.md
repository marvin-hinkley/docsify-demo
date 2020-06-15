
      ---
      title: Taxes
      ---

       Setting up the software to charge tax on your orders requires work in 4 areas:

**Tax Rates** 
==============

First, you must set up tax rates. This can be done at the [country](default.aspx?pageid=edit_countries), [state](default.aspx?pageid=edit_states_provinces), or [zip code level](default.aspx?pageid=tax_by_post_code).

If you set up tax rates at multiple levels (ie state and zip), the rates will be added together to get the final tax rate.

**Products** 
=============

Next, you must make sure that your products are taxable, and that they are assigned to the correct tax class. Do this through [Manage Products](default.aspx?pageid=manage_products) by navigating to the product in question and checking these 2 attributes:  
  

Tax Class
---------

 ![](images/1415742102400.png)  
This is set at the parent product level, and should be set to whatever class you created tax rates for in the step above.  
  
  

Is Taxable
----------

 ![](images/1415742184457.png)  
This is set at the product variant level. If this is set to yes then the product will be taxed at the rates you set up for the assigned class. If set to no, tax will be ignored for this product. 

**Customer Status** 
====================

If your site is using [customer levels](default.aspx?pageid=customer_levels), be careful with this setting:  
  
 ![](images/1415742268548.png)

If this is set to yes, then any customers in this level will not pay taxes, regardless of how you have everything else set up. Be sure that this is only set to yes for customers you intend to be tax-free (non-profit organizations, etc).   
  

**Tax Calculation Mode** 
=========================

Finally, you must tell the software whether it should charge tax on the billing or shipping address (this varies by law in different locations). This is done with the TaxCalcMode [Setting](default.aspx?pageid=settings). If set to 'billing', orders are taxes based on the billing address. If set to 'shipping', orders will be taxed based on the shipping address.
      