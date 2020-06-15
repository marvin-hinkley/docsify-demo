
      ---
      title: EncryptKey
      ---

      From the **Configuration** Menu, click **Change EncryptKey**.   
  
If you are [storing credit card information](default.aspx?pageid=storing_credit_card_information) on your site, it is highly recommended that the web.config EncryptKey be changed at least every 90 days. That must be done through this page of the admin console, so that the software can update encrypted records with the new key information.  
  
If set to Auto, a random secure encrypt key will be generated and inserted into the web.config. If set to manual, you must specify the key. EncryptKeys should be at least 8 characters long, and should not contain special characters (letters & numbers only).

Before this change can be made, the .NET user account (typically ASPNET for WindowsXP or NETWORK SERVICE for Windows Server 2003/Vista or IIS\_IUSRS for Windows Server 2008/Windows7) must be given read/write/modify access to the folder the web.config file resides in, and decrypt the web.config file in the [Site Setup Wizard](default.aspx?pageid=site_setup_wizard). Contact your host for assistance with making that change, and backup the database and web.config file prior to changing the encrypt key.   
  
This can take some time, do not stop the process once it has begun!  
 ![](images/1415379492888.png)
      