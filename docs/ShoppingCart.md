
      ---
      title: ShoppingCart
      ---

      ### Description:

This node allows you to programmatically add to or remove from a customer's shopping cart.

### Full Syntax:

<ShoppingCart Action="Get|Update|Clear" CustomerEMail="string" CustomerGUID="uniqueidentifier" CustomerID="integer" CartType="ShoppingCart|WishCart|RecurringCart">  
<Add ExtensionData="string" Quantity="integer" VariantID="integer" Notes="string" FullSKU="string" ShippingAddressGUID="uniqueidentifier" ShippingAddressID="integer" CustomerEnteredPrice="decimal" TextOption="string" ChosenColorSKUModifier="string" ChosenColor="string" ChosenSizeSKUMOdifier="string" ChosenSize="string" VariantGUID="uniqueidentifier" ProductGUID="uniqueidentifier" ProductID="integer"/>  
<Delete ShoppingCartRecGUID="uniqueidentifier" ShoppingCartRecID="integer"/> <SetQuantity Quantity="integer" ShoppingCartRecGUID="uniqueidentifier" ShoppingCartRecID="integer"/>  
</ShoppingCart>

### Notes:

*   **Only the Clear and Get actions are currently implemented!**
*   Kit products & kits are not yet supported.
*   The Get action is processed through the 'DumpShoppingCart.xml.config' XML package.

### Warnings:

If using WSI to add/remove products from a customer's cart, be sure to explain why to them at some point!

### Example(s):

**Clear a specified customer's cart contents.**  
<ShoppingCart Action="Clear" CustomerEMail="customer@somedomain.com">  
</ShoppingCart>
      