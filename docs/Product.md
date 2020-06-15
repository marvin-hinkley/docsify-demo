
      ---
      title: Product
      ---

      ### Description:

This node allows you to add or edit a product.

### Full Syntax:

<Product Action="Add|Update|Delete|Nuke|Lookup" EnsureDefaultVariant="boolean" GUID="uniqueidentifier" SKU="string" Name="string" ID="integer">  
<Name>string</Name>  
<Summary>string</Summary>  
<Description>string</Description>  
<SpecTitle>string</SpecTitle>  
<MiscText>string</MiscText>  
<Notes>string</Notes>  
<FroogleDescription>string</FroogleDescription>  
<SKU>string</SKU>  
<ManufacturerPartNumber>string</ManufacturerPartNumber>  
<SwatchImageMap>string</SwatchImageMap>  
<SE>  
<SEName>string</SEName>  
<SETitle>string</SETitle>  
<SEKeywords>string</SEKeywords>  
<SEDescription>string</SEDescription>  
<SENoScript>string</SENoScript>  
<SEAltText>string</SEAltText>  
</SE>  
<SizeOptionPrompt>string</SizeOptionPrompt>  
<ColorOptionPrompt>string</ColorOptionPrompt>  
<ProductType Name="string" ID="integer" GUID="uniqueidentifier"/>  
<TaxClass Name="string" ID="integer" GUID="uniqueidentifier"/>  
<SalesPrompt Name="string" ID="integer" GUID="uniqueidentifier"/>  
<SpecCall>string</SpecCall>  
<SpecsInline>string</SpecsInline>  
<Display>  
<XmlPackage>string</XmlPackage>  
<ColWidth>integer</ColWidth>  
<SkinID>integer</SkinID>  
<TemplateName>string</TemplateName>  
</Display>  
<Images UseAppConfigs="boolean" >  
<Icon Extension="gif|jpg|png|jpeg" Delete="boolean">base64 encoded image data here</Icon>  
<Medium Extension="gif|jpg|png|jpeg" Delete="boolean">base64 encoded image data here</Medium>  
<Large Extension="gif|jpg|png|jpeg" Delete="boolean">base64 encoded image data here</Large>  
<ImageFilenameOverride></ImageFilenameOverride>  
</Images>  
<QuantityDiscount Name="string" ID="integer" GUID="uniqueidentifier"/>  
<RelatedProducts>  
<CX ID="integer" GUID="uniqueidentifier"/>  
<CX ID="integer" GUID="uniqueidentifier"/>  
<CX ID="integer" GUID="uniqueidentifier"/>  
<CX ID="integer" GUID="uniqueidentifier"/>  
<CX ID="integer" GUID="uniqueidentifier"/>  
</RelatedProducts>  
<UpsellProducts DiscountPercentage="">  
<CX ID="integer" GUID="uniqueidentifier"/>  
<CX ID="integer" GUID="uniqueidentifier"/>  
<CX ID="integer" GUID="uniqueidentifier"/>  
<CX ID="integer" GUID="uniqueidentifier"/>  
<CX ID="integer" GUID="uniqueidentifier"/>  
</UpsellProducts>  
<RequiresProducts>  
<CX ID="integer" GUID="uniqueidentifier"/>  
<CX ID="integer" GUID="uniqueidentifier"/>  
<CX ID="integer" GUID="uniqueidentifier"/>  
<CX ID="integer" GUID="uniqueidentifier"/>  
<CX ID="integer" GUID="uniqueidentifier"/>  
</RequiresProducts>  
<InventoryType>  
<TrackInventoryBySizeAndColor></TrackInventoryBySizeAndColor>  
<WarehouseLocation></WarehouseLocation>  
</InventoryType>  
<IsFeatured>boolean</IsFeatured>  
<IsAKit>boolean</IsAKit>  
<IsSystem>boolean</IsSystem>  
<ShowBuyButton>boolean</ShowBuyButton>  
<Published>boolean</Published>  
<Wholesale>boolean</Wholesale>  
<RequiresRegistration>boolean</RequiresRegistration>  
<HidePriceUntilCart>boolean</HidePriceUntilCart>  
<IsCallToOrder>boolean</IsCallToOrder>  
<ExcludeFromPriceFeeds>boolean</ExcludeFromPriceFeeds>  
<GoogleCheckoutAllowed>boolean</GoogleCheckoutAllowed>  
<RequiresTextOption>boolean</RequiresTextOption>  
<TextOptionMaxLength>integer</TextOptionMaxLength>  
<TextOptionPrompt>string</TextOptionPrompt>  
<AvailableStartDate>datetime</AvailableStartDate>  
<AvailableStopDate>datetime</AvailableStopDate>  
<StoreMappings AutoCleanup="boolean" PreserveExistingRecords="boolean">  
<Store StoreId="int" StoreName="string" />  
<Store StoreId="int" StoreName="string" />  
</StoreMappings>  
<Mappings AutoCleanup="boolean">  
<Entity EntityType="Manufacturer|Distributor|Category|Section|Genre|Vector" Name="string" XPath="string" ID="integer" GUID="uniqueidentifier" DisplayOrder="integer"/>  
<Entity EntityType="Manufacturer|Distributor|Category|Section|Genre|Vector" Name="string" XPath="string" ID="integer" GUID="uniqueidentifier" DisplayOrder="integer"/>  
<Entity EntityType="Manufacturer|Distributor|Category|Section|Genre|Vector" Name="string" XPath="string" ID="integer" GUID="uniqueidentifier" DisplayOrder="integer"/>  
<Entity EntityType="Manufacturer|Distributor|Category|Section|Genre|Vector" Name="string" XPath="string" ID="integer" GUID="uniqueidentifier" DisplayOrder="integer"/>  
<Entity EntityType="Manufacturer|Distributor|Category|Section|Genre|Vector" Name="string" XPath="string" ID="integer" GUID="uniqueidentifier" DisplayOrder="integer"/>  
</Mappings>  
<ExtensionData>string</ExtensionData>  
<ExtensionData2>string</ExtensionData2>  
<ExtensionData3>string</ExtensionData3>  
<ExtensionData4>string</ExtensionData4>  
<ExtensionData5>string</ExtensionData5>  
<Kit AutoCleanup="boolean"> <!-- only used if IsAKit is 1 -->  
<KitGroup>  
<Name>string</Name>  
<Description>string</Description>  
<DisplayOrder>integer</DisplayOrder>  
<KitGroupTypeID>integer</KitGroupTypeID>  
<IsRequired>boolean</IsRequired>  
<IsReadOnly>integer</IsReadOnly> <KitItem>  
<Name>string</Name>  
<Description>string</Description>  
<PriceDelta>decimal</PriceDelta>  
<IsDefault>boolean</IsDefault>  
<DisplayOrder>integer</DisplayOrder>  
<TextOptionMaxLength>integer</TextOptionMaxLength>  
<TextOptionWidth>integer</TextOptionWidth>  
<TextOptionHeight>integer</TextOptionHeight>  
<WeightDelta>decimal</WeightDelta>  
<InventoryQuantityDelta>integer</InventoryQuantityDelta> </KitItem>  
</KitGroup>  
</Kit>  
<Variants AutoCleanup="boolean">  
<Variant Action="Add|Update|Delete|Nuke|Lookup" Name="string" SKUSuffix="" GUID="uniqueidentifier" ID="integer">  
<IsDefault>boolean</IsDefault>  
<Name>string</Name>  
<Description>string</Description>  
<SE>  
<SEName>string</SEName>  
<SEKeywords>string</SEKeywords>  
<SEDescription>string</SEDescription>  
<SENoScript>string</SENoScript>  
<SEAltText>string</SEAltText>  
</SE>  
<FroogleDescription>string</FroogleDescription>  
<SKUSuffix>string</SKUSuffix>  
<ManufacturerPartNumber>string</ManufacturerPartNumber>

<GTIN>integer</GTIN>  
<Price>decimal</Price>  
<SalePrice>decimal</SalePrice>  
<Weight>decimal</Weight>  
<MSRP>decimal</MSRP>  
<Cost>decimal</Cost>  
<Points>integer</Points>  
<Dimensions>string</Dimensions>  
<Inventory>integer</Inventory>  
<DisplayOrder>integer</DisplayOrder>  
<Notes>string</Notes>  
<IsTaxable>boolean</IsTaxable>  
<IsShipSeparately>boolean</IsShipSeparately>  
<IsDownload>boolean</IsDownload>  
<DownloadLocation>string</DownloadLocation>  
<FreeShipping>boolean</FreeShipping>  
<Published>boolean</Published>  
<Wholesale>boolean</Wholesale>  
<IsRecurring>boolean</IsRecurring>  
<RecurringInterval>integer</RecurringInterval>  
<RecurringIntervalType>integer</RecurringIntervalType>  
<RestrictedQuantities>string</RestrictedQuantities>  
<MinimumQuantity>integer</MinimumQuantity>  
<Images ClearBeforeImport="boolean">  
<Icon Extension="gif|jpg|png|jpeg">base64 encoded image data here</Icon>  
<Medium Extension="gif|jpg|png|jpeg">base64 encoded image data here</Medium>  
<Large Extension="gif|jpg|png|jpeg">base64 encoded image data here</Large>  
<ImageFilenameOverride></ImageFilenameOverride>  
</Images>  
<CustomerEntersPrice>boolean</CustomerEntersPrice>  
<CustomerEntersPricePrompt>string</CustomerEntersPricePrompt>  
<ExtensionData>string</ExtensionData>  
<ExtensionData2>string</ExtensionData2>  
<ExtensionData3>string</ExtensionData3>  
<ExtensionData4>string</ExtensionData4>  
<ExtensionData5>string</ExtensionData5>  
<Sizes>  
<Size SKUModifier="string" PriceDelta="decimal">red</Size>  
<Size SKUModifier="string" PriceDelta="decimal">green</Size>  
<Size SKUModifier="string" PriceDelta="decimal">blue</Size>  
</Sizes>  
<Colors>  
<Color SKUModifier="string" PriceDelta="decimal">s</Color>  
<Color SKUModifier="string" PriceDelta="decimal">m</Color>  
<Color SKUModifier="string" PriceDelta="decimal">l</Color>  
</Colors>  
<InventoryBySizeAndColor>  
<Inv Color="string" Size="string" Quantity="integer" VendorID="string" VendorFullSKU="string" ExtensionData="string"/>  
<Inv Color="string" Size="string" Quantity="integer" VendorID="string" VendorFullSKU="string" ExtensionData="string"/>  
<Inv Color="string" Size="string" Quantity="integer" VendorID="string" VendorFullSKU="string" ExtensionData="string"/>  
<Inv Color="string" Size="string" Quantity="integer" VendorID="string" VendorFullSKU="string" ExtensionData="string"/>  
</InventoryBySizeAndColor>  
</Variant>  
</Variants>  
</Product>

### Notes:

*   On a lookup, both a Name and a SKU node must be passed.
*   On an update, if you want to set a field to NULL or "empty string" use an empty element syntax (e.g. <Summary></Summary>).
*   On an update, if you want to leave the existing value on that field, omit the field from the Xml input document.
*   If an Update, Nuke, or Delete is done, the request should have an ID or GUID for the best processing. If none is provided, a lookup will be done based on the combination of product name and SKU, but this will slow down processing, especially on bulk updates.
*   Incremental updates are supported
*   You can assign your own GUID on product Add. The GUID and new ID will be returned to you for association within your calling system.
*   UseAppConfigs on the Image node tells WSI to use the image resize AppConfigs for any images you provide.
*   If the EnsureDefaultVariant attribute is set to true, WSI will pick one of the product's variants and flag it as the default.

### Warnings:

Remember that between product data, variants, kits, inventory, entity mappings, etc a _lot_ of tables are involved in product data. Be very sure that you understand the DB structure and how products are put together before doing any bulk product updates.
      