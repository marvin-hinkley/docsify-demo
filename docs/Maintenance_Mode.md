
      ---
      title: Maintenance Mode
      ---

      Store owners may occasionally need to take their sites offline temporarily for maintenance, software upgrading, product updates, etc.  There are 2 ways of doing this:  

Down for Maintenance Page
-------------------------

This approach takes makes the site completely inaccessible - for customers and admins both - and shows them whatever HTML page the store owner designs. This approach is best for times when the site is undergoing technical changes or maintenance that may result in errors if it is touched in the meantime, like an upgrade.

1.  Create a "Site Down For Maintenance" page. The page must be in plain .htm file.
2.  Place the page you created in the web content folder (root).
3.  Go to the web.config file. Look for the following:
    *   SiteDownForMaintenance and change its value to true.
    *   SiteDownForMaintenancePage and change the value to the name of the page you have created.
4.  Save the file when you're done.

If you are getting a redirect loop or error on a valid file, then verify the site Application Pool in IIS is set for Classic Managed Pipeline Mode, as Integrated Mode can cause this issue.  

Disabling the Front End Only
----------------------------

This method shows customers only the contents of the Template.MaintenancePage topic.  The admin console is still accessible, and admins are able to browse the front-end of the site.  This approach is best for when making big content changes to the site, like getting ready for a big sale.  

1.  Edit the Template.MaintenancePage topic to display whatever content you want your customers to see during the maintenance.
2.  Set the 'DisplayMaintenancePage.Enable' setting to true.
3.  Click the 'Refresh Store' button at the top of the admin console.
      