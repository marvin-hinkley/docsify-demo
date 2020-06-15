
      ---
      title: License Keys
      ---

      Unlicensed Software Message
===========================

Every site needs to have a license key in place or the front-end of the site will be disabled so _only_ an 'unlicensed' nag message will display. The admin console will function while unlicensed, though the nag message will display there as well.

The licensing check is based on the URL that customers hit the site at. If a customer goes to www.someshop.com, the software will verify that the license file installed on the site is for www.someshop.com. If the URL displayed in the address bar doesn't match the URL in that license key (for example is www.someothershop.com, an IP address, etc) the 'unlicensed' message will be displayed.

Guidelines
==========

*   If you want your site to be accessible both with 'www' and without, make sure you enter 'www' in the key URL.
*   Sites can always be accessed at the IP address, however postbacks will trigger the 'Unlicensed Software' message. This will allow the site to be indexed or reached via IP for other reasons, but not used for checkout.
*   The **Unlicensed Software** message will _only_ display to requests that hit the site at an invalid address.

Development and Staging Licenses
================================

Licenses automatically enable stores running in a "localhost" environment, and stores running on staging "AspDotNetStorefront" subdomains (for example, http://staging.aspdotnetstorefront.mystore.com).

As long as the test URL is 'localhost' or has an 'aspdotnetstorefront' subdomain, you may have as many test sites as necessary, even if the test URLs vary. Simply copy the .licx file that you will generate below to each of the sites /images folders, per the directions below

Generating & Installing License Keys
====================================

1.  Log into [http://license.aspdotnetstorefront.com](http://license.aspdotnetstorefront.com) with the account that was used for your original purchase.
2.  On the Licenses tab, click on the GUID of the license you wish to manage, and a panel will expand showing you that license's details. Enter the domain(s) you want to generate a key for in the box(es) under Licensed Domains, and click the 'Set domain(s)' button. See the note about staging/testing sites above: you should only enter the live site's domain here, the key will automatically allow the site to run on valid test sites as explained above.
3.  Enter the domain name in all lowercase characters. UPPER CASE characters in the domain name cause the license to fail.
4.  Click **Retrieve License** to download the license to your computer. _Do not change the filename._
5.  The license file must be uploaded to the **{root}/images folder**. Be sure to keep the .licx extension intact.
6.  Verify that the .NET user account (typically ASPNET for WindowsXP or NETWORK SERVICE for Windows Server 2003/Vista or IIS\_IUSRS for Windows Server 2008/Windows7) has read access to the license file.
7.  Click “Refresh Store” in the upper right of the Admin Console.

Troubleshooting
===============

If you have followed all of the steps above and continue to see the unlicensed message, or see the unlicensed message again after the site has been running licensed for some time, check the following things:

*   First and foremost, verify that your site is _only_ being accessed at the domain(s) it is licensed for. IP addresses, domain aliases (that aren't licensed), etc should not be used. If necessary, most hosts are able to track how requests to your site are made, to help narrow down how your site is being accessed incorrectly.
*   Ensure that the user account your site is running under has the proper permissions to the **{root}/images** folder on your site, as described in step 6 above. Your host can verify this for you if you don't have access to do so.
*   Verify the Information in the **Configuration > About** page in the admin console.
*   Verify that you only have a single .licx file in the {root}/images folder on your site, of the correct license file retrieved from your license portal.
*   Ensure that the license file is named properly. This will be a 'random' sequence of letters/numbers (a GUID) assigned by the \[Company Name\] site when you download the license file - be sure to remove any file 'copy' numbers at the end of the name such as (1). If the file has been renamed, you can retrieve the file from our site to obtain it again with the proper name.
*   The END DATE when using a staging license URL (\*.aspdotnetstorefront.\*.com) has been removed from all license files retrieved since May 2014. If yours is showing as expired in the **Configuration > About** page of your admin console, please retrieve a new key from your [license portal](http://license.aspdotnetstorefront.com/) and replace the existing license key, which will remove the staging expiration.
*   Verify that the domain(s) entered in the license file are correct: Look for typos, additional spaces before or after the entry, and no UPPERCASE characters.
*   There are two license rules when validating licenses, but only one will be run at a time, depending on what URL is accessed. The staging license has a rule and the localhost/production licenses have a rule. If the site is accessed using staging, then the localhost and production URLs will show as invalid in the admin Domains tab and possibly show the unlicensed red banner on the storefront, and vice versa. If you are wanting to stage a site on a LIVE site, you will need to contact the [Help Desk](https://support.aspdotnetstorefront.com) to get your staging URL added to the production license so you can avoid this conflict.

If you are unable to determine the cause of the license failure, submit a full screen shot image of the admin console **Configuration > About** page (including the address bar showing the accessed URL) to our \[Help Desk\] for support.
      