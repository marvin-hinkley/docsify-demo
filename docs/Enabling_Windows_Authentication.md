
      ---
      title: Enabling Windows Authentication
      ---

      **Configuring IIS 7 to Force Authentication on the Admin Site**
===============================================================

This article describes how to use IIS authentication to further protect and secure your AspDotNetStorefront admin site. The concepts covered here require an understanding of Windows Security, and should be undertaken by a knowledgeable IT professional. Improperly configured security settings on a publicly facing server can potentially make the server vulnerable to attack or prevent legitimate users from accessing the system.

**Choosing between Windows Authentication and Basic Authentication**
====================================================================

IIS 7 providers administrators with the option of choose three settings for authenticating users.   
  
For the purpose of this article, we will cover the two applicable options.   
  
Windows Authentication in IIS 7 is the most secure option, as it uses hashing technology to prevent sending clear text usernames and passwords over the internet. Many web browsers do not support this however, so if your admin site is accessed by clients using browsers other than Microsoft Internet Explorer, Basic Authentication should be used instead.   
  
Basic Authentication can be used on admin sites that must be accessed by a wide range of browsers and devices. One important thing to keep in mind with Basic Authentication is that usernames and passwords are not hashed, so additional precautions should be taken to ensure that your credentials are safe. Sites using Basic Authentication should always use SSL when connecting to the admin site. This will ensure that credentials are encrypted in transit to and from the website.

**Disabling Anonymous Access to the Admin Site**
================================================

1.  Open the IIS Management Console on the web server
2.  Expand the Sites folder
3.  Expand your AspDotNetStorefront web site  
    ![](http://manual.aspdotnetstorefront.com/images/product/msx/IIS7_windows_auth_1.png)
4.  Select the Admin folder
5.  Double-Click the IIS - Authentication option
6.  Under Authentication, select the Anonymous Authentication and click 'Disable' in the Actions pane on the right
7.  For Windows Authentication: Select the Windows Authentication and click 'Enable' in the Actions pane on the right
8.  For Basic Authentication: Select the Basic Authentication and click 'Enable' in the Actions pane on the right  
    You can potentially enable both authentication mechanisms on the site. If both Basic and Windows Authentication are enabled, IIS will first try to use Windows Authentication, and then attempt Basic if that fails.   
      
    If using Basic Authentication, you will receive a warning stating that "...credentials will be sent in clear text over the wire". This warning does not apply to valid SSL connections.  
      
    With Windows Authentication you will get an Alert stating that "Challenge-based and login redirect-based authentication cannot be used simultaneously." but it can be ignored for sites using CLASSIC managed pipeline mode in the app pool.  
    For sites using Integrated mode, [THIS ARTICLE](http://mvolo.com/iis-70-twolevel-authentication-with-forms-authentication-and-windows-authentication/) may be useful (a knowledgeable developer will be required).  
    ![](http://manual.aspdotnetstorefront.com/images/product/msx/IIS7_windows_auth_2.png)
9.  If using Windows Authentication only, restart the site. If using Basic Authentication, select Basic Authentication and click "Edit..." in the Actions menu to the right, and enter your site domain (Realm is optional), then click OK  
    ![](http://manual.aspdotnetstorefront.com/images/product/msx/IIS7_basic_auth_domain.png)
10.  If requiring HTTPS for the admin console, double-click the IIS - SSL Settings for the Admin folder, and check the "Require SSL". NOTE that SSL must be in place and valid for this option to be available  
    ![](http://manual.aspdotnetstorefront.com/images/product/msx/IIS7_ssl_require.png)
11.  Restart the site

**Giving Users Access to the Admin Site**
=========================================

Once Basic or Windows Authentication is enabled on your admin site, user access to the entire directory is controlled using NTFS permissions. To assign a user permission to access your admin site:   
  

1.  Create a new user account in Windows using Computer Management (or Active Directory Users and Computers if your server is a member of an Active Directory domain).
2.  Using Windows Explorer, browse to the directory that contains your AspDotNetStorefront web site files.
3.  Right click the Admin folder and choose Properties.
4.  Click the Security tab and click Add.
5.  Enter the name of the user you just created and click OK, or click advanced to view a list of all users you can add.
6.  Assign the user Read, List, and Read & Execute permissions to the admin site.  
    ![](http://manual.aspdotnetstorefront.com/images/product/ml8/enabling_windows_authentication.jpg)
7.  7\. Click OK.

**Testing Authentication**
==========================

1.  Go to http://yoursite/admin or https://yoursite/admin (depending on whether SSL is required or not).
2.  2\. If all steps were done properly, you will be presented with a login prompt.  
    ![](http://manual.aspdotnetstorefront.com/images/product/msx/iis7_login.png)
3.  Enter your Windows user account username and password and click OK.
4.  You should now be taken to your Admin site’s login page.

**About this Article**
======================

This article is provided as-is for the convenience of our customers. \[Company Name\] does not perform general IT consulting tasks or management of dedicated servers. If you need assistance configuring user accounts or security on your server, please contact your hosting provider, IT department, or a qualified consultant. \[Company Name\] support cannot assist with these tasks.
      