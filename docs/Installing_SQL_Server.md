
      ---
      title: Installing SQL Server
      ---

      The \[Company Name\] software will run on SQL Server 2008 or higher. The free (Express) versions are fine for most sites. The links and information below are for 2012.

1.  First, download the installer from: [http://www.microsoft.com/en-us/download/details.aspx?id=29062](http://www.microsoft.com/en-us/download/details.aspx?id=29062)
2.  Next, [follow these](http://msdn.microsoft.com/en-us/library/ms143219(v=sql.110).aspx) directions for installing SQL Server. The default options are fine for most steps, but keep an eye out for these items:
    *   On the 'Feature Selection' page (step 13 in the linked instructions), make sure to install Management Tools.
    *   On the 'Database Engine Configuration - Account Provisioning' page (step 20 in the linked instructions), choose Mixed Mode Authentication. You will be prompted to create a strong password for connecting to the SQL instance you are installing. Make sure that you do not lose that password! By default, the username for that account will be 'sa'.
      