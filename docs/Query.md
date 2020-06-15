
      ---
      title: Query
      ---

      ### Description:

This node allows you to execute almost any query (or stored procedure) against the storefront database, and get data back.

### Full Syntax:

<Query Name="string" RowName="string">  
<SQL>  
<!\[CDATA\[  
select \* from whatever where whatever  
\]\]>  
</SQL>  
</Query>

### Notes:

*   **Name** \- This can be any name you want to assign to the query. This will be put in the XML output, so your automation can find the query results in the XML document WSI returns.
*   **RowName** \- This is a label used to indicate a new row of returned data in the XML document WSI returns. It can be used for your automation to extract information from the XML doc.
*   SQL queries do not have to be wrapped in CDATA tags, but it's easier to do so, so you don't have to worry about escaping characters that affect XML formatting.
*   You can execute stored procedures as well. Any valid SQL will be executed.

### Warnings:

This is an extremely powerful and dangerous WSI node. Be sure you know exactly what your SQL is doing, and test against a separate environment before attempting this on your live site.

### Example(s):

**This query will return all captured orders for AffiliateID 10 that are in the database and that were created in 2007.**  
<Query Name="Query493" RowName="row">  
<SQL>  
<!\[CDATA\[  
select OrderNumber from Orders where TransactionState='CAPTURED' and CapturedOn IS NOT NULL and AffiliateID=10 where year(OrderDate)=2007  
\]\]>  
</SQL>  
</Query>

**This query will return all tax rates for all states by tax class.**  
<Query Name="TaxRates" RowName="row ">  
<SQL>  
<!\[CDATA\[  
select State.StateID, StateTaxRate.TaxClassID, TaxRate, State.Name, State.Abbreviation, TaxClass.Name as TaxClassName   
FROM StateTaxRate INNER JOIN State ON StateTaxRate.StateID = State.StateID INNER JOIN  
TaxClass ON StateTaxRate.TaxClassID = TaxClass.TaxClassID  
\]\]>  
</SQL>  
</Query>
      