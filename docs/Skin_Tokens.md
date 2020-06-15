
      ---
      title: Skin Tokens
      ---

      Skin tokens are text that you place in the template.master file for your skin to add certain information to your site. The tokens are parsed by the software and replaced with the correct information each time a page is invoked. Below is a list of skin tokens and a description of what they do, with screenshots.  
  
For designers familiar with previous versions of \[Company Name\] software, it is important to note that the skin token format has changed slightly in this version. Skin designers should now use the standard master page format <%$ Tokens:TOKENNAME %>  
  
**<%$ Tokens:GOOGLE\_ECOM\_TRACKING\_V2 %>** - Adds the appropriate google analytics ecommerce tracking code to the orderconfirmation.aspx page when the site is in Live mode. If this is working properly, nothing will be displayed to the customer.  
  
**<%$ Tokens:COUNTRYDIVVISIBILITY %>** - DEPRECATED - Returns "hidden" if only one language is set up, or "visible" if multiple languages exist. Can be used to set the visibility properties of the <%$ Tokens:COUNTRYSELECTLIST %> token.  **You can use this token in Topics as (!COUNTRYDIVVISIBILITY!)**  
  
**<%$ Tokens:COUNTRYSELECTLIST %>** - DEPRECATED - Displays a dropdown list of installed locales that customers can use to choose the language to view the site in.  
**You can use this token in Topics as (!COUNTRYSELECTLIST!)  ,  or use the control in your template.master as <aspdnsf:LanguageSelectList ID="ctrlLanguageList" runat="server" Caption="Country:" />**  
  
**<%$ Tokens:CURRENCYDIVVISIBILITY %>** - DEPRECATED - Returns "hidden" if only one currency is set up, or "visible" if multiple currencies exist. Can be used to set the visibility properties of the <%$ Tokens:CURRENCYSELECTLIST %> token. **You can use this token in Topics as (!CURRENCYDIVVISIBILITY!)**  
  
**<%$ Tokens:CURRENCYSELECTLIST %>** - DEPRECATED - Displays a dropdown list of installed currencies that customers can use to choose the currency to view the site in.  
**You can use this token in Topics as (!CURRENCYSELECTLIST!)  ,  or use the control in your template.master as <aspdnsf:CurrencySelectList ID="ctrlCurrencyList" runat="server" Caption="Currency:" />**  
  
**<%$ Tokens:VATDIVVISIBILITY %>** - DEPRECATED - Returns "hidden" if either VAT is disabled or VAT.AllowCustomerToChooseSetting is false, or "visible" if VAT is on and VAT.AllowCustomerToChooseSetting is true. Can be used to set the visibility properties of the <%$ Tokens:VATSELECTLIST %> token. **You can use this token in Topics as (!VATDIVVISIBILITY!)**  
  
**<%$ Tokens:VATSELECTLIST %>** - DEPRECATED - If VAT is enabled and VAT.AllowCustomerToChooseSetting is true, this displays a dropdown that allows customers to decide whether prices are shown with or without VAT added.  
**You can use this token in Topics as (!VATSELECTLIST!)  ,  or use the control in your template.master as <aspdnsf:VatSelectList ID="ctrlVatList" runat="server" Caption="VAT Mode:" />**  
  
**<%$ Tokens:PAGEINFO %>** - Outputs the full page info (invocation, currency, locale, etc). This is only viewable by viewing the page source, does not display.  
  
**<%$ Tokens:USERNAME %>** - Displays "You're logged in as <customer name="">" where customer name is the currently logged-in customer, with a link to their account page  
  
**<%$ Tokens:SIGNINOUT\_TEXT %>** - Displays "Login" or "Logout" depending on the current login state.  
  
**<%$ Tokens:SIGNINOUT\_LINK %>** - Displays "Login" or "Logout" depending on the current login state, with links to either signin.aspx or signout.aspx.  
  
**<%$ Tokens:METATITLE %>** - Displays the page's meta title information.  
  
**<%$ Tokens:METADESCRIPTION %>** - Displays the page's meta description information.  
  
**<%$ Tokens:METAKEYWORDS %>** - Displays the page's meta keywords information.  
  
**<%$ Tokens:CURRENCY\_LOCALE\_ROBOTS\_TAG %>** - Adds the 'robots noindex,nofollow,noarchive" meta tag to the page.  
  
**<%$ Tokens:CARTPROMPT %>** - Displays the value of the CartPrompt AppConfig.  
  
**<%$ Tokens:SKINID %>** - Returns the ID of the skin the current customer is viewing the site in.  
  
**<%$ Tokens:NUM\_CART\_ITEMS %>** - Displays the number of items in the current customer's cart.  
  
**<%$ Tokens:STRINGRESOURCE, stringname %>** - Displays the contents of the referenced string resource.  
  
**<%$ Tokens:STRINGRESOURCEFORMAT, stringname, stringname %>** - This token displays the first string listed, with any {#} tokens replaced with the contents of the second (or additional) string.

For example: Assume string1.aspx.cs contains the text "This is my string that allows this bit - {0} - to be replaced", and string2.aspx.cs contains "Hello World". Invoking the token as "<%$ Tokens:STRINGRESOURCEFORMAT, string1.aspx.cs, string2.aspx.cs %>" would result in "This is my string that allows this bit - Hello World - to be replaced".

**<%$ Tokens:APPCONFIG %>** - Returns the value of the specified AppConfig.  
  
**<%$ Tokens:APPCONFIGUSINT %>** - Returns the integer value of the specified AppConfig.  
  
**<%$ Tokens:APPCONFIGBOOL %>** - Returns the boolean value of the specified AppConfig.  
  
**<%$ Tokens:TOPIC %>** - Returns the content of the specified topic.  
  
**<%$ Tokens:TOPICTITLE %>** - Returns the title of the specified topic.  
  
**<%$ Tokens:TOPICLINK %>** - Returns a link to the specified topic.  
  
**<%$ Tokens:USER\_MENU\_NAME %>** - Displays "my account" if not logged in, or the customer's full name if they are.  
  
**<%$ Tokens:STRINGFORMAT %>** - Same as STRINGRESOURCEFORMAT above.  
  
**<%$ Tokens:XMLPACKAGE %>** - Runs the specified XML package with the runtime params specified (if any). 

This tag allows you to pass custom parameters to XML packages. For example, invoking the token with the format <%$ Tokens:XMLPACKAGE, xmlpackagename, parametername=value %> will run the specified package and pass it a runtime parameter with the value you specify. That can be accessed in the XML package with <xsl:value-of select="/root/Runtime/parametername" />

**<%$ Tokens:CUSTOMERID %>** - Returns the ID of the current customer.  
  
**<%$ Tokens:SKINIMAGEDIR %>** - Returns the path to the image folder for the skin currently being used.  
  
**<%$ Tokens:SKINIMAGE %>** - Returns the specified image from the current skin's /images folder.  
  
**<%$ Tokens:ADMINLINK %>** - Returns a link to the site's admin folder.  
  
**<%$ Tokens:BuySafeSeal %>** - Required to display the buySAFE seal  
  
**<%$ Tokens:BongoExtend %>** - Required to display the Bongo Extend overlay if using [that integration](default.aspx?pageid=bongo_extend).  
  
**<%$ Tokens:VBV %>** - This displays a MasterCard SecureCode/Verified by VISA logo wherever the token is placed, if your CardinalCommerce.Centinel.Enabled [Setting](default.aspx?pageid=settings) is set to Yes.  
  

Breadcrumbs
===========

Please note that the 'SECTION\_TITLE' token that was found in earlier versions is no longer supported. That token has instead been replaced by the following code. Wherever this literal is in your template.master file, the skinning engine will replace it with the breadcrumb to the current page.  
  

`<``div` `id``=``"breadcrumb"``>`

`Now In:`

`<``asp:Literal` `ID``=``"SectionTitle"` `runat``=``"server"` `Text``=``''` `/>`

`</``div``>`

  
  
Only the asp:literal is actually required, putting this in a div simply allows for easier styling.
      