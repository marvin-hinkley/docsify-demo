
      ---
      title: GetEntityHelper
      ---

      ### Description:

This returns the EntityHelper data currently loaded in your site's cache for the specified entity type.

### Full Syntax:

<GetEntityHelper EntityType="Manufacturer|Distributor|Category|Section|Genre|Vector"/>

### Notes:

*   The results are in nested tree order, where each level is ordered by DisplayOrder then Name.

### Warnings:

On large sites with many entities, this XML document can become very large.

### Example(s):

**Get Category EntityHelper info**  
<AspDotNetStorefrontImport>  
<GetEntityHelper EntityType="Category"/>  
</AspDotNetStorefrontImport>  
  
**Example result:**  
  
<?xml version="1.0" encoding="utf-8"?>  
<AspDotNetStorefrontImportResult Version="" DateTime="3/4/2007 7:29:48 PM">  
<GetEntityHelper EntityType="Category">  
<root>  
<Entity>  
<EntityID>24</EntityID>  
<Name>Books</Name>  
<ColWidth>4</ColWidth>  
<Description />  
<SEKeywords />  
<SEDescription />  
<SETitle />  
<SENoScript />  
<SEAltText />  
<ParentEntityID>0</ParentEntityID>  
<DisplayOrder>1</DisplayOrder>  
<SortByLooks>0</SortByLooks>  
<XmlPackage />  
<Published>1</Published>  
<SEName>books</SEName>  
<ContentsBGColor />  
<PageBGColor />  
<GraphicsColor />  
<NumObjects>3</NumObjects>  
<PageSize>20</PageSize>  
<QuantityDiscountID />  
<SkinID>0</SkinID>  
<TemplateName />  
</Entity>  
<Entity>  
<EntityID>21</EntityID>  
<Name>cat1</Name>  
<ColWidth>4</ColWidth>  
<Description />  
<SEKeywords />  
<SEDescription />  
<SETitle />  
<SENoScript />  
<SEAltText />  
<ParentEntityID>0</ParentEntityID>  
<DisplayOrder>1</DisplayOrder>  
<SortByLooks>0</SortByLooks>  
<XmlPackage />  
<Published>1</Published>  
<SEName>cat1</SEName>  
<ContentsBGColor />  
<PageBGColor />  
<GraphicsColor />  
<NumObjects>0</NumObjects>  
<PageSize>20</PageSize>  
<QuantityDiscountID />  
<SkinID>0</SkinID>  
<TemplateName />  
<Entity>  
<EntityID>22</EntityID>  
<Name>cat1-1</Name>  
<ColWidth>4</ColWidth>  
<Description />  
<SEKeywords />  
<SEDescription />  
<SETitle />  
<SENoScript />  
<SEAltText />  
<ParentEntityID>21</ParentEntityID>  
<DisplayOrder>1</DisplayOrder>  
<SortByLooks>0</SortByLooks>  
<XmlPackage />  
<Published>1</Published>  
<SEName>cat1-1</SEName>  
<ContentsBGColor />  
<PageBGColor />  
<GraphicsColor />  
<NumObjects>0</NumObjects>  
<PageSize>20</PageSize>  
<QuantityDiscountID />  
<SkinID>0</SkinID>  
<TemplateName />  
<Entity>  
<EntityID>23</EntityID>  
<Name>cat-1-1-1</Name>  
<ColWidth>4</ColWidth>  
<Description />  
<SEKeywords />  
<SEDescription />  
<SETitle />  
<SENoScript />  
<SEAltText />  
<ParentEntityID>22</ParentEntityID>  
<DisplayOrder>1</DisplayOrder>  
<SortByLooks>0</SortByLooks>  
<XmlPackage />  
<Published>1</Published>  
<SEName>cat-1-1-1</SEName>  
<ContentsBGColor />  
<PageBGColor />  
<GraphicsColor />  
<NumObjects>2</NumObjects>  
<PageSize>20</PageSize>  
<QuantityDiscountID />  
<SkinID>0</SkinID>  
<TemplateName />  
</Entity>  
<Entity>  
<EntityID>25</EntityID>  
<Name>cat-1-1-2</Name>  
<ColWidth>4</ColWidth>  
<Description />  
<SEKeywords />  
<SEDescription />  
<SETitle />  
<SENoScript />  
<SEAltText />  
<ParentEntityID>22</ParentEntityID>  
<DisplayOrder>1</DisplayOrder>  
<SortByLooks>0</SortByLooks>  
<XmlPackage />  
<Published>1</Published>  
<SEName>cat-1-1-2</SEName>  
<ContentsBGColor />  
<PageBGColor />  
<GraphicsColor />  
<NumObjects>1</NumObjects>  
<PageSize>20</PageSize>  
<QuantityDiscountID />  
<SkinID>0</SkinID>  
<TemplateName />  
</Entity>  
</Entity>  
</Entity>  
<Entity>  
<EntityID>26</EntityID>  
<Name>Category 1</Name>  
<ColWidth>4</ColWidth>  
<Description />  
<SEKeywords />  
<SEDescription />  
<SETitle />  
<SENoScript />  
<SEAltText />  
<ParentEntityID>0</ParentEntityID>  
<DisplayOrder>1</DisplayOrder>  
<SortByLooks>0</SortByLooks>  
<XmlPackage />  
<Published>1</Published>  
<SEName>category-1</SEName>  
<ContentsBGColor />  
<PageBGColor />  
<GraphicsColor />  
<NumObjects>1</NumObjects>  
<PageSize>20</PageSize>  
<QuantityDiscountID />  
<SkinID>0</SkinID>  
<TemplateName />  
</Entity>  
<Entity>  
<EntityID>3</EntityID>  
<Name>Golf</Name>  
<ColWidth>4</ColWidth>  
<Description />  
<SEKeywords />  
<SEDescription />  
<SETitle />  
<SENoScript />  
<SEAltText />  
<ParentEntityID>0</ParentEntityID>  
<DisplayOrder>1</DisplayOrder>  
<SortByLooks>0</SortByLooks>  
<XmlPackage />  
<Published>1</Published>  
<SEName>golf</SEName>  
<ContentsBGColor />  
<PageBGColor />  
<GraphicsColor />  
<NumObjects>1</NumObjects>  
<PageSize>20</PageSize>  
<QuantityDiscountID />  
<SkinID>0</SkinID>  
<TemplateName />  
</Entity>  
<Entity>  
<EntityID>2</EntityID>  
<Name>PWS Items</Name>  
<ColWidth>4</ColWidth>  
<Description />  
<SEKeywords />  
<SEDescription />  
<SETitle />  
<SENoScript />  
<SEAltText />  
<ParentEntityID>0</ParentEntityID>  
<DisplayOrder>1</DisplayOrder>  
<SortByLooks>0</SortByLooks>  
<XmlPackage />  
<Published>1</Published>  
<SEName>pws-items</SEName>  
<ContentsBGColor />  
<PageBGColor />  
<GraphicsColor />  
<NumObjects>2</NumObjects>  
<PageSize>20</PageSize>  
<QuantityDiscountID />  
<SkinID>0</SkinID>  
<TemplateName />  
</Entity>  
<Entity>  
<EntityID>15</EntityID>  
<Name>Random Items</Name>  
<ColWidth>4</ColWidth>  
<Description />  
<SEKeywords />  
<SEDescription />  
<SETitle />  
<SENoScript />  
<SEAltText />  
<ParentEntityID>0</ParentEntityID>  
<DisplayOrder>1</DisplayOrder>  
<SortByLooks>0</SortByLooks>  
<XmlPackage />  
<Published>1</Published>  
<SEName>random-items</SEName>  
<ContentsBGColor />  
<PageBGColor />  
<GraphicsColor />  
<NumObjects>1</NumObjects>  
<PageSize>20</PageSize>  
<QuantityDiscountID />  
<SkinID>0</SkinID>  
<TemplateName />  
</Entity>  
<Entity>  
<EntityID>1</EntityID>  
<Name>Test Cat</Name>  
<ColWidth>4</ColWidth>  
<Description />  
<SEKeywords />  
<SEDescription />  
<SETitle />  
<SENoScript />  
<SEAltText />  
<ParentEntityID>0</ParentEntityID>  
<DisplayOrder>1</DisplayOrder>  
<SortByLooks>0</SortByLooks>  
<XmlPackage>entity.grid.xml.config</XmlPackage>  
<Published>1</Published>  
<SEName>test-cat</SEName>  
<ContentsBGColor />  
<PageBGColor />  
<GraphicsColor />  
<NumObjects>9</NumObjects>  
<PageSize>20</PageSize>  
<QuantityDiscountID />  
<SkinID>0</SkinID>  
<TemplateName>testcat.ascx</TemplateName>  
</Entity>  
</root>  
</GetEntityHelper>  
</AspDotNetStorefrontImportResult>
      