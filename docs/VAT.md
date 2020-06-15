
      ---
      title: VAT
      ---

      VAT is the 'Value Added Tax' as practiced by member states of the European Union. Stores based in an EU country will most likely be responsible for VAT, and will need to use the information below to configure it. See [here](http://en.wikipedia.org/wiki/European_Union_Value_Added_Tax) for more information on VAT in general.

Enabling VAT
============

1.  First, be sure that you have [set up taxes](default.aspx?pageid=edit_countries) for the countries you wish to sell to. When customers are anonymous (not logged in or registered), taxes that are displayed will be calculated based on the tax rates set for the country specified in the VAT.CountryID [Setting](default.aspx?pageid=settings) (see below). Once the customer registers and/or logs in, taxes will be based on their country's tax rates.  
      
    
2.  Set the VAT.Enabled Setting to **Yes**.  
      
    
3.  Configure the following Settings according to your site's preferences:
    
    **Setting Name**
    
    **Description**
    
    VAT.CountryID
    
    This should be set to the ID of the country your store is based in. The country ID can be found on the **Configuration > Edit Countries** page in the admin console.
    
    VAT.RoundPerItem
    
    Setting this to **Yes** makes the software apply tax and then round off the cost for each item individually before adding the totals together. Leaving this set to **No** results in more mathematically accurate totals, but can lead to results that appear slightly off to customers.
    

NOTE Enabling VAT will add a text box to the customer account pages where they can enter their business VAT registration ID if they have one. The cart will verify it based on the country set on the customer's Billing address, and the ID should be entered as the numbers with no country code (such as 123456789 and not UK 123456789).

Display
=======

These [Settings](default.aspx?pageid=settings) control how the taxes display on your site when VAT is enabled:  
  

**Setting Name**

**Description**

VAT.DefaultSetting

This setting determines whether prices on the site are displayed with tax built in ("inc vat") or without ("ex vat"). Different countries have different rules for how these prices must be displayed, check with a local accountant or attorney for the rules for your area. Set this to 1 for tax inclusive, or 2 for tax exclusive.

VAT.AllowCustomerToChooseSetting

If this is set to **Yes**, customers will be able to choose from a dropdown menu whether or not they want taxes to be included in prices displayed or not. This will override the VAT.DefaultSetting described above for that customer.
      