
      ---
      title: Source Code
      ---

      \[Company Name\] Source code can be purchased [here](http://www.aspdotnetstorefront.com/p-208-source-code.aspx).   
  
At the Solution level, \[Company Name\] is organized into 14 projects and folders. Three of these source code projects are the most commonly modified Source Code projects by developers, and are labeled with "one of the three most important" below. These are the three most important projects to familiarize yourself with.

To Get Started:

1.  Open up the AspDotNetStorefront solution in Visual Studio.
2.  If all of your projects are expanded, collapse them.
3.  As we visit each project, expand it so you can see the classes inside.

AspDotNetStorefrontProcessors Folder
====================================

This folder contains the 37 current Payment gateway Integration projects and provides a useful model for you to follow should you want to create your own custom payment gateway e.g. Creating a project named GatewayMyCustomeGateway (Replacing my custom gateway with a name that is meaningful to your gateway).

AspDotNetStorefrontAdmin
========================

This small project is just a placeholder that provides a namespace for our AdminMasterPage base in our AdminPageBase objects.

AspDotNetStorefrontBuySafe
==========================

This project is our wrapper for the by safe web service integration. This contains our service/web references to the BuySafe API.

AspDotNetStorefrontCommon
=========================

In previous versions of AspDotNetStorefront the common project was the general logic folder for quite a bit of the AspDotNetStorefront code. In later versions that has been reduced to a handful of simple utilities, A CSV exporter, an object for managing Excel files, an FTP client, and a helper to work with the Windows registry.

AspDotNetStorefrontControls (one of the three most important)
=============================================================

The AspDotNetStorefrontControls project is a key project that manages much of the user interaction that is not accomplished in the XML packages. These server controls handle much of the Input and validation for our account creation, checkout process, shopping cart Display, payment method input, Shipping method selection, shipping and tax estimator, Paging controls, and base kit controls.  
As much of the modifications that we do make to AspDotNetStorefront we find ourselves often modifying the order of the controls, the layout of the controls, and even augmenting the data that the controls ask for. This is one of our 3 key areas that we highly recommend taking the time to know if you find you are going to be working with version 8 and 9 AspDotNetStorefront’s

The AspDotNetStorefrontControls project contains server controls for features used on both the front end of the site and in the admin console. In development, some of the more common controls to modify for requirements are the Account, Address, Cart Summary and Shopping Cart Controls.

The account control is used on the front end of the site in both create account and the customer account pages. It contains their email address, password, phone number and email preferences. In some cases, you might want to modify the layout, order of the fields in the display, or add a new field to the account (for example, a custom B2B site might require a tax identifier field).

The address control is used for the shipping and billing addresses throughout the site.

The cart summary control displays the subtotal, discount total, shipping total, tax total and order total. This control displays throughout the checkout process.

The shopping cart control displays the line items on the shopping cart page. This is one of the most common controls to modify in development out of the server controls in the project. Sometimes, a merchant will want to change the layout of their shopping cart, or, display the extended price (or subtotal) in addition to the unit price. Or maybe weight is an important field on their product and they want to display weight with the line items. The shopping cart control is where you want to be to make those changes.

AspDotNetStorefrontCore (one of the three most important)
=========================================================

The AspDotNetStorefrontCore project Could be considered the brains of our operation. This project is where all the Objects and Business logic of our AspDotNetStorefront exists. We will do things in here like modifying our tax rates, are shipping options, or cart Price calculations. Essentially all modifications that require a change to the default logic of AspDotNetStorefront will interact with the code within this project. We highly recommend getting familiar with the classes that are in this project as well as implementing best practices of managing changes in this project as your strategy will greatly impact the amount of effort that is required to upgrade storefront in the future.

AspDotNetStorefrontEventHandlers
================================

The AspDotNetStorefrontEventHandlers project is for a system of callouts that can post information to endpoint URLs when certain events happen on the site like: customer creation, payment on an order, and order being shipping and many more. This is not typically a project that you spend much time in, like the AspDotNetStorefrontWSI project you will read about below. In these projects if you use the features, you typically spend more time interacting with the feature set than the code itself.

AspDotNetStorefrontGateways (one of the three most important)
=============================================================

The AspDotNetStorefrontGateways project handles order creation logic – everything from moving the shopping cart items to the orders shopping cart items table to calling the configured payment gateway and storing confirmation numbers. We recommend familiarizing yourself with this project, and how payment processing takes place.

AspDotNetStorefrontLayout
=========================

The AspDotNetStorefrontLayout project is used by the admin.

AspDotNetStorefrontPromotions
=============================

In most cases, you won’t need to modify the AspDotNetStorefrontPromotions project, but it is a great project to familiarize yourself with if you ever find a need for a different type of promotion than what is supported out-of-box. The promotion engine handles promotions in two parts: Rules (or qualifies/disqualifies) and Discounts. A large amount of rules are currently supported for things like product id, customer level id, country, email address, minimum cart amount and much more. If the rules qualify the customer for the promotion, they get a discount. The discount (fixed or percentage) could be – a free gift, an order discount, a line item discount (will apply to only a single line item if the line item product id is a part of the rules), or a shipping discount.

AspDotNetStorefrontWSI
======================

The AspDotNetStorefrontWSI project is for the Web Service Interface (WSI) feature. It’s an XML based tool that functions similarly to an API and allows bulk tasks on things like product to be performed from remote systems. In most cases if you are using the WSI feature, you won’t need to modify the source code, or be familiar with the code itself. You’ll need to familiarize yourself with the XML format for interacting with the WSI.

/Web folder
===========

You should be aware of the classes in the /web/App\_Code folder that aren’t necessarily source code – but contain some application logic that you may someday need to modify. For example, Skinbase.cs is inherited from in all of the root .aspx pages and is used by many controls in the site and supports the “Skins” concept of the site (skins mapped per store).

Vortx.Mobile
============

The Vortx.Mobile project contains the logic for the mobile version of AspDotNetStorefront.

XSLTObjects
===========

The XSLTObjects project is utilized by the XmlPackages feature in the AspDotNetStorefrontCore project.
      