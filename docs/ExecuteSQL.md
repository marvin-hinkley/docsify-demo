
      ---
      title: ExecuteSQL
      ---

      ### Description:

This node can execute almost any SQL statement against your storefront database. You may need this to perform mass updates, perform scheduled/triggered activities, etc.

This is generally used for 'execute' type SQL queries, which will not have any output. For queries that will return results you need to be able to access, use the [Query](http://manual.aspdotnetstorefront.com/p-1458-query.aspx) node instead.

### Full Syntax:

<ExecuteSQL Name="string">  
<SQL>  
<!\[CDATA\[  
your SQL here  
\]\]>  
</SQL>  
</ExecuteSQL>

### Notes:

*   **Name** \- Name can be any string value you want to assign to this SQL execution, so you can reference the output status returned by WSI in the XML doc.
*   You do not have to wrap your query in CDATA tags, but it's usually easier, so you don't have to worry about escaping characters that can affect XML formatting.
*   You can execute stored procedures this way as well. Any valid SQL commands should be executed.

### Warnings:

This is an extremely powerful and dangerous WSI node. Be sure that you know what you are doing, and test your SQL against a separate test site before running it on your live environment.

### Example(s):

**This example sets the SalePrice of all products to be 10%:**  
<ExecuteSQL Name="SetSale10PercentOff">  
<SQL>  
<!\[CDATA\[  
update ProductVariant set SalePrice=(Price\*0.90)  
\]\]>  
</SQL>  
</ExecuteSQL>

**This example sets the (simple) Inventory of all products in Category 14 to 0:**  
<ExecuteSQL Name="ClearInventory">  
<SQL>  
<!\[CDATA\[  
update ProductVariant set Inventory=0 where ProductID in (select ProductID from ProductCategory where CategoryID=14)  
\]\]>  
</SQL>  
</ExecuteSQL>
      