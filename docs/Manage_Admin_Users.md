
      ---
      title: Manage Admin Users
      ---

      The software comes preloaded with one default administrator account:  
  
**Email: admin@aspdotnetstorefront.com  
Password: Admin$11**  
  
Store administrators are recommended to change those credentials as soon as possible, to valid email addresses and personalized passwords. In many cases, it will also be necessary to create/remove additional admin accounts.

Adding an Admin Account
=======================

1.  Admin accounts are basically customer accounts that have been promoted to have special access. If the account you want to use as a new admin has not already been created, do so first. This can be done by registering an account through the front end exactly as a customer work, or by creating the account through the admin console at **Contacts > Create Contact**.  
      
    
2.  Once the account is created, look it up in the admin console under **Contacts > Manage Contacts**. Click the **Name** to edit the contact.  
     ![](images/1415979247802.png)  
      
    
3.  At the bottom of the Edit Contact page, within the Tools section, click either the **Set Admin** or **Set Super Admin** button to promote the customer to an admin account. Super admins have access to do everything in the admin site. Regular admin accounts are restricted from changing certain [Settings](default.aspx?pageid=settings) and from promoting/demoting other admin users.  
     ![](images/1415979340963.png)

*   The regular Admin limitations are:  
      
    CANNOT access:  
    \- Configuration - Settings that are "super admin only"  
    \- Security Log  
    \- Change Encrypt Key  
    \- Run SQL  
    \- Setup Email  
    \- Site Setup Wizard / Payment Methods  
    \- Setting user permissions
  
Also when storing credit card numbers (StoreCCInDB TRUE) the regular Admin can be set to allow or disallow viewing credit card numbers

Removing an Admin Account
=========================

To demote an admin account back to a regular customer account, look up the account in the admin console under [](http://manual.aspdotnetstorefront.com/p-1044-viewedit-customers-and-users.aspx)**Contacts > Manage Contacts** and click the **Set Standard User** button.
      