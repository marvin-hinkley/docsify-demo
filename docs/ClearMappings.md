
      ---
      title: ClearMappings
      ---

      ### Description:

Clears the mappings of all products to any entity.

### Full Syntax:

<ClearMappings EntityType="Manufacturer|Distributor|Category|Section|Genre|Vector" EntityID="integer" EntityGUID="uniqueidentifier"/>

### Notes:

*   At least one of EntityID or EntityGUID must be supplied

### Warnings:

None

### Example(s):

**Clear all product mappings to Manufacturer 14**  
<ClearMappings EntityType="Manufacturer" EntityID="14"/>
      