
      ---
      title: Shipping and Tax Estimator
      ---

      The shopping cart page can display a Shipping & Tax Estimator, giving customers an idea what their final order total will be. The estimator will show the price with the cheapest shipping method, though customers can still choose a different method during checkout if desired. This will work with fixed rates or [realtime rates](default.aspx?pageid=real_time_shipping_rates). For anonymous customers, the user would have to need to select Country and or City, State, and Postal Code. The lowest cost shipping rates will be presented as the estimated shipping rates. Postal Code field is required if Real-time shipping is the Shipping Method configured on the site.

Scope
=====

Shipping and Tax Estimator supports the following:

*   All Product types including Gift Card Products, Free Shipping Products and No Shipping Required Products
*   Coupon and Gift Card Discounts 
*   Customer Level Discounts and settings 
*   Cart Upsells
*   VAT Exclusive and VAT Inclusive 
*   All Shipping Calculation Types including Real-time shipping and all settings related to shipping

Limitations
===========

Shipping and Tax Estimator does not support the following:

*   Multishipping Checkout estimates 
*   TaxCalcMode Setting 
*   Phone Order Entry 

Shopping Cart Setup
===================

To enable the feature:

1.  Set up your shipping rates.  
      
    
2.  Set up your tax rates.  
      
    
3.  Set the ShowShippingAndTaxEstimate [Setting](default.aspx?pageid=settings)  to **Yes**.

Product Page Setup
==================

To enable the Shipping Estimator on the product detail page:

1.  Add the following line to the XML package you are using to display your products:  
    
    `<``xsl:value-of` `select``=``"aspdnsf:AjaxShippingEstimator(VariantID)"` `disable-output-escaping``=``"yes"``/>  
    `
    
2.  Add the following line to the template.master file for the skin you are using:
    
3.  `<``script` `type``=``"text/javascript"` `src``=``"jscripts/ajaxshipping.js"``></``script``>`
    

Frequently Asked Questions
==========================

**Q:** How does the Shipping and Tax Estimator work? Does the Shipping and Tax Estimator support both for Anonymous and Registered Users?   
  
**A:** To enable the Shipping and tax estimator control set Setting: ShowShippingAndTaxEstimate to **Yes**. This feature allows your customers to be presented with an estimate of their shipping and tax costs from the cart and before going through checkout. The customer must select the country and / or state/ or zip /or city where they are purchasing from and they will be presented with the cheapest shipping method available depending on the information you have set up for shipping choices in the admin console. Yes, it supports registered and unregistered users.   
  
  
**Q:** Will the inclusive and exclusive in VAT.Enabled work the same?   
  
**A:** Yes it will work the same, if you use inclusive it will automatically include the tax in shipping method otherwise it will be exclusive. But for a user that is not registered, the tax is always excluded.   
  
  
**Q:** Can I just select the country and leave the other address fields blank?   
  
**A:** Yes if you’re not using the Calculate Shipping By Weight & Zone and Calculate Shipping By Total & Zone shipping Method, otherwise it will require you to enter a zip code. The Shipping and Tax Estimator will be more accurate if all the address information is complete.
      