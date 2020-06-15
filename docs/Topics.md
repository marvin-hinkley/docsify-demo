
      ---
      title: Topics
      ---

      From the **Content** Menu, click **Manage Topics**.  
  
Topics are free form content blocks that can be displayed on your site, either embedded within other pages, or on a page of their own. These are often used for 'FAQ' pages, policy pages, special instructions, etc.   
  
Topics can contain HTML and scripting, though a working knowledge of those technologies is necessary. Content is entered through the 3rd-party 'RAD Editor' control created by Telerik.   
  
Topics can be used several ways:

*   At a direct URL, with the format: http://www.yoursite.com/t-topicname.aspx
*   Embedding in a .aspx page in this format: <aspdnsf:Topic ID="IDName" runat="server" TopicName="TopicName" />
*   In a skin template.master file, in this format: <%$ Tokens:TOPIC, topicname %>

Topic List
==========

 ![](images/1415986108910.png)

This part of the page lists the existing topics. Use the Filter section to locate a specific topic. Clicking on one of the names or the **Create Topic** button will display topic detail for editing.

Topic Details
=============

 ![](images/1415986249102.png)

This area is where the topic's attributes and contents are set. The fields are:

**Field Name**

**Description**

Topic Name

This is the name of the topic. This will not be visible to customers unless linking to the topic in a URL, in which case the name will be part of the URL.

Title

The is the topic's formal title. If nothing is present in the 'Search Engine Page Title' field explained below, this value will be used for the page title displayed in the browser.

Description

 This is the content of the topic. The Telerik RAD editor can accept HTML, if you click the <> button at the lower left. Note that the HTML needs to be properly formatted, or you can affect the rendering of the entire page this topic is displaying on.

Published

If unchecked, the topic will not be visible on the store.

Display Order

 This value determines the order that the topics will appear in on the [sitemap](default.aspx?pageid=sitemap). Leaving this set to 1 for all topics will cause them to be displayed alphabetically.

Search Engine Page Title

This is the title that will display in the browser. This value will also be used to generate a title meta tag for the page, which an help with indexing by outside search engines.

Search Engine Page Keywords

A comma-separate list of words to be turned into a keyword meta tag. Populating this field will help increase indexing by search engines.

Search Engine Page Description

A page description which will be turned into a description meta tag. Populating this field will help increase indexing by search engines.

Password

Entering a value here will password-protect the topic, so only customers who know that password can access the page. Leaving the field blank allows all customers to view the page.

Requires Disclaimer

Setting this to yes will require customers to agree to a disclaimer before viewing the topic page. See [here](default.aspx?pageid=disclaimers) for more information on disclaimers.

Publish in Site Map

If this field is set to yes, the topic will appear in your [](http://manual.aspdotnetstorefront.com/p-1032-sitemap.aspx)[sitemap](default.aspx?pageid=sitemap).

Frequently Used

Check this box if the topic is frequently updated. This will help you locate the topic using the Filter section on the Topic List page.

File Based Topics
=================

Topic pages can also be rendered from ordinary .htm files located on your site. The files should go in the App\_Templates/Skin\_#/ folder, and _must_ have .htm file extensions. Also remember that they must be complete, valid html files with opening and closing html, head, and body tags.

Topics created this way are accessed just like any other topic: /t-topicname.aspx (where topicname is the filename, without extension).
      