
      ---
      title: Product Filtering
      ---

      Sometimes store admins won't want to allow all customers to see all of their products. This may be done for promotional purposes, [wholesale sites](default.aspx?pageid=wholesale_store_setup), or any number of other reasons. This can be done by filtering products by [customer level](default.aspx?pageid=customer_levels)  or [affiliate](default.aspx?pageid=manage_affiliates).

Customer Level Filtering
========================

1.  First, set up the [](http://manual.aspdotnetstorefront.com/p-450-customer-levels.aspx)[customer levels](default.aspx?pageid=customer_levels) you need, for example Gold Membership, Elite customers, or whatever you need to call them. Remember that customers will see these level names!  
      
    
2.  Add the customers you want to have special access to the appropriate customer levels.  
      
    
3.  Next, map the products you want to restrict to the newly-created customer levels. Do this by checking the appropriate box on the **Mappings** tab for the product in **[Products > Manage Products](default.aspx?pageid=manage_products)**.  
      ![](images/1415985691484.png)  
      
    From the Mappings tab, you can also click **Customer Level Quick Add** to create a new Customer Level with basic discount settings.  
      
     ![](images/1415985410792.png)  
      
    
4.  Finally, set the **FilterProductsByCustomerLevel** [Setting](default.aspx?pageid=settings) to true.

Customers that do not belong to the customer levels those products are mapped to will now be unable to see those products. Be sure to explain to your special customers that they will have to log in before seeing the restricted products.

Affiliate Filtering
===================

1.  First, create the [affiliates](default.aspx?pageid=manage_affiliates) you need.  
      
    
2.  Next, map the products you want to restrict to the newly-created affiliates. Do this by checking the appropriate box on the **Mappings** tab for the product in [Products > Manage Products](default.aspx?pageid=manage_products).  
      ![](images/1415985717426.png)  
      
    
3.   Finally, set the **FilterProductsByAffiliate** [Setting](default.aspx?pageid=settings) to true.

Customers that do not arrive at your site by way of an affiliate link (as explained [here](default.aspx?pageid=manage_affiliates)) will not see the restricted products. Be sure to explain this to your special customers if necessary! This can be confusing for customers, as they can see different product lists depending on how they reach your site.
      