
      ---
      title: General Information
      ---

      Security Considerations
=======================

Theoretically, the WSI interface allows complete access to your store database, which may include sensitive data. Adherence to proper security practices defined here are mandatory for proper deployment and usage.

*   Turn off all protocols except SOAP
*   You should use Microsoft Web Services Enhancements 3.0 for Username Token authenticated connections to the WSI web service. WSE3 must be installed on the client and server sides. Your client calling the WSI must also then properly create an authenticated request
*   If you are NOT using WSI on your site, do NOT deploy the WSI files to your site. There simply is no point to having them there if you are not using them.
*   Make sure you are running the web service over HTTPS protocol in a production environment. Running over HTTP is ok in dev/test setup, but you must use SSL encryption for production data transfers.

When using WSE3 Authenticated invocation of WSI from your client program, you must use the Admin Email and HASHED Password from the master \[Company Name\] database! You cannot put the password in clear text in the client. It must be the hashed raw value from the storefront database! If you are using the NON WSE3 invocation, you use the clear text password for the admin user.

Performance Notes
=================

WSI is not really designed to import massive amounts of products, entities, or customers in a single 'pass'. While this import option can handle more at once than the standard Excel product import, we still recommend that imports be done & reviewed incrementally, and that transactions be used.

See [this page](default.aspx?pageid=transaction) for more information on Transaction nodes.

Excel Bulk Import Tool
======================

The [Excel import tool](default.aspx?pageid=import_export) is actually running through WSI. While the Excel tool will continue to function, we _highly_recommend that store owners switch to using the WSI feature instead. Though more complicated to set up, it is far more flexible, can import every field rather than the limited data set supported by the Excel import, and supports larger imports.

Caching
=======

WSI processes and imports XML nodes at the data level, bypassing the 'application layer' of \[Company Name\], including the cache. Because of this, if front-end caching is enabled on your store, products & entities imported through WSI may not be reflected immediately on the front end. You can either way for the cache to update (determined by the CacheDurationMinutes AppConfig), or restart the site to force an update.

There is also a ResetCache processing node element in the WSI that you can include in your Xml import document that can also do this automatically. Do not execute that action too often via WSI however, or it may negatively affect your store performance by clearing the cache too frequently.

Troubleshooting
===============

**System.Web.Services.Protocols.SoapHeaderException: SOAP header Security was not understood...**   
This means that you have not followed all of the installation steps to properly enable your web site to use WSE3. Verify that you have added the web.config elements, that WSE3 is installed on the server, and that you have all the proper WSI class files on your web site.

**Invalid security header on WSI calls**   
This means that you are not using time synchronization (a Windows function) on your client and web site servers. Time sync MUST be used on both machines, or SOAP calls will not work. Please see your host or IT manager for assistance with enabling time sync.
      