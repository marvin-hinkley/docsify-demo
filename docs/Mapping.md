
      ---
      title: Mapping
      ---

      ### Description:

This node allows you to add/delete product mappings to any of the entities, and set the display order of those products within the entity.

### Full Syntax:

<Mapping Action="Add|Delete" EntityType="Manufacturer|Distributor|Category|Section|Genre|Vector" EntityID="integer" EntityGUID="uniqueidentifier" ObjectType="Product" ObjectID="integer" ObjectGUID="uniqueidentifier" DisplayOrder="integer"/>

### Notes:

*   Adding a new mapping does not delete any of the existing ones. If you want to 'move' a product from one entity to another, it'll take both an add, and a delete. If multiple mappings are being removed, you may want to use the ClearMappings node.
*   At least one of EntityID or EntityGUID and ProductID or ProductGUID must be provided.
*   Since there is no 'update' action, changing a product's display order within an entity with this node would require both a delete action (for the old display order) and an add action (to set the new one).

### Warnings:

None

### Example(s):

**Add a mapping from Product 14 to Category 3.**  
<Mapping Action="Add" EntityType="Category" EntityID="3" ObjectType="Product" ObjectID="14" DisplayOrder="4"/>
      