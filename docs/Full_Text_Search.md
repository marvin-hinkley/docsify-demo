
      ---
      title: Full Text Search
      ---

      From the **Configuration** Menu, click **Setup Full Text Search**.   
  
Full text search is a feature of SQL that makes searching for products on the site more flexible and responsive. With the standard search features, if a customer looks for "Green shirt", only products that have _exactly_ that phrase in that order will be returned. With full text search, the same query would return all products that contain the word "green" and all products that contain the word "shirt", along with those containing the full phrase.

Should I use Full Text Search?
==============================

Full Text Search requires special components be installed on the server and can use a lot more hosting resources that basic search.  Because of this, many hosting environments do not support full text indexing, and some environments that do will run it very slowly. Also, many sites simply will not need this feature. If your product lines are simple or small, full text indexing is not going to significantly improve your search feature. Check with your host or server administrator to determine whether or not this feature will work and would be useful in your case.

Prerequisites
=============

Full text search has the following requirements:

*   SQL Server 2005+
*   Microsoft Full-Text Engine for SQL Server (MSFTESQL) service installed
*   Disk space sufficient for the index files (check with your server administrator for an idea of how large those files are likely to grow in your case)

Check with your hosting provider to find out if your hosting plan supports full text search indexing. [AspDotNetStorefront Shared & Cloud hosting plans](http://www.aspdotnetstorefront.com/t-hosting.aspx) are full text search capable.

Setup
=====

To enable this feature in the software (once the MSFTESQL service is installed and running on the server), simply fill in the required fields on this page and click the **Install Full-Text Search** button:

 ![](images/1415913308913.png)

**Field Name**

**Description**

Please Select Language

Choose from the available languages to determine which 'Noise Words' will be added to the index by default. See below for information on noise words.

Create New/Reuse Catalog

This radio button determines whether SQL will create a new full text index, or reuse an existing one (from a previous site, for example). If previous catalogs exist, they will be listed below so the desired one can be chosen.

New Catalog Name

The name to give to the new full text index SQL will create.

New Catalog Path

If your server administrator wants the index files in a specific location, that path can be listed here. Otherwise, the files will be created in SQL's default location (...Program Files\\Microsoft SQL Server\\MSSQL.1\\MSSQL\\FTData).

  

Noise Words
===========

After Full-Text Search has been successfully installed, go to **Configuration > Setup Full-Text Search** to manage noise words.  
  
Noise words are words that are very common in the selected language and are best left out of searches to improve results - words like 'the', 'and', 'your', etc. If a language was chosen during the installation described above, then a pre-generated list of noise words was created automatically. This list can be viewed and modified by clicking the **View/Maintain Noise Words** button on this page:  
  
![](images/1415913774176.png)  

  

Each word can be edited or deleted with the buttons shown below. You can also add new noise words with the form at the top of the screen:  
 ![](images/1415914054683.png)  

​

Troubleshooting
===============

If after installation the search function of the application fails and/or behaves abnormally, the following troubleshooting steps should be done:

1.  Verify that the DB table dbo.NoiseWords was created.  
      
    
2.  Check that the functions dbo.GetValidSearchString and dbo.KeywordSearch were created in the DB.  
      
    
3.  Check if the specified FT catalog that was defined in the set up was created in the specified directory. If the installation directory was left blank, check ...\\Program Files\\Microsoft SQL Server\\MSSQL.1\\MSSQL\\FTData folder.  
      
    
4.  Check if the stored procedures aspdnsf\_GetProducts and aspdnsf\_GetProductsOriginal were created.  
      
    
5.  Perform a search with a wild/universal character (\*) such as “ki\*” which should return results such as “Kit”, “King” and “Kitty”.  
      
    
6.  Access the Noise Words page and confirm if the list of common words is complete. Add, edit and/or delete as necessary.

**References:**

[http://msdn.microsoft.com/en-us/library/ms142547.aspx](http://msdn.microsoft.com/en-us/library/ms142547.aspx)   
[http://msdn.microsoft.com/en-us/library/ms345119.aspx](http://msdn.microsoft.com/en-us/library/ms345119.aspx)   
[http://msdn.microsoft.com/en-us/library/ms189826.aspx](http://msdn.microsoft.com/en-us/library/ms189826.aspx)   
[http://www.developer.com/db/article.php/3446891](http://www.developer.com/db/article.php/3446891)   
[http://msdn.microsoft.com/en-us/library/ms143508.aspx](http://msdn.microsoft.com/en-us/library/ms143508.aspx)  
  
NOTE: The above TroubleShooting section pertains ONLY to SQL 2005.

**Troubleshooting for SQL 2008+ installs:**  
SQL 2008+ utilizes a slightly different method for full-text search and when troubleshooting you may need to verify that the SQL instance was installed with Full-Text Search. If this query returns a '1' then FTS is installed:  
  
SELECT SERVERPROPERTY('IsFullTextInstalled')  
  
If it is not installed, rerun the SQL installer and be sure **Full-Text Search** option is selected under the **Database Engine Services**.

If you are using [Guided Navigation](default.aspx?pageid=guided_navigation), be sure to enable the setting: **GuidedNavigation.UseFullTextSearch**
      