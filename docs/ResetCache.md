
      ---
      title: ResetCache
      ---

      ### Description:

If this node is in your input document, it will do the same action as the **Refresh Store** link does in the admin console. This will reload all cached Entity Helpers, AppConfigs, etc. You can issue this node to force the storefront to update after you have added categories, manufacturers, products, etc.

### Full Syntax:

<ResetCache Confirm="true"/>

### Notes:

*   The Confirm flag must be present and set to true, or the ResetCache node will be ignored.
*   This element cannot be inside a <Transaction> node.

### Warnings:

Calling this action too often will degrade storefront performance. You should call this at most once per input document, typically at the end.

### Example(s):

<AspDotNetStorefrontImport>  
... nodes here to add products, add categories, etc...  
... more nodes here to do more things ...  
<ResetCache Confirm="true"/>  
</AspDotNetStorefrontImport>
      