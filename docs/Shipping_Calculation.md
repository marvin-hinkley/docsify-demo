
      ---
      title: Shipping Calculation
      ---

      From **Configuration** Menu, click **Shipping Calculation**.  
  
On this page, store administrators determine how the software will calculate shipping costs for orders. Select one of the calculation methods (described below) and click **Save**. **

Free Shipping
=============

**All orders, regardless of contents, will receive free shipping.  

Real-time Rates 
================

With Real Time Shipping (RTS), your website connects to one or more of the major shipping carriers (UPS, USPS, FedEx, Australia Post, and Canada Post) and gets the price that the carrier would charge to ship that order based on the weight and/or size of the products ordered, and the origin and destination of the package. See [here](default.aspx?pageid=real_time_shipping_rates) for directions on enabling real time shipping.  

Custom Shipping Calculations
============================

Use Individual Item Shipping Costs
----------------------------------

This calculation method allows you to set a shipping cost on each product variant (see [here](default.aspx?pageid=manage_products) for information on setting up product attributes). The shipping costs will be added together to generate your customers' shipping total.  
  
The option to set a shipping cost on product variants will appear once this shipping calculation method has been selected.  
**  

Calculate Shipping By Weight
----------------------------

**This method uses a simple table based on the total weight of the order (see [](http://manual.aspdotnetstorefront.com/p-960-product-attributes.aspx)[here](default.aspx?pageid=manage_products) for information on setting up product weights) to calculate shipping costs. Click **Edit** to setup shipping costs per method.  
You can specify a low-end and high-end for each range, and specify different costs for each shipping method.   
Be sure your weight ranges do not leave gaps that order weights could fall into. If your table goes from 1-2, 3-4, 5-6, etc, an order of 2.5 lbs will fail.

Calculate Shipping By Total  This calculation method lets you base your shipping rates on the total dollar amount of the customer's order. This method can also be used to give a certain range of orders free shipping. Click **Edit** to setup shipping costs per method.   
  
Be sure that your table covers all totals that a customer may get. If someone has an order total lower or higher than your table accounts for, or that falls into a gap in your table, the order will fail.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**

Use Fixed Prices
----------------

**This is the simplest shipping calculation method to set up. Each shipping method has one price, regardless of the order contents. Click **Edit** to setup shipping costs per method. 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Use Fixed Percentage Of Total**  
-----------------------------------

This method charges a percentage of the order total for shipping. Click **Edit** to setup shipping costs per method. 

**Calculate Shipping By Total & Percent**  This is the most complicated of the fixed shipping rates to set up, but allows for greater flexibility in pricing than the other methods. The Base Charge is the base shipping dollar amount. The software then adds to that charge a percentage of the order total, based on the Shipping Charge As % of Total that you enter. The Minimum Charge field is optional, but allows you to set a minimum value for each range that will override the calculated price if it's below that minimum. In the example table below, an order of $10 would be charged $5 for ground shipping, since the base amount ($3) plus the percentage ($1) is less than the minimum. A $45 dollar order would be charged $7.50 ($3 base plus $45 x 10%). Click **Edit** to setup shipping costs per method.   
  
Be sure that your table covers all totals that a customer may get. If someone has an order total lower or higher than your table accounts for, or that falls into a gap in your table, the order will fail.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**

Custom Shipping Calculations By Zone
====================================

**

**Calculate Shipping By Weight & Zone** 
----------------------------------------

This method allows you to charge different amounts based on the destination zip code (or zip code range, see [here](default.aspx?pageid=shipping_zones) for information on zones) and the order weight. Click **Edit** to setup shipping costs per method. 

**Calculate Shipping By Total & Zone** 
---------------------------------------

This method allows you to charge different amounts based on the destination zip code (or zip code range, see [here](default.aspx?pageid=shipping_zones) for information on zones) and the order total.  Click **Edit** to setup shipping costs per method.
      