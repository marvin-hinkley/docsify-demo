
      ---
      title: Clear Test Orders from the Database
      ---

      Site administrators often want to remove test orders from the DB before going live. Rows will need to be removed from 4 tables to completely remove the test orders. The following SQL statements will clear those orders out. Make sure you have a good backup of your database before making changes to it.

1.  In the \[Company Name\] admin console, go to **Configuration > Run SQL**.  
      
    
2.  Type the following commands and click Submit. Make sure to replace **lastordernumbertokeep** with the order number you want to use.  
      
    DELETE FROM Orders WHERE OrderNumber < lastordernumbertokeep  
    DELETE FROM Orders\_CustomCart WHERE OrderNumber < lastordernumbertokeep  
    DELETE FROM Orders\_KitCart WHERE OrderNumber < lastordernumbertokeep  
    DELETE FROM Orders\_ShoppingCart WHERE OrderNumber < lastordernumbertokeep  
      
     ![](images/1416404995189.png)  
      
      
    These statements assume that you want to remove ALL orders before "lastordernumbertokeep." If that is not the case, you may need to edit these statements.
      