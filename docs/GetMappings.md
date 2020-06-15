
      ---
      title: GetMappings
      ---

      ### Description:

Returns ProductID, GUID, and DisplayOrder for all products mapped to the specified entity.

### Full Syntax:

<GetMappings EntityType="Manufacturer|Distributor|Category|Section|Genre|Vector" EntityID="integer" EntityGUID="uniqueidentifier"/>

### Notes:

None

### Warnings:

None

### Example(s):

**Return all products for category 1.**  
<GetMappings EntityType="Category" EntityID="1"/>
      