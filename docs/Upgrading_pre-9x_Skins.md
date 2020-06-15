
      ---
      title: Upgrading pre-9x Skins
      ---

      This page would welcome a sponsor from the \[Company Name\] community.  

\[Company name\] Skin Conversion Guide
======================================

Upgrading to 9.5
----------------

*   [Overview](#overview)
*   [Asp.net Themes and Directory Structure Changes](#themes)
    *   [Creating new skins through Themes and Templates](#newskins)
    *   [Invoking a Theme](#invoke)
*   [Tokens](#tokens)
*   [Master Page Conversion](#conversion)
*   [Menu](#menu)
*   [Template Controls](#templateControls)
*   [Aspx Page Conversion](#aspxConversion)
*   [Summary](#summary)
*   [Frequently Asked Questions](#faq)
*   [Troubleshooting Guide](#troubleshooting)
*   [Parser Token Conversion Table](#parser)

Overview
--------

This guide covers converting the template.ascx file into MasterPage templates.

For this document we’ll refer to the original skinning template as "skin template" and the MasterPage as "master template".

As with the move to using MasterPage templates, Asp.net themes were also incorporated into the website. This is to have better design-time support for the template and the actual pages.

Asp.net Themes and Directory Structure Changes
----------------------------------------------

When we moved to master pages and Asp.Net theming we had to break our skin folder into two different locations. This means that as part of the conversion process you'll need to know where to put different types of files. The diagram blelow helps illustrate where to put things. Basically images and styles go into the App\_Themes/Skin\_N folder, while most everything else goes in the App\_Templates/Skin\_N folder. No need to pull everything over from your old skin though. This is a good opportunity to clean house a bit.

![](images/structuredifferences.jpg)

### Creating new skins through Themes and Templates

1.  Open your old skin folder and the new website in separate explorer windows side by side
2.  Then go to the App\_Themes folder of the website. Copy the default skin, Skin\_1. Rename the new folder, the format should be Skin\_N where N is any number (e.g. “Skin\_4” since the build is pre loaded with Skin\_1, Skin\_2, and Skin\_3).
3.  Copy your custom stylesheet(s) (usually just style.css) and your images folder from your old skin in over the top of the contents in the new folder. You will probably want to remove new style.css and keep base.css
4.  Next, go to the App\_Templates folder of the website and copy the default skin, Skin\_1. When you rename your copy it should have the same name as the folder you created in App\_theme. (e.g. “Skin\_4”)
5.  Copy the template.ascx and the xmlpackage folder from your old skin to this new folder.
6.  Rename the template.master file that is already there and keep it for reference. You can delete this file when your conversion is done.
7.  Now rename the template.ascx file to template.master.
8.  You are now ready to begin converting your old template. See the Tokens and Master Page Sections below to guide you through the conversion.

### Invoking a Theme

Upon installation, Skin 1 is the default theme. Most sites have one theme, but it is possible to have multiple themes for a single site. Themes are identified as numbers (e.g. skin\_1, skin\_2, etc. For now, we follow the naming convention from previous builds). Keep in mind that the mobile skin is skin\_2 and skin\_3 is the responsive skin.

Themes are explicitly invoked via:

*   http://www.yourdomain.com/default.aspx?skinid=1 (to load theme 1)
*   http://www.yourdomain.com/default.aspx?skinid=3 (to load theme 3)

Tokens
------

You'll need to convert each template page token to the new style of token.

Please consult [this page](default.aspx?pageid=skinning_tokens) for a list of all “tokens” which can be included in your skin template files. There are about 150 tokens which are supported, for common dynamic elements like "UserName", "SignInOut\_Link", "Num\_Cart\_Items", etc...

For master pages, tokens are implemented via asp.net custom expression style in this format:  
<%$ Tokens:{The token name} {Optional parameters} %>  
  
To illustrate:  
the token: (!PAGEINFO!)  
will become: <asp:Literal ID="ltrPageInfo" runat="server" Text='<%$ Tokens:PageInfo %>' />  
  

This is a new parsing method. The parser token can be placed as a string on a property control such as Text and Visible attribute.

![](images/3.jpg)

![](images/4.jpg)

Basic Tokens:

1.  <%$Tokens:PageInfo%>  
    This line is optional, but EXTREMELY helpful for debug/run-time info. And we STRONGLY ask that you leave them in your skin, to help with any customer support we may need to provide.  
    ![](images/5.jpg)
2.  <%$ Tokens:UserName%>  
    This is the login name of the customer. If the customer is not registered this portion will be blank.  
    ![](images/6.jpg)
3.  <%$Tokens:SignInOut\_Link%>  
    This is for the link redirect. If the customer is registered and this is clicked, he will be redirected to the “logout.aspx” link. If not registered, the link URL will be on “signin.aspx”  
    ![](images/7.jpg)
4.  <%$Tokens:SignOut\_Text%>  
    This is what the customer will see if they log out at run time.  
    ![](images/8.jpg)
5.  <%$Tokens:Num\_Cart\_Items%>  
    This will return the number of items in the shopping cart  
    ![](images/9.jpg)

Master Page Conversion
----------------------

To convert an existing skin template.ascx into template.master, you’ll need to follow these steps.

1.  The head tag of the template must have:
    *   The runat="server" attribute. This is to support asp.net Themes
    *   Remove the stylesheet reference. It will be added automatically by asp.net depending on the theme used.
    *   Replace Parser tokens into its expression equivalent using the Tokens expression.
    *   Skin Template:
        
        ![](images/10.jpg)
    *   Master Template:
        
        ![](images/11.jpg)
2.  Add a <form> tag to the page. For this version, the form element will be a prerequisite. Preferably placed right after the <body> tag. You'll also want to add in the script manager check just inside the form. It is easiest to copy this code in from the default skin.
    *   Add the form tag and script manager check just after the opening body tag  
        ![](images/14.jpg)
    *   Don't forget your closing form tag  
        ![](images/closeform.jpg)
    *   There can only be 1 form tag on the template. The old skin template uses a form tag for the search which needs to be removed in favor of the search user control.  
        ![](images/12.jpg)
    *   Replace that with  
        ![](images/13.jpg)
    *   Remove any other forms on the page.  
          
        
3.  Change the control type of the PageContent from Placeholder to ContentPlaceHolder. Keep in mind that the ID should remain the same and is required to be “PageContent”. This will serve as the content area for the child pages.  
      
    Skin template uses <asp:PlaceHolder></asp:PlaceHolder>  
    ![](images/15.jpg)  
    Master template uses <asp:ContentPlaceHolder><asp:ContentPlaceHolder>  
    ![](images/16.jpg)
4.  We recommend replacing rev.categories and it's the other old entity menus with the new entitymenu xmlpackage.
    
    Replace this:
    
    ![](images/revcategoriescode.jpg)
    
    With this:
    
    ![](images/entitymenucode.jpg)
    
    The topic in the image above contains the HTML code and references to the entitymenu xml package so that you can adjust the display order and remove unwanted entity menus from the topic editor in the admin console.
    
5.  Replace the ComponentArt menu. This will be discussed in the next section.
6.  We've removed the tables used for layout and added a lot of new features since version 8 so you'll need to bring the base.css file from the default skin to your App\_Themes/Skin\_N folder. Make sure that when you do this you remove any CSS resets that may be in your exising styles and place them in their own file that gets included before the base.css file. We recommend nameing this file \_reset.css because Asp.Net themes include stylesheets in alphabetical order by default.
    

Menu
----

We've removed support for the ComponentArt menu.

The new default template has a vertical menu rather than a horizontal menu for categories and other entities. It also has a static horizontal menu of common links

![](images/newtemplate.jpg)

If you are happy with the default static horizontal menu we recommend replacing the componentart menu with the new Template.Topnavigation topic.

![](images/TemplateHorizontalNavCode.jpg)

If you need a dynamic horizontal menu we recommend using the entitymenu xmlpackage from the default skin and adjusting the styles to create a CSS dropdown menu. These styles are not provided in the default skin. The responsive skin, Skin\_3, also provides an example of how to do this.

![](images/DynamicHorizontalMenu.jpg)

Template Controls
-----------------

In version 9 we also started incorporating user controls into the site.

**Search Control**  
The search UI and functionality has been encapsulated into a user control.  
![](images/23.jpg)

**Select List Controls**  
These controls are provide options to change settings for

*   Locale
*   Currency
*   VAT

  
![](images/25.jpg)  

Aspx Page Conversion
--------------------

You can convert any custom aspx pages you may have using the following technique.

1.  Convert the pages into Masterpage child pages
    
    *   Open any aspx page (in this example we used default.aspx) then add the MasterPageFile directive. This is so as to have design-time support and visualization of the current page as part of the MasterPage.  
        ![](images/17.jpg)
    *   Now that the page will be living inside the MasterPage, you’ll need to tweak the page so as to accommodate the content areas that the masterpage provides.
        *   Strip the page of any html markup other than what should be present in the content itself.
        *   Add an asp.net Content control as the root control on the page. Make sure that ContentPlaceHolderID is “PageContent”
        *   Add a panel with an ID of “pnlContent” as the only child control of the Content control
        *   Insert the contents of the page inside the pnlContent control.
        *   If there are <form> tags, remove them. Only the masterpage file can have the form tag.
    
    Default.aspx as child page:  
    ![](images/19.jpg)
    

Summary
-------

This guide provided information on converting the skin template to master template. There is still support for the old skinning, however, the preferred approach now is to use MasterPages as this will help greatly in the design-time support.

Frequently Asked Questions
--------------------------

Q: Am I allowed to add another content placeholder on my default MasterPage?  
A: Yes. You will need to handle that per page if you want to introduce content.  
  
Q: Can I use my existing ComponentArt menu?  
A: For this version, we chose not to support ComponentArt.  
  
Q: Can I use my customized ComponentArt menu styles?  
A: We’ve deprecated those styles. The default skin 1 was designed to look like the old ComponentArt version. Customize the asp.net styles instead.  
  
Q: Will Parser tokens still be supported?  
A: Parser tokens will still be supported except for the Metatitle, Metadescription and Metakeywords. Parser token through custom expression is the preferred migration path.  
  

Troubleshooting Guide
---------------------

*   Broken images in template through usage of (!SKINID!) parser token
    *   You can reference it through the App\_Themes directory although it won’t give you design-time visual on the MasterPage.
    *   The preferred approach is to use either:  
        Asp.net Theme’s SkinID property  
        ![](images/26.jpg)  
        Or the Token:SkinImage  
        ![](images/27.jpg)
    *   For topic pages, hardcoded links to skins/skin\_N/images should be corrected to reference App\_Themes/Skin\_N/images folder.
*   Template won’t show preview on DreamWeaver or similar tools
    *   Dreamweaver determines whether to show a preview mode depending on the extension of the file. It doesn’t recognize the .master extension.
    *   The preferred editor is Visual Studio.
*   Page just refreshes after a postback action
    *   There might be a nested <form> tag. The main form tag is declared on the MasterPage and is required to be there only. All the pages should not have their own form tags.
    *   If a customization is done that requires its own form tag, a workaround would be to separate that into another page and provide a button to redirect to that page instead.
*   Error: Cannot set property value to property name for a user control upon loading the designer.
    *   This is a bug with Visual Studio 2008. You might need to restart the IDE to view the control. For more information, see [https://connect.microsoft.com/VisualStudio/feedback/ViewFeedback.aspx?FeedbackID=361826](https://connect.microsoft.com/VisualStudio/feedback/ViewFeedback.aspx?FeedbackID=361826)

Parser Token Conversion Table
-----------------------------

These are just a list of some of the common tokens encounted when converting your skin. For a more complete list see [Skin Tokens](default.aspx?pageid=skinning_tokens).

Parser Token

Replacement

(!METATITLE!)

<title>

(!METADESCRIPTION!)

<meta name="description" content="">

(!METAKEYWORDS!)

<meta name="keywords" content="">

(!SECTION\_TITLE!)

Asp.net Literal control with id of _"SectionTitle"_

(!SKINID!)

Tokens:SkinID

(!PAGEINFO!)

Tokens:PageInfo

(!NUM\_CART\_ITEMS!)

Tokens:Num\_Cart\_Items

(!SIGNINOUT\_LINK!)

Tokens:SignInOut\_Link

(!SIGNINOUT\_TEXT!)

Tokens:SignInOut\_Text

(!USERNAME!)

Tokens:UserName

(!CURRENCY\_LOCALE\_ROBOTS\_TAG!)

Tokens: Currency\_Locale\_Robots\_Tag

(!AppConfig Name="_xxx_"!)

Tokens:AppConfig, _xxx_

Tokens:AppConfigBool, _xxx_

Tokens:AppConfigUSInt, _xxx_

(!XmlPackage Name="_xxx_"!)

Tokens:XmlPackage, _xxx_

Tokens:XmlPackage, _xxx_, _{additional runtime parameters ampersand delimited}_

(!COUNTRYSELECTLIST!)

LanguageSelectList control

<aspdnsf:LanguageSelectList ID="ctrlLocaleList" runat="server" Caption="Language:" CssClass="MLSettings" />

(!CURRENCYSELECTLIST!)

CurrencySelectList control

<aspdnsf:CurrencySelectList ID="ctrlCurrencyList" runat="server" Caption="Currency:" CssClass="MLSettings" />

(!VATSELECTLIST!)

VATSelectList control

<aspdnsf:VatSelectList ID="ctrlVatList" runat="server" Caption="VAT Mode:" CssClass="MLSettings" />

Topsearchform

Search control

\* Deprecated due to having it’s own <form> tag hanlding it’s own postback.

Add to cart form

Addtocart’s behavior was modified from having a having it’s own <form> tag and postback url for each instance originally(addtocart.aspx) to making it postback to the current page . Add to cart processing now happens in showproduct.aspx code-behind.
      