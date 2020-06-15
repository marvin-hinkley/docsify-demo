
      ---
      title: GetCustomer
      ---

      ### Description:

Returns customer data.

### Full Syntax:

<GetCustomer ID="integer" GUID="uniqueidentifier" GetAll="boolean" EMail="string"/>

### Notes:

*   Only one of the identifiers is needed if you're specifying a customer, however remember that email may not be a unique identifier on your site if you're allowing duplicate email addresses.
*   If GetAll is set to true, all data for all customers (including addresses) will be returned.

### Warnings:

This can return a huge amount of data, if GetAll is true.

### Example(s):

**Return the data for the specified customer.**  
<AspDotNetStorefrontImport Version="7.1">  
<GetCustomer EMail="admin@aspdotnetstorefront.com"/>  
</AspDotNetStorefrontImport>
      