
      ---
      title: Upgrading a Customized Store
      ---

      This page would welcome a sponsor from the \[Company Name\] community.

  

This guide is not a step by step guide specific to each version. For a step-by-step guide, [click here.](default.aspx?pageid=upgrading) This is a guide for developers, on the most common tools and practices for performing professional upgrades with customizations.

With proper planning and attention to detail, an upgrade with even a large amount of source code modifications can go smoothly. This guide is broken down into 4 phases:

1.  The Assessment Phase
2.  The Planning Phase
3.  The Local Upgrade Phase
4.  The Deployment Phase

The more unknowns you can hash out during the assessment phase, the less chance there will be for surprises when you deploy. If you plan courses of action for how to handle each customization, you can more accurately estimate how long the local upgrade will take. If you keep your local upgrade separate from the live site deployment, you can deal with issues before they have a chance to disrupt the live site.

Preparing for an Upgrade - The Assessment Phase
-----------------------------------------------

### The Assessment

Before performing an upgrade, you should do an upgrade assessment. Even if whoever handed you the upgrade swears up and down that it's version nine-dot-whatever and there has never been a source code modification. Sometimes this person will be wrong, and if you have an estimate tied to the upgrade, that will also become wrong.

There are 4 things that an upgrade assessment will tell you, in order to prepare you for the task.

*   The version of the AspDotNetStorefront database
*   The version of the AspDotNetStorefront code that you are upgrading from(don't assume this from the database, there are some sites out there in the wild that a rogue developer may have incorrectly upgraded)
*   A complete list of modified files that will need featured identified, to decide whether or not they should be merged or abandoned.
*   A complete list of schema changes

To begin the assessment, you will need:

*   A fresh backup of the database.
*   An out-of-box copy of the version of AspDotNetStorefront that you are upgrading from (include source if source is owned).
*   An out-of-box copy of the version of AspDotNetStorefront that you are upgrading to (include source if source is owned).
*   The latest copy of all site files. If source control is owned, you will need this.
*   A file comparison tool. [Beyond Compare](http://www.scootersoftware.com/) is highly recommended, and is a great investment not just for upgrades, but for deploying custom development changes to production.
*   A schema comparison tool. In Visual Studio 2012, go to the menu SQL-->Schema Compare-->New Schema Comparison.

Start the assessment:

1.  Bring up a diff of the files (including source if applicable) between the customized code and the out-of-box code of the same version.
2.  Bring up a diff of the out-of-box code of the version you are upgrading from and the latest version of the code. (You'll need this to make judgement calls on how complex it will be to merge a feature into the new version). Alternatively, if you have the ability to do a three way diff, when you are looking at a specific file, you can bring the file up in all three versions of the code (oob version upgrading from, oob customized version, oob version upgrading to).
3.  Generate a report, leaving out the files that match.
4.  Bring up a diff of the schema.
5.  Document modifications, and custom controls, pages and xml packages separate from the report.

You can often analyze a set of changes to group it into a single feature in your documentation. For example "Custom Business ID field: AspDotNetStorefrontCore/Customer.cs, account.aspx, account.aspx.cs, createaccount.aspx, createaccount.aspx.cs." Usually if there is a schema modification, it is tied to a specific feature, and you can list it there. However, sometimes you will find schema modifications that have survived a feature that no longer exists, and you should still document it.

Your diff report and your documentation should paint a picture of all of the site customizations and their magnitude.

The Planning Phase
------------------

### Translating the Assessment Into a Plan

With each customization found in the assessment, there will need to be some questions asked:

*   Is this customization still being used? Was the ROI worth it, and is it still worth it enough to merge?
*   Was the customization a bug fix or a patch? Is this now resolved in the version being upgraded to?
*   Is this a feature that was implemented in an outdated framework, or that could be replaced by something newer, better, or more efficient? In some cases, you will find that migrating a feature into a new version will be more time consuming than re-writing it.

Once you ask these questions of every customization you find, you can offer up options or recommendations. Here are some made up examples:

*   The Custom Business ID Field: Integral to the website, required for B2B Customers, must be merged. Based on assessment, merge will be simple.
*   Custom Ratings Feature: Built with the MooTools JavaScript framework in 2007. Ratings not very widely used on the site, and more often the administrator has to deal with spam. The feature is currently causing javascript errors in newer IE browsers. Latest version of AspDotNetStorefront uses jQuery, and although it is aliased and MooTools could be ported over, using one framework is ideal. We have four options:
    1.  Migrate the custom ratings feature and upgrade it to the latest version of MooTools to see if the JavaScript Error can be resolved.
    2.  Completely abandon the feature. Turn on the OOB ratings. The custom ratings feature is utilizing out-of-box schema, so the existing customer ratings won't be lost.
    3.  Abandon the feature. Integrate with a third party ratings tool, like PowerReviews, in a later development phase.
    4.  Abandon the feature. Rewrite the feature with a better user experience in the jQuery framework.
*   A one line fix to a problem with the PayPal Payment Gateway: Although the code is different, this has been fixed in the latest version. Recommend not merging this code.

At this point you can probably see that if the assessment were skipped, the planning phase would either be non existent or willy-nilly.

If the planning phase is skipped, then the developer has to stop mid-upgrade when they happen upon a feature that needs a decision made by the merchant. Or worse, they make the decision for the merchant, and then tell the merchant out of the blue that their upgrade is going to cost more, because of x, y and z.

Once a decision has been made on features that have multiple options, you will end up with a proper spec for the upgrade. The developer knows what to expect, and the whoever is paying for the upgrade knows what to expect. Now people don't have to run around with their hair on fire, apologizing and panicking.

The Local Upgrade Phase
-----------------------

You should perform the first upgrade locally, in a development environment. When you upgrade locally, you will do all of the merging of code customizations, and deal with any errors in the upgrade script. You did the assessment and planning phase already, so you know exactly what you are going to do.

To begin the assessment, you will need:

*   A fresh backup of the database. Keep this around, just in case you need do-overs.
*   A database that you can restore the backup of the production site to, and access locally for both running the site locally and accessing via SQL Server Management Studio
*   SQL Server Management Studio
*   Visual Studio
*   An out-of-box copy of the version of AspDotNetStorefront that you are upgrading from (include source if source is owned).
*   An out-of-box copy of the version of AspDotNetStorefront that you are upgrading to (include source if source is owned).
*   The lastest copy of all site files. If source control is owned, you will need this.
*   A file comparison tool. [Beyond Compare](http://www.scootersoftware.com/) is highly recommended, and is a great investment not just for upgrades, but for deploying custom development changes to production.

Here are the general steps to performing an upgrade of a customized site locally.

### Step 1. Get a Copy of the Production Site Running Locally.

Make sure the fully customized, original site files (and source, if applicable) are installed locally. Make sure you have the correct Encrypt Key from production, and that you have a database connection string to a restored backup of the Production Site \*\*\*\*Do not perform this upgrade on the production database itself\*\*\*\* You should be able to access this database from SQL Server Management Studio.

Run the website in Visual Studio (either through IIS express or the solution file), and make sure it matches production (you didn't get the wrong database, or the wrong files). Get a localhost license file if necessary.

After you've got it running and everything looks good, stop, and exit.

### Step 2. Get a Clean Copy of the Latest Version Ready.

Make sure you have a clean copy of the latest version (including source, if applicable) installed and ready to go.

### Step 3. Remember the Encrypt Key

Copy the encrypt key and database connection string, and put it in the web.config file of the Clean Copy of the Latest version that you have ready.

### Step 4. Run the Upgrade Script on the Database

Run the correct upgrade script (or series of upgrade scripts if applicable) on the database that you have backed up and restored from production. If there are errors in any of the scripts, you are going to have to handle them on a case by case basis. In most cases, this won't happen. But, if there was a particularly messy schema modification, you might have to alter the upgrade scripts. If you had an error, and you addressed it in the script, restore the database with the backup again and start over until you can execute all of the upgrade scripts without an error. You will use the final scripts that work when you upgrade in production.

### Step 5. Run the Clean Copy of The Latest Version

Make sure you have a localhost license for the version you are upgrading to, and place it in the latest version's images folder. Fire up the latest version in Visual Studio, with the correct Encrypt Key and Database Connection String to the database you just upgraded. Now attempt to run the site. Unless the schema is extremely customized, the site should run. You may see some errors about missing XmlPackages.

### Step 6. Begin Merging the Identified Customizations Into The New Version

When you merge the customizations identified (in the assessment and planning phases), take care that you aren't just doing a diff between the old customized site and the new site. You should only be merging the files that are a part of the customizations that you identified.

For each of these files, you should have either a three-way-diff or two separate diffs open of the out-of-the box old version vs. the out-of-the-box new version, and the out-of-the-box old version vs the customized old version. If the file is completely custom, of course, you can just move it straight into the new version.

For the App\_Themes & App\_Template Skins, you'll want to make a quick diff beforehand. Of course the master.template is customized, but there might be some new things added. Like, version 9.4.0+ requires a block of code for jQuery. For the most part, you can just copy over the top of the App\_Templates & App\_Themes Skins with your customized ones. Copy over the top, but don't delete any \*new\* files in the skins. For example, version 9.4.1 requires a css file named "base.css" that you don't want to delete.

### Step 7. Run the Newly Upgraded Site

After everything is merged, you should be able to build and run the site. Fix any build issues. If there are any runtime errors, address these as well. Make sure you can log in as an administrator, and successfuly create an order as a customer.

### Step 8. Quality Assurance

Each company is going to have it's own procedures for quality assurance. The more QA you do after your upgrade, the smoother your upgrade on production will be. At the minimum, you should stage your site somewhere that the stakeholders for the site (whoever is paying for the upgrade) can test and make sure everything works as they expect.

The Deployment Phase
--------------------

Since you already upgraded locally, the upgrade to production should go smoothly. You already upgraded the site files, so moving to production will be a matter of moving those files up and running your upgrade script(s).

### Prepare the Deployent Package

Complete the following to prepare the deployment package:

1.  If you have source code, in Visual Studio navigate to the configuration manager and set all projects to build for "Release" instead of "Debug."
2.  Copy the web folder of the solution into a separate directory.
3.  Make sure you have a production license in the images folder for the domain you are deploying to.
4.  Open up the Web.Config file, and make sure the Encrypt Key matches production and that the Database Connection String is for the live database.
5.  Your deployment package is complete. If you are using RDP to deploy to production, you should zip up the folder.

### Back up the Live Site Files

Do not skip this step. Even if you think you got the latest copy of everything a week ago, get a copy right before you deploy. Remember that product/entity/topic images can be uploaded to the server at any time through the admin, and you don't want to be responsible for losing someone's work. Backing up the live site files can take a little bit, so plan on doing this before bringing up a site down for maintenance page. When you schedule the time to do the upgrade, make sure to start the backup of the site files at least 1 hour before the time you have scheduled so you can get it done in time.

### Site Down For Maintenance

Prepare a directory in IIS with a site down for maintenance page that you can temporarily point the website too. Most sites that have been around the block will already have one that you can use.

### Backup the Live Database

You don't want to backup the database until \*after\* you have the site down for maintenance page up. This way, if you need to restore, your restore point will include any and all transactions that happened while the site was still running. Create a full database backup (.bak) and make sure you know where it is located.

### Move up the site files

Before you proceed, make sure you completed all of the steps in creating the deployment package - especially the Encrypt Key and Database Connection String.

1.  In the live site web folder, delete everything but the images directory.
2.  Copy your deployment package into the web folder.
3.  Copying the files can take awhile, so feel free to move on to upgrading the database. Just make sure the files are all in place before you run the site after the upgrade.

### Upgrade the Database

Run your upgrade scripts against the production database.

### Point the Site in IIS Back at the Site Files

Once all files are in place and your database upgrade is complete, you can take down the site down for maintenance page and bring back up the upgraded site.

### Testing

Make sure you can sign in as an administrator and see the admin console homepage. Make sure you can checkout from start to finish and view the receipt. Your upgrade is complete.

Summary
-------

### Upgrade Pitfalls and Common Mistakes

*   Not backing up the site files before an upgrade.
*   Not backing up a database before an upgrade.
*   Overwriting the Live Encrypt Key with a Development Encrypt Key.
*   Leaving old files that were deprecated/removed in the new version.
*   Deleting files in the new version that were necessary.
*   Not testing checkout from start to finish post upgrade.
      