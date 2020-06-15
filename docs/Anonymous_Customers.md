
      ---
      title: Anonymous Customers
      ---

      This page would welcome a sponsor from the \[Company Name\] community.

  

  
An anonymous customer is any customer who visits your site and does something that causes a record to be created for them in the database. This could be anything from adding an item to the cart/wishlist, choosing a locale or currency, etc. A record is created for them in the Customer table (and other tables if necessary) in the database with just the basic information to save their session data. If that customer later goes on to register, those records are converted into a full customer record.

Checkout
========

By default, anonymous customers must register before they can actually complete an order. If store admins wish to change that, they can set the **PasswordIsOptionalDuringCheckout** [Setting](default.aspx?pageid=settings) to true. Once that's done, site visitors will have the option to Register & Checkout or Skip Registration & Checkout.   
  
We highly recommend that this feature not be used unless absolutely necessary. The time savings to the customer is negligible (the only difference is they don't have to set a password), and it has several drawbacks:

*   Customers cannot quickly reorder the same thing, as they can when registered. 
*   Depending on the settings explained below, customers may only be able to purchase once. 
*   Record keeping can be difficult when some customer information is missing.

Important Related Settings
==========================

If you decide to enable this feature, there are several other Settings to take into consideration:

**Setting Name**

**Description**

AnonCheckoutReqEmail

This determines whether or not customers must enter an email address to checkout, even when anonymous. We highly recommend that this be set to true, as your store cannot send out receipt/shipped emails otherwise, and it can make order tracking difficult if that information isn't present.

AllowCustomerDuplicateEMailAddresses

If you allow anonymous checkout and require an email address, customers who don't register will only be able to purchase from your site once per email address unless you set this to true. Note that setting this to true can cause issues down the road with extra records in your database, and if a customer decides to register some day a store admin will have to manually go through the DB and remove those extra records (or at least one) so the customer can register.
      