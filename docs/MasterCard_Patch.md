
      ---
      title: MasterCard Patch
      ---

      MasterCard recently added the series-2 card numbers to their list of possible numbers issued to cardholders (2xxx-xxxx-xxxx-xxxx). The in-cart validation available in AspDotNetStorefront requires a patch in order to recognize this new card number format (AppConfig/Setting: ValidateCreditCardNumbers TRUE).

NOTE: The patch affects source code files so please check with your developer to determine if your site has ASPDNSFCore and/or GatewayAuthorizeNet modifications and requires the SOURCE patch, or if your site is eligible for the COMPILED web files.

NOTE: These instructions assume you are a subscriber to our [Gold YRB benefits](http://www.AspDotNetStorefront.com/p-1552.aspx) program. If you do not see the patch in your license portal 'Software Updates' tab (version 9.5.0.0), then please check your eligibility with our [ASPDNSF Help Desk](https://support.aspdotnetstorefront.com) . If you have onboarded to our [preFIX](http://www.aspdotnetstorefront.com/t-prefix.aspx) model, then you don’t need to take any action – your store is always-up-to-date.

### Installing the MasterCard Patch

COMPILED (sites with no ASPDNSFCore or GatewayAuthorizeNet source code modifications):

1.  Backup your site files. Please contact your site host if necessary.
2.  Verify with your developer that your site is eligible for the COMPILED patch version.
3.  Download the patch through your [AspDotNetStorefront License Portal](https://license.AspDotNetStorefront.com) 'Software Updates' tab ( 9.5.0.0 MasterCard Patch (compiled) ).
4.  Execute the installation file locally (double-click patch-mastercard-950-compiled.exe), selecting an empty folder location on your computer.
5.  Open the extracted Web folder and Rename the Admin folder to match your site Admin folder name if different.
6.  Select all 3 folders ({Admin}, bin, OPCControls) and copy them to your site root folder using FTP, overwriting the existing files.
7.  Access your site Admin and Refresh Store (button).

SOURCE (sites with ASPDNSFCore or GatewayAuthorizeNet source code modifications - this should only be done by a knowledgeable developer):

1.  Backup the site and source files. Please contact the site host and developer(s) if necessary.
2.  Verify that the site requires the SOURCE patch version.
3.  Download the patch through your [AspDotNetStorefront License Portal](https://license.aspdotnetstorefront.com/) 'Software Updates' tab ( 9.5.0.0 MasterCard Patch (source) ).
4.  Execute the installation file locally (double-click patch-mastercard-950-source.exe), selecting an empty folder location on your computer.
5.  Compare the ASPDNSFCore and ASPDNSFGatewayProcessors folder contents with the existing current site file source code and merge as needed.
6.  Compile the source code and copy/publish the DLLs (AspDotNetStorefrontCore.dll and GatewayAuthorizeNet.dll) to the site bin folder, overwriting the existing files.
7.  Open the extracted Web folder and Rename the Admin folder to match the site Admin folder name if different.
8.  Select the {Admin} and OPCControls folders, and copy them to the site root folder using FTP, overwriting the existing files.
9.  Access your site Admin and Refresh Store (button).

NOTE: Your javascript may be cached if you immediately attempt to test a series-2 card. Please refresh the checkout page cache in your browser using Ctrl+F5 if the test fails to pass validation.
      