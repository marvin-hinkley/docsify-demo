
      ---
      title: UndoLastImport
      ---

      ### Description:

This node allows you to 'roll back' previous WSI imports. When this node is submitted to WSI, the 'aspdnsf\_UndoImport' stored procedure is run. That sproc deletes rows from the majority of tables that WSI updates, WHERE IsImport=1.

### Full Syntax:

<UndoLastImport Confirm="true"/>

### Notes:

*   This node will only execute if the Confirm attribute is included and set to true.
*   If you want to be able to use this, make sure that the import XML you send to WSI when adding the rows you may want to remove later has the SetImportFlag attribute set to true in the AspDotNetStorefrontImport header.

### Warnings:

This action cannot be undone, and cannot be part of a Transaction! Be absolutely sure you want to delete the data before executing this node.
      