
      ---
      title: Xml Packages
      ---

      XmlPackage Overview & Operation
===============================

XmlPackages are a means by which developers can extend the functionality of the software without necessarily having to know asp.net and/or recompile the storefront. This allows a great deal of customization to the front-end of the software without having to purchase the source code. That said, a knowledge of XML, Xsl (Xslt), HTML, SQL, etc is required and customizations of this sort should only be attempted by experienced developers. There are many tutorials and good books on those technologies, so they are not discussed here, except where any unusual exceptions or requirements are imposed by the storefront. _XML documents are CasE SEnSITivE!!!_ Also, Xmldocuments must have various attributes and element values properly “XML Encoded”. There is an XSD schema in the /XmlPackages folder to help you create properly structured packages.   
  
AspDotNetStorefront support staff cannot assist with issues that arise from customization of XML Packages, so make sure you have a backup before making any changes!   
  

How an XML Package works
------------------------

Conceptually, an XmlPackage is pretty simple. The XmlPackage takes an input data set (or SQL statement), combines it with system and customer parameters, and then produces output in either XML or HTML format. XmlPackages are named with the .xml.config extension (e.g. MyXmlPackage1.xml.config). They are named this way to prevent someone from “browsing” your XmlPackage file.   
  
XmlPackages execute as follows:   
  
    1. Package is instantiated by Name (the filename, e.g. MyXmlPackage1.xml.config)  
    2. Package reads .xml.config file (we use XML structure itself to define the specification of the XmlPackage, and we   
        add .config as an extension to prevent anyone from viewing your XmlPackages stored on your web site with a   
        browser, for additional security protection).  
    3. Code adds additional run-time parameters to the XmlPackage  
    4. Code adds additional system defined parameters to the XmlPackage  
    5. DataSets are built from the SQL statements in the XmlPackage  
    6. DataSets are converted into XmlDocument   
        fragments and combined with the system data (also XmlDocument fragments) to form the XML Data Document.  
    7. XmlDocument is XSL “Transformed” into final XML or HTML   
  
There are 2 types of XmlPackages, with 2 different purposes:   
  
**Internal Packages**: These are used internally by AspDotNetStorefront to provide efficient access to nested “entity” (e.g. category, section, library, etc) and “object” (e.g. product, document) structures in the database. The storefront will NOT function if these XmlPackages are removed.   
  
When used internally as a helper object, the XmlPackage typically produces an in-memory XmlDocument object, as a result of input SQL statements, and various customer, system, and user-defined parameters. Examples of these internal packages can be found by looking at files such as EntityHelper/EntityMgr.xml.config.   
  
This manual does not describe in further detail how the XmlPackages are internally used by the storefront for managing entities. You can refer to the EntityHelper.cs, XmlPackage2.cs, and HierarchicalTableMgr.cs classes in the common project, and the ShowEntityPage.cs class in the storefront project. Various consumer pages of these objects include the SiteMap.cs classes, and pages like showproduct.aspx, showcategory.aspx, etc.   
  
**Display Rendering Packages**: These XmlPackages allow generation of dynamic HTML output for product, entity and other pages. Developers can modify or add to the display packages that ship 'out of the box' in the XmlPackages folder. This type of XmlPackage outputs HTML to be rendered within a store page, typically rendering within the skin in the contents area.  
  
Next, we discuss how users can add new XmlPackages to the storefront WITHOUT recompiling any code in the storefront. This is important, as it allows developers to add custom page formats for their clients. For example, a particular store client may want their category pages to be displayed in a certain manner, which is not one of the formats provided with the software. The developer can author an XmlPackage (in a simple text editor like Notepad, if required), copy that XmlPackage to the server, and tell the storefront to use that XmlPackage to render the specified category via the admin site by setting the 'Page Display' setting on the category.   
  
**Installing an XML Package**   
  
XmlPackages are installed by placing them in the /App\_Templates/Skin\_#/XmlPackages folder in the web site. XmlPackages are stored by skin because different skin layouts may require different versions of the package. Also, the /App\_Templates/Admin\_Default/XmlPackages contains the XmlPackages (typically Internal XmlPackages) that are needed by the Admin site to function properly. When your XmlPackage is ready for use, just copy (or FTP) the file into that directory. Then you can assign that XmlPackage to any product or entity in the storefront through the admin site by setting the 'Display Format XML Package' attribute.   
  
**Invoking XML Packages by Themselves**   
  
The 'engine.aspx' page allows you to invoke any XML package specified in the query string, and have its contents rendered in the page contents area. Note that not all XML packages can be executed in this manner, as many XML packages DEPEND on system, page, or user information (e.g. query string categoryid= string, etc). However, much like topic pages produce standalone page output, XmlPackages can be used in the engine.aspx page to produce standalone XmlPackage driven page output. This basically extends the topic concept to a programmatic level, allowing developers to add dynamic data driven content pages to the storefront without ever touching the source code.  
  
To invoke an XML package this way, use ether:   
  
    http://www.yoursite.com/engine.aspx?xmlpackage=nameofpackage   
or   
    http://www.yoursite.com/x-nameofpackage.aspx   
  
When executing XmlPackages in this way you may want to override the page title, keywords, description, etc. There are five elements that you can include in the package to set these values. They are included in the SearchEngine setting node and are named: SectionTitle, SETitle, SEKeywords, SEDescription, and SENoScript. Each of the elements can contain either an xpath statement that locates the element within the XML Data Document that contains the data or a XSLT stylesheet to transform multiple nodes in to one value to be placed in the output. The XPath statement must return only one node and the stylesheet should be designed to work with the full XML Data Document.   
  

**XML Package Structure**
-------------------------

XML Packages can contain:   
  
    1 - SQL Queries to be executed  
    2 - Web Queries  
    3 - Xsl transforms  
    4 - Search Engine Setting definitions  
    5 - Post Processing Queries  
    6 - Set Cookie instructions   
  
An XSD Schema (XmlPackages/xmlpackage.xsd) is provided to describe the structure of the package. You can use this schema to validate the structure of your package (this does not validate the logic or structure any of the XSLT stylesheets or SQL queries).   
  
**SQL Queries**   
  
The Query element is defined as: <query name=”Sections” rowElementName=”Section” runif=”paramname”>   
  
The name attribute is used for the name of the child of the root element in the XML Data Document for this query. The rowElementName is the element name for each row returned by the query. Elements for each field are created using the exact spelling of the field or field alias in the query. _Remember, all names are case sensitive_. So, to reference the Name field from a query that has the above definition you would use the following path: /root/Sections/Section/Name. The runif attribute can be used to run the query under only certain circumstances. The value should be either a querystring/form/cookie param or a setting. If the specified querystring/form/cookie param or a setting doesn't exist or is an empty the query will not be executed. This could be used for a page where the query should not be run until the page is submitted with a form field.   
  
Each query has a <sql> element that can contain any valid SQL statement. The SQL statements are executed in .NET using the SqlClient data provider and are executed as parameterized queries.   
  
**Query Parameters**   
  
There are two types of query parameters that can be defined: the queryparam element and querystringreplace element.   
  
**_Queryparam_**   
A queryparam element defines a parameter that is evaluated at SQL execution time and has the format @paramname. For each queryparam element there must be a @paramname variable in the SQL statement. (e.g. select \* From product where productid = @productid). The queryparam element has the following attributes (all of which are required):

\* paramname – the name of the param as it is in the SQL statement.

\* paramtype – defines where the parameter value is obtained, valid values are request, appconfig, and runtime

\- request param values are retrieved from the Web request object (i.e. a Querystring, Form, Cookie value)

\- appconfig params are retrieved from the store's cached AppConfig table (Settings)

\- runtime params are retrieved from an internal runtime parameters table

\* requestparamname – this is the name of the request, AppConfig, or runtime field that is used for the value to be substituted in the query. It must match exactly or the item will not be found or it may find a different parameter altogether.

\* sqlDataType – defines the .Net SqlDataType for this parameter. The allowed types can be viewed in the XmlPackages/xmlpackage.xsd file.  They are defined in the element definition <xsd:simpleTypename="SqlDataType">.

\* defvalue – the default value to use in case the value is not found in the specified request, AppConfig, or runtime collection

\* validationpattern – a regular expression that can be used to filter the data so that invalid ranges of values are not sent to the query.   
  
**_Querystringreplace_**   
The second type of query parameter is the querystringreplace parameter. It is used to make the SQL string dynamic in terms of table names, field names, WHERE clause fields, and ORDER BY clause fields. It is not intended to be used for filtering parameters in the WHERE clause (for security reasons). This element has the following attributes (all of which are required):

\* replaceTag – a user defined string embedded in the SQL statement that will be replaced at run time.

\* replacetype - defines where the string replacement value is obtained. Valid values are request, AppConfig, and runtime and behave the same as those defined above in the queryparam element.

\* replaceparamname - this is the name of the request, AppConfig, or runtime field that is used for the value to be substituted for the replaceTag string in the query. It must match exactly or the item will not be found or it may find a different parameter altogether.

\* defvalue - the default value to use in case the value is not found in the specified request, AppConfig, or runtime collection

\* validationpattern – a regular expression that can be used to filter the data so that invalid ranges of values are not sent to the query.   
  
Here is an example query element:   
  
  <query name="Entities" rowElementName="Entity">   
  <sql>   
     <!\[CDATA\[   
      select Name,Description from {EntityName} with (NOLOCK) where {EntityName}ID=@EntityID   
    \]\]>   
  </sql>   
  <querystringreplace replaceTag="{EntityName}"   
        replacetype="runtime"   
        replaceparamname="EntityName"   
        defvalue=""   
        validationpattern="(category)|(section)|(affiliate)|(manufacturer)|(distributor)|(library)" />   
  <queryparam paramname="@EntityID"   
        paramtype="runtime"   
        requestparamname="EntityID"   
        sqlDataType="int"   
        defvalue="0"   
        validationpattern="" />   
    </query>   
  
It would produce a document fragment like this:   
  
  <Entities>   
    <Entity>   
      <Name>Test Entity1</Name>   
      <Description>Test Description</Description>   
    </Entity>   
    <Entity>   
      <Name>Test Entity2</Name>   
      <Description>Test Description</Description>   
    </Entity>   
    …   
  </Entities>   
  
The query element can also contain an XSL transform element named querytransform. This element can contain an XSL transform that can be used to shape the output XML for this query differently than it comes from the database and before it is added to the final XML Data Document. It is optional but there can be no more than one transform for the query. The output of this transform must be a valid XML document fragment or the entire package will fail.   
  
  
**Web Queries**   
  
Web queries allow you to get data from an external data source via URL. The URL can return XML or text data (as specified by the RetType attribute). The name attribute is used for the node name in the XML Data Document under which all returned content is inserted. The url element contains the url of the web document (including any querystring parameters) to get the data from. The URL should be fully formed, e.g. http://www.somesite.com/xmldoc.aspx?param1=123. The querystring replace element is used much the same as in sql queries. It describes a tag in the URL string that can be replaced by some value from a request (querystring, form, cookie, or server) variable, a runtime variable or a setting. Finally, the query can contain an XSL transform. If a transform is specified, the returned data will be transformed and the results of the transform are added to the XML Data Document instead of the raw results from the URL. Transforms are only run when the RetType attribute is “xml”. Again you can refer to the schema for a more technical description of the webquery element. A RetType of text causes the return data to be put in a CDATA element unmodified from how it was received.   
  
Example:   
  
  <webquery name=”WebData1” RetType=”xml”>   
    <url>http://www.somesite.com/xmldatafeed.aspx?param1={param1}</url>   
    <querystringreplace replaceTag=”{param1}” replacetype=”request”   
      replaceparamname=”productid” defvalue=”0”  
      validationpattern=”^\\d{1,10}$”/>   
  </webquery>   
  
  
System Defined DataSets   
  
In addition to your defined SQL queries, the storefront automatically adds the following DataSets to the XML package before execution. This means that all of these datasets are available to your XSL Transform via intermediate XML Document.   
  
System Data Set:   
  
  <System>   
    <IsAdminSite>False</IsAdminSite>   
    <IsAdminSiteInt>0</IsAdminSiteInt>   
    <PublishedOnly>1</PublishedOnly>   
    <CustomerID>0</CustomerID>   
    <CustomerLevelID>0</CustomerLevelID>   
    <CustomerLevelName />   
    <CustomerFirstName />   
    <CustomerLastName />   
    <CustomerFullName />  
    <CustomerRoles />   
    <IsAdminUser>false</IsAdminUser>   
    <IsSuperUser>false</IsSuperUser>   
    <LocaleSetting>en-US</LocaleSetting>   
    <WebConfigLocaleSetting>en-US</WebConfigLocaleSetting>   
    <SqlServerLocaleSetting>en-US</SqlServerLocaleSetting>   
    <Date>11/30/2005</Date>   
    <Time>1:28 AM</Time>   
    <SkinID>1</SkinID>   
    <AffiliateID>0</AffiliateID>   
    <IPAddress>192.168.0.40</IPAddress>   
    <QueryString>SectionID=1&SEName=test-section</QueryString>   
    <UseStaticLinks>false</UseStaticLinks>   
    <PageName>showsection.aspx</PageName>   
    <FullPageName>/version60/showsection.aspx</FullPageName>   
    <XmlPackageName>aspdnsf.xml.config</XmlPackageName>   
    <StoreUrl>http://dotnetstorefront6/version60/</StoreUrl>   
  </System>   
  
Runtime DataSet (a bit redundant with the runtime params, but still necessary and helpful sometimes in your XSL transform):   
  
  <Runtime>   
    <AffiliateID>0</AffiliateID>  
    <CustomerID>0</CustomerID>  
    <EntityName>Section</EntityName>  
    <IsAdminUser>False</IsAdminUser>  
    <UseStaticLinks>False</UseStaticLinks>  
    <Date>11/30/2005</Date>  
    <CustomerLevelName />  
    <StoreUrl>http://dotnetstorefront6/version60/</StoreUrl>  
    <Time>1:28 AM</Time>  
    <EntityID>1</EntityID>  
    <SkinID>1</SkinID>  
    <IsAdminSite>False</IsAdminSite>  
    <QueryString>SectionID=1&amp;SEName=test-section</QueryString>  
    <CustomerLevelID>0</CustomerLevelID>  
    <CustomerFullName />  
    <CustomerFirstName />  
    <XmlPackageName>aspdnsf.xml.config</XmlPackageName>  
    <IsSuperUser>False</IsSuperUser>  
    <PublishedOnly>1</PublishedOnly>  
    <IsAdminSiteInt>0</IsAdminSiteInt>  
    <IPAddress>192.168.0.40</IPAddress>  
    <CustomerRoles />  
    <PageName>showsection.aspx</PageName>  
    <CustomerLastName />  
    <WebConfigLocaleSetting>en-US</WebConfigLocaleSetting>  
    <FullPageName>/version60/showsection.aspx</FullPageName>  
    <LocaleSetting>en-US</LocaleSetting>  
    <SqlServerLocaleSetting>en-US</SqlServerLocaleSetting>  
    <StoreUrl>http://dotnetstorefront6/version60/</StoreUrl>  
  </Runtime>   
  
QueryString data set (whatever was on page URL invocation):   
  
  <QueryString>   
    <SectionID>1</SectionID>  
    <SEName>test-section</SEName>  
  </QueryString>   
  
Form Data Set (whatever was on page FORM post):   
  
  <Form />   
  
Session State (helpful with customer data and/or user defined session info):   
  
  <Session>   
    <CustomerID>58640</CustomerID>  
    <CustomerGUID>559ca809-884b-4072-b612-ac235c9ac743</CustomerGUID>  
    <ViewState>System.Web.UI.Triplet</ViewState>  
  </Session>   
  
Server Variables Info (not used too often, but may be required in some situations):   
  
  <ServerVariables>   
    <HTTP\_HOST>localhost</HTTP\_HOST>  
    <HTTP\_USER\_AGENT>Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR1.1.4322)   
    </HTTP\_USER\_AGENT>  
    <AUTH\_TYPE>Forms</AUTH\_TYPE>  
    <AUTH\_USER>559ca809-884b-4072-b612-ac235c9ac743</AUTH\_USER>  
    <AUTH\_PASSWORD />  
    <HTTPS>off</HTTPS>  
    <LOCAL\_ADDR>127.0.0.1</LOCAL\_ADDR>  
    <PATH\_INFO>/aspdotnetstorefront/showsection.aspx</PATH\_INFO>  
    <PATH\_TRANSLATED>c:\\websites\\aspdotnetstorefront\\showsection.aspx</PATH\_TRANSLATED>  
    <SCRIPT\_NAME>/aspdotnetstorefront/showsection.aspx</SCRIPT\_NAME>  
    <SERVER\_NAME>localhost</SERVER\_NAME>  
    <SERVER\_PORT\_SECURE>0</SERVER\_PORT\_SECURE>  
  </ServerVariables>   
  
These data sets are ALL available to your Xsl transform code, along with ALL the params you have defined, AND the runtime params added by the system.   
  
  
**XSL Transform**   
  
The output Package is obtained by applying an XSL transform to the resulting XmlDoc. The XmlDoc contains the SQL data, web data, and system data. This is done using the transform in the <PackageTransform> element. An XmlPackage doesn’t require any query elements to run but the PackageTransform is required and must contain a valid XSLT stylehseet. As stated previously The XmlPackage uses .NET extension objects to implement high level logic not available in normal XSL. For this to work it is required that a new namespace be added to the XSL stylesheet. The xsl:stylesheet element must have the attribute xmlns:aspdnsf="urn:aspdnsf" here’s the full stylesheet element:

<xsl:stylesheet version="1.0" xmlns:XSL="http://www.w3.org/1999/XSL/Transform"xmlns:aspdnsf="urn:aspdnsf">

Although not required it is a good idea to use an output element as well and set the method attribute to HTML. Here’s a sample:

<xsl:output method="html" omit-xml-declaration="yes" />

After that all you need to do is add templates to transform the XML DataDocument into html.   
  
  
**Search Engine Settings**   
  
In some instances you may want to control the page title, keywords meta tag, description meta tag, and SectionTitle sections. These items can be set by adding the SearchEngineSetting node to the package and including 1 or all of the following child nodes: SectionTitle, SETitle, SEKeywords, and SEDescription. Each node can contain either an XPath statement, an XSLT stylesheet, or static text and you must specify which type it contains in the node’s actionType attribute (either “xpath”, “transform”, or “text”). The XPath statement or the stylesheet is executed against the XML Data Document. If the node contains an XPath statement, it must return a single node (a nodeset will cause a runtime error). This is for when you just want to pick the value of one element from the XML Data Document. When a stylesheet is specified, you can combine as much information from the XML Data Document as you need. Here is an example of specifying some of the SE settings:   
  
    <SearchEngineSettings>   
    <SETitle actionType="transform">  
      <xsl:stylesheet version="1.0" xmlns:XSL="http://www.w3.org/1999/XSL/Transform" xmlns:aspdnsf=   
      "urn:aspdnsf">  
      <xsl:output method="html" omit-xml-declaration="yes" />  
      <xsl:template match="/">  
      <xsl:value-of select="concat(/root/Sections/Section/SEName, ' - ',/root/Sections/Section/Description)" />  
      </xsl:template>  
      </xsl:stylesheet>  
    </SETitle>  
    <SEKeywords actionType="xpath">  
      /root/Sections/Section/SEKeywords  
    </SEKeywords>  
    <SEDescription actionType="text">  
      This is my static text to use for the search engine description meta tag  
    </SEDescription>  
  </SearchEngineSettings>   
  
When using a stylesheet you can use any of the extension functions described later in this article. Please refer to the schema (in the XmlPackages/xmlpackage.xsd file) for the full technical description of this node.   
  
  
**Post Processing**   
  
An XmlPackage can have post processing instructions. The post processing instructions include executing SQL queries (typically for insert or update), Web Queries, or setting cookie values. The actions take place after the XML DataDocument is created and before the transform is executed. So, after you have queried the database and/or retrieved data from the web you can execute commands to update your database, update your web data source, or set a user cookie value.   
  
  
**Queryafter**   
  
Queryafter elements are used to define SQL queries that are executed after the XML DataDocument is built. This elements operates much like the <query> element except that the <querystringreplace> and <queryparam> elements can draw their values from the XML DataDocument (using an xpath statment). Typically you would use this to update data in your database after you gathered the data for the package transform. The <queryafter> element also contains a runif element that can be used to prevent the query from running. The runif element tests for the existence of the value or element you specify and if it does not exist or if it exists and is empty then the query is not executed.   
  
Example:   
  
  <queryafter>   
    <sql>   
      <!\[CDATA\[   
      update customer set lastlogin = datetime where customerid = @custid   
      \]\]>   
    </sql>   
    <queryparam paramname="@ custid " paramtype="xpath" requestparamname="/root/System/CustomerID"   
    sqlDataType="int" defvalue="0"   
    ::validationpattern="" />   
  </queryafter>   
  
**AspDotNetStorefront Xsl Extensions**   
  
XmlPackages produce either:   
  
    1 - XML Output  
    2 - HTML Output   
  
When producing XML Output, it is your job to ensure that resulting XML is what you intended and compliant with XML standards. When producing HTML output, you can pretty much spit out whatever you want from the package, as long as you know how it will be used, and that it will be valid for that use. However, when producing HTML you may need to create blocks of HTML code which are non-trivial (e.g. an add to cart form with validation for a product). Since these types of would be extremely difficult to generate via XSLT, the HTML output from the XmlPackage can use custom XSL extension functions. These functions implement high-level logic that is not possible in XSLT alone (e.g. checking to see if an image file exists on the server before displaying it). The functions are used in your packages like this:   
  
    <xsl:value-of select=”aspdnsf:functionname(arguments)” disable-ouput-escaping=”yes”>   
  
The disable-output-escaping parameter is only required when the function’s output is not valid XML. Also, XSL is case sensitive, as are the function names. Also, note that all functions must be prefixed with "aspdnsf:".   
  
These functions are defined in the XSLTExtensionBase class, and are listed below.   
  

**Debugging XML Packages**
--------------------------

If you set the Xml.DumpTransform [Setting](default.aspx?pageid=settings) to Yes, the XmlPackage engine will write intermediate .xml files into the /image directory (they are put here because normally the site already has write permissions to that folder). The xml files will be appropriately-named based on the name of the XML package, and also intermediate stage files will be written out.   
  
The above procedure will cause debug information for every package used on the page to be display. If you only want to debug a specific package you can add the debug=”true” attribute to the package element. This will cause debug information to be displayed on the page regardless of the setting the Xml.DumpTransform AppConfig.   
  
To debug your XSL transforms, you can use your favorite XSL debug tool to take the intermediate .xml data file dumped out, and apply your transform directly to it. Also, Visual Studio 2005/2008 will debug transforms in-line. In order to do this you will need to put a break point in the XmlPackage2.TransformString method before the m\_Transform.Transform method is called. When the code reaches your breakpoint, choose the File|Open menu item and open the transform file in the images folder, the file will be named fullpackagename\_store.runtime.XSL (e.g. product.SimpleProduct.xml.config\_store.runtime.XSL). After you have the file opened you can set breakpoints in the transform and view local variables (i.e. param or variable tags in the transform) as you step through the transform. Again you must turn on debugging for the package using the package element’s debug attribute (debug=”true”) or by setting the AppConfig parameter Xml.DumpTransform to true.   
  
  

**AspDotNetStorefront XSLT Functions**
--------------------------------------

These are the built-in XSLT functions included with the software and used in our XML Packages. These functions can be used in new/edited XML Packages without having source code access, however adding new functions would require purchase of the source code.   
  
**AddtoCartForm**   
  **Description**: Returns the “add to cart form” with javascript validation required to be able to let the site user add   
  this product to the cart. This can include sizes, colors, inventory checking logic, etc.  
  **Sample**: <xsl:value-of select="aspdnsf:AddtoCartForm(ProductID, VariantID, ColorChangeProductImage)"   
  disableoutput-escaping="yes"/>   
  
    **Argument Name**: sProductId   
    **Data Type**: Integer   
    **Description**:   
  
    **Argument Name**: sVariantID   
    **Data Type**: Integer   
    **Description**:   
  
    **Argument Name**: sColorChangeProductImage   
    **Data Type**: Boolean   
    **Description**: If the product has color options will selecting a color from the drop down cause the product image   
    to change to the color selected.   
  
**AddtoCartForm**   
  **Description**: Returns the “add to cart form” with javascript validation required to be able to let the site user add   
  this product to the cart. This can include sizes, colors, inventory checking logic, etc.  
  **Sample**: <xsl:value-of select="aspdnsf:AddtoCartForm(ProductID, VariantID, ColorChangeProductImage, true)"   
  disableoutput-escaping="yes"/>   
  
    **Argument Name**: sProductId   
    **Data Type**: Integer   
    **Description**:   
  
    **Argument Name**: sVariantID   
    **Data Type**: Integer   
    **Description**:   
  
    **Argument Name**: sColorChangeProductImage   
    **Data Type**: Boolean   
    **Description**: If the product has color options will selecting a color from the drop down cause the product image   
    to change to the color selected.  
  
    **Argument Name**: sShowWishListButton  
    **Data Type**: Boolean   
    **Description**: If true, the product page will show the 'Add to Wish List' button regardless of the ShowWishButtons store Setting.  
  
**AddtoCartFormERP**   
  **Description**:   
  **Sample**: <xsl:value-of select="aspdnsf:AddtoCartForm(ProductID, VariantID, ColorChangeProductImage,   
  VariantStyleFlag)" disableoutput-escaping="yes"/>   
  
    **Argument Name**: sProductId   
    **Data Type**: Integer   
    **Description**:   
  
    **Argument Name**: sVariantID   
    **Data Type**: Integer   
    **Description**:   
  
    **Argument Name**: sColorChangeProductImage   
    **Data Type**: Boolean   
    **Description**: If the product has color options will selecting a color from the drop down cause the product image   
    to change to the color selected.   
  
    **Argument Name**: sVariantStyleFlag   
    **Data Type**:   
    **Description**:   
  
**AjaxShippingEstimator**   
  **Description**: Displays the AJAX Shipping Estimator tool on the product detail page.  
  **Sample**: <xsl:value-of select="aspdnsf:AjaxShippingEstimator(VariantID)" disable-output-escaping="yes"/>   
  
    **Argument Name**: VariantID   
    **Data Type**: Integer   
    **Description**: Variant to calculate the estimate on   
  
**AppConfig**   
    **Description**: Returns the value of the specified AppConfig.  
    **Sample**: <xsl:value-of select="aspdnsf:AppConfig(AdminDir)" disable-output-escaping="yes"/>   
  
    **Argument Name**: AppConfigName   
    **Data Type**: String   
    **Description**: Name of the AppConfig to check   
  
**AppConfigBool**   
  **Description**: Returns the value of the specified boolean Appconfig in lower case (i.e. “true’ or “false”).  
  **Sample**: <xsl:value-of select="aspdnsf:AppConfigBool(UseSSL)" disable-output-escaping="yes"/>   
  
    **Argument Name**: AppConfigName   
    **Data Type**: String   
    **Description**: Name of the AppConfig to check   
  
**CartSubTotal**   
  **Description**: Returns shoppingcart.cs.90 + the current customer's subtotal.  
  **Sample**: <xsl:value-of select=”aspdnsf:CartSubTotal()” disable-output-escaping=”yes”>   
  
**CategoryLink**   
  **Description**: Returns a page name for the specified Category page in the site, using static links if required (e.g.c-  
  17-boots.aspx). NOTE: This function is for backward compatibility with Parser functions only and should not be   
  used in XmlPackage transforms because it outputs invalid XML when using the IncludeATag.   
  **Sample**: <xsl:value-of select="aspdnsf:CategoryLink (CategoryID, SEName, IncludeATag, TagInnerText)"   
  disableoutput-escaping="yes"/>   
  
    **Argument Name**: CategoryID   
    **Data Type**: Integer   
    **Description**: ID of the desired category   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this category, if known. If blank, the store will figure it out, but   
    that takes an extra database query   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
    **Argument Name**: TagInnerText   
    **Data Type**: String   
    **Description**: The text that goes inside the <a> tag, only used when the IncludeATag is true (set to empty string   
    otherwise)   
  
**CleanPaymentGateway**   
  **Description**: Returns Payment Gateway cleaned (no spaces or weird chars, all uppercased)  
  **Sample**:   
  
    **Argument Name**: GW   
    **Data Type**: String   
    **Description**: Gateway name   
  
**CleanPaymentMethod**   
  **Description**: Returns Payment Method cleaned (no spaces weird chars, all uppercased)  
  **Sample**:   
  
    **Argument Name**: PM   
    **Data Type**: String   
    **Description**: Payment method name   
  
**CleanShippingMethod**   
  **Description**: Returns Shipping Method cleaned (no spaces weird chars, all uppercased)  
  **Sample**:   
  
    **Argument Name**: SM   
    **Data Type**: String   
    **Description**: Shipping method name   
  
**ConvertToBase64**   
  **Description**: Converts input into base 64 encoding  
  **Sample**:   
  
    **Argument Name**: Input   
    **Data Type**: String   
    **Description**: Value to be converted   
  
**CreateXmlFromDelimitedString**   
    **Description**:   
  **Sample**:   
  
    **Argument Name**: delimitedString   
    **Data Type**: string   
    **Description**:   
  
    **Argument Name**: delimiter   
    **Data Type**: string   
    **Description**:   
  
    **Argument Name**: rootname   
    **Data Type**: string   
    **Description**:   
  
    **Argument Name**: elementname   
    **Data Type**: string   
    **Description**:   
  
**CustomerID**   
  **Description**: Returns the currently logged in customer id, or 0 if anon customer with no customer record yet  
  **Sample**: <xsl:value-of select=”aspdnsf:CustomerID()” >   
  
**DateCompare**   
  **Description**: returns:   
  
    if Date1 < Date2 => -1   
    if Date1 = Date2 => 0   
    if Date1 > Date2 -> 1   
    (if Date1 or Date2 is empty string, they will be set to "now")   
  
  **Sample**:   
  
    **Argument Name**: Date1   
    **Data Type**: String   
    **Description**: First date   
  
    **Argument Name**: Date2   
    **Data Type**: String   
    **Description**: Second date   
  
**Decode**   
  **Description**: Decodes markup that might have been encoded during a conversion to XML  
  **Sample**: <xsl:value-of select="aspdnsf:Decode()" disable-output-escaping="yes"/>   
  
**Decrypt**   
  **Description**: Returns the decrypted value of the data that was encrypted using the ASPDNSF Encrypt method  
  **Sample**: <xsl:value-of select="aspdnsf:Decrypt(EncryptedData)" disable-output-escaping="yes"/>   
  
    **Argument Name**: EncryptedData   
    **Data Type**: String   
    **Description**: The data you want decrypted   
  
**DecryptCCNumber**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: CardNumberCrypt   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: OrderNumber   
    **Data Type**: String   
    **Description**:   
  
**DisplayAddressString**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: AddressID   
    **Data Type**:   
    **Description**:   
  
**DisplayOrderOptions**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: OrderOptions   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ViewInLocaleSetting   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: UseFullPathToImages   
    **Data Type**: String   
    **Description**:   
  
**DisplayProductStockHint**   
  **Description**: Display 'out of stock' or 'in stock' message  
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: Integer   
    **Description**: The product to check stock levels on   
  
    **Argument Name**: Pages   
    **Data Type**: String   
    **Description**: Entity or Product   
  
**DistributorLink**   
  **Description**: Creates a link to the Distributor page.  
  **Sample**:   
  
    **Argument Name**: DistributorID   
    **Data Type**: String   
    **Description**: ID of the Distributor   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The Search Engine name of the distributor   
  
    **Argument Name**: IncludeATag   
    **Data Type**: String   
    **Description**: Flag to create an achor tag   
  
    **Argument Name**: TagInnerText   
    **Data Type**: String   
    **Description**: The iStringnnertext of the anchor tag   
  
**DocumentAndLibraryLink**   
  **Description**: Returns link to that document page (with Library breadcrumb navigation), using static links if   
  required (e.g. p-1-test.aspx). NOTE: This function is for backward compatibility with Parser functions only and   
  should not be used in XmlPackage transforms because it outputs invalid XML when using the IncludeATag.   
  **Sample**: <xsl:value-of select="aspdnsf:DocumentandLibraryLink(DocumentID, SEName, LibraryID, IncludeATag,   
  TagInnerText)" disable-output-escaping="yes"/>   
  
    **Argument Name**: DocumentID   
    **Data Type**: Integer   
    **Description**: Document ID   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: Product SE name   
  
    **Argument Name**: LibraryID   
    **Data Type**: Integer   
    **Description**: LibraryID that the document is assigned to   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
    **Argument Name**: TagInnerText   
    **Data Type**: String   
    **Description**: The text that goes inside the <a> tag, only used when the IncludeATag is true (set to empty string   
    otherwise)   
  
**DocumentLink**   
  **Description**: Returns a link to the specified document page. NOTE: This function is for backward compatibility with   
  Parser functions only and should not be used in XmlPackage transforms because it outputs invalid XML when   
  using the IncludeATag.   
  **Sample**: <xsl:value-of select="aspdnsf:DocumentLink(DocumentID, SEName, IncludeATag, TagInnerText)"   
  disable-output-escaping="yes"/>   
  
    **Argument Name**: DocumentID   
    **Data Type**: Integer   
    **Description**: Document ID   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: Product SE name   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
    **Argument Name**: TagInnerText   
    **Data Type**: String   
    **Description**: The text that goes inside the <a> tag, only used when the IncludeATag is true (set to empty string   
    otherwise)   
  
**Ellipses**   
  **Description**: Returns shortened value of text with an ellipses (...) on the end. For example "This is one of our most   
  popular products" might be changed to "This is one of..."  
  **Sample**:   
  
    **Argument Name**: Content   
    **Data Type**: String   
    **Description**: Text to shorten   
  
  
    **Argument Name**: ReturnLength   
    **Data Type**: String   
    **Description**: How long the final return should be   
  
    **Argument Name**: BreakBetweenWords   
    **Data Type**: String   
    **Description**: (true/false) If this is set to true, the ellipses will be added at the end of a word before ReturnLength   
    if the ReturnLength would be in the middle of a word. For example the string "There is more information here"   
    would return "There is more..." even if the ReturnLength would have had it cut off at "There is more infor"   
  
**EmailProductToFriend**   
  **Description**: Returns an a hyperlink to a page to where you can email the product page  
  **Sample**: <xsl:value-of select="aspdnsf:EmailProductToFriend(ProductID, CategoryID)" disable-  
  outputescaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: Integer

  
    **Description**: The productID to email a link to   
  
    **Argument Name**: CategoryID   
    **Data Type**: Integer

  
    **Description**: Not used by default   
  
**EncryptString**   
  **Description**: Uses the Security.MungeString function to encrypt text  
  **Sample**:   
  
    **Argument Name**: String2Encrypt   
    **Data Type**: String   
    **Description**: Text to encrypt   
  
**EntityLink**   
  **Description**: Returns a link to the specified entity page. NOTE: This function is for backward compatibility with   
  Parser functions only and should not be used in XmlPackage transforms because it outputs invalid XML when using   
  the IncludeATag.   
  **Sample**: <xsl:value-of select="aspdnsf:EntityLink(EntityID, SEName, EntityName, IncludeATag)"disable-output-  
  escaping="yes"/>   
  
    **Argument Name**: EntityID   
    **Data Type**: Integer   
    **Description**: ID of the desired entity   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this entity, if known. If blank, the store will figure it out,   
    but that takes an extra database query   
  
    **Argument Name**: EntityName   
    **Data Type**: String   
    **Description**: The name of the entity (“product”, “category”, “section”, etc.)   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
**EntityPageFilterOptions**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: EntityName   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: EntityID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SectionFilterID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: CategoryFilterID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ManufacturerFilterID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ProductTypeFilterID   
    **Data Type**: String   
    **Description**:   
  
**EntityPageHeaderDescription**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: EntityName   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: EntityID   
    **Data Type**: String   
    **Description**:   
  
**EvalBool**   
  **Description**: If the string = YES, TRUE, or 1, the software returns true. Otherwise, it returns false.  
  **Sample**:   
  
    **Argument Name**: EvalString   
    **Data Type**: String   
    **Description**: String to evaluate   
  
**FileExists**   
  **Description**: Checks to see if the specified file exists and returns true/false  
  **Sample**:   
  
    **Argument Name**: FNOrUrl   
    **Data Type**: String   
    **Description**: Relative URL or physical file path to check   
  
**FormatCurrency**   
  **Description**: Returns the currency value formatted for the specified locale  
  **Sample**: <xsl:value-of select="aspdnsf:FormatCurrency(CurrencyValue, LocaleSetting)" disable-  
  outputescaping="yes"/>   
  
    **Argument Name**: CurrencyValue   
    **Data Type**: Decimal   
    **Description**: Amount to convert   
  
    **Argument Name**: LocaleSetting   
    **Data Type**: String   
    **Description**: User or server default locale setting   
  
**FormatCurrencyHelper**   
  **Description**: Internal helper function only.   
  
**FormatDate**   
  **Description**: Parses incoming date string DateString and reformats it to a new date string according to the   
  FormatString parameter  
  **Sample**:   
  
    **Argument Name**: StrDate   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SourceLocale   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: strFmt   
    **Data Type**: String   
    **Description**:   
  
**FormatDecimal**   
  **Description**: Returns a localized, rounded decimal of the length specified.  
  **Sample**:   
  
    **Argument Name**: DecimalValue   
    **Data Type**: String   
    **Description**: Original decimal value   
  
    **Argument Name**: intFixPlaces   
    **Data Type**: String   
    **Description**: Number of places to round the decimal to   
  
**GenreLink**   
  **Description**: Creates a link to the Genre page.  
  **Sample**:   
  
    **Argument Name**: GenreID   
    **Data Type**: Integer   
    **Description**: ID of the desired genre   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this genre, if known. If blank, the store will figure it out, but that   
    takes an extra database query   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
    **Argument Name**: TagInnerText   
    **Data Type**: String   
    **Description**: The text that goes inside the <a> tag, only used when the IncludeATag is true (set to empty string   
    otherwise)   
  
**GetCartPrice**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: intProductID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: intQuantity   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: decProductPrice   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: intTaxClassID   
    **Data Type**: String   
    **Description**:   
  
**GetCustomerLevelPrice**   
  **Description**: Returns a localized price for the specified variant, based on the customer level of the current   
  customer.  
  **Sample**:   
  
    **Argument Name**: VariantID   
    **Data Type**: String   
    **Description**: Variant to get the price of   
  
    **Argument Name**: Price   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Points   
    **Data Type**: String   
    **Description**: Not used by default   
  
**GetJSPopupRoutines**   
  **Description**: Returns the JS code that creates popups for various features on the site - order option tooltips, CCV   
  code image, etc.  
  **Sample**:   
  
**GetKitItemOptions**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ThisGroupID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: GroupIsRequired   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: GroupName   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: GroupDescription   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: KitGroupTypeID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: HidePriceUntilCart   
    **Data Type**: String   
    **Description**:   
  
**GetKitPrice**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Price   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SalePrice   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ExtendedPrice   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: HidePriceUntilCart   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Colors   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ShoppingCartRecID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: intTaxClassID   
    **Data Type**: String   
    **Description**:   
  
**GetLocaleShortDateString**   
  **Description**: Returns a localized version of the supplied date without the time  
  **Sample**:   
  
    **Argument Name**: DateTimeString   
    **Data Type**: String   
    **Description**: Full string to shorten   
  
**GetMLValue**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: MLContent   
    **Data Type**: XPathNodeIterator   
    **Description**:   
  
    **Argument Name**: Locale   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: XMLEncodeOutput   
    **Data Type**: String   
    **Description**:   
  
**GetNativeShortDateString**   
  **Description**: Returns a shortened (non-localized) version of the supplied date without the time  
  **Sample**:   
  
    **Argument Name**: DateTimeString   
    **Data Type**: String   
    **Description**: Full string to shorten   
  
**GetNewKitItemOptions**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Price   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SalePrice   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ExtendedPrice   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: HidePriceUntilCart   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Colors   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ShoppingCartRecID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: intTaxClassID   
    **Data Type**: String   
    **Description**:   
  
**GetNewsBoxExpanded**   
  **Description**: Returns a list of news items in an option frame  
  **Sample**: <xsl:value-of select="aspdnsf:GetNewsBoxExpanded(ShowCopy, ShowNum, IncludeFrame, Teaser)"disable-output-escaping="yes"/>   
  
    **Argument Name**: ShowCopy   
    **Data Type**: Boolean   
    **Description**: Shows the entire content of the article   
  
    **Argument Name**: ShowNum   
    **Data Type**: Integer   
    **Description**: The number of news items to show   
  
    **Argument Name**: IncludeFrame   
    **Data Type**: Boolean   
    **Description**: Create a frame around the list of specials, 1 = yes, 0 = no   
  
    **Argument Name**: Optional string rendered at the top of the list (inside the frame if it exists)   
    **Data Type**: String   
    **Description**: Teaser   
  
**GetOrderReceiptCCNumber**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: Last4   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: CardType   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: CardExpirationMonth   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: CardExpirationYear   
    **Data Type**: String   
    **Description**:   
  
**GetPackItmQtyScroller**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: PackID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: PresetProducts   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: NumItemsInPack   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SourceEntityID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SourceEntityName   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: CartRecID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ShoppingCartRecID   
    **Data Type**: String   
    **Description**:   
  
**GetPackPrice**   
  **Description**: Deprecated. Please use GetVariantPrice instead.   
  **Description**:   
  **Sample**:   
  
    **Argument Name**:   
    **Data Type**:   
    **Description**:   
  
**GetPackTypePrompt**   
  **Description**: Returns the name of the specified pack plus the value of the 'dyop.aspx.12' string (if the pack name   
  does not already end in that text).  
  **Sample**:   
  
    **Argument Name**: PackName   
    **Data Type**: String   
    **Description**: Name of the desired pack   
  
**GetPollBox**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: PollID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Large   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Category   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Section   
    **Data Type**: String   
    **Description**:   
  
**GetProductDiscountID**   
  **Description**: Returns the quantity discount table ID the specified product uses (if any)  
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Product to check for a quantity discount table on   
  
**GetRatingStarsImage**   
  **Description**: Creates an image displaying 0-5 stars (and fractions of them) based on the rating value supplied.  
  **Sample**:   
  
    **Argument Name**: Rating   
    **Data Type**: String   
    **Description**: Rating value to create an image for. 0.00 - 5.0   
  
**GetReceiptCss**   
  **Description**: Returns the content of CSS file based on skin ID  
  **Sample**:   
  
    **Argument Name**: SkinID   
    **Data Type**: Integer   
    **Description**: SkinID to lookup the CSS for   
  
**GetRootEntityContextOfPage**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: EntityName   
    **Data Type**: String   
    **Description**:   
  
**GetSpecialsBoxExpanded**   
  **Description**: Returns a formatted list of randomly selected items marked as being on special in the specified   
  category  
  **Sample**: <xsl:value-of select="aspdnsf:GetSpecialsBoxExpandedRandom(CategoryID, ShowPics, IncludeFrame,   
  Teaser)" disable-output-escaping="yes"/>   
  
    **Argument Name**: CategoryID   
    **Data Type**: Integer   
    **Description**: Category containing the products to display   
  
    **Argument Name**: ShowPics   
    **Data Type**: Boolean   
    **Description**: 1 = Show product pictures, 0 = don’t show pictures   
  
    **Argument Name**: IncludeFrame   
    **Data Type**: Boolean   
    **Description**: Create a frame around the list of specials, 1 = yes, 0 = no   
  
    **Argument Name**: Teaser   
    **Data Type**: String   
    **Description**: Optional string rendered at the top of the list (inside the frame if it exists)   
  
**GetSpecialsBoxExpandedRandom**   
  **Description**: Returns a formatted list of randomly selected items marked as being on special in the specified   
  category  
  **Sample**: <xsl:value-of select="aspdnsf:GetSpecialsBoxExpandedRandom(CategoryID, ShowPics, IncludeFrame,   
  Teaser)" disable-output-escaping="yes"/>   
  
    **Argument Name**: CategoryID   
    **Data Type**: Integer   
    **Description**: Category containing the products to display   
  
    **Argument Name**: ShowPics   
    **Data Type**: Boolean   
    **Description**: 1 = Show product pictures, 0 = don’t show pictures   
  
    **Argument Name**: IncludeFrame   
    **Data Type**: Boolean   
    **Description**: Create a frame around the list of specials, 1 = yes, 0 = no   
  
    **Argument Name**: Teaser   
    **Data Type**: String   
    **Description**: Optional string rendered at the top of the list (inside the frame if it exists)   
  
**GetSplitString**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: StringToSplit   
    **Data Type**:   
    **Description**:   
  
    **Argument Name**: SplitChar   
    **Data Type**:   
    **Description**:   
  
    **Argument Name**: intReturnIndex   
    **Data Type**:   
    **Description**:   
  
**GetStoreHTTPLocation**   
  **Description**: Returns the full URL of the store.  
  **Sample**:   
  
    **Argument Name**: TryToUseSSL   
    **Data Type**: String   
    **Description**: If true, the software will use https instead of http.   
  
**GetString**   
  **Description**: Deprecated, use StringResource instead.   
  
**GetUpsellVariantPrice**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: VariantID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: HidePriceUntilCart   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Price   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SalePrice   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ExtPrice   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Points   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SalesPromptName   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ShowPriceLabel   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: TaxClassID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: decUpSelldiscountPct   
    **Data Type**: String   
    **Description**:   
  
**GetVariantPrice**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: VariantID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: HidePriceUntilCart   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Price   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SalePrice   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ExtPrice   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Points   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SalesPromptName   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ShowPriceLabel   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: TaxClassID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ChosenAttributesPriceDelta   
    **Data Type**: String   
    **Description**:   
  
**GiftCardKey**   
  **Description**: Returns a number in the format #####-#####-#####  
  **Sample**:   
  
**HasZoomify**   
  **Description**: Returns false if the specified image/entity does not have Zoomify images, and true if it does  
  **Sample**:   
  
    **Argument Name**: ID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: EntityOrObjectName   
    **Data Type**: String   
    **Description**:   
  
**HelpBox**   
  **Description**: Displays a table with a header image and the contents of the 'helpbox' topic.  
  **Sample**:   
  
**HtmlDecode**   
  **Description**: Strips HTML tags out of the supplied string  
  **Sample**:   
  
    **Argument Name**: HtmlContent   
    **Data Type**: String   
    **Description**: String to decode   
  
**HtmlEncode**   
  **Description**: HTML-encodes the supplied string  
  **Sample**:   
  
    **Argument Name**: HtmlContent   
    **Data Type**: String   
    **Description**: String to encode   
  
**ImageGallery**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**:   
    **Data Type**:   
    **Description**:   
  
**ImageURL**   
  **Description**: Returns the path (relative or full URL) to the specified image  
  **Sample**: <xsl:value-of select="aspdnsf:ImageUrl(ID, EntityOrObjectName, DesiredSize, FullUrl)" disable-  
  outputescaping="yes"/>   
  
    **Argument Name**: ID   
    **Data Type**: Integer   
    **Description**: Product, Category, Section, or Manufacturer ID   
  
    **Argument Name**: EntityOrObjectName   
    **Data Type**: String   
    **Description**: “Product”, “Category”, “Section”, or “Manufacturer”   
  
    **Argument Name**: DesiredSize   
    **Data Type**: String   
    **Description**: icon, medium, large   
  
    **Argument Name**: FullURL   
    **Data Type**: Boolean   
    **Description**: Determine whether the path is a relative path (e.g. images/product/icon/imgname.jpg) or a full URL   
    (e.g. http://www.mydomain.com/images/product/medium/myimage.jpg)   
  
**InStr**   
  **Description**: Reports the index of the first occurrence of strFind within strSource  
  **Sample**:   
  
    **Argument Name**: strSource   
    **Data Type**: String   
    **Description**: Complete string   
  
    **Argument Name**: strFind   
    **Data Type**: String   
    **Description**: String to find   
  
**IsEmailGiftCard**   
  **Description**: Returns true if the specified product is an email type gift card  
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: Integer   
    **Description**: Product to check gift card type of   
  
**IsStringEmpty**   
  **Description**: Returns true if the specified string is empty, false if it is not  
  **Sample**:   
  
    **Argument Name**: StringValue   
    **Data Type**: String   
    **Description**: String to check   
  
**LibraryLink**   
  **Description**: Returns a page name for the specified Library page in the site, using static links if required  
  **Sample**: <xsl:value-of select="aspdnsf:LibraryLink(LibraryID, SEName, IncludeATag, TagInnerText)" disableoutput-  
  escaping="yes"/>   
  
    **Argument Name**: LibraryID   
    **Data Type**: Integer   
    **Description**: ID of the desired category   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this library, if known. If blank, the store will figure it out, but that   
    takes an extra database query   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
    **Argument Name**: TagInnerText   
    **Data Type**: String   
    **Description**: The text that goes inside the <a> tag, only used when the IncludeATag is true (set to empty string   
    otherwise)   
  
**LocateImageUrl**   
  **Description**: When given a relative path, returns the full URL to the specified image (localized if possible)  
  **Sample**:   
  
    **Argument Name**: ImgUrl   
    **Data Type**: String   
    **Description**: Relative path to the desired image   
  
    **Argument Name**: Locale   
    **Data Type**: String   
    **Description**: given an input image string like /skins/skin\_1/images/shoppingcart.gif, the software will try to resolve   
    it to the proper locale by:  
  
      /skins/skin\_1/images/shoppingcart.LocaleSetting.gif first  
      /skins/skin\_1/images/shoppingcart.WebConfigLocale.gif second  
      /skins/skin\_1/images/shoppingcart.gif last   
  
**LoginOutPrompt**   
  **Description**: Returns a login link or a logout link depending the user's current login state  
  **Sample**: <xsl:value-of select="aspdnsf:LoginOutPrompt()" disable-output-escaping="yes"/>   
  
**LookupEntityImage**   
  **Description**: Returns an <img> tag specifically for the specified entity.  
  **Sample**: <xsl:value-of select="aspdnsf:LookupEntityImage(ID, EntityName, DesiredSize, IncludeATag)"   
  disableoutput-escaping="yes"/>   
  
    **Argument Name**: ID   
    **Data Type**: Integer   
    **Description**: Category, Section, or Manufacturer ID   
  
    **Argument Name**: EntityName   
    **Data Type**: String   
    **Description**: “Category,” “Section”, or “Manufacturer”   
  
    **Argument Name**: DesiredSize   
    **Data Type**: String   
    **Description**: icon, medium, large   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag around the <img> tag with the href attribute set to the page url   
  
**LookupImage**   
  **Description**: Returns the fully qualified <img src=”…”….> tag for the desired image. NoPicture or NoPictureIcon   
  may be returned also in some cases. This method will not produce a link to the large image when a medium image is  
  requested. The SKU and ImageFileNameOverride arguments are optional and will cause the ID to be used as the   
  filename.  
  **Sample**: <xsl:value-of select="aspdnsf:LookupImage(ID, EntityOrObjectname, DesiredSize, DesiredSize,   
  IncludeATag)" disable-output-escaping="yes"/>   
  
    **Argument Name**: ID   
    **Data Type**: Integer   
    **Description**: The ID of the object for which you want the image   
  
    **Argument Name**: EntityOrObjectName   
    **Data Type**: String <  
    **Description**: The name of the object (“product”, “category”, “section”, etc.) for which you want the image   
  
    **Argument Name**: ImageFileNameOverride   
    **Data Type**: String   
    **Description**: The desired object’s ImageFileNameOverride value (optional)   
  
    **Argument Name**: SKU   
    **Data Type**: String   
    **Description**: The desired object’s SKU (optional, if using UseSKUForProductImageName)   
  
    **Argument Name**: DesiredSize   
    **Data Type**: String   
    **Description**: icon, medium, large, swatch   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag around the <img> tag with the href attribute set to the page url   
  
**LookupProductImage**   
  **Description**: Returns an <img> tag specifically for a product. The ImageFileNameOverride or SKU parameter will   
  allow this method to perform much faster than the standard LookupImage function if you use   
  ImageFileNameOverride or UseSKUForProductImageName on your product's images. Either parameter   
  can be an empty string if not used.  
  **Sample**: <xsl:value-of select="aspdnsf:LookupProductImage(ProductID, ImageFileNameOverride, SKU,   
  DesiredSize, IncludeATag)" disable-output-escaping="yes"/>   
  
    **Argument Name**: ID   
    **Data Type**: Integer   
    **Description**: The ID of the product for which you want the image   
  
    **Argument Name**: ImageFileNameOverride   
    **Data Type**: String   
    **Description**: The desired products’s ImageFileNameOverride value (optional)   
  
    **Argument Name**: SKU   
    **Data Type**: String   
    **Description**: The desired product’s SKU (optional, if using UseSKUForProductImageName)   
  
    **Argument Name**: DesiredSize   
    **Data Type**: String   
    **Description**: icon, medium, large, swatch   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag around the <img> tag with the href attribute set to the page url   
  
**LookupVariantImage**   
  **Description**: Returns an <img> tag specifically for a variant. The ImageFileNameOverride or SKU parameter will   
  allow this method to perform much faster than the standard LookupImage function if you use   
  ImageFileNameOverride or UseSKUForProductImageName on your product's images. Either parameter   
  can be an empty string if not used.  
  **Sample**: <xsl:value-of select="aspdnsf:LookupVariantImage(ProductID, VariantID, ImageFileNameOverride, SKU,   
  DesiredSize, IncludeATag)" disable-output-escaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: Integer   
    **Description**: The ID of the product for which you want the image   
  
    **Argument Name**: VariantID   
    **Data Type**: Integer   
    **Description**: The ID of the variant for which you want the image   
  
    **Argument Name**: ImageFileNameOverride   
    **Data Type**: String   
    **Description**: The desired products’s ImageFileNameOverride value (optional)   
  
    **Argument Name**: SKU   
    **Data Type**: String   
    **Description**: The desired product’s SKU (optional, if using UseSKUForProductImageName)   
  
    **Argument Name**: DesiredSize   
    **Data Type**: String   
    **Description**: icon, medium, large , swatch   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag around the <img> tag with the href attribute set to the page url   
  
**LookupZoomify**   
  **Description**: Displays the Zoomify image for the specified entity or product  
  **Sample**:   
  
    **Argument Name**: ID   
    **Data Type**: String   
    **Description**: The ID of the product or entity to find the image for   
  
    **Argument Name**: EntityOrObjectName   
    **Data Type**: String   
    **Description**: The name of the object (“product”, “category”, “section”, etc.) for which you want the image   
  
    **Argument Name**: DesiredSize   
    **Data Type**: String   
    **Description**: icon, medium, large   
  
**ManufacturerLink**   
  **Description**: Returns a page name for the specified Manufacturer page in the site, using static links if required   
  (e.g.m-17-hats.aspx). NOTE: This function is for backward compatibility with Parser functions only and should not   
  be used in XmlPackage transforms because it outputs invalid XML when using the IncludeATag.   
  **Sample**: <xsl:value-of select=”aspdnsf:ManufacturerLink(ManufacturerID, SEName, TagInnerText)” disableoutput-  
  escaping=”yes”>   
  
    **Argument Name**: ManufacturerID   
    **Data Type**: Integer   
    **Description**: ID of the desired manufacturer   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this manufacturer, if known. If blank, the store will figure it out, but   
    that takes an extra database query   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
    **Argument Name**: TagInnerText   
    **Data Type**: String   
    **Description**: The text that goes inside the <a> tag, only used when the IncludeATag is true (set to empty string   
    otherwise)   
  
**MicroPayBalance**   
  **Description**: Returns the current customer's MicroPay balance, localized if multiple currencies are set up.  
  **Sample**:   
  
**MiniCartOrderOption**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: intOrderOptionID   
    **Data Type**: String   
    **Description**:   
  
**MiniCartProductImage**   
  **Description**: Returns the icon image for a product for display within the minicart.  
  **Sample**:   
  
    **Argument Name**: intProductID   
    **Data Type**: String   
    **Description**: Product for which you want the icon image   
  
    **Argument Name**: ImageFileNameOverride   
    **Data Type**: String   
    **Description**: ImageFileNameOverride value for the product (if the product uses ImageFileNameOverride)   
  
    **Argument Name**: SKU   
    **Data Type**: String   
    **Description**: Product SKU (if using UseSKUForProductImageName )   
  
**ObjectLink**   
  **Description**: Returns link to that Object page in the site, using static links if required (e.g. p--17-test.aspx). NOTE:   
  This function is for backward compatibility with Parser functions only and should not be used in XmlPackage   
  transforms because it outputs invalid XML when using the IncludeATag.   
  **Sample**: <xsl:value-of select="aspdnsf:ObjectLink(ObjectID, SEName, EntityName, IncludeATag)" disable-output-  
  escaping="yes"/>   
  
    **Argument Name**: ObjectID   
    **Data Type**: Integer   
    **Description**: ID of the desired object   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this object, if known. If blank, the store will figure it out, but that   
    takes an extra database query   
  
    **Argument Name**: EntityName   
    **Data Type**: String   
    **Description**: The name of the object (“product”, “category”, “section”, etc.)   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
**OnLiveServer**   
  **Description**: Returns true if the LiveServer AppConfig has a value in it, false if not.  
  **Sample**:   
  
    **Argument Name**: NotUsed   
    **Data Type**: String   
    **Description**: Pass an empty string   
  
**OrderOptionsAsXML**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: strOrderOptions   
    **Data Type**: String   
    **Description**:   
  
**OrderShippingCalculation**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: PaymentMethod   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ShippingMethod   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ShippingTotal   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ShippingCalculationID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ShipAddresses   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: IsAllDownloadComponents   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: IsAllFreeShippingComponents   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: IsAllSystemComponents   
    **Data Type**: String   
    **Description**:   
  
**Owns**   
  **Description**: Returns true if the Customer has previously purchased this product.  
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Product to check for previous purchases of   
  
**PagingControl**   
  **Description**: Displays the paging controls on product/entity pages  
  **Sample**:   
  
    **Argument Name**: BaseURL   
    **Data Type**: String   
    **Description**: URL for the product/entity main page (page 1, without ?pagenum params)   
  
    **Argument Name**: PageNum   
    **Data Type**: String   
    **Description**: Current page number   
  
    **Argument Name**: NumPages   
    **Data Type**: String   
    **Description**: Max number of pages for this product/entity   
  
**ProductAndCategoryLink**   
  **Description**: Returns link to that product page (with category breadcrumb navigation), using static links if required   
  (e.g. p-17-boots.aspx). NOTE: This function is for backward compatibility with Parser functions only and should not   
  be used in XmlPackage transforms because it outputs invalid XML when using the IncludeATag.   
  **Sample**: <xsl:value-of select="aspdnsf:ProductandCategoryLink(ProductID, SEName, CategoryID, IncludeATag)"   
  disable-output-escaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: Integer   
    **Description**: ID of the desired product   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this product, if known. If blank, the store will figure it out, but that   
  takes an extra database query   
  
    **Argument Name**: CategoryID   
    **Data Type**: String   
    **Description**: ID of the category to display breadcrumbs for   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
**ProductAndEntityLink**   
  **Description**: Returns link to that product page (with entity breadcrumb navigation), using static links if required   
  (e.g. p-17-boots.aspx). NOTE: This function is for backward compatibility with Parser functions only and should not   
  be used in XmlPackage transforms because it outputs invalid XML when using the IncludeATag.   
  **Sample**: <xsl:value-of select="aspdnsf:ProductAndEntityLink(ProductID, SEName, EntityID, EntityName,   
  IncludeATag)" disable-output-escaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: Integer   
    **Description**: ID of the desired product   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this product, if known. If blank, the store will figure it out, but that   
    takes an extra database query   
  
    **Argument Name**: EntityID   
    **Data Type**: String   
    **Description**: ID of the category to display breadcrumbs for   
  
    **Argument Name**: EntityName   
    **Data Type**: String   
    **Description**: "category", "section", "manufacturer", etc   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
**ProductAndManufacturerLink**   
  **Description**: Returns link to that product page (with manufacturer breadcrumb navigation), using static links if   
  required (e.g. p-17-boots.aspx). NOTE: This function is for backward compatibility with Parser functions only and   
  should not be used in XmlPackage transforms because it outputs invalid XML when using the IncludeATag.   
  **Sample**: <xsl:value-of select="aspdnsf:ProductandManufacturerLink(ProductID, SEName, ManufacturerID,   
  IncludeATag)" disable-output-escaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: Integer   
    **Description**: ID of the desired product   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this product, if known. If blank, the store will figure it out, but that   
    takes an extra database query   
  
    **Argument Name**: ManufacturerID   
    **Data Type**: String   
    **Description**: ID of the manufacturer to display breadcrumbs for   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
**ProductAndSectionLink**   
  **Description**: Returns link to that product page (with section breadcrumb navigation), using static links if   
  required (e.g. p-17-boots.aspx). NOTE: This function is for backward compatibility with Parser functions only and   
  should not be used in XmlPackage transforms because it outputs invalid XML when using the IncludeATag.   
  **Sample**: <xsl:value-of select="aspdnsf:ProductandSectionLink(ProductID, SEName, SectionID,   
  IncludeATag)" disable-output-escaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: Integer   
    **Description**: ID of the desired product   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this product, if known. If blank, the store will figure it out, but that   
    takes an extra database query   
  
    **Argument Name**: SectionID   
    **Data Type**: String   
    **Description**: ID of the section to display breadcrumbs for   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
**ProductDescriptionFile**   
  **Description**: Returns the contents the product description file  
  **Sample**: <xsl:value-of select="aspdnsf:ProductDescriptionFile(ProductID, IncludeBRBefore)" disable-  
  outputescaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Product to find the description file for   
  
    **Argument Name**: IncludeBRBefore   
    **Data Type**: Boolean   
    **Description**: Return a <br> tag before the contents of the file if true   
  
**ProductEntityList**   
  **Description**: Returns a list of all the entities of the specified type that the specified product is mapped to, with a link  
  to the landing page for each entity.  
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Specified product   
  
    **Argument Name**: EntityName   
    **Data Type**: String   
    **Description**: "category", "section", "manufacturer", etc   
  
**ProductImageUrl**   
  **Description**: Returns the path (relative or full URL) to the specified product image.  
  **Sample**: <xsl:value-of select="aspdnsf:ProductImageUrl(ProductID, ImageFileNameOverride, SKU, DesiredSize,   
  FullUrl)" disable-output-escaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Specified product   
  
    **Argument Name**: ImageFileNameOverride   
    **Data Type**: String   
    **Description**: The desired product’s ImageFileNameOverride value (optional)   
  
    **Argument Name**: SKU   
    **Data Type**: String   
    **Description**: The desired product’s SKU (optional, if using UseSKUForProductImageName)   
  
    **Argument Name**: DesiredSize   
    **Data Type**: String   
    **Description**: icon, medium, large   
  
    **Argument Name**: FullUrl   
    **Data Type**: String   
    **Description**: Determine whether the path is a relative path (e.g. images/product/icon/imgname.jpg) or a full URL   
    (e.g. http://www.mydomain.com/images/product/medium/myimage.jpg)   
  
**ProductLink**   
  **Description**: Returns a link to that product page, using static links if required (e.g. p-17-boots.aspx). NOTE: This   
  function is for backward compatibility with Parser functions only and should not be used in XmlPackage transforms   
  because it outputs invalid XML when using the IncludeATag.   
  **Sample**: <xsl:value-of select="aspdnsf:ProductLink(ProductID, SEName, IncludeATag)" disable-output-  
  escaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: Integer   
    **Description**: ID of the desired product   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this product, if known. If blank, the store will figure it out, but that   
  takes an extra database query   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
**ProductNavLinks**   
  **Description**: Returns the next-previous product navigation for products within the specified category or section  
  **Sample**: <xsl:value-of select="aspdnsf:ProductNavLinks(ProductID, SectionID)" disable-output-escaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Specified product   
  
    **Argument Name**: SectionID   
    **Data Type**: String   
    **Description**: Desired section (specify this OR category)   
  
    **Argument Name**: CategoryID   
    **Data Type**: String   
    **Description**: Desired category (specify this OR section)   
  
**ProductProperName**   
  **Description**: Returns the full localized name of a product (parent product name + variant name)  
  **Sample**: <xsl:value-of select="aspdnsf:ProductProperName(ProductID, VariantID)" disable-output-  
  escaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Specified product   
  
    **Argument Name**: VariantID   
    **Data Type**: String   
    **Description**: Specified variant   
  
**ProductRatings**   
  **Description**: Returns the Product Rating display  
  **Sample**: <xsl:value-of select="aspdnsf:ProductRatings(ProductID, CategoryID, SectionID, ManufacturerID,   
  IncludeBRBefore)" disable-output-escaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Product to display ratings for   
  
    **Argument Name**: CategoryID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SectionID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ManufacturerID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: IncludeBRBefore   
    **Data Type**: String   
    **Description**: Return a <br> tag and a dividing line between the product description section and the ratings if true   
  
**ProductSpecs**   
  **Description**: Returns the contents the product spec file  
  **Sample**: <xsl:value-of select="aspdnsf:ProductSpecs(ProductID, IncludeBRBefore, ShowSpecsInline, SpecUrl,   
  IFrameHeight)" disable-outputescaping="yes"/>   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Product to find the spec file for   
  
    **Argument Name**: IncludeBRBefore   
    **Data Type**: String   
    **Description**: Return a <br> tag before the contents of the file if true   
  
    **Argument Name**: ShowSpecsInline   
    **Data Type**: String   
    **Description**: If true, specs will be displayed normally on the page immediately below the product description   
  
    **Argument Name**: SpecUrl   
    **Data Type**: String   
    **Description**: If the specs are hosted off-site, provide the URL here and they will be displayed in an iFrame   
  
    **Argument Name**: IFrameHeight   
    **Data Type**: String   
    **Description**: Height of the iFrame if off-site specs are being used   
  
**ProductSpecsLink**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ShowSpecsInline   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SpecTitle   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SKU   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SpecUrl   
    **Data Type**: String   
    **Description**:   
  
**ReadFile**   
  **Description**: Outputs the contents of the specified file (for example, a JS file)  
  **Sample**:   
  
    **Argument Name**: FName   
    **Data Type**: String   
    **Description**: File to read/display. This can be just the filename, the software will scan the whole virtual folder the   
    site resides in first, then attempt to do a drive search to find the file.   
  
**RelatedProducts**   
  **Description**: Runs the relatedproducts.xml.config XML Package to display related products  
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Product to display related products of   
  
**RemoteUrl**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: URL   
    **Data Type**: String   
    **Description**: Calls a remote URL and returns the response   
  
**ReplaceNewLineWithBR**   
  **Description**: Replaces any occurences of \\n with <br/>  
  **Sample**:   
  
    **Argument Name**: Content   
    **Data Type**: String   
    **Description**: Text to perform the find/replace on   
  
**SearchBox**   
  **Description**: Returns a form that contains an input control and submit button and posts to the search.aspx page  
  **Sample**: <xsl:value-of select="aspdnsf:SearchBox()" disable-output-escaping="yes"/>   
  
**SectionLink**   
  **Description**:   
  **Sample**:   
  
  **Description**: Returns a page name for the specified Section page in the site, using static links if required (e.g.s-  
  17-boots.aspx). NOTE: This function is for backward compatibility with Parser functions only and should not be used   
  in XmlPackage transforms because it outputs invalid XML when using the IncludeATag.   
  **Sample**: <xsl:value-of select="aspdnsf:SectionLink (SectionID, SEName, IncludeATag, TagInnerText)"   
  disableoutput-escaping="yes"/>   
  
    **Argument Name**: SectionID   
    **Data Type**: Integer   
    **Description**: ID of the desired category   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this section, if known. If blank, the store will figure it out, but that   
    takes an extra database query   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
    **Argument Name**: TagInnerText   
    **Data Type**: String   
    **Description**: The text that goes inside the <a> tag, only used when the IncludeATag is true (set to empty string   
    otherwise)   
  
**SelectElementsFromIDDelimitedString**   
  **Description**:   
  **Sample**:   
  
    **Argument Name**: delimitedString   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: delimiter   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: selection   
    **Data Type**: XPathNodeIterator   
    **Description**:   
  
    **Argument Name**: element   
    **Data Type**: String   
    **Description**:   
  
**SendMail**   
  **Description**: Sends an email with the details specified below, using the AppLogic.SendMail function. MailMe\_From\*   
  AppConfigs are used for the email's 'From' data.  
  **Sample**:   
  
    **Argument Name**: Subject   
    **Data Type**: String   
    **Description**: Desired Subject line   
  
    **Argument Name**: Body   
    **Data Type**: String   
    **Description**: Content of the email   
  
    **Argument Name**: UseHtml   
    **Data Type**: String   
    **Description**: (true/false) Should the email body be in HTML format   
  
    **Argument Name**: ToAddress   
    **Data Type**: String   
    **Description**: Destination address   
  
**SetTrace**   
  **Description**: If the HttpContext.Current.Items collection does not already contain an XmlPackageTracePoint, it is   
  added and set to the value of the TraceName param. If the XmlPackageTracePoint already exists, it is overwritten   
  with the new value.  
  **Sample**:   
  
    **Argument Name**: TraceName   
    **Data Type**: String   
    **Description**: Value to insert   
  
**ShowInventoryTable**   
  **Description**: If the ShowInventoryTable AppConfig is true, this will return a table with the product's inventory   
  status. Normal store customers will see only "Yes/No" for in-stock, store admins will see actual stock levels.  
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Product to display the inventory for   
  
**ShowQuantityDiscountTable**   
  **Description**: If the specified product has an active quantity discount table, the discount displayed.  
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Product to display the quantity discount table for   
  
**ShowRelatedProducts**   
  **Description**: Deprecated, use RelatedProducts instead.  
  **Sample**:   
  
**ShowUpsellProducts**   
  **Description**: Displays upsell products for the specified product ID  
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Product to display upsell products for   
  
**SizeColorQtyOption**   
  **Description**: Returns the controls that allow customers to enter a quantity, set a price (if needed), and choose   
  sizes/colors.  
  **Sample**:   
  
    **Argument Name**: ProductID   
    **Data Type**: String   
    **Description**: Product to display controls for   
  
    **Argument Name**: VariantID   
    **Data Type**: String   
    **Description**: Variant to display controls for   
  
    **Argument Name**: Colors   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: Sizes   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: ColorPrompt   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: SizePrompt   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: RestrictedQuantities   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: boolCustomerEntersPrice   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: CustomerEntersPricePrompt   
    **Data Type**: String   
    **Description**:   
  
    **Argument Name**: intTaxClassID   
    **Data Type**: String   
    **Description**:   
  
**SkinID**   
  **Description**: Returns the # of the skin the current customer is seeing the site in.  
  **Sample**:   
  
**SplitString**   
  **Description**: Splits a string and puts it inside tags using the specified TagName, e.g.   
  <TagName>value1</TagName><TagName>value2</TagName>,etc. The values will be XML Encoded.  
  **Sample**:   
  
    **Argument Name**: S   
    **Data Type**: String   
    **Description**: String to split   
  
    **Argument Name**: Delimiter   
    **Data Type**: String   
    **Description**: Character to split the string on   
  
    **Argument Name**: TagName   
    **Data Type**: String   
    **Description**: Tag to put the split strings in   
  
**Store\_Version**   
  **Description**: Returns the store version  
  **Sample**:   
  
    **Argument Name**: NotUsed   
    **Data Type**: String   
    **Description**: Pass an empty string   
  
**StoreVersion**   
  **Description**: Returns the store version  
  **Sample**:   
  
    **Argument Name**: NotUsed   
    **Data Type**: String   
    **Description**: Pass an empty string   
  
**StrCapitalize**   
  **Description**: Returns capitalized (first letter only) string (invariant culture).  
  **Sample**:   
  
    **Argument Name**: S   
    **Data Type**: String   
    **Description**: String to capitalize   
  
**StrFormat**   
  **Description**: Uses a delimited list of params to format a string that has format tags in it.  
  **Sample**:   
  
    **Argument Name**: SrcString   
    **Data Type**: String   
    **Description**: String to format   
  
    **Argument Name**: FormatParams   
    **Data Type**: String   
    **Description**: Delimited list of Format tags   
  
    **Argument Name**: Delimiter   
    **Data Type**: String   
    **Description**: Delimiter char to split the list of FormatParams on   
  
**StrFormatString Resource**   
  **Description**: Uses a delimited list of params to format a StringResource that has format tags in it.  
  **Sample**:   
  
    **Argument Name**: StringResourceName   
    **Data Type**: String   
    **Description**: String resource to format   
  
    **Argument Name**: FormatParams   
    **Data Type**: String   
    **Description**: Delimited list of Format tags   
  
    **Argument Name**: Delimiter   
    **Data Type**: String   
    **Description**: Delimiter char to split the list of FormatParams on   
  
**StringResource**   
  **Description**: Returns the specified string resource value.  
  **Sample**: <xsl:value-of select="aspdnsf:StringResource(StringResourceName)" disable-output-escaping="yes"/>   
  
    **Argument Name**: StringResourceName   
    **Data Type**: String   
    **Description**: String resource to return   
  
**StripHtml**   
  **Description**: Strings HTML tags out of a supplied string.  
  **Sample**:   
  
    **Argument Name**: TheString   
    **Data Type**: String   
    **Description**: String to remove HTML tags from   
  
**StrReplace**   
  **Description**: Replaces the old value of a string with a new value  
  **Sample**:   
  
    **Argument Name**: S   
    **Data Type**: String   
    **Description**: String to be changed   
  
    **Argument Name**: OldValue   
    **Data Type**: String   
    **Description**: String's current value   
  
    **Argument Name**: NewValue   
    **Data Type**: String   
    **Description**: New value to be assigned   
  
**StrToLower**   
  **Description**: Returns lowercase of a string (invariant culture).  
  **Sample**:   
  
    **Argument Name**: S   
    **Data Type**: String   
    **Description**: String to be made lowercase   
  
**StrToUpper**   
  **Description**: Returns uppercase of a string (invariant culture).  
  **Sample**:   
  
    **Argument Name**: S   
    **Data Type**: String   
    **Description**: String to be made uppercase   
  
**StrTrim**   
  **Description**: Returns trimmed (no trailing/leading whitespace) string.  
  **Sample**:   
  
    **Argument Name**: S   
    **Data Type**: String   
    **Description**: String to be trimmed   
  
**StrTrimEnd**   
  **Description**: Returns a string with any trailing whitespace trimmed.  
  **Sample**:   
  
    **Argument Name**: S   
    **Data Type**: String   
    **Description**: String to be trimmed   
  
**StrTrimStart**   
  **Description**: Returns a string with any leading whitespace trimmed.  
  **Sample**:   
  
    **Argument Name**: S   
    **Data Type**: String   
    **Description**: String to be trimmed   
  
**ToLower**   
  **Description**: Returns a copy of the specified string converted to lowercase using the casing rules of the invariant   
  culture.  
  **Sample**:   
  
    **Argument Name**: StrValue   
    **Data Type**: String   
    **Description**: String to be converted   
  
**Topic**   
  **Description**: Returns the contents of the specified topic with any parser tokens replaced with their intended values.   
  NOTE: If the TopicName and TopicID provided do not reference the same topic, the topic specified by Name will be   
  returned.   
  **Sample**:   
  
    **Argument Name**: TopicName   
    **Data Type**: String   
    **Description**: Name of the topic to replace   
  
    **Argument Name**: TopicID   
    **Data Type**: String   
    **Description**: ID of the topic to replace   
**ToUpper**   
  **Description**: Returns a copy of the specified string converted to uppercase using the casing rules of the invariant   
  culture.  
  **Sample**:   
  
    **Argument Name**: StrValue   
    **Data Type**: String   
    **Description**: String to be converted   
  
**UpsellProducts**   
  **Description**: Deprecated, use ShowUpsellProducts instead.   
  
**User\_Menu\_Name**   
  **Description**: If the customer is not logged in, returns the value of skinbase.cs.7. If they are, it returns the full   
  customer name.  
  **Sample**:   
  
**User\_Name**   
  **Description**: If the current customer is not logged in, returns an emptry string. If the current user is an admin,   
  returns the full name. If the current user is a customer, returns the value of skinbase.cs.1 + their name and their   
  customer level name (if any) as a link to the account page.  
  **Sample**:   
  
**VectorLink**   
  **Description**: Returns a page name for the specified Vector page in the site, using static links if required (e.g.   
  v-17-hats.aspx). NOTE: This function is for backward compatibility with Parser functions only and should not be   
  used in XmlPackage transforms because it outputs invalid XML when using the IncludeATag.   
  **Sample**: <xsl:value-of select=”aspdnsf:VectorLink(VectorID, SEName, TagInnerText)” disableoutput-  
  escaping=”yes”>   
  
    **Argument Name**: VectorID   
    **Data Type**: Integer   
    **Description**: ID of the desired vector   
  
    **Argument Name**: SEName   
    **Data Type**: String   
    **Description**: The SEName field from the db for this vector, if known. If blank, the store will figure it out, but that   
  takes an extra database query   
  
    **Argument Name**: IncludeATag   
    **Data Type**: Boolean   
    **Description**: Returns an <a> tag with the href attribute set to the page url   
  
    **Argument Name**: TagInnerText   
    **Data Type**: String   
    **Description**: The text that goes inside the <a> tag, only used when the IncludeATag is true (set to empty string   
  otherwise)   
  
**XmlPackage**   
  **Description**: Returns the finale, transformed results of running the specified XML package, named with a .xml.config  
  extension. NOTE: Be careful that the XML Package does not refer to itself directly or indirectly or you could cause   
  endless recursion!   
  **Sample**:   
  
    **Argument Name**: PackageName   
    **Data Type**: String   
    **Description**: XML Package to run   
  
**XmlPackageAsXML**   
  **Description**: Returns XML ready to be modified or traversed using the available .NET methods for working with XML  
  **Sample**:   
  
    **Argument Name**: packageName   
    **Data Type**: String   
    **Description**: Package to run   
  
    **Argument Name**: runtimeParams   
    **Data Type**: String   
    **Description**: Parameters to use when running the specified XML Package
      