
      ---
      title: Varying Settings by Store
      ---

      Some store owners will want features to work differently on different stores within the same MultiStore instance. To allow this, the MultiStore software allows each store in the instance to have its own copy of each Setting if desired, so they can be set differently. Note that the steps below are not required! If you want to use the same setting across all of your stores, simply set the Default value (see below) and that setting will apply to all stores. In most cases however there will be at least a couple of settings that you want to vary from store to store. In the example below, we'll look at the LiveServer Setting.

1.  First, go to **Configuration > Settings**, enter 'LiveServer' in the **Search All Fields** box, then click **Apply Filter**. You should see something like this:   
    ![](images/1415830150325.png)  
      
    
2.  Click the Setting name to edit.  
    ![](images/1415830190820.png)  
    Notice that since only one value has been entered so far, the software indicates that the same value will be used for all stores - (Default) yourdomain.com_._ All of our stores aren't going to have the same name, so we want to change that!  
      
    
3.  Click in the field for Default Store (your store will be labeled differently, depending on what you called it) and enter the domain for that store, then do the same for Store 2.  
     ![](images/1415830295446.png)  
      
    
4.  Click **Save and Close**, and you will be returned to the main Settings page. Note that you will now have multiple copies of the Setting you changed - one default, and one for each store that you set a value for. As long as a store-specific version of an Setting exists, that value will be used. If there isn't a store-specific version (for example, if we added a Store 3 on this site later on), the software would 'fall back' to the 'Default Store' value.
      