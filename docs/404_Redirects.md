
      ---
      title: 404 Redirects
      ---

      If a customer on your site tries to access a page name that doesn't exist, the software has the ability to display a customized 404 page that can be edited through the admin site and inherits your site's skin. This page can also be configured to recommend pages on your site based on the incorrect address the customer tried to go to. This can help cut down on abandons and customer frustration.

Enabling the Custom 404 Page
============================

1.  First, open the web.config file in the root of your site (in Visual Studio or a text editor like Notepad) and find the "customErrors mode" line. Change it to read:  
      
    
    `<``customErrors` `mode``=``"On"``>`
    
      
     ![](images/1415918635644.png)  
      
    This is case-sensitive! 'on' will not work, use 'On'.[  
    ](http://manual.aspdotnetstorefront.com/p-1281-custom-error-pages.aspx)
2.  Go to [Content > Manage Topics](default.aspx?pageid=topics) in the admin console, and find the **pagenotfound** topic. Edit it to show the content you would like to display to customers who end up on this page on your site:  
     ![](images/1415918787660.png)

Setting up Page Recommendations
===============================

The steps above enable the basic 404 redirect, to display a friendly error message. The software can also try to make guesses (using the [Levenshtein Distance Algorithm](http://en.wikipedia.org/wiki/Levenshtein_distance)) at what page the customer was looking for, and provide links to those guesses. To set that up, configure the following [Settings](default.aspx?pageid=settings):  
  

**Setting Name**

**Description**

404.ComparisonDistance

This setting controls how 'loosely' the software will compare a customer's mistaken page name with existing pages on the site. The higher this is set to, the 'looser' the comparison is and the more likely the site is to find a possible match, but the longer the search can take.

404.NumberOfSuggestedLinks

This setting determines how many suggestions the 404 page will display.

404.VisibleSuggestions

This controls what areas of the store the software will look in when making its guesses. If left blank, it will check products, categories, manufacturers, sections, and topics. Valid values are: product, category, manufacturer, section, topic (or any combination of those).

Show404SuggestionLinks

If this is true, the suggestions the software makes will be links to those pages.
      