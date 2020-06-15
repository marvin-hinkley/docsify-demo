
      ---
      title: Go Live Checklist
      ---

      **_Compunix, providing tools for your store’s successful “Go-Live”_**  
An important step in the “go-live” process is making sure your new store does not lose the search rankings your have established through your current store. Setting up [301 redirects](http://www.ecommercecartmods.com/p-36-301-url-redirect-for-aspdotnetstorefront.aspx) ensures you carry over search engine page rankings and helps customers find the right pages during site transfers. If you’re looking to transfer existing storefront pages this [URL redirect](http://www.ecommercecartmods.com/p-105-existing-pages-url-redirect-for-aspdotnetstorefront.aspx) will help.  
Below is a checklist of tasks that should be done before setting a site to 'go live'. These steps will increase security and performance, and also (in some cases) make your site appear more professional.   
  
**Properly Secure Your Site**   
Follow the directions in our [Security Best Practices guide](default.aspx?pageid=security_best_practices) to properly secure your site. These steps should ALL be performed before considering a site ready to go live. Ideally your 'Security Audit' section at the top of your admin page should be cleared.   
  
**Enable HTTP Compression**   
Optimize your bandwidth by GZipping static and dynamic content.  
  
**Add a P3P Privacy Policy & Compact Privacy Policy**   
Your sites' cookie can be blocked if your site doesn't have a P3P Privacy Policy. See [this blog](http://www.hanselman.com/blog/TheImportanceOfP3PAndACompactPrivacyPolicy.aspx) for more information.   
  
**Add an SSL Certificate**   
Customers look for the "closed lock" on your site when they want to checkout. A SSL Certificate is not only good business, for many Gateways it's required. The brand of certificate rarely matters anymore, so don't get talked into a $300/yr certificate when a $30 one will do the same thing.  
  
In order to use SSL on multiple site domains, a certificate that supports multiple domains is required, or multiple single site certificates. You will also need to create a new LiveServer appconfig for each store and set it to the appropriate domain.  
  
**Turn off Debug Mode**   
Edit your web.config file, and search for "debug". Make sure you set it to false (debug="false"). This will improve your website load times, and overall performance.   
  
**Rename Admin folder**   
"Admin" is easy to guess, so rename your Administration site. Then set the AdminDir AppConfig to the name of the new folder, so the store will know where to find it.   
  
**Lock-down your Administration site**   
Require a Windows Authenticated login for your admin folder. You can request this via your hosting company.   
  
**Re-compress product images**   
You can maximize your bandwidth, and even double your throughput by heavily compressing your product images.  
  
**Set-up redirects for non-www requests**   
If you want to make sure \*all\* requests go to your www-site instead of your non-www site, setup a redirect in IIS. [Here's how](http://www.webmasterworld.com/microsoft_asp_net/3412550.htm).   
  
**Review robots.txt**   
Make sure that you're not excessively-blocking search engine spiders. Consider the images folder... do you want your product images to be searchable? Have you added any custom pages that you don't want indexed?   
  
**Generate MachineKeys**   
Open the web.config file, and search for "MachineKey". Every site should have a unique set of validation and decryption keys. You can generate your own [here](http://www.developerfusion.com/tools/generatemachinekey/).  
  
**Set a memory limit for your AppPool**   
Here's a good [whitepaper](http://www.asp.net/learn/whitepapers/aspnet-and-iis6/) (somewhat dated, but still accurate) on how to configure the AppPool for your web application.   
  
**Remove unused files from the site**   
Any files that your site doesn't use should be removed for your site (don't delete the file, just move it off the site in case you need it later). After removing any file, be sure to test your site to ensure you didn't break any functionality. Here's a list of files that are often removed:

ajaxPricing.aspx   
ajaxShipping.aspx   
authnetpost.aspx   
bestsellers.aspx   
cardinalauth.aspx   
cardinalecheckauth.aspx   
cardinalecheckform.aspx   
cardinalechecknotify.aspx   
cardinalecheck\_process.aspx   
cardinalform.aspx   
cardinal\_process.aspx   
internationalcheckout.aspx   
lat\_account.aspx   
lat\_driver.aspx   
lat\_getlinking.aspx   
lat\_signin.aspx   
lat\_signout.aspx   
lat\_signup.aspx   
nxfeed.aspx   
ogone\_postsale.aspx   
ogone\_return.aspx   
paypalcancel.aspx   
paypalexpressok.aspx   
paypalnotification.aspx   
paypalok.aspx   
paypalok.aspx.cs   
recentadditions.aspx   
recentcomments.aspx   
requestcatalog.aspx   
scriptedrecurringimport.aspx   
searchnx.aspx   
secureauth.aspx   
secureauthhsbc.aspx   
secureform.aspx   
secureformhsbc.aspx   
secureprocess.aspx   
secureprocesshsbc.aspx   
sendform.aspx   
twocheckout\_return.aspx   
worldpayreturn.aspx

**Set a custom error page and enable custom errors**   
In the web.config file there is a "customErrors" element. When you are convinced that your site is working properly you should set customErrors to On and create a static .htm page to be shown to your customers when an error occurs on the site. This will A) prevent your customers from seeing an ugly .NET exception if an error does occur, and B) will prevent your site from disclosing potentially sensitive information about your hosting environment such as the database name (in the case of a SQL error) or disk path of your site.
      