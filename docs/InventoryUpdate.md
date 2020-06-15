
      ---
      title: InventoryUpdate
      ---

      ### Description:

This node is used to update product inventory levels.

### Full Syntax:

<AspDotNetStorefrontImport Version="7.1">  
<InventoryUpdate MatchKey="VendorFullSKU|VendorID|VariantID|VariantSKU">  
<Inv Color="string" ExtensionData="" WeightDelta="decimal" VendorFullSKU="string" VendorID="string" WarehouseLocation="string" Quantity="integer" Size="string" VariantSKU="string" VariantID="integer" />  
<Inv Color="string" ExtensionData="" WeightDelta="decimal" VendorFullSKU="string" VendorID="string" WarehouseLocation="string" Quantity="integer" Size="string" VariantSKU="string" VariantID="integer" />  
</InventoryUpdate>  
</AspDotNetStorefrontImport>

### Notes:

*   **MatchKey** \- Only used if the product is tracking inventory by size and color. This tells it which of the fields to use as an ID to locate the desired product.
*   On the <Inv> node, you only need the VariantID and Quantity fields if no MatchKey is specified (simply inventory update).

### Warnings:

None

### Example(s):

**Set the regular inventory for variantID 47 to 376.**  
<AspDotNetStorefrontImport Version="7.1">  
<InventoryUpdate>  
<Inv Quantity="376" VariantID="47" />  
</InventoryUpdate>  
</AspDotNetStorefrontImport>
      