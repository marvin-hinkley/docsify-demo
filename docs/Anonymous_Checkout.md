
      ---
      title: Anonymous Checkout
      ---

      The anonymous checkout feature allows customers to check out without creating an account. Many customers prefer this as it allows them to get through checkout more quickly. It is generally recommended, however, that the feature isn't used unless absolutely necessary. The only thing customers gain is a few seconds spent creating a password during registration, but they lose the ability to reorder automatically, create a [wishlist](default.aspx?pageid=wishlists), etc. Order management also becomes more difficult, depending on how the feature is set up (see below).   
  
If the feature is enabled, customers will still have the option to register if desired, as seen here:

 ![](images/1415375151767.png)

  

It is important to be aware of the difference between a regular [anonymous customer](default.aspx?pageid=anonymous_customers) and a customer who has gone through anonymous checkout. An anonymous customer (as far as the software is concerned) is any customer who visits your site and does something that causes a record to be created for them in the database. This could be anything from adding an item to the cart/wishlist, choosing a locale or currency, etc. Anonymous checkout is a complete order, with the only difference from regular checkout being that the customer cannot log back into the site in the future.

Setup
=====

To enable anonymous checkout, simply set the **PasswordIsOptionalDuringCheckout** [Setting](default.aspx?pageid=settings) to **Yes**. There are several other Settings that need to be considered if this feature is going to be used:

**Setting Name**

**Description**

AnonCheckoutReqEmail

If this is set to **Yes**, anonymous customers still have to enter an email address (just not a password) when going through checkout. It is HIGHLY recommended that this is left true. If you do not have your customer's email address it can be difficult to track orders and you cannot send them receipts or other email notifications.

PayPal.Express.AllowAnonCheckout

If this is set to **Yes**, customers can pay through [PayPal Express](default.aspx?pageid=paypal_express_checkout) (if it is enabled) without registering on your site. This is usually required by PayPal's terms and conditions.

HidePasswordFieldDuringCheckout

If using Smart One Page Checkout, this Setting will also need to be set to **Yes** to enable anonymous checkout.

AllowCustomerDuplicateEMailAddresses

This is a [Global Config Parameter](default.aspx?pageid=global_config_parameters). If this is set to **Yes**, customers can use the same email address multiple times for multiple anonymous checkout orders. It is HIGHLY recommended that this be left set to **No**. If set to **Yes**, accurate tracking of orders/customers can become incredibly difficult and your fraud risks increase greatly.

Anonymous.AllowAlreadyRegisteredEmail

This is a [Global Config Parameter](default.aspx?pageid=global_config_parameters). If this is set to **Yes**, customers can use the same email address multiple times for multiple anonymous checkout orders, even if they already have a registered account using the same email, but will only allow a single registered account. It is HIGHLY recommended that this be set to **Yes**. If set to **Yes**, please set AllowCustomerDuplicateEMailAddresses to **No**.

Notes
=====

*   If **AllowCustomerDuplicateEMailAddresses** is set to **Yes**, the signin logic only considers the most recently registered account for each email address when evaluating passwords for signin. This eliminates issues with confusion of which password to validate to sign into accounts with duplicate addresses.
*   Unregistered accounts (customer records made during an anonymous checkout order) are ignored when considering if an email address is already in use. Only registered accounts will trigger the **AllowCustomerDuplicateEMailAddresses** handling.
*   Please remember that customers who check out anonymously will **never** have their credit card information stored, regardless of the **StoreCCInDB** [Setting](default.aspx?pageid=settings) . If store owners need to capture that information, they will need to turn off anonymous checkout.
*   Anonymous customers' sessions end when they close the browser.

**PreserveActiveCartOnSignin** defines what happens to the anonymous user’s cart. If true, the cart items will be moved over on signin. ClearOldCartOnSignin defines what happens to the registered users cart. If set to **Yes** the cart will be cleared, if set to **No**, the items will remain.

*   PreserveActiveCartOnSignin = true & ClearOldCartOnSignin = true: The cart from the anonymous user will remain.
*   PreserveActiveCartOnSignin = true & ClearOldCartOnSignin = false (default): the carts will be merged.
*   PreserveActiveCartOnSignin = false & ClearOldCartOnSignin = true: The cart will be emptied when a user signs in.
*   PreserveActiveCartOnSignin = false & ClearOldCartOnSignin = false: The cart from the registered user will remain.
      