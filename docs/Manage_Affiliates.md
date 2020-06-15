
      ---
      title: Manage Affiliates
      ---

      Affiliates are 3rd parties who refer customers to your site. The \[Company Name\] software can track those referrals so that store admins can determine what commission to pay them. Once a customer is assigned an affiliate ID (see below for how that can be done), every order they place is also tagged with that ID. You can create Affiliate accounts either manually through the admin (instructions below), or by having the Affiliate [complete a signup](#auto) on your storefront.

\[Company Name\] does not do any type of commission calculation, it only tracks and reports on affiliate referrals.

Manually add a new Affiliate
============================

To add a new affiliate, navigate to **Marketing > Manage Affiliates** in the admin console. Click **Add New** and complete the form fields. When finished, click **Save**.

Assigning an Affiliate ID to a Customer
=======================================

Customers can be assigned to an affiliate in 2 ways:   

**Through the Admin Site** 
---------------------------

To manually assign a customer to an affiliate, go to [Contacts > Manage Contacts](default.aspx?pageid=view_edit_contacts) in the admin console, find their account, then click on the customer's Name to edit.  
  
Within the customer's account details, choose the desired affiliate from the dropdown menu, then click **Save** to update the account.  
 ![](images/1415394114000.png) 

  

**Via Querystring** 
--------------------

  
Customers can also be assigned to an affiliate through the use of a querystring, which is the preferred way to do it. That will ensure that customers are automatically assigned an affiate ID when appropriate, to ensure that all orders are correctly tracked.   
  
To do this, the URL that an affiliate uses to refer customers to your site needs to be in this format:

http:/www.yourstore.com/default.aspx?affiliateID=#####

Replace the '#####' with the affiliate ID. To find the ID, simply look up the affiliate under **Marketing > Manage Affiliates** in the admin console, and look at the number to the left of their name.  
  
  ![](images/1415394282121.png)

### **

Automatic Affiliate Signup
==========================

**

If desired, store admins can allow affiliates to register on their site automatically, without having to go through the admin. To do this, they will need to go to the following URL, and fill out the form:

http://www.yourstore.com/lat\_signup.aspx

 ![](images/1415394469164.png)

  

After registration, new affiliates will be taken to http://www.yourstore.com/lat\_account.aspx and will see a page similar to this (note that it will differ according to your skin):  
  
 ![](images/1415395044153.png) 

  

From here, they can click the links to edit their account information or view the affiliate information you've set up for your site. That information is contained in the following topics, which can be edited at [Content > Manage Topics](default.aspx?pageid=topics) in the admin console:

*   affiliate 
*   affiliate\_teaser 
*   affiliate\_faq 
*   affiliate\_terms

And the file: \\App\_Templates\\Skin\_#\\affiliate\_linking.htm
      