
      ---
      title: Modify Hosts File
      ---

      Sometimes developers will need to test multiple store functions without actually having access to multiple IPs to do a standard install. This is easily ‘faked’, by modifying the system HOSTS file.   

1.  First, create multiple sites in IIS, one for each store. These must be sites, not applications. When creating the stores, make sure that you specify a Host Header, which should be the URL you want to access the store at:  
    ![](http://manual.aspdotnetstorefront.com/images/product/ml9/modhost.png)  
      
    You can instead create the additional sites as additional bindings within one site. Use 'Edit Bindings' on the base site and add the additional URLs  
      
    ![](http://manual.aspdotnetstorefront.com/images/product/ml9/edit_bindings.png)  
      
    
2.  Once the stores are created, open the hosts.config file on your machine in a text editor. This is generally found in the ‘C:\\Windows\\System32\\drivers\\etc’ folder. Under the last line, add 1 line for each of the stores you want to ‘fake’ as shown below. The 127.0.0.1 is the machine’s local IP address, and the second part is the address you want to hit the store at. This should match what you set for the host header above. Once you’ve added all the necessary lines, save the host file and perform an IISRESET, and you will be able to browse to the sites you listed locally.  
      
    ![](http://manual.aspdotnetstorefront.com/images/product/ml9/modhost2.png)
      