
      ---
      title: Wholesale Store Setup
      ---

      Some sites will want to prevent customers who are not registered and signed in from seeing prices or adding products to the cart. The easiest way to do this is with the 'Wholesale only site' feature.   
  
To enable this, set the WholesaleOnlySite AppConfig to true. Once this is done, customers who are not logged in and a member of a [customer level](default.aspx?pageid=customer_levels) will not be able to see prices or add items to the cart/wishlist. Store admins will have to manually assign newly-registered customers to the desired customer levels, or use tools like [WSI](default.aspx?pageid=integrating).   

If configuring the store this way, it may be best to remove all links to login/registration pages from the skin and .aspx pages, or to put an easily-noticeable warning on the login page, to avoid confusing customers.

To further restrict access to the site, you can [force all site visitors to log in before they can view anything](default.aspx?pageid=require_login).  
  
This page would welcome a sponsor from the \[Company Name\] community.

**Automating Customer Level Assignment** 
=========================================

Some sites may want to have newly-registered customers automatically assigned to a customer level so that they can immediately begin purchasing. While store admins might be inclined to use the DefaultCustomerLevelID [Setting](default.aspx?pageid=settings) for this, _that will not work!_. The DefaultCustomerLevelID functions as a 'mask' for customers that do not have a non-zero customer level assigned on their specific customer record. That does not override the WholesaleOnlySite behavior. Each customer must be individually assigned to a customer level before they'll be able to see product prices on a wholesale site. This can be done several ways with custom code, or with a simple database trigger like the one shown below.   

This is a customization. The support department cannot assist with implementing or troubleshooting this type of modification. This should only be attempted by a developer familiar with this kind of work.

`CREATE` `TRIGGER` `trg_CustomerLevelUpd`

`ON` `Customer`

`FOR` `UPDATE`

`AS`

`UPDATE` `Customer` `SET` `CustomerLevelID = 99` `WHERE` `IsRegistered > 0` `and` `CustomerLevelID = 0`
      