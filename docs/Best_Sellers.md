
      ---
      title: Best Sellers
      ---

      The bestsellers page gives store owners a built-in way to display the most popular items on their store. To display the bestseller products, you can do any of the following:

1.  Directly invoke the link http://www.yourstore.com/bestsellers.aspx  
      
    
2.  Call the xml package from your template.master file  
    Example:  
      
    
    `<``div` `id``=``"bestsellers"``><%$ Tokens:XMLPACKAGE, bestsellers %> </``div``>`
    

![](images/1416404433746.png)

  

There are also 2 [Settings](default.aspx?pageid=settings) that can affect how this page looks:

**Setting Name**

**Description**

BestSellersN

This sets the maximum number of products that will display on the page.

BestSellersShowPics

If this is set to Yes, icon images will be displayed for each product on this page.
      