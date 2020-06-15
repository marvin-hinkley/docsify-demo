
      ---
      title: Upgrading
      ---

      The current \[Company Name\] software version as of \[Current Version Release Date\] is: \[Current Version\]

Please don't ever upgrade straight onto your live store. Always use a staging environment to thoroughly test the success of your upgrade. You should also be sensible about timing - do not start an upgrade right before a major marketing push or at the height of your big sales season!  
  
Before beginning the upgrade, you should verify with your host that they are able to run your site under .NET 4.5 in IIS7 and that your database is running on SQL Server 2008 or higher. _Do not ask them to actually change the .NET version yet_, but you need to know that it's possible for them to quickly make that change for the final step of upgrading your site. If you find that your database is on an earlier version of SQL Server, it would be best to have that upgraded on the live site before continuing with the upgrade process.  
  
If your host is unable to meet either of those requirements, you will need to move your current site to another hosting environment before performing the upgrade. Our [in-house hosting](http://www.aspdotnetstorefront.com/t-hosting.aspx) may be just what you need!  
  
**Feature considerations:** In addition to the [9500 Release Notes](default.aspx#pageid=release_notes#removed-features "9500 Release Notes"), please read the [Release Notes (pre-9500)](http://manual.aspdotnetstorefront.com/c-143-release-notes.aspx "Release Notes (pre-9500)") for all versions between your existing version and 9500 as you may have customizations that have been addressed and are no longer needed, or a feature you currently use is no longer available "out of the box".  It is especially important to verify that the gateway you are using on your older site is still supported before performing the upgrade, as you'll need to start the processing of switching otherwise.

Outline of the upgrade
======================

You will:

*   Start with a clean installation of the latest version, connected to an upgraded backup of your live site's database.
*   Transfer your design elements, so that the new version looks familiar.
*   Upload the latest text that displays on the site.
*   Install the new license key.
*   Tidy up a few loose ends.
*   Test and learn all about the things that changed.
*   Consider how the new feature-set meets your business needs, and if there are any gaps you will compare the cost of building any custom code afresh on the new version against the cost of 'migrating' earlier custom changes.

Preparing for your upgrade
==========================

*   If you are using Full-Text Search on your site currently, log into the admin console and turn that off before doing anything else!
*   Before making any changes to your live site, always ensure that you have a full, working backup of both the contents of the site itself and the database!
*   If you were encrypting the web.config on the site previously, you will need to log into the admin site, go to the [Site Setup Wizard](default.aspx?pageid=site_setup_wizard), and change the **Encrypt Web.config** option to **No** before starting the upgrade, or those keys will be unreadable. See [this page](default.aspx?pageid=encryptkey) for more information, or if you run into any trouble making that change.
*   Be sure to read each step below carefully, even if you have done upgrades before, as there have been a lot of exciting changes in recent versions!

Start with a clean build
========================

1.  Contact your website host to request a backup of your live site files & database. Download both of these backups to the computer you will be performing the test upgrade on. For the rest of the document, this backup copy of your live site will be referred to as the **site backup**.
2.  Download the new software release from the [AspDotNetStorefront Software Downloads](http://license.aspdotnetstorefront.com/?tab=downloads) page in your license portal and run the file, which will extract the new files to your computer. For the rest of the document, this extracted copy of the new version will be referred to as the **new files**.
3.  Find the [Install Guide](default.aspx?pageid=installation) that matches the version of Windows you'll be installing the software on. Follow those directions for installing the files and 3rd party software, configuring IIS, etc. When you get to the database portion, instead of creating a new database you will restore the database backup provided by your hosting provider over an empty database created on your machine.
4.  If the AdminDir Setting has been changed on your live site (meaning you access your admin console at something other than yoursite.com/admin), rename the admin folder in the new files to match the name on your live site.

Connect to & Upgrade your Database
==================================

1.  Open the web.config file from the site backup you obtained from your host. Copy the EncryptKey value, and paste it into the matching key in the web.config file in your new files.
2.  Find the 'DBConn' line near the top of the new web.config, and update it to connect to the local database you made in section 1 above. Note that the format of this line changed between versions so you cannot simply copy & paste the old line into the new file.  The 'Initial Catalog', 'User Id', and 'Password' values may match those from the site backup's web.config file, but the 'Data Source' will almost certainly be different for your new install. The install guide you used when creating that database earlier can help you figure out what those values should be.
3.  Connect to your local database using SQL Server Management Studio (If you don't have SQL Server Management Studio, you can download the Express version from Microsoft [here](http://www.microsoft.com/downloads/details.aspx?FamilyId=C243A5AE-4BD1-4E3D-94B8-5A0F62BF7796&DisplayLang=en)).
4.  Right-click on the database you restored from a backup earlier, and choose Properties. Click on Options in the left nav, find the option labeled 'Compatibility level', make sure it's set on at least 'SQL Server 2005 (90)', and click OK. If you do not see an option higher than 'SQL Server 2000 (80)' you will need to contact your host and have them upgrade you to a more recent version of SQL Server before continuing with the upgrade
5.  Run the file called "Update 9.0 to Latest.sql" from the new files' /db folder against the database you restored earlier. When it completes, you should see a 'Query completed successfully' message at the bottom of the window. If you see 'Query completed with errors', scroll through the results and find any text in red. Copy that and submit a new\[Help Desk\]ticket to determine if the errors will be a problem.
6.  As an optional step, perform the [Performance Tuning](default.aspx?pageid=performance_tuning) process on the database you just upgraded, to verify that it will run successfully on your live site later. This step can take a very long time. If your upgrade is time-sensitive, skip this step for now and it can be done after the rest of the upgrade is completed (see section 8 below).

Running upgrade scripts requires some proficiency with Microsoft SQL. If you reach this step and you're not sure how to execute SQL scripts, you might benefit from letting AspDotNetStorefront help.  
[Learn More >>](http://licenseportal.aspdotnetstorefront.com/p-1039-expert-upgrade-service.aspx)

Copy in old Content and Install a License
=========================================

1.  Copy the contents of the /descriptions, /download, /images, /orderdownloads and /topics (if you have one) folders from the site backup into your new files. If prompted to overwrite a file, click yes.
2.  Delete the .licx file from the /images folder in the new files.
3.  Download a new license file from the Licenses tab of the [license portal](http://license.aspdotnetstorefront.com/?tab=licenses). To do this, click Manage Version on the license for the store you are upgrading and change the drop down to the version you are upgrading to. Click 'OK', then click the 'Retrieve License' link. The new license file will be saved to your computer.
4.  Copy the new license file you just downloaded into the new site's /images folder.

Skinning
========

At this point, you have a decision to make:

*   If you want to start with a fresh skin and take advantage of our new skins that are responsive 'out of the box', jump to the next section. Once the rest of the upgrade is done, you can use the information [here](default.aspx?pageid=skinning) to design your new skin.
*   If you want to reproduce your old skin and you're upgrading from an earlier 9x version, follow [these](default.aspx?pageid=upgrading_aspdotnetstorefront__skinning___special_considerations) directions and then come back here and continue with the next section.
*   If you want to reproduce your old skin and you're upgrading from a pre-9x version, follow [these](default.aspx?pageid=skin_conversion_guide) directions and then come back here and continue with the next section.

If you're not familiar with this kind of work, skinning can seem a little overwhelming. We have development partners standing by to help.  
[Find a Partner >>](http://www.aspdotnetstorefront.com/c-269-enterprise-partners.aspx)

Customizations
==============

If you have never had a developer do any customization to your site (aside from skinning), you can skip this section. Otherwise, this is the time to get those customizations put into the new files. Some things to keep in mind during this process are:

1.  Do you actually need the customization anymore? Perhaps your business requirements have changed, or we may even have added the feature to the 'out of the box' software!
2.  Is it cheaper to pay a developer to migrate the existing modification from your old site, or should you start over? Sometimes various things like problems getting your code from the old developer, updating the code to account for changes in the 'out of the box' software (when required), changes to your business requirements, etc can make it easier to just start from scratch.

If you're not an experienced developer, we have development partners standing by to help.  
[Find a Partner >>](http://www.aspdotnetstorefront.com/c-269-enterprise-partners.aspx)

Finishing Touches & Testing
===========================

1.  Open the upgraded site in a browser and verify that it starts and that the admin site is accessible.
2.  Log into the admin console and follow the "Reload from Excel file on Server" directions on [this page](default.aspx?pageid=prompts) to load the latest prompts on your site. Be sure to select "Leave my modified prompts" AND "Replace Existing". If you have multiple locales or are not using en-US, you may need to rename the new excel files in the /StringResources folder appropriately for your locale before reloading them, and also consider not selecting "Replace Existing" if your localized strings are not all considered "modified strings".
3.  If you are upgrading from a previous 9.x version and are using [Avalara](default.aspx?pageid=avalara), your tax class codes may need adjusting. Verify that the tax class codes under **Configuration > Tax Classes** are not blank and match the Tax Class Codes in your Avalara account. You can set that code to "FR" for tax classes you do not want Avalara to charge for.
4.  If your skin links to the sitemap, check that the link is correct. Previous versions had a sitemap page named 'sitemap2.aspx', and it is now called 'sitemap.aspx'. Have your developer update that link if necessary.
5.  Due to changes required by the upgrade to .NET 4.5, several email Settings that previously supported comma- or semicolon-delimited lists no longer allow that.  Check your MailMe\_ToAddress and GotOrderEmailTo AppConfigs, and ensure that they only contain a single email address.  If you need emails to go to multiple addresses, check with your email host about distribution groups or mail forwarding rules.
6.  [Thoroughly test](http://blog.aspdotnetstorefront.com/2011/05/test-thoroughly-or-test-patience/) your site, to ensure that all functions are working as they should be. Product pages, admin functions, credit card processing - everything should be checked just to be safe.

Deploying the Upgraded Site
===========================

Once the upgraded site is thoroughly tested and you are satisfied with the upgrade, you are ready to push it live! This can be a long process, and most likely will require some help from your host. Contact them first and verify that they are available and able to assist quickly during the time you're planning to push to the live site, and leave yourself plenty of time. Some of the steps below (especially database-related ones) you will not be able to do yourself in many hosting environments. In those cases, work with your host to get them done, but make sure they happen in the order listed here.

1.  Put your site in [maintenance mode](default.aspx?pageid=maintenance_mode__temporarily_disabling_the_site).
2.  Have your host back up your live site's files and database again, just to be safe.
3.  Verify that your live site's database Compatibility Level is set to at least 2005, as was done in step 3 of section 2 above.
4.  Connect to the live site database and run the "Update 9.0 to Latest.sql" from the new site's /db folder.
5.  Connect to your live site's files through an FTP client and delete all files in the root of your site (your host can help you figure out which folder that is if you're unsure). This step is important, do not simply overwrite the old files.
6.  Upload the new files from the site you set up to the folder you just emptied on your live site.
7.  Update the web.config file that you just uploaded to the live site, setting the DBConn values to the correct information to connect to your live database. Those values will likely be the same as what is in your old site backup's web.config, but your host can verify that.
8.  Have your host switch the site to run under .NET 4.5.
9.  Take your site out of maintenance mode and verify that it starts and looks correct.

Wrapping Up
===========

After everything on the upgraded site has been tested and verified to be working correctly, there are a few things to do before you should consider the upgrade complete:

1.  Go to **Configuration > Site Setup Wizard** and switch the **Encrypt the web.config** option to **Yes**, then click **Save**.
2.  Verify that all other [Security Best Practices](default.aspx?pageid=security_best_practices) are being followed.
3.  Perform the [Performance Tuning](default.aspx?pageid=performance_tuning) process on your site, preferably during "off hours".
4.  If you were using Full-Text Search on your site prior to the upgrade, turn it back on in the admin console.
      