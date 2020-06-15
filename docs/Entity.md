
      ---
      title: Entity
      ---

      ### Description:

This node allows you to add new entities, or update existing ones.

### Full Syntax:

<Entity EntityType="Manufacturer|Distributor|Category|Section|Genre|Vector" Action="Add|Update|Delete|Nuke|Lookup" ID="integer" XPathLookup="x/y/z" GUID="uniqueidentifier" RemoveMappings="boolean">  
<Name>string</Name>  
<XPath>string</XPath>  
<SE>  
<SEName>string</SEName>  
<SETitle>string</SETitle>  
<SEKeywords>string</SEKeywords>  
<SEDescription>string</SEDescription>  
<SENoScript>string</SENoScript>  
<SEAltText>string</SEAltText>  
</SE>  
<Address1>string</Address1>  
<Address2>string</Address2>  
<Suite>string</Suite>  
<City>string</City>  
<State>string</State>  
<ZipCode>string</ZipCode>  
<Country>string</Country>  
<Phone>string</Phone>  
<FAX>string</FAX>  
<URL>string</URL>  
<EMail>string</EMail>  
<Summary>string</Summary>  
<Description>string</Description>  
<Display>  
<XmlPackage>string</XmlPackage>  
<ColWidth>integer</ColWidth>  
<PageSize>integer</PageSize>  
<SkinID>integer</SkinID>  
<TemplateName>string</TemplateName>  
</Display>  
<Images>  
<Icon Extension="gif|jpg|png|jpeg" Delete="boolean">base64 encoded image data here</Icon>  
<Medium Extension="gif|jpg|png|jpeg" Delete="boolean">base64 encoded image data here</Medium>  
<Large Extension="gif|jpg|png|jpeg" Delete="boolean">base64 encoded image data here</Large>  
<ImageFilenameOverride></ImageFilenameOverride>  
</Images>  
<QuantityDiscount Name="string" ID="integer" GUID="uniqueidentifier"/>  
<DisplayOrder>integer</DisplayOrder>  
<Published>boolean</Published>  
<Wholesale>boolean</Wholesale>  
<ExtensionData>string</ExtensionData>  
<StoreMappings AutoCleanup="boolean" PreserveExistingRecords="boolean">  
<Store StoreId="int" StoreName="string" />  
<Store StoreId="int" StoreName="string" />  
</StoreMappings>  
</Entity>

### Notes:

*   Entities can be nested, to form a parent-child relationship. In nested relationship, entities can be nested the way you want using the Xpath node (e.g. /ParentCat/SubCat/SubSubCat/etc). For example, if adding a category called 'SciFi' under an existing category of 'Books', setting the Xpath node to <XPath>/Books/SciFi</XPath> will add the new category as a child of the old one.
*   On an update, if you want to set a field to NULL or "empty string" use an empty element syntax (e.g. <Summary>string</Summary>).
*   On an update, if you want to NOT TOUCH the existing value on that field, omit the field from the Xml input document.
*   _Only name field is required_. All other fields are optional. ML-encoded data can be included (<ml>....</ml>) to import values in multiple locales at once.
*   If the XPathLookup attribute is not null, the software will look for the matching entity name & type at that xpath, rather than the root level.

### Warnings:

Remember that entities are tied to many other elements within the store. Be fully aware of the changes you're making before doing them.

### Example(s):

**Example 1: Add a new root category:**

<Entity EntityType="Category " Action="Add">  
<Name>Books</Name>  
</Entity>

**Example 2: Update the name for Category 14:**

<Entity EntityType="Category " Action="Update" ID="14">  
<Name>Books Updated</Name>  
</Entity>

**Example 3: Update the name for Category 283F1634-6B3B-4452-B795-2B586B4D47DB:**

<Entity EntityType="Category " Action="Update" GUID="283F1634-6B3B-4452-B795-2B586B4D47DB">  
<Name>Books Updated</Name>  
</Entity>

**Example 4: Update the XmlPackage being used for Category 3:**

<Entity EntityType="Category " Action="Update" ID="3">  
<XmlPackage>entity.grid.xml.config</ XmlPackage >  
</Entity>
      