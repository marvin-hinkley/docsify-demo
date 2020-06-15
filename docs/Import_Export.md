
      ---
      title: Import/Export
      ---

      From Products Menu, click **Import/Export**.  
  
On this page (as well as [this one](default.aspx?pageid=xml_product_import)), products can be imported in bulk. This page requires those products to be in an Excel file, formatted like [this sample file](docs/ExcelImport-95.xls).  
  
**When an import file is processed, the software looks at each entry and compares it to existing products in the storefront. If the SKU of a product in the import file matches an existing product, that existing product is updated with the information from the new file. If there is no SKU match, then a new product is created with that information.** 

Importing Products
==================

To import a new product list, use the **Choose File** button to locate the import file, then click **Upload**.  
  
   ![](images/1419375341091.png)  
  
  
Once the file has been processed (this can take a while if it is a large import file), the screen below will be shown. It is a good idea to click the **View Import Log** link and make sure that there are no errors showing. If everything looks ok, click the **Click Here to Accept Import** button to complete the process. If there are problems showing in the log file, or you wish to cancel the import, click the **Click Here to Undo the Import** button.  
  
 ![](images/1415981686078.png)

Excel Product Import Fields
===========================

This section explains the usage of the fields in the Excel Import spreadsheet - for detailed descriptions of what those fields do, see [this page](default.aspx?pageid=manage_products).

Standard Products
-----------------

**Field Name**

**Description**

ProductName\*

This is the name of the product, as it will appear to your customers.

ProductTypeID\*

Here you specify the [Product Type](default.aspx?pageid=product_types) (Generic Product, Kit Product, etc).

Manufacturer\*

This is the [Manufacturer](default.aspx?pageid=manage_manufacturers) your new product will be mapped to. If no manufacturers are set up or used for your business, use the "Generic Mfg" that comes preloaded in the software.

Distributor

This is the [Distributor](default.aspx?pageid=manage_distributors) that your product will be assigned to (for drop shipping purposes).

Category1

This field (and the next 3) can be used to map the new product to a category. The format should be /category/subcat/subsubcat/etc (be sure to include the preceding /). For example, /Books/Science Fiction/Robert A. Heinlein. If a category listed in this field doesn't exist when the import runs, it will be created.

Department1

This field (and the next 3) can be used to map the new product to a [Department](default.aspx?pageid=manage_departments).

Summary

Provides an overview about the product.

Description

Provides a description about the product.

SEKeywords

Contains keywords used to create the meta tags on product pages.

SEDescription

Contains description used to create the meta tags on product pages.

SETitle

Contains title used to create the meta tags on product pages.

SKU

This is your SKU for the product. This can be any alphanumeric sequence you like.

Manufacturer PartNumber

This value will be sent in distributor emails if populated (optional).

XmlPackage

Provides the type of Xml Package (layout) set up on the product.

ColWidth

If multiple variants exist and are being displayed in one of the grid XML packages, determines how many columns to arrange them in.

SalesPromptID

Contains the integer that determines the Sales Prompt Name issued on the product.

Published

Determines whether or not the product appears on the front end of the site.

RequiresRegistration

Hides the product from [anonymous customers](default.aspx?pageid=anonymous_customers).

RelatedProducts

Insert Product IDs here. These product will be displayed in a special box at the bottom of the main product's page.

MiscText

Provides any statement the store owner desires. For internal use only.

TrackInventoryBySizeAndColor

Allows you to specify individual inventory level for every size/color combination set up on the product variant(s).  
(Using this method will not work with Kits tied to the variant)

IsAKit

Set this as a [kit product](default.aspx?pageid=kit_products).

ImageFilename Override

Enter the full image name including the file extension if using this method for images. This automatically overrides images mapped by the ProductID (or SKU). Example: product123.png

ExtensionData

Generates product's information as internal notes, special instructions, etc.

SEAltText

Alt text that will display in place of product images if the image cannot load for some reason.

VariantName

Name of this product variant (optional). This value will be appended to the parent product name if filled in.

IsDefaultVariant

Sets the variant as default.

SKUSuffix

This value will be appended to the parent product SKU on receipts and during checkout )optional).

ManufacturerPartNumber

This value will be sent in distributor emails if populated (optional).

Description

Provides a description about the variant.

SEKeywords

Contains keywords used to create the meta tags on variant pages.

SEDescription

Contains description used to create the meta tags on variant pages.

SETitle

Contains title used to create the meta tags on variant pages.

Price\*

The price that will be displayed to customers.

SalePrice

Specifies the sale price of the product.

MSRP

Manufacturer's Suggested Retail Price; For internal use only.

Cost

The quoted product price paid by the store owner to the manufacturer. For internal use only.

Weight

Variant weight, used for shipping calculations.

Dimensions

Size of the package the item ships in.

Inventory

Determines the listing of item on hand.

Display Order

Contains the order by which a certain variant will be shown at the StoreFront.

Colors

Contains the variant's list of colors.

ColorSKUModifiers

Contains the variant's list of SKUs assigned for each color.

Sizes

Contains the variant's list of sizes.

SizeSKUModifiers

Contains the variant's list of SKUs assigned for each size.

IsTaxable

Determines whether or not this variant is taxed under the class set for the parent product.

IsShipSeparately

If using realtime shipping, this instructs the carrier to calculate the cost of shipping this item in its own box.

IsDownload

Set yes if the product is downloadable.

DownloadLocation

This is the URL the customers will click once they purchased the dowloadable product.

Published

Determines whether or not the variant appears on the front end of the site. NOTE: The default variant requires publishing when setting up the variants in an import.

ImageFilename Override

Enter the full image name including the file extension if using this method for images. This automatically overrides images mapped by the ProductID (or SKU). Example: product123.png

Extension Data

Generates variant's information as internal notes, special instructions, etc.

SEAltText

Alt text that will display in place of variant images if the image cannot load for some reason.

StoreMappings

This is a comma-delimited list of the stores you wish to map this product to. Each store can be listed by ID, or by name. NOTE: If any of your stores have commas in their names, you must use IDs for this field.

GTIN

Global Trade Item Number for the product variant.

\* denotes a required field

Kit Products
------------

**Field Name**

**Description**

ProductName\*

This is the name of the kit product, as it will appear to your customers.

ProductTypeID\*

Here you specify the Product Type as [Kit Product](default.aspx?pageid=kit_products).

Manufacturer\*

This is the Manufacturer where your kit product will be mapped to. If no manufacturers are set up or used for your business, use the Generic Mfg that comes preloaded in the software.

Category

This field (and the next 3) can be used to map the kit product to a category. The format should be /category/subcat/subsubcat/etc (be sure to include the preceding/).

Department

This field (and the next3) can be used to map the new product to a department.

Summary

Provides an overview about the kit product.

Description

Provides a description about the kit product.

SKU

This your SKU for the KIT product.

ManufacturerPartNumber

This value will be sent in distributor emails if populated (optional).

XmlPackage

The XML Package type is product.kitproduct.xml.config.

ColWidth

If multiple kit products exist and are being displayed in one category, determines how many columns to arrange them in.

SalesPromptID

Contains the integer that determines the Sales Prompt Name issued on the kit product. To manage SalesPromptID, go to Misc menu, click on [Sales Prompts](http://manual.aspdotnetstorefront.com/p-391-sales-prompts.aspx).

Published

Determines whether or not the kit product appears on the front end of the site.

Requires Registration

Hides the product from [anonymous customers](default.aspx?pageid=anonymous_customers).

TrackInvetoryBySizeAndColor

Allows you to specify individual inventory level for every size/color combination set up on the kit product variant.

IsAKit\*

Set this as a kit product.

Is Default Variant

Sets the variant as default.

Price\*

The price that will be displayed to customers.

IsTaxable

Determines whether or not the kit item is taxed under the class set for the kit product.

IsShipSeparately

If using realtime shipping, this instructs the carrier to calculate the cost shipping this kit product in its own box.

IsDownload

Set yes if the kit product is downloadable.

Published

Determines whether or not the kit item product appears on the front end of the site.

KitGroupDef

These are set of fields that defines the Kit Group.

Name

This is the name of the kit group, as it may appear to your clients.

Description

Provides a description about the kit group.

DisplayOrder

Contains the order by which a certain kit group will be shown at the Storefront.

KitGroupTypeID\*\*

Determines the kit group type contained in the drop down menu when creating a kit group

IsRequired

Enables the customer to select at least one item from the kit group before adding the kit to their cart.

Name\*

This is the name of the kit item, as it may appear to your clients.

Description

Provides a description about the kit item.

Display Order

Contains the order by which a certain kit item will be shown at the Storefront.

Price Delta

The amount that this kit item changes the base kit price.

IsDefault

Sets the kit item as default display when the user views the kit group.

TextOptionMaxLength

Determines the maximum length of text option field.

TextOptionMaxWidth

Determines the maximum width of text option field.

TextOptionMaxHeight

Determines the maximum height of text option field.

\* denotes a required field

\*\* KitGroupTypeID Values:

1.  Single Select Dropdown List 
2.  Single Select Radio List
3.  Multi Select Checkbox 
4.  Textbox 
5.  Text Area 
6.  File Upload

  
**If you are requiring t​o import more than 10,000 rows of product data at once, you will need to add an AppConfig (Settings): ImportMaxRowsExcel with the value of your maximum row count.**
      