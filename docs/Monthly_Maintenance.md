
      ---
      title: Monthly Maintenance
      ---

      From the **Configuration** menu, click **Monthly Maintenance**.   
  
From this page, store admins can run periodic maintenance which is necessary for keeping the store running smoothly and quickly. For the first 5 tasks, store admins can choose whether to do that maintenance for all records, no records, or only records older than 30/60/90/120/150/180 days old. Multiple actions can be performed at once. This should be done during off-peak hours, as various parts of the database may be temporarily locked during maintenance, preventing customers from using the site normally.

These tasks can take a while to complete. Once you click **Go** to start the process, do not interact with the admin site until you see the completed message. All currently logged-in admin users will be logged out.  
  
   ![](images/1421176144734.png)

**Option Name**

**Description**

Clear Shopping Carts

This will clear the contents of any saved customer shopping carts older than the age selected. If you have changed prices on your store or discontinued items, you may wish to do this to ensure that customers do not check out with products/prices they should not get because they added them before they change.

Clear Wish Lists

This will clear the contents of any saved customer wish lists older than the age selected. If you have changed prices on your store or discontinued items, you may wish to do this to ensure that customers do not check out with products/prices they should not get because they added them before they change.

Erase Credit Cards/eCheck from Order Records

This option will remove the (encrypted) CC information from order records older than the date selected. This information is generally not required after the initial purchase is made, so storing it presents an unnecessary risk.

Clear Profiles

This option clears the customer Profile which stores the cookie data and site settings for customers. Although it is generally safe to delete all Profile data, it is best to retain the last 30 days.

Clear Product Views

This option clears the customer product views, which are saved for uses such as [dynamic related products](default.aspx?pageid=related_products).

Clear RT Shipping Request/Response

This option clears the RTShippingRequests and RTShippingResponses stored in the database. 

Clear Search Logs 

If activated, all search logs older than the period you specify will be removed from the database. 

Purge Anon Customers

This will clear the records of anonymous customers - customers who performed an action on your site that caused a temporary record to be created for them (added to the cart, chose a locale, etc) but never registered or checked out. These records are not necessary and clearing them will not hurt the store.

Erase Credit Card/eCheck info from Address records

If your site is storing credit card numbers, customers who have allowed their information to be stored will have their credit card info in their Address records, completely separate from any orders they've placed. This option will clear that information out of your database.

Purge all records that are marked as Deleted

Many of the **Delete** buttons in the store admin site do not actually permanently remove the selected object (products, customers, etc). Those things are just marked as deleted in the database, and no longer appear in the admin site. This is so that they can be recovered in the future if necessary. If you wish to permanently remove those records, this option will do so.

Tune Indexes

This option performs basic maintenance on your database, which can increase site performance.

Clear old Localization Data

If checked, data for locales that no longer exist will be removed from the LocalizedObjectName database table. Note that this only affects localization data used for the product and entity grids in the admin console.

Save Settings

This option saves your selections on this page, so that you can quickly perform the same tasks next time maintenance needs to be run.

If your database is too large for Monthly Maintenance to be run from within the admin console (times out or throws error), you will need to run the stored procedure directly on the database (requires database access - check with your server host):  

1.  Access the database using SQL Server Management Studio or other valid means
2.  Go to **Programmability > Stored Procedures**
3.  Right-click on **aspdnsf\_MonthlyMaintenance** and choose **Execute Stored Procedure**
4.  Use a value of 1 for YES, or 0 for NO for the tinyint items
5.  Use the number of days (such as 30) for the smallint items for the number of days back to retain (A value of -1 will "Clear All Regardless of Age", and a value of 0 will produce no change.)
6.  Click **OK** and wait for the process to complete.
      