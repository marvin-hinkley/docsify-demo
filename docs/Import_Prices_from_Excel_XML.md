
      ---
      title: Import Prices from Excel/XML
      ---

      From **Products** Menu, click **Import/Export**, then click **Import Prices from Excel/XML**.  
On this page, store administrators can import Cost, Price, Sale Price, and Inventory levels from the Excel file created through the **[Products > Import/Export > Export Prices To Excel/XML](http://help.aspdotnetstorefront.com/manual/951/default.aspx?pageid=export_prices_to_excel_xml)** page.

The Excel file needs to stay formatted exactly as the export creates it, change nothing but the cell values.

NOTE: Although MSRP does not import, it can be added. For customers with valid Year-Round Benefits, contact the [Support Help Desk](https://support.aspdotnetstorefront.com/)

  

Import Prices
=============

1.  Click the **Choose File** button, locate the Excel file to import, then click Submit.  
     ![](images/1415984368786.png)  
      
    
2.  A message will appear, indicating that the import was successful.  
     ![](images/1415984400793.png)

Many stores with a lot of products will want to use formulas within Excel to modified multiple prices at once. This will cause a problem, as Excel does not actually store the values you see in the cells, it stores the formula. Importing that will result in invalid information in your prices. To avoid this, make the desired changes to your file and then save it as a CSV (comma separated file). This removes the formulas, but stores the values. Once that's done, re-open the file and save it as an XLS (Excel) file again. It is now ready to import.
      