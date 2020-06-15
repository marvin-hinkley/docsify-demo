
      ---
      title: Manage Ratings
      ---

      _**Compunix, providing solutions to capture more customer ratings.**_  
As all merchants know, product reviews are hard to obtain; increase online sales and boost search optimization with an advanced [custom product reviews plugin](http://www.ecommercecartmods.com/p-213-product-reviews-and-ratings-module-for-aspdotnetstorefront.aspx). This review and rating solution allow for reviews to have multiple questions and include a groups rating engine with automated review request emails sent to customers.  
  
From the **Products** Menu, click **Manage Ratings**   
  
Enabling ratings allows customers to make comments on your products, which can help boost sales and determine if it's desirable to keep selling certain products. Bear in mind that enabling this feature will add to the maintenance of the store, as you will want to keep a fairly close eye on your ratings to ensure inappropriate material is not being posted on your site.

It is not possible to enable ratings on some products and not others. If ratings are enabled, they appear on all products.

Managing Ratings
================

On this page in the admin console, you can see a list of all of your current ratings. Ratings can be searched by term, and filtered by whether or not they contain phrases you have set up as bad words on your site.  
   ![](images/1419881382939.png)  

Enabling Ratings
----------------

To turn ratings on, you will need to set your RatingsEnabled [Setting](default.aspx?pageid=settings) to **Yes**. There are also 3 other [](http://manual.aspdotnetstorefront.com/p-978-appconfig-parameters.aspx)[Settings](default.aspx?pageid=settings) which affect how your ratings feature works:  
  

**Setting Name**

**Description**

RatingsCanBeDoneByAnons

If this is set to **Yes**, customers do not have to register to post comments on your site. We highly recommend this is left false, as it will cut down on spam/junk postings.

RatingsCommentFrameVisibility

If this is set to **Visible**, the voting worker window will be shown on product pages. This is for debugging purposes only, this should be set to **hidden** on a live site.

RatingsPageSize

This determines how many ratings show per page on product detail pages. If the number of ratings on the product exceeds this, customers will have to click a link to navigate through the list. We recommend this be kept to a pretty small number.

Ratings Display
---------------

If a product does not yet have a comment, customers will see this on the product detail page:  
 ![](images/1415402374868.png)  

  

If they click the link to create a rating, this window will open:  
  
 ![](images/1415402455673.png)  
  
  
Once the rating is saved, customers will see a box similar to this on the product detail page:  
  

 ![](images/1415402431082.png)

  

Badwords
========

From the **Products** menu, click **Manage Ratings**, then click **Manage BadWords**.  
  
If you're using ratings on your site, you'll want to make sure that inappropriate content doesn't get posted. The Manage Badwords page helps make this faster. You can enter words into the text box on this page and save them, and any ratings containing those words will be flagged. Use the **Has Bad Words** dropdown in the **Filter** section on the Manage Ratings page to filter just those ratings which contain bad words. Click the **Delete** button in each row to delete the rating.

Words must be entered one at a time, and \[Company Name\] looks for _exact_ matches. If 'pizza' was entered as a badword, a post with 'pizzas' would not be flagged. The entries are also not case-sensitive, so ABC is the same as abc.
      