
      ---
      title: Security Best Practices
      ---

      The AspDotNetStorefront software is Visa PA-DSS Certified and has been through several 3rd-party security audits, and live sites running our software pass daily scans by 3rd-party tools like [McAfee Hackersafe](http://www.hackersafe.eu/) and [ControlScan](https://www.controlscan.com/index.php). While we constantly work to make the software as secure as possible, there are extra steps that site administrators should take to protect their data:

*   Rename the /admin folder to something unique to your site so it cannot be easily guessed. To do this:
    *   Log into your admin site, and change the AdminDir [Setting](default.aspx?pageid=settings) to whatever you intend to name the folder. 
    *   Log out of the admin site, connect to your site through FTP, and rename the /admin folder to what you set in the AdminDir Setting. 
    *   Restart the site
*   Use IIS Integrated Authentication on your admin folder. You can request this via your hosting company (be sure it is only done on the admin folder), and there are directions for doing this on dedicated servers [here](default.aspx?pageid=enabling_windows_authentication).
*   Verify that the Anonymous.PersistCookie Setting is set to false. When set to false, that setting will clear all customer session data (login status, payment info, etc) when the browser is closed. This is _highly_ recommended for PCI compliance.
*   Use CAPTCHA images on your admin site. These can be enabled in the SECURITY Setting Config Group on your site, and can help prevent scripted attacks against your website.
*   Make sure that your web settings do not allow directory browsing or direct file retrieval! This should be standard security procedure for your host, but verify with them that the anonymous Internet user account does not have rights to browse files on the site.
*   Remove extraneous files that are not used by the software, such as .psd files, .sln files, .csproj or .vbproj files, etc. This operates on the same principle as turning off or removing unnecessary Windows services on servers to shrink the total attack surface, making your website more secure.
*   Be sure not to upload any of the folders that the original download may contain that are not necessary for the running of the site. Only the contents of the /web folder are needed on the production server. Source folders (ASPDNSFCore, ASPDNSFGateways, etc), the /db folder, and others do not need to be on the live site. Experienced developers can also precompile the application for deployment using Visual Studio or command line tools, which can help prevent unauthorized modifications to your production site, and also improves application start time on the first page load.
*   Create a custom error page and set <customErrors mode="RemoteOnly" defaultRedirect="MyErrorPage.htm"> in your web.config files, except during debug sessions. This not only prevents exposure of sensitive pathing and database schema information, but also prevents customers from seeing ugly exception messages if a legitimate customer does somehow encounter an error. The custom error page should be a plain HTML file, and can contain whatever verbiage and styling you want users to see in the chance event that your site has a problem.
*   Use [SSL](default.aspx?pageid=ssl). While it is possible to run a site without an SSL certificate installed (depending on the gateway), we **HIGHLY** recommend against it. SSL Certificates are no longer expensive, and most hosting providers resell them at a discount to their customers. Internet shoppers are savvy about security, and know to look for the "lock" on their browser telling them the site is secure. Not using SSL is dangerous, against payment card industry regulations, and shows your customers that you aren't concerned about their security.
*   Review your [credit card storing](default.aspx?pageid=storing_credit_card_information) policies. It is very rare to have to store CC information anymore, and it is **HIGHLY** recommended that you do not.
*   Consider signing up for one of the 3rd-party tools like [McAfee Hackersafe](http://www.hackersafe.eu/) or [ControlScan](https://www.controlscan.com/index.php). These services can scan your site daily to ensure that there are no known vulnerabilities not only in your AspDotNetStorefront software, but also in other server components and firewall configurations as well.
*   Stay up to date with your software. This not only includes AspDotNetStorefront, but also third party components and operating system patches as well.
*   Set permissions properly on your website. It is important to understand the difference between the Anonymous Internet User Account and the ASP.NET Process account
*   The ASP.NET Process account is a service account used by the web server to execute ASP.NET applications. This is the account that your AspDotNetStorefront website runs as. This account requires:
    *   Read permissions on the entire site.
    *   Write/Modify permissions to the root images folder
    *   Write permissions on the OrderDownloads folder
    *   Temporary Write/Modify permissions on the root folder for the web.config file only while encrypting/decrypting the web.config. Otherwise, Write permissions on the root folder should be disabled (set as Read only).
    *   The Anonymous Internet User Account is used by IIS to display and execute static HTML files, images, scripts, and legacy web applications (such as classic ASP). This account requires...
    *   Read access to the site for the purpose of displaying images, CSS, Javascript, and static HTML files.
    *   This account requires NO Write permissions on your site. Write permissions for the Anonymous Internet User account should be disabled if possible.
*   Remove unused site files. These files will have to be determined on a site-by-site basis based on the features being used.  
    Some commonly-removed files are:  
    \* ajaxPricing.aspx   
    \* ajaxShipping.aspx  
    \* auctioncheckout.aspx  
    \* authnetpost.aspx  
    \* bestsellers.aspx  
    \* cardinalauth.aspx  
    \* cardinalecheckauth.aspx  
    \* cardinalecheckform.aspx  
    \* cardinalechecknotify.aspx  
    \* cardinalecheck\_process.aspx  
    \* cardinalform.aspx  
    \* cardinal\_process.aspx  
    \* internationalcheckout.aspx  
    \* lat\_account.aspx  
    \* lat\_driver.aspx  
    \* lat\_getlinking.aspx  
    \* lat\_signin.aspx  
    \* lat\_signout.aspx  
    \* lat\_signup.aspx  
    \* nxfeed.aspx  
    \* ogone\_postsale.aspx  
    \* ogone\_return.aspx  
    \* paypalcancel.aspx  
    \* paypalexpressok.aspx  
    \* paypalnotification.aspx  
    \* paypalok.aspx  
    \* paypalok.aspx.cs  
    \* recentadditions.aspx  
    \* recentcomments.aspx  
    \* requestcatalog.aspx  
    \* scriptedrecurringimport.aspx  
    \* searchnx.aspx  
    \* secureauth.aspx  
    \* secureauthhsbc.aspx  
    \* secureform.aspx  
    \* secureformhsbc.aspx  
    \* secureprocess.aspx  
    \* secureprocesshsbc.aspx  
    \* sendform.aspx  
    \* twocheckout\_return.aspx  
    \* worldpayreturn.aspx

It is the store owner's responsibility to ensure that these and other security precautions are taken. All sites should have documented and enforced password policies, apply Windows security patches as needed, maintain physical security of the server, etc. All sites need to begin pursuing PCI compliance as well, as merchant gateways are constantly becoming more strict in their regulations. Companies like [Coalfire Systems](http://www.coalfire.com/) can assist with this.
      