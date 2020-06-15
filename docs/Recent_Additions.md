
      ---
      title: Recent Additions
      ---

      The Recent Additions page gives store owners a built-in way to display the newest items on their store. To display these products, you can do any of the following:

1.  Directly invoke the link http://www.yourstore.com/recentadditions.aspx  
      
    
2.  Call the xml package from your template.master file  
    Example:  
      
    
    `<``div` `id``=``"bestsellers"``><%$ Tokens:XMLPACKAGE, recentadditions %> </``div``>`
    

 ![](images/1416418518858.png)

  

The page defaults to a value of 180 days back from the current date to pull products using the CreatedOn value, for display on this page. In order to change that value, you will need to create a new AppConfig: **RecentAdditionsNumDays**

In your Configuration - Settings menu, click the Create Setting button, and enter these values:  
  
**Name:** RecentAdditionsNumDays  
**Description:** The number of days back from the current date to pull products using the CreatedOn date for display on the RecentAdditions.aspx page.  
**Value:** 180 \[or whatever value you desire\]  
**Group:** MISC  
**Advanced - Value Type:** Integer  
**SAVE**

The page defaults to a value of 100 maximum number of products to display on the page. In order to change that value, you will need to create a new AppConfig: **RecentAdditionsN**

In your Configuration - Settings menu, click the Create Setting button, and enter these values:  
  
**Name:** RecentAdditionsN  
**Description:**The maximum number of products to display on the RecentAdditions.aspx page.  
**Value:** 100 \[or whatever value you desire\]  
**Group:** MISC  
**Advanced - Value Type:** Integer  
**SAVE**
      