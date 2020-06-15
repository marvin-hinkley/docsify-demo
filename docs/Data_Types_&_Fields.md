
      ---
      title: Data Types & Fields
      ---

      ### STRING fields

String fields can contain any text (properly XmlEncoded) that you need. CDATA field values can also be used to specify string data contents if markup/encoding issues become problematic (see below).

### ML fields (for multi-lingual sites)

Multi-lingual data that store admins enter (names, descriptions, etc) are stored in what is referred to as 'ML Format'. The WSI interface supports specification of ML formatted fields. Any such field can have its value set as a sub Xml fragment in this format:

    <ml>  
        <locale name="en-US">en us value</locale>  
        <locale name="ja-JP">ja jp value</locale>  
    </ml>  
  
e.g.  
  
    <Name>  
        <ml>  
            <locale name="en-US">en us value</locale>  
            <locale name="ja-JP">ja jp value</locale>  
        </ml>  
    </Name>

### CDATA Fields

Almost any "string" field can also be specified in CDATA syntax, if that is more convenient to avoid Encoding problems, e.g.:

 <Description >  
 <!\[CDATA\[  
 Complex product description here, including HTML markup. CDATA tags ensures that's preserved.  
 \]\]>  
 </Description >

### BOOLEAN Fields

All Boolean fields can be any of:

*   1, "true", "TRUE", "True", "yes", "Yes", "YES" - meaning logical "true"

...or:

*   0, "false", "FALSE", "False", "no", "No", "NO" - meaning logical "false"

### DECIMAL Fields

All Decimal fields (e.g. prices, weights, etc) must be in en-US decimal format, without commas or leading currency signs (e.g. xx.xx). The format is always ####.##, regardless of your store master locale setting. Do _not_ use your locale's special formatting (ie commas for decimal separators).

### DATETIME Fields

All DateTime field values MUST be in your store master locale format. That is controlled by the locale settings in your web.config file. The text "NULL" can be used to assign a date field to "no value".

### WSI Import Doc Header Attributes

The import doc has a number of header attributes, which can affect how the document is processed:

   <AspDotNetStorefrontImport Version="7.1" AutoLazyAdd="true|false" AutoCleanup="true|false" Verbose="true|false" TransactionsEnabled="true|false">   
  
   ...your XML...   
  
   </AspDotNetStorefrontImport>

Each attribute is listed and described below:

**Version**: This should be set to 7.1

**AutoLazyAdd (Default=false)**: This should be set to either true or false. This flag affects how an update action behaves if an item doesn't exist (e.g. you issue an update action on a product that doesn't exist). If AutoLazyAdd="false", then an error will be raised in the case you update a non-existent item. If AutoLazyAdd="true", the product will be automatically added, using the values in the update action node. Note that this can lead to the creation of products that have most fields defaulted/empty. _Be very careful with the use of this flag!_

**AutoCleanup (Default=false)**: This flag is not yet supported at the document level. See the AutoCleanup attribute on various processing nodes, which are supported.

**Verbose (Default=false)**: This flag indicates whether or not to output information processing nodes in the resulting XmlDocument. Setting Verbose="true" will enable easier debugging of WSI actions and allow you to trace through all execution steps, and SQL statements. Your client should ignore any informational nodes produced, when processing the output for automation.

**UseImplicitTransactions (Default=false)**: This flag controls whether or not nodes in the input document are handled in transaction mode or not implicitly. This flag does NOT affect explicit <Transaction>...</Transaction> blocks which are always honored. If UseImplicitTransactions="true", then if there are processing nodes in the input Xml document which are not nested inside a <Transaction> block, the WSI will create an implicit default transaction for EACH node it processes. This can allow you to ensure the node and all resulting data either commits or rolls back on any error (e.g. when adding a Product). If UseImplicitTransactions="false", then any non Transaction block nodes are just executed as is. They can partially succeed or fail, and you will have to examine the output result Xml document to determine what was performed.

**SetImportFlag**: If this is set to true, new rows that are added to the database as part of a WSI action have the 'IsImport' value set to true, so that they can be 'rolled back' later with the UndoLastImport node.

### Execution Sequence

The WSI processes elements sequentially, IN THE ORDER THEY APPEAR in your input Xml document!

### Transactions

WSI supports transactional processing (and rollback) for many operations (e.g. bulk adding products, categories, etc.). The input Xml doc header attribute must have TransactionsEnabled="true". Note that some nodes CANNOT be put inside a transaction as there is no way to roll them back (e.g. updating an order transaction state from AUTH to CAPTURED)...See the notes on each action element description on whether it can be inside a transaction or not.

You can have more than one transaction in a single input document also, and each transaction can optionally be given a name.
      