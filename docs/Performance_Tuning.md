
      ---
      title: Performance Tuning
      ---

      One of the things that upgrading to version 9.5 or higher does is convert columns in the database from an older data type that Microsoft no longer recommends (ntext) to the newer, preferred data type (nvarchar).  This can result in a small performance boost, but only if an update to existing data is performed, which can take a long time to run.  **After your site has been upgraded to version 9.5 or higher**, follow the directions below to apply this update to your site:  

This script can take a very long time to run on some sites, and can result in a slowdown of the site while it is running. Running the script overnight or during "off hours" is recommended if possible. Once the script is started, it should not be interrupted.

1.  If your site is using [Full Text Search](default.aspx?pageid=full_text_search), turn it off under **Configuration > Setup Full-Text Search** in the admin console.
2.  Connect to your live site's database and run the script called 'Performance Tuning for 9.5 and Higher.sql', found in the /db folder in the installation files you extracted during the upgrade (you can download the software again [here](http://license.aspdotnetstorefront.com/?tab=downloads) if necessary).  You may have to have your host perform this step.  If so, it is best to warn them that the script may run for a long time.
3.  When the script completes, verify that you see a 'Query completed successfully' message at the bottom of the window.  If you see 'Query completed with errors', scroll through the results and find any text in red.  Copy that and submit it to our\[Help Desk\]to determine if the errors will be a problem.
4.  If you were using Full Text Search before, you can now turn it back on.
      