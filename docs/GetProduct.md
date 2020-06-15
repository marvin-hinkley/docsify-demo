
      ---
      title: GetProduct
      ---

      ### Description:

Returns product data.

### Full Syntax:

<GetProduct ID="integer" GUID="uniqueidentifier" IncludeImages="boolean" GetAll="boolean" GetAllLocale="boolean" IncludeVariants="boolean" ForEntityGUID="uniqueidentifier" ForEntityID="integer" ForEntityType="Manufacturer|Distributor|Category|Section|Genre|Vector|Affiliate|CustomerLevel"/>

### Notes:

*   If you specify an ID or GUID, information for only that product will be returned.
*   If you specify an EntityType and an entity identifier (ID or GUID) then all products mapped to that entity will be returned.
*   If GetAllLocale is left out of the request, only the information for the web.config locale will be returned.
*   If IncludeVariants is true, it will recursively include all variant data also.

### Warnings:

This can return a huge amount of data, especially if IncludeImages or GetAllLocale are true.

### Example(s):

**Return the bare product data for product ID 4**  
<GetProduct ID="4"/>

**Return the product data for product ID 4 including variant data**  
<GetProduct ID="4" IncludeVariants="true"/>

**Return the product data for product ID 4 including variant data and images as base 64 encoded strings**  
<GetProduct ID="4" IncludeVariants="true" IncludeImages="true"/>

**Return the product data and variants for Category 1**  
<GetProduct ForEntityType="Category" ForEntityID="1" IncludeVariants="true" />
      