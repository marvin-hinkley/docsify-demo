
      ---
      title: Guided Navigation
      ---

      Installation Guide
==================

### Before You Begin

Please read through the entire installation guide and make sure you understand the installation process before you begin an installation on your live site. If there are any steps of this installation process that are unclear, please contact our\[Help Desk\]to request assistance.

*   In order to safely complete this installation on a live website you need to be able to backup your site files and database, and have a plan and permission to restore them should you encounter a problem during the installation process.
*   Different hosting providers and environments will have different methods of backing up and restoring databases. Please work with your hosting company to discuss the backup and restore tools that are available to you.
*   This installation process requires a level of technical expertise.
*   Please ensure that:

*   You have file access to the root of your website (FTP or RDC are the most common).
*   You have SuperAdmin Access to your \[Company Name\] site.

### Installation

1.  Backup your database.
2.  Backup your site files.
3.  Copy the contents from the installation folder into your website.
    1.  Move the **Web/App\_Themes/Skin\_1/GuidedNavigation.css** file to the **App\_Themes/Skin\_{your skinID}** folder on your website.
    2.  Copy the **Web/jscripts** and **Web/XmlPackages** folders over the existing folders on your website.
    3.  You will be prompted to overwrite **page.search.xml.config**. Please do.
4.  Navigate to the installer page by going to **http://www.yourdomain.com/e-guidednavigationinstall.aspx?install=true** in your browser.
5.  Click the **Begin Installation** button.
6.  Login to the admin console of your website and click **Refresh Store** to finish the installation.
7.  Remove the **guidednavigationinstall.xml.config** xmlpackage from your XmlPackage folder. It is no longer needed.
8.  Refer to the Usage Guide below for information on setting up Guided Navigation.

User Guide
==========

*   [Quick Start Guide](#quickStart)
    *   [Setting up your categories](#settingUpCategory)
    *   [Setting up your first reductive attributes](#settingUpAttributes)
    *   [Layout Options](#layoutOptions)
*   [What is Guided Navigation?](#whatIsGuidedNav)
*   [Guided Navigation Structure](#guidedStructure)
*   [Configuration Options](#configurationOptions)
*   [Appendix](#appendix)
    *   [Running SQL in the admin console](#runSql)

Quick Start Guide
-----------------

### Setting up your categories to use guided navigation

To use Guided Navigation on a category page, you'll need to choose the Guided Navigation Grid layout from the page layout drop down and save your category.

​

![](images/GuidedNavSelection.jpg)

​

If you want to use guided navigation on all of your category pages you can run the following SQL in your admin console under **Configuration > Advanced > Run SQL**:

​

``

`UPDATE` `Category` `SET` `XmlPackage =` `'entity.guidednavigationgrid.xml.config'`



``

\*For help with this see the [run sql section](#runSql) in the appendix

If you were to look at the category page now it would look something like this:

​

![Guided Navigation with no attributes.](Images/GuidedNoAttributes.jpg)

​

Now it's time to add some attributes to these products.

### Setting up your first reductive attributes.

To set up your reductive attributes you'll need to log in to the admin console and create a new department. We'll use "Color" for this example.

Go to **Products > Product Groups > Departments** (button) and click the **Create Department** button.

​

![Navigate to the manage departments screen.](Images/AddNewSection.jpg)

​

Name the department with the name of your attribute group, "Color" for example and then click **Save and Close**.

​

![Add a new Reductive Group](Images/CreateAttributeGroup.jpg)

​

Now we'll add an attribute to our attribute group by clicking the plus sign next to the newly created attribute group.

​

![Add an attribute group](Images/DepartmentAdd.jpg)

​

Give your new attribute group its first attribute. "Red" for example and then click **Save and Close**.

​

![Add an attribute](Images/AddNewAttribute.jpg)

​

Repeat this process until you've got all the attributes you want.

​

![Finished Attributes](Images/FirstAttributeGroup.jpg)

​

Now that we've got an attribute group we need to map some products to these attributes. Open the first attribute (Red in our case) and assign some products to it using the **Products** tab. Click the "Products For Department" link. Make sure to check the "Show Unmapped Products" checkbox to view products not currently mapped to the Department. If you did not choose to use the guided navigation on all of your categories, only consider products that are in a category you are using guided navigation on.

​

![Map Products](Images/MapProducts.jpg)

​

Repeat this process until you've got a few products mapped up to the attributes. Remember to **REFRESH STORE** (Reset Cache) at the top of your admin after making changes.

Now your category page should look something like this:

​

![Guided Navigation page with attributes](Images/GuidedWithAttributes.jpg)

​

### Layout Options

Guided Navigation has a few different layout options. Feel free to try a few of these options until you get the one you are looking for.

#### One Column

The default option is the one column layout. This layout works well when your site already has a vertical navigation down one side on every page of the site. To turn this option on, change the [Setting](default.aspx?pageid=settings): **GuidedNavigation.LayoutStyle** to **onecolumn**. One drawback to this option however is that it can push a lot of your products down below the fold.

#### Two Column

The second option is a two column layout. This is an excellent option if your site is full width. In other words does not have a vertical navigation on every page of the site. To turn this option on, change the [Setting](default.aspx?pageid=settings): **GuidedNavigation.LayoutStyle** to **twocolumn**.

#### Replace a column

If the one column and two column layouts do not work for you because you've got a two column template and you want to have a vertical navigation on all pages of your site, but you would like to replace the vertical navigation on other pages of the site then this is probably your best option. You can replace a given element in your template with the contents of the guided navigation by providing a CSS selector in the [Setting](default.aspx?pageid=settings): **GuidedNavigation.NavigationElementSelector**. An example selector could be **#verticalNavWrapper**. This would replace your vertical navigation with guided navigation. Try it out! If it doesn't look right just change the Setting back to blank. If the guided navigation doesn't show up, check to make sure your CSS ID is spelled correctly and includes the pound sign (#).

What is Guided Navigation?
--------------------------

Guided Navigation is a supplementary navigation that allows shoppers to narrow (or reduce) a product set based on attributes the shopper is looking for. It is more flexible than standard hierarchical navigation because it allows the user to define different combinations of search attributes rather than traversing a category hierarchy.

Guided Navigation always begins by showing a product set to the user. This product set can be defined by a top level category or a search the user performs. Guided Navigation only makes sense in the context of product listing pages and should not be shown on pages other than product listing pages.

### Reductive Elements

Guided Navigation is comprised of two basic structures: Reductive Groups and Reductive Attributes. On any given reductive page there are multiple Reductive Groups, each containing multiple Reductive Attributes. The image below contains an example of a reductive group (Color) with multiple reductive attributes (Blue, Green, Red.). As a shopper is browsing they will be able to choose one reductive attribute per group.

![Reductive Group](Images/ReductiveGroup.jpg)

### Building Guided Navigation

When a Guided Navigation page is loaded, the navigation is built based upon the product set currently being viewed. This is a key concept when planning or modifying your Guided Navigation. Every Reductive Attribute with matching products will be shown and every Reductive Group with Reductive Attributes will be shown. In other words, in the example above, if there were no "Blue" products in our current product set, the "Blue" Reductive Attribute would not be shown. If there were no products in any of the "Color" attributes, the "Color" Reductive Group would not be shown. This calculation is made every time a user selects another reductive attribute, so the navigation will narrow itself with each selection the user makes.

If you would like some Reductive Groups to show on some categories and not others, the only way to do that is to carefully map the products in each category such that each unwanted Reductive Group is empty for that category (A Reductive Group is considered empty when all of its Reductive Attributes are empty).

Guided Navigation Structure
---------------------------

Default instances of Guided Navigation use the \[Company Name\] Categories as top level product groupings. These should be the most basic product groupings on your site. They are the starting point for a user's shopping experience.

Guided Navigation is defined by \[Company Name\] Departments. Each top level Department defines a Reductive Group and each second level Department defines a reductive attribute. In the example below, the department hierarchy shows several Reductive Groups (Color, Price Range, Rating, etc.) and the Reductive Attributes under Color. Size, Color, and Price also have child Attribute departments.

​

![Reductive Group](Images/DepartmentSetup.jpg)

​

Products should be mapped to the appropriate Reductive Attribute departments. There is no need to map anything to Reductive Group departments.

Configuration Options
---------------------

To see all of the different configuration options for the guided navigation search the store [Settings](default.aspx?pageid=settings) for "guided".

#### GuidedNavigation.UseDropdowns

*   If this is set to **Yes**, Reductive Groups will be shown as dropdown menus rather than link lists.  
      
    If any particular reductive group has "dropdown" in its Custom Field, that particular group will show as a drop down. See the Product Groups page for more information on [Custom Fields](default.aspx?pageid=product_groups).

#### GuidedNavigation.LinkCount

*   The number of Reductive Attribute links to show before a "more..." button.

#### GuidedNavigation.ShowCounts

*   When set to **Yes** the number of products in each reductive attribute will be shown next to each reductive attribute.

#### GuidedNavigation.UseHierarchy

*   (Advanced) Enables Reductive Hierarchy. Children will only be displayed when the parent is selected. Hierarchical levels alternate between section headers and actual departments. If this is set to **No**, only the first two levels (group and departments) will display on the site.

#### GuidedNavigation.ShowSelected

*   If **Yes**, the "You have selected" section will show above the Guided Navigation.

#### GuidedNavigation.UseFullTextSearch

*   Full Text Search for Guided Navigation must be enabled here.

#### GuidedNavigation.ShowEmpties

*   Show empty categories (unlinked). This drastically changes the behavior of the navigation. All Reductive Groups and Attributes will be shown on every page, regardless of their count. When an attribute is chosen in a group, the whole group will still show, with the selected attribute bolded, and the rest disabled.

#### GuidedNavigation.LayoutStyle

*   This allows you to change the layout of the guided navigation page from a one column layout to a two column layout. The default value is **onecolumn**. The other option is **twocolumn**.

#### GuidedNavigation.NavigationElementSelector

*   This option allows you to replace a section of your website with the guided navigation options. To do this you need to find a unique CSS selector that identifies a section of your template. This is designed to be used to override a default navigation area.

Appendix
--------

### Running SQL in the admin console

Warning! You should always back up your database before running sql statements. You can easily break your website with a typo in your sql command.

1.  Log in to the admin console of your website.
2.  Navigate to **Configuration > Advanced > Run SQL**.
3.  Copy the sql you want run and paste it into the textbox on the Run SQL admin screen. Click **Submit**.
4.  Click the **Refresh Store** button in the admin console.
      