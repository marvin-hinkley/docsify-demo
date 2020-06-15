
      ---
      title: Admin Login Troubleshooting
      ---

      Symptoms
========

When trying to log into the admin site, the user is continually returned to the admin login screen without any error message.  The account is not locked and the database is not showing bad logins for that user.

Cause
=====

This can be caused by 2 things:  Time synch problems between the web server and DB server, or having Role Management enabled in IIS.

Solution
========

Time Synchronization
--------------------

If the website and SQL database are installed on separate servers, the clocks MUST be reasonably in synch and the servers must be set to the same time zone.  AspDotNetStorefront uses the SQL GetDate() function to set the last activity time for admin users.  If your web server is out of synch with the DB server, there is a possibility that the last activity will fall outside of the admin session timeout limits, at which point the admin will be logged out immediately.  
  
**Explanation for necessity of time synch:** On every page load in the admin, the site checks how long it’s been since the last activity (page load, button submit, etc). If that’s been longer than the number of minutes set in the SessionTimeoutInMinutes AppConfig, then the session has expired and the admin is immediately logged out.  
  
If when logging into the site, the fileserver time and database server time are further apart than that timeout period, when the admin home page tries to load it will appear as though the session timeout has already expired and the admin is immediately logged out.

To verify this is the issue, use the following steps:  

1.  Download the TimeCheck.zip file from [here  
    ](http://www.aspdotnetstorefront.com/download/timecheck.zip)
2.  Extract the timecheck.aspx file and upload it to the root of your site
3.  Attempt to log in to your admin site
4.  Immediately afterwards, go to www.yoursite.com/timecheck.aspx and make note of the time returned.  This is the current time on your web server
5.  Connect to your SQL DB using Microsoft's SQL Management Studio, Enterprise Manager, or your host's SQL query tool.
6.  Run the following query:  
    
    `SELECT` `cs.LastActivity`
    
     `FROM` `CustomerSession cs`
    
     `JOIN` `Customer c` `ON` `cs.CustomerID = c.CustomerID`
    
     `WHERE` `c.Email =` `'Your admin user account'`
    
7.  Compare the last activity time with the time reported in step 4.  These times should match almost exactly.  If the difference between the two is greater than the amount specified in the **SessionTimeoutInMinutes** Setting you are likely to experience the problem described in this article.  To resolve this issue, synchronize your server clocks, or set a higher value in that Setting.

Role Management
---------------

In previous versions of the software, attempting to enable role management on the ASPDNSF site (or a parent site) in IIS could cause this behavior (or the site may exhibit a "Server Error in '/' Application" Object reference error).  Ensure that role management has not been enabled by doing the following.

**IIS 6**:

1.  Open IIS Manager
2.  Right-click the website in the left tree and go to Properties
3.  Go to the ASP.NET tab
4.  Click Edit Configuration
5.  Go to the Authentication tab
6.  Ensure the Membership Provider Class is AspNetSqlMembershipProvider
7.  Ensure that Role Management Enabled is UNCHECKED
8.  Apply any changes and restart IIS

**IIS 7+**:

1.  Open IIS Manager
2.  Select / Left-click the website in the left tree
3.  Double-click the .NET Roles icon in the Features View window (in the ASP.NET section)
4.  Select / Left-click the Disable link in the Actions pane on the right side
5.  "Are you sure you want to disable roles?" YES
      