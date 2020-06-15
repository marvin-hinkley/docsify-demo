
      ---
      title: Authentication
      ---

      There are 2 methods to securely submit XML to the web service through the /ipx.asmx page:

**DoItUsernamePwd** \- Admin email address & password are provided in clear text. This is the preferred method, provided that an SSL certificate is in place and the web service call is made over HTTPS.

**DoItWSE3** \- This method requires that the admin password be the hashed value extracted directly from the storefront database. While slightly more secure than DoItUsernamePwd, it does require that [WSE3](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=018a09fd-3a74-43c5-8ec1-8d789091255d) be installed on the server.

WSE3
====

Since the development of WSI, Microsoft has dropped support for the WSE addon, and is no longer doing new development on it. This has lead to some problems with newer versions of Visual Studio that do not natively support the older WSE product. There are solutions available online to allow VS 2010 to work with WSE 3.0, allowing developers to create applications that connect securely to the WSI service, however for the most part, the WSE3 authentication is not necessary. If an SSL certificate is in place and all calls to WSI are made over HTTPS, submissions/responses will be secured. **If you decide to rely on SSL for securing WSI requests** and bypass WSE3, it is not necessary to uncomment web.config references to WSE3 as explained in the [install guide](default.aspx?pageid=installation1). If that's already been done, it is safe to re-comment those sections to disable WSE3.

WSE has a known issue that Microsoft never corrected which can lead to authentication failures even when using valid credentials, if hashed passwords are being used. The issue revolves around special characters that hashed passwords in SQL contain which the WSE addon cannot handle. Developers can work around this by using plain text passwords (not recommended), or by simply resetting the admin password being used for WSI authentication. It can take several attempts, but eventually a hashed password that does not contain an invalid character will be created and authentication will succeed.
      