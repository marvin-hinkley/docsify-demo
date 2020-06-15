
      ---
      title: Mobile Skin
      ---

      [  
](http://manual.aspdotnetstorefront.com/images/product/MSx/header.themeid_cascade.png) ![](images/1416241718172.png)   ![](images/1416241738399.png)   [![](images/1416241757501.png)](http://manual.aspdotnetstorefront.com/images/product/MSx/action.themeid_cascade.png) 

Enabling Mobile Support
=======================

To turn on mobile device handling on your site, simply set the **Mobile.IsEnabled** [Setting](default.aspx?pageid=settings) to **Yes**. For more information on configuration that can be done, see the 'Customizing the Mobile Platform' section below.

Customizing the Mobile Platform
===============================

The mobile platform handles customers on mobile devices by switching them to use a new skin that has modified XmlPackages, a template designed for smaller screens, and uses jQuery Mobile tools to make navigation more mobile-friendly. The template for this skin is a standard .NET master page and can be edited just like the normal desktop skin can, but some additional familiarity with jQuery Mobile may be necessary depending on what changes you're trying to make. There is some extremely user-friendly and helpful documentation on the jQuery Mobile platform at [http://jquerymobile.com/test/](http://jquerymobile.com/test/).

The mobile skin is SkinID 2 (see **Mobile.SkinID** below). If your site was upgraded from an earlier version or you've had a new skin created for your site, that ID may need to change. Check with your developer to find out what to set that to.

The mobile platform has quite a few [Settings](default.aspx?pageid=settings) that can be modified to change appearance and behavior:

**Setting Name**

**Description**

Mobile.Action.ThemeId  
(see examples above)

This setting changes the appearance of 'call to action' buttons like Next, Previous, Add to Cart, etc. You can switch between 5 jQuery Mobile themes by changing this to a, b, c, d, or e.

Mobile.AllowAddressChangeOnCheckoutShipping

If this is set to true, customers will be able to choose from a dropdown list of all their saved addresses during checkout. If false, orders will automatically go to the customer's default shipping address.

Mobile.ContactPhoneNumber

This controls the phone number to link to if you have Mobile.IncludePhoneLinks set to Yes.

Mobile.DefaultLocaleSetting

This sets the locale to use for mobile device display. This should generally be set to the same as the DefaultLocale Setting.

Mobile.DefaultXmlPackageEntity

For developers only! This Setting changes the XmlPackage that will be used for entity display on the mobile skin. This can be changed, or you can edit the existing mobile.entity.default.xml.config XmlPackage  will be in your mobile skin's XmlPackages folder.

Mobile.DefaultXmlPackageProduct

For developers only! This Setting changes the XmlPackage  that will be used for product display on the mobile skin. This can be changed, or you can edit the existing mobile.product.default.xml.config XmlPackage  will be in your mobile skin's XmlPackages folder.

Mobile.Entity.ImageWidth

For developers only! This controls the width of product images on entity pages. Your images do not have to match this size when they're uploaded to the site, they will be resized with CSS.

Mobile.Entity.PageSize

This sets the number of products to list per page on mobile entity pages.

Mobile.Header.ThemeId  
(see examples above)

This setting changes the appearance of the header at the top of every mobile page. You can switch between 5 jQuery Mobile themes by changing this to a, b, c, d, or e.

Mobile.IncludeEmailLinks

If Yes, the mobile skin will show a link to send an email in the footer of every page. The email address is taken from the GotOrderEmailFrom Setting.

Mobile.IncludePhoneLinks

If Yes, the mobile skin will show a link to call your store in the footer of every page. The number displayed comes from the Mobile.ContactPhoneNumber Setting.

Mobile.IsEnabled

If this is set to No, all customers will be shown the desktop skin regardless of the device they are on.

Mobile.PageExceptions

For developers only! Pages listed in this AppConfig will not trigger switching mobile devices to the mobile skin. Multiple pages can be listed as a comma separated list.

Mobile.PayPal.Express.ButtonImageURL

For developers only! This sets the URL for the PayPal Express button.

Mobile.ProductSlider.ImageWidth

For developers only! Sets the width of product images that display in the product slider, which is used for featured products, recently-viewed products, related products, upsell products, and "also bought" products.

Mobile.ProductSlider.MaxProducts

Sets the max number of products to show in the product slider. Keep this number low to increase page load times. This value should be evenly divisible by the value of Mobile.ProductSlider.Width for best results.

Mobile.ProductSlider.Width

For developers only! This defines the number of products each 'pane' of the product slider will display.

Mobile.ShortUserAgentList

For developers only! This list of comma separated values is part of what the mobile platform matches against to identify mobile devices. See also Mobile.UserAgentList.

Mobile.ShowAlternateCheckouts

If true, Google Checkout and/or PayPal Express will show up on your mobile shopping cart page if they are also enabled on the main site.

Mobile.ShowMobileOniPad

If true, the site will switch iPad users to the mobile skin.

Mobile.SkinId

This sets which skin to switch users on mobile devices to. This is Skin 2 on a clean 9.3 install, but may be different if you have upgraded or had custom skins built. Check with your developer before changing this.

Mobile.ThemeId  
(see examples above)

This setting changes the general appearance of the mobile skin, controlled by jQuery Mobile. You can switch between 5 jQuery Mobile themes by changing this to a, b, c, d, or e. Note that the skin can be further customized by having a developer/designer modify the template and stylesheets for you. _You are not limited to these 5 themes!_

Mobile.UserAgentList

For developers only! This list of comma separated values is part of what the mobile platform matches against to identify mobile devices. See also Mobile.ShortUserAgentList.

  
The default entity displayed on the Mobile home page is the Departments (a.k.a. Sections). If you wish to change that, you can do so by editing the Topic: Mobile.9HomeTopIntro for the entityname="section" and changing the "section" to the entity you wish to be displayed on the home page, such as "category"  
  
The "MSx" logo in the stock mobile skin header is hard-coded text that can be replaced in the mobile template.master file. If unfamiliar with editing the template.master file, please consult a knowledgeable [developer](http://www.aspdotnetstorefront.com/c-270-development-partners.aspx) for assistance.
      