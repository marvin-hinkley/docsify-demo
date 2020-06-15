
      ---
      title: Basic Search
      ---

      The basic search function searches the fields listed below. [Advanced Search](default.aspx?pageid=advanced_search) functions differently.

**Products/Variants:**

*   Name
*   SKU
*   Manufacturer's Part number
*   Description

**Entities:**

*   Name

Search can be used on your site 2 ways:   
  
**Control:**   
You can embed the basic search control into your skin wherever you would like the search box to appear, such as:   

`<``aspdnsf:Search` `ID``=``"ctrlSearch"` `runat``=``"server"` `CssClass``=``"search"` `SearchButtonCaption``=``"Go"`

`SearchCaption="<%$ Tokens: StringResource, common.cs.82 %>"`

`SearchTextMinLength="<%$ Tokens:AppConfigUSInt, MinSearchStringLength %>"`

`SearchTextMinLengthInvalidErrorMessage="<%$ Tokens: StringResource, search.aspx.2 %>"`

`ValidateInputLength="true" ShowValidationMessageBox="true" ShowValidationSummary="false" />`

  
**Basic Search Page Link:**   
You can link directly to the /search.aspx page from within the [Topic](default.aspx?pageid=topics): **Template.TopNavigation**   
  
**Additional Notes:**   
[Setting](default.aspx?pageid=settings): **SearchDescriptionsByDefault** allows the search to include product descriptions as well.   
  
You can use an XmlPackage based display for the Basic Search (and the [Advanced Search](default.aspx?pageid=advanced_search)), selectable with the [Settings](default.aspx?pageid=settings): **XmlPackage.SearchPage** and **XmlPackage.SearchAdvPage**   
  
It is recommended that [Full Text Search](default.aspx?pageid=full_text_search) not be enabled in order for the Basic Search to operate effectively. You may want to experiment with FTS enabled/disabled to determine your preferred behavior.
      