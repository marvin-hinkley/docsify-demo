
      ---
      title: GetEntity
      ---

      ### Description:

Returns data for the specified entity, including mappings and sub-entities.

### Full Syntax:

<GetEntity XPathLookup="/x/y/z" EntityType="Manufacturer|Distributor|Category|Section|Genre|Vector" EntityGUID="uniqueidentifier" EntityID="integer" IncludeImages="boolean" GetAllLocale="boolean" Recursive="boolean"/>

### Notes:

*   If ID and GUID are left blank, WSI will return all of the entities of the specified type from the root all the way down the tree.
*   If you specify an ID or GUID, WSI will return all of that entity's data, as well as any sub-entities under it.
*   If IncludeImages is true, all image data (icon, medium, and large) images will be returned for all entities.
*   The desired entity can be specified by ID, GUID, or Xpath.

### Warnings:

Depending on what you specify (or more importantly, don't specify) and your entity structure, the returned data set could be huge.

### Example(s):

**Return all information for all categories.**  
<GetEntity EntityType="Category" EntityID="1" Recursive="boolean" IncludeImages="boolean"/>
      