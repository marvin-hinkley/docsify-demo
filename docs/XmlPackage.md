
      ---
      title: XmlPackage
      ---

      ### Description:

This node allows you to run any XML package that exists on the site, with specified runtime parameters if necessary.

### Full Syntax:

<XmlPackage Name="string" RuntimeParams="pararm1=value1&param2=value2&param3=value3" OutputType="INLINE|CDATA"/>

### Notes:

*   If the OutputType is set to INLINE, the output results are nested inside the InnerXml area of this node in the WSI output Xml document. If CDATA, WSI will create a CDATA section inside the WSI output Xml document. This allows you to return almost any kind of data from the XmlPackage.
*   OutputType is default to INLINE if not provided.
*   The XmlPackage must already exist on the storefront site, in one of the supported XmlPackage directories ({root}/XmlPackages or the skin XmlPackages folder).

### Warnings:

This is an extremely powerful node. XML packages should only be executed after they have been thoroughly tested in a separate environment.

### Example(s):

**This example runs the skin.helloworld.xml.config, which responds with a simple greeting**  
<AspDotNetStorefrontImport>  
<XmlPackage Name=" skin.helloworld.xml.config" OutputType="CDATA"/>  
</AspDotNetStorefrontImport>  
  
Returns:  
  
<?xml version="1.0" encoding="utf-8"?>  
<AspDotNetStorefrontImportResult Version="" DateTime="3/4/2007 7:25:07 PM">  
<XmlPackage Name="skin.helloworld.xml.config"><!\[CDATA\[<b>Hello World</b>\]\]></XmlPackage>  
</AspDotNetStorefrontImportResult>
      