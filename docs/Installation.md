
      ---
      title: Installation
      ---

      **System Requirements**
=======================

*   [WSE 3.0](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=018a09fd-3a74-43c5-8ec1-8d789091255d) (only required if submitting requests using username token authentication)
*   SSL certificate for your domain (strongly recommended)

Install WSI
===========

1.  Ensure that the [WSE 3.0](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=018a09fd-3a74-43c5-8ec1-8d789091255d) addon from Microsoft is installed on your server.
2.  Open your **web.config** file, and search for WSI. You should find 4 sections that are commented out, each marked with a **WSI Web Service Interface** label. All 4 sections need to be un-commented.
3.  Verify that you can browse to http://www.yoursite.com/ipx.asmx and that the page loads without error. WSI is installed!
      