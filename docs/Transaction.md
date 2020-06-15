
      ---
      title: Transaction
      ---

      ### Description:

You can use this node to start a transaction group. All nodes in that group must complete successfully for the transaction to commit, or they are all rolled back. You can use any of the supported nodes inside the transaction node. When the transaction executes, the Transaction element is echoed to the output Xml document, along with the results of each node inside that transaction. At the end of the Transaction output node, there will either be a final <Commit/> or <Rollback/> node which indicates the final status of the transaction.

Each transaction can be given a name, so your output handler can associate transaction results. If no name is given to the transaction, it will be assigned a default name by the WSI (e.g. Transaction1, Transaction2, etc...)

### Full Syntax:

<Transaction Name="string">

### Notes:

*   You can have more than one transaction in a single WSI input Xml doc. Each transaction will commit or rollback individually
*   Not all WSI nodes are allowed inside a Transaction element
*   Transaction nodes cannot be nested!

### Warnings:

None

### Example(s):

<Transaction Name="TX1">  
... your XML nodes here ...  
</Transaction>
      