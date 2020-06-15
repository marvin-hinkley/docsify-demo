
      ---
      title: Adding a MoreStore
      ---

      This document explains the basic steps involved in creating additional stores (called "MoreStore") in the MultiStore product after installing the default store. The base installation of the software is exactly the same as in previous versions. Please see the guides [here](default.aspx?pageid=installation) for detailed installation instructions.  
  
These instructions assume you have already obtained the necessary domain name you are using for the additional store and have pointed it to the proper IP address. Production URLs should not be pointed to the site until they are fully tested and ready to 'Go live'. Staging URLs are typically subdomains created as a DNS A record and pointed to the proper site IP address. Please consult your site host for information on the proper IP address and IIS setup as needed.   
  
**How does the software know what to do with the URL requests?**  

1.  You setup DNS A records (typically) for the additional URLs, pointed to the site IP addresse(s), in your domain management
2.  When a request comes into IIS for a URL, it associates it to the site and hands the request over to the software
3.  The software attempts to identify the request based on the URLs entered in the Domains tab per store ID
4.  If the software finds a match, it displays the appropriate skin and settings for that store ID. If it does not find a match, it displays the default store in the domains tab.

​This page would welcome a sponsor from the \[Company Name\] community.  

**Create the store in IIS**
===========================

1.  First, create the additional store you’re going to be using in IIS. This can be done several ways. While the example below shows separate websites for each store, the storefronts can all be applications under one website, separate sites, or even just domain aliases of the first site you set up. _The important thing to note here is: each site/application should use the same home directory – wherever you installed the software_. They all run off of the same copy of the files and the same database.  
      
    This step may be skipped depending on the site host. Please check with your site host concerning proper IIS setup as needed.  
      
    If you only have a single IP to use for testing sites, you can ‘fake’ additional websites by modifying the host file. See [this page](default.aspx?pageid=modify_hosts_file) for directions on how to do that.  
      
    ![](images/1415312859374.png)  
      
      
    Additional Considerations: The MultiStore installation should only use a single application pool for all the "stores". Using separate AppPools is not the best way to do this, especially for a large amount of stores, since it will create a new worker process for each store. That means that the same code is loaded into memory multiple times for each store, rather than just loading the code once, regardless of which store is currently being accessed.  
      
    We recommend setting up a single website in IIS with a single application pool to use for all the stores. The stores should all share the same IP address and be secured with a MultiDomain (UCC or wildcard) SSL certificate to cover all the store domains.  
      
    

**Create the store in the admin console**

1.  In the admin console, navigate to **Configuration > Manage Stores**.  
      
    
2.  Click **Create Store**. Enter a name for the store in the **Store Name** field. Enter the store URLs in the **Production**, **Staging**, and **Development** fields, then select which **Skin ID** to use for the MoreStore. Click **Save**.  
     ![](images/1415313962220.png)  
      
      
    
3.  Click the **Refresh Store** button in the upper right of the admin console.  
      
    
4.  Follow the directions [here](default.aspx?pageid=license_keys_versions_ml8_0_1_4_and_multistore_9_1_0_1_and_above) to license the MoreStore.
      