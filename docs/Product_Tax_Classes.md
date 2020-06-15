
      ---
      title: Product Tax Classes
      ---

      ​Avalara - Helping you manage your sales tax compliance.  
BILLIONS of sales tax transactions processed. MILLIONS of exemption certificates managed. HUNDREDS OF THOUSANDS of sales tax returns filed.  
BILLIONS of dollars in taxes remitted. 100+ countries around the world. MARKET LEADER.   
From the **Configuration** Menu, click **Tax Classes**   
  
Tax classes allow store administrators to assign different tax rates to different products, as is required by law in some areas. While many stores will be able to account for all the tax rates they need with the default classes that come preloaded in the software, new classes can easily be added from this page. Existing classes can also be edited or removed.   
 ![](images/1415744276269.png)  

  

  
To create a new tax class, simply click **Create** and fill in the required fields.   
  
The \*Tax Class is the Name of your new tax class.  
  
The Tax Code is optional and serves as a notes field for store administrators, or can be used to match with special tax codes when using the [Avalara AvaTax](default.aspx?pageid=avalara_configuration) service. Note when using the Avalara tax service that the shipping tax class should be set to "FR" for the Tax Code value.  
  
The Display Order field is used to determine the order of application for order-level Promotions (see below for detailed example).   
 ![](images/1415745846630.png)  

  

  
Products are assigned to tax classes through [Manage Products](default.aspx?pageid=manage_products), through the Tax Class dropdown menu.  ![](images/1415746017219.png)  
  

  

  

**Tax Class Display Order and affect on order-level promotions**
----------------------------------------------------------------

Example:   
  
Product 1 - $10, 8% tax rate, tax display order 2 (Shipping)  
Product 2 - $50, 10% tax rate, tax display order 1 (Goods)  
Product 3 - $20, 12% tax rate, tax display order 3 (Tobacco)  
  
Promotion: $65 off, order level discount  
  
Order the products by tax display order (Product 2, Product 1, Product 3) and remove the order level discount line by line until it's used up:  
65 - 50 leaves 15 discount remaining and nothing to tax  
15 - 10 leaves 5 discount remaining and nothing to tax  
5 - 20 leaves no discount remaining and 15 remaining to tax  
  
Product 2: 0 \* .10 = 0  
Product 1: 0 \* .08 = 0  
Product 3: 15 \* .12 = 1.80  
  
80 + 1.80 - 65 = $16.80 total
      