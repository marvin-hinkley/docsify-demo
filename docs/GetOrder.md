
      ---
      title: GetOrder
      ---

      ### Description:

Returns order data.

### Full Syntax:

<GetOrder GetAll="boolean" OrderNumber="integer"/>

### Notes:

*   This actually executes the <Get> WSI node, specifying Orders as the table, with 'DumpOrder.xml.config' for the XmlPackage and an order number (if provided) as the DefaultWhereClause.
*   If GetAll is set to true, all data for all orders will be returned.

### Warnings:

This can return a huge amount of data if GetAll is true.

### Example(s):

**Get all order data for order number 43254.**  
<GetOrder GetAll="false" OrderNumber="43254"/>
      