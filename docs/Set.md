
      ---
      title: Set
      ---

      ### Description:

This node can be used to update fields in almost any table, keying off of ID, GUID, or a columnID you specify.

### Full Syntax:

<Set Table="string" ID="integer" GUID="uniqueidentifier" IDColumn="string" GUIDColumn="string">  
<Field1>value</Field1>  
<Field2>value</Field2>  
</Set>

### Notes:

*   **Table** \- Name of the table you are updating.
*   **Name** \- The name of this 'set' action. Your WSI integration app can use this to find the results in the XML document we return.
*   **ID** \- The ID of the row being updated. Unless a specific column is specified, WSI will figure out the ID column for you.
*   **GUID** \- The GUID of the row being updated. Unless a specific column is specified, WSI will figure out the GUID column for you.
*   **IDColumn** \- Force WSI to use a specific column as the identity column used for ID matching. This is generally not needed. If you do specify a column here, be sure each value in it is unique!
*   **GUIDColumn** \- Force WSI to use a specific column as the identity column used for GUID matching. This is generally not needed. If you do specify a column here, be sure each value in it is unique!
*   You must specify either an ID or a GUID for every Set.
*   Set can only affect one matching record at a time, but it can update multiple fields in that record.
*   Only the specified fields are updated. Other fields are not touched.
*   Use other update nodes provided by WSI when available, <Set> should be a 'last resort'.

### Warnings:

This is a very powerful node, which should only be used if absolutely necessary, by someone familiar with SQL. This node should be contained in a Transaction node.

### Example(s):

**Update a Product Name**  
<AspDotNetStorefrontImport>  
<Set Table="Product" ID="14">  
<Name>Lion King Updated Name</Name>  
</Set>  
</AspDotNetStorefrontImport>

**Update an Order record with shipping tracking information. Note that the WSI knows that the "ID" identity column for an order is "OrderNumber" and sets that for you during execution. Unless specifying a different column to use, you always just provide an ID or GUID and WSI will figure it out.**  
<AspDotNetStorefrontImport>  
<Set Table="Orders" ID="100003>  
<ShippedOn>3/4/2007</ShippedOn>  
<ShippedVia>FedEx</ShippedVia>  
<ShippingTrackingNumber>12345</ShippingTrackingNumber>  
</Set>  
</AspDotNetStorefrontImport>
      