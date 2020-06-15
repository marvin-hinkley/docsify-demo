
      ---
      title: Get
      ---

      ### Description:

The Get node is a multi-purpose data retrieval function, which can be used to retrieve any information from the database. If desired, that information can be output in a specific format determined by a custom XML package.

### Full Syntax:

<Get Table="string" Name="string"> <IDColumn>string</IDColumn>  
<XmlPackage RuntimeParams="x=1&y=2">packagename</XmlPackage>  
<DefaultWhereClause>IsNew=1</DefaultWhereClause>  
<OrderBy>DisplayOrder, Name</OrderBy>  
<Criteria Field1="value" Field2="value" Field3="value"... />  
</Get>

### Notes:

*   **Table** \- The name of the table to retrieve data from.
*   **Name** \- The name of this 'get' action. Your WSI integration app can use this to find the results in the XML document we return.
*   **IDColumn** \- You can (optionally) force WSI to use a specific column as the identifier column.
*   **XmlPackage** \- The name of the XmlPackage you want to process each row of results. This is optional, if no package is specified the results will be returned in simple XML format. Using an XmlPackage allows server side processing of the results before the data is returned (ie data formatting, decrypting CC information, etc).
*   **RuntimeParams** \- Any runtime parameters that should be passed to the XmlPackage.
*   **DefaultWhereClause** \- Specify a WHERE clause to use to constrain the results (optional). If provided, this must be in proper SQL Server syntax.
*   **OrderBy** \- Specify a field name to sort results on.
*   **Criteria** \- Specify multiple fields with desired values, which are 'AND'ed together into a SQL constraint to restrict data returned (optional).
*   You should only use this node when there is not an existing WSI node that already returns the data you need.
*   There is no functional difference between listing your entire WHERE clause in the 'DefaultWhereClause' node, or listing out individual criteria with Criteria nodes. Either way, the SQL query is built as SELECT <IDColumn> FROM <TableName> with (NOLOCK) WHERE + <Criteria Nodes> + AND + <DefaultWhereClause>.

### Warnings:

This is a very powerful element that should only be used by those familiar with SQL. Depending on what's being requested, this element can take a while to process, and may return a very large data set.

### Example(s):

**This example returns all "New" orders, and uses the DumpOrder XmlPackage to format each order as it is returned. Multiple orders can be returned. The XmlPackage fires on "each" row in the result set to do formatting and processing. We are also passing in a RunTime param to tell the XmlPackage additional instructions.**  
<AspDotNetStorefrontImport Verbose="true">  
<Get Table="Orders" Name="Get1">  
<XmlPackage RuntimeParams="ShowCardNumber=true">DumpOrder.xml.config</XmlPackage>  
<OrderBy>OrderNumber desc</OrderBy>  
<Criteria IsNew="1" />  
</Get>  
</AspDotNetStorefrontImport>

**This example retrieves the Customer information for Customer with e-mail address 'sales@aspdotnetstorefront.com'. Again, an XmlPackage is used to process each result row.**   
<AspDotNetStorefrontImport Verbose="true">  
<Get Table="Customer" Name="Get1">  
<XmlPackage>DumpCustomer.xml.config</XmlPackage>  
<DefaultWhereClause />  
<OrderBy>CustomerID asc</OrderBy>  
<Criteria Email="sales@aspdotnetstorefront.com" />  
</Get>  
</AspDotNetStorefrontImport>

**This example retrieves the Customer information for Customer 14, not using any XmlPackage.**  
<AspDotNetStorefrontImport Verbose="true">  
<Get Table="Customer" Name="Get1">   
<Criteria CustomerID="15" />  
</Get>  
</AspDotNetStorefrontImport>

**This example retrieves the Customer information for all customers from affiliate 13 who have the OkToEMail flag set to true.**  
<AspDotNetStorefrontImport Verbose="true">  
<Get Table="Customer" Name="Get1">   
<Criteria AffiliateID="13" OkToEMail="1" />  
</Get>  
</AspDotNetStorefrontImport>

**This example retrieves all customers for Affiliate 13 who have Notes fields which are not null and e-mail addresses from domain "@pdq.com".**   
<AspDotNetStorefrontImport Verbose="true">  
<Get Table="Customer" Name="Get1">   
<Criteria AffiliateID="13" />  
<DefaultWhereClause>(Notes IS NOT NULL and Notes <>   
'') and Email lke '%@pdq.com'</DefaultWhereClause>  
</Get>  
</AspDotNetStorefrontImport>
      