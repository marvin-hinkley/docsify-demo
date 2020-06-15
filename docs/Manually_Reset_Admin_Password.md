
      ---
      title: Manually Reset Admin Password
      ---

      In the event that you lose your super admin user password and are unable to recover it via email, the password can be manually reset in the database.
=====================================================================================================================================================

Using these methods to reset passwords may violate VISA PA-DSS guidelines, and should only be used if there is no other alternative. On sites with properly configured Email settings, admins may recover a lost password simply by using the [Forgot Your Password](default.aspx?pageid=forgot_password_reset_procedure) function on the admin signin page.

If you are getting looped back to the admin signin page with no error, refer to [this](default.aspx?pageid=admin_login_troubleshooting) article.  
  

Always ensure that you have a recent backup of the database before making any adhoc changes. Enlist the assistance of your website server host if necessary.  
  

Procedure - Option 1
====================

It is strongly recommended to setup more than one Super Admin account for a store, so you have a quick backup if you lose access to the admin.  
  

1.  Access the storefront anonymously and create a new customer account using information you have access to.  
      
    
2.  Connect to your database using SQL Server Management Studio, Enterprise Manager, or your web-based query tool. Enlist the assistance of your website server host if necessary.  
      
    
3.  In a new query window, issue the following SQL statement:  
    
    `UPDATE` `Customer`
    
    `SET` `IsAdmin=``'3'`
    
    `WHERE` `Email=``'your new super admin email address here'`
    
4.  Access the admin console using the newly created super admin account.  
      
    
5.  Access the previous super admin account in the **Contacts >  Manage Contacts** page, and edit the access as needed.

Procedure - Option 2
====================

1.  Connect to your database using SQL Server Management Studio, Enterprise Manager, or your web-based query tool. Enlist the assistance of your website server host if necessary.  
      
    
2.  In a new query window, issue the following SQL statement:  
      
    
    `UPDATE` `[Customer]`
    
     `SET` `[``Password``] =` `'your new password here'``,`
    
     `[SaltKey] = -1,`
    
     `[LockedUntil] = DateAdd(mi, -1, GetDate()),`
    
     `[BadLoginCount] = 0,`
    
     `[PwdChangeRequired] = 0,`
    
     `[PwdChanged] = GetDate()`
    
     `WHERE` `Email=``'your admin email address here'`
    
3.  Execute the query.  It should return: (1 row(s) affected)      
      
    
4.  In order for the password to be usable, it must be re-encrypted.  Do this by forcing the site to restart, either through IIS or by "touching" the web.config file.
      