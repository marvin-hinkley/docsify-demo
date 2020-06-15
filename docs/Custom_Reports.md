
      ---
      title: Custom Reports
      ---

      From the admin console, click **Reports** in the left navigation.  
  
If the built-in reports don't meet the needs of your site, the store administrator can create custom reports and run them through this page. The reports are simply SQL commands stored in the database, which can be run at any time. The Custom Reports/Reports page is simply the display page for reports created using the method below or built-in reports, and contains no additional means to create, modify or format the reports.

### **

Adding a Custom Report
======================

**

First you'll need to add your custom report to the database through a SQL query.   
  
Values to be used:

*   Name: Name of your custom report 
*   Description: Description of your custom report 
*   SQL Command: SQL query to call/populate your SQL report

For beginners with SQL consult w3schools [Introduction to SQL](http://www.w3schools.com/sql/sql_intro.asp)

**Sample Query**
----------------

`INSERT` `INTO` `CustomReport (``Name``, Description, SQLCommand)`

`VALUES` `(``'Test Report'``,` `'Test Description of our report'``,` `'SELECT Email, BillingZip FROM ORDERS'``)`

You can use the Configuration > Run SQL tool in the admin console to submit your customer report to the database. Once you've submitted your query to the database it's time to test your custom report. In the admin console, go to the Reports page, choose your custom report from the drop down list, then click Get Report. If there are no errors in your SQL statement or the SQL Command you're using to generate your custom report, your results should appear in a data grid on the right. If there are errors, they should appear onscreen right away. You may also want to choose View System Log from the Configuration menu to track down any custom report issues.    
  
Once the report has run, you can click to **Save Excel Export**.
      