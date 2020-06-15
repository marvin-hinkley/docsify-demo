
      ---
      title: Promotions
      ---

      This page would welcome a sponsor from the \[Company Name\] community.

  

From the **Marketing** menu, click **Promotions**.  
On the main promotions page, you will see a list of all the existing promotions, along with some basic information for each and the option to edit existing items (click a Promo Title to edit):

 ![](images/1415376013922.png)

Creating a Promotion
====================

Basic Promotion Details
-----------------------

To add a new promotion, click the **Add New** button, and fill out the form:

 ![](images/1415376125070.png)

Field Name

Description

Promo Title

The Title of the Promotion. Not viewable by customers.

Promo Code

The code is the value that customers will enter on the shopping cart page to use this coupon, like 'SpringSale2012', 'FreeShipping', etc - the coupon code.  
THIS CODE IS NOT CASE SENSITIVE, so it can be entered any way you like.

Description

The Description of the Promotion. Viewable by customers.

Priority

This is an integer value (1,2,3,42, etc). If all promotions are the same priority, all applicable promotions are applied. If you have multiple promotions that would normally apply, for example a priority '1' promotion and priority '2' promotion, the higher priority '1' promotion will be applied. NOTE: Priority 0 means that the promo can always be combined with any other promotion!

Promo Status

If set to Active, this promotion can be used. If not, the promotion cannot be used by any customer.

Auto Applied

If this is checked, the site will try to apply the promotion to every customer's cart. Those who qualify based on other restrictions (see below) will automatically get this discount.

Discount Description Message

This text will display next to each place your customer's discounts are shown. This should be something like 'You saved xx', 'Discount', etc.

Product Discount Alert

This value is used for auto-assigned promotions that use the 'Enable Product Requirement' rule (see below). Any products specified as valid for this promo will have this call to action text displayed on the product page, and on entity pages that contain those products. This value is defaulted to 'Special Offer!'. If the field is cleared out entirely, no call to action text will be displayed.

Promotion Discounts
-------------------

After filling in the basic fields listed above, you'll need to setup the promo discount on the top of the right hand side of the form. Note that a promotion can contain both a discount on shipping and another discount type, but only one of the other types (indicated by the radio button selections below) can be chosen per promotion.

**

### Discount Shipping

**

If this is checked, customers using this promotion will get a discount on shipping rates. The discount can be either a fixed amount (i.e. $3 off) or a percentage of the normal shipping rate. If desired, you can enter a shipping method name that your site offers, and all matching shipping methods will be displayed. If you check one or more, the promotion will only apply for customers who use the selected shipping method(s).  
  
![](images/1415384741800.png)  

If your site has Multi-Ship enabled (**AllowMultipleShippingAddresses** [Setting](default.aspx?pageid=settings)), you cannot use shipping discounts.   
  
Please be aware that the shipping portion of a promotion is calculated and applied separately from the rest of the promotion. It is possible for a promotion to not be valid for any of the products in the cart, but still have the shipping part of the promotion be applied to the order.

**

### Discount Order

**

If selected, the order subtotal will be discounted by the amount chosen. This can be a fixed amount (i.e. $15.00 off), or a percentage of the subtotal. ![](images/1415385035804.png)

### Discount Applicable Line Items

If selected, the specified discount will be taken off for each applicable product in the cart. Products that are discounted are specified in the **Enable Product Requirement** rule in the Promo Requirements section (see below). Remember that this is per instance of the allowed item(s) in the cart. If a $3 discount is specified, $3 will be taken off of each 'copy' of the allowed item(s) in the shopping cart.![](images/1415385168576.png)

### Gift With Purchase

If selected, this promotion will automatically add the specified product(s) to the cart with the specified discount. If you want to give a free product or set up a BOGO-type discount, enter a 100% discount here. You may search for products by name, and check the ones you want to be given.  
 ![](images/1415385279241.png)  
NOTE: Remember that promotions do not go below the product level, so you cannot specify a specific variant, size/color, or kit option here. You may select a gifted product with multiple variants but _only the default variant will be added to the cart_. **DO NOT set a product with variant attributes (size/color) as a gifted item.**  
  
If the 'Per Qualifying Product' box is checked, then the customer will get one gift item for _each_ qualifying paid item in the cart, once the promotion qualifications have been met. Leave this box unchecked if you only want to allow _one_ free gift item per _order_.

Promo Limits
------------

Once you've selected the discount type above, you can specify limits on the discount. These rules limit when the coupon will work, and how much of a discount can be given through the promotion. To limit which orders a promotion will apply to, see the Promo Requirements section below.

### Enable Start Date

If checked, the promotion will not be valid until the date entered in the text box. Use the date picker to select a date, and it will be properly formatted for your store's locale. ![](images/1415385367698.png)

### Enable Expiration Date

If checked, the promotion will not be valid after the date entered in the text box. Use the date picker to select a date, and it will be properly formatted for your store's locale. ![](images/1415385435169.png)

### Enable Maximum Number of Uses

If this is checked, the promotion can not be used more times than the value entered in the text box. If the **Per Customer** box is not checked, then that value is the total number of times the promotion can be used on your site among all customers. If it is, each customer can use the promotion that many times.  
  
 ![](images/1415385472878.png)

Promo Requirements
------------------

The rules created in this section can restrict promotions to only work for certain customers, products, etc. Try to use as few of these restrictions as possible for each promotion, to limit confusion for your customers and staff.

### Enable Product Requirement

If this is checked, then the promotion will only apply discounts to the product(s) listed here. To add products, enter a search term and then check off the ones you want to apply to the promotion. The list can be set to require **All** (every checked product must be in the cart before the promotion will apply) or **Any** (as long as one checked product is in the cart the promotion will apply). If a value is set in the **Require Quantity** field, the customer would need to have that many of the required product(s) in the cart to obtain the discount.  
  
 ![](images/1415385833991.png)

### Enable Category Requirement

If this is checked, the promotion will only apply to products that are mapped to the selected category/categories. To add a category, enter a search term and then check off the one(s) you want to apply to the promotion.  
  
 ![](images/1415385853521.png)

### Enable Department Requirement

If checked, this promotion will only apply if the shopper's cart includes a product from one of the selected Departments. To add a department, enter a search term and then check the one(s) you want to apply to the promotion.  
 ![](images/1415385876120.png)

### Enable Manufacturer Requirement

If this is checked, the promotion will only apply to products that are mapped to the selected manufacturer(s). To add a manufacturer, enter a search term and then check off the one(s) you want to apply to the promotion.  
 ![](images/1415385908167.png)

### Enable Minimum Cart Subtotal Requirement

If checked, the promotion will only apply to the order if the cart subtotal meets or exceeds the value set in the text box.  
  
 ![](images/1415385956659.png)

### Enable Email Address Requirement

If checked, this promotion will only apply to customers whose email addresses are listed in the text box. Those addresses can be typed in manually (separated with a comma) or imported from a single column **Email Address** CSV file.  
  
 ![](images/1415386069982.png)

### Enable Customer Level Requirement

If checked, the promotion will only apply to customers who belong to the selected customer level(s). To add a level, enter a search term and then check off the one(s) you want to apply to the promotion.  
  
 ![](images/1415386133654.png)

### Enable Shipping State Requirement

If checked, this promotion will only apply to customers whose shipping address State is included in the comma-separated list of two-letter state codes listed here. Example: OR,CA,AZ,TX. Customers must enter a shipping address BEFORE trying to use this promotion.  
  
 ![](images/1415386168900.png)

### Enable Shipping Zip Code Requirement

If checked, this promotion will only be valid for users whose shipping address Zip Code is specified in the comma separated list. Customers will need to enter a shipping address BEFORE using this promotion code.  
 ![](images/1415386207775.png)

### Enable Shipping Country Requirement

If checked, this promotion will only apply to customers whose shipping address Country is included in the comma-separated list of full country names. Example: United States,Canada. Customers must enter a shipping address BEFORE trying to use this promotion.  
 ![](images/1415386240426.png)

Setup Customer Targeting
------------------------

The rules in this section set up restrictions based on what customers have bought in the past. These can be used to prevent customers from using a promotion more frequently than you want, while still allowing them to use the promo multiple times if it's been long enough (or they've purchased enough) to meet your requirements.

For all of the rules below, to set up a promotion that doesn't expire just set the end date to a date far in the future. The start date can also be set in the past, to make these restrictions include historical orders.  
  

### Enable Minimum Number of Past Orders

If checked, this promotion will only apply to customers who have more past orders within the given date range than the number specified.   
 ![](images/1415386319596.png)

### Enable Past Orders Minimum Amount

If checked, this promotion will only apply to customers who have past orders within the given date range that total more than the minimum required here.   
  
 ![](images/1415386410766.png)

### Enable Past Orders Minimum Number of Products

If checked, this promotion will only apply to customers who have past orders within the given date range that contain more of the specified products than the quantity entered here. To list specific products, use the search box to find products and check them off.  
 ![](images/1415386440949.png)

### Enable Past Orders Value of Products

If checked, this promotion will only apply to customers who have past orders within the given date range that contain products who's invoiced total, when summed, is greater than the listed amount required. To list specific products, use the search box to find products and check them off.  
  
 ![](images/1415386469320.png)

Notes
=====

Payment methods that take customers off of your site to pay (PayPal Express) have limited support for promotions. Since oftentimes your customer will leave the site to pay before they have logged in, the shopping cart doesn't have information like shipping addresses, customer levels, email addresses, and so on to know whether the promo code the customer tried to use is valid. Whenever possible we update orders later on in the process to re-validate promotion codes that were entered, but keep in mind that with offsite payment methods, some rule types simply will not work as reliably as when paying onsite. If you expect many of your customers to pay with those methods, you may want to limit your promotions to rules that do not require knowledge of the customer's address, email, order history, etc.

Order-level and line-item-level promotions should not generally be used together. Order level discounts will be taken off of the base line item subtotal before any other discounts are applied, so you can end up with orders that are discounted more than desired. Use the Priority attribute on promotions to limit how many (and which) promos can be used on each order.
      