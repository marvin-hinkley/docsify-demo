
      ---
      title: Skin Selector
      ---

      From the **Content** menu, click **Manage Skins**.  
  
This page allows you to preview and change each of your store's skins.  

Previewing & Changing Store Skins
=================================

1.  Select a store from the dropdown menu. If you have only configured a single store, _Default Store_ will be pre-selected.  
    ![](images/1415028977175.png)  
      
    
2.  Choose a skin from the menu, and click **Preview** to see an example of your store using the chosen skin. To apply the skin to your store, click **Apply Skin**.  
      
    

Adding a custom skin
====================

If you are building your a custom skin for AspDotNetStorefront, you can add 2 files to your custom skin to support it within the Skin Selector page in the admin console.  

1.  Create a folder within your custom skin called **SkinInfo**. This should be stored in the **App\_Templates/Skin\_x** directory.  
      
    
2.  Create a **preview.jpg** file which is a  screenshot of your custom skin. Image dimensions should be no larger than 1180 x 911 pixels.  
      
    
3.  Create a **skininfo.xml** file which stores information about your custom skin. You can use the skininfo.xml file from the default skin (Skin\_1) as a template to create your own xml file.   
    
    `<``Skin` `version``=``"1.0"``>`
    
     `<``DisplayName``>Default</``DisplayName``>`
    
     `<``Description``>This is the default skin that ships with AspDotNetStorefront. It is a great starting point for your own custom skin.</``Description``>`
    
     `<``Author``>`
    
     `<``Name``>AspDotNetStorefront</``Name``>`
    
     `<``Email``>sales@aspdotnetstorefront.com</``Email``>`
    
     `<``Url``>http://www.aspdotnetstorefront.com</``Url``>`
    
     `</``Author``>`
    
     `<``MobileOnly``>false</``MobileOnly``>`
    
     `<``Colors``>`
    
     `<``Color``>`
    
     `<``Name``>Primary Color</``Name``>`
    
     `<``Value``>#F5F5F5</``Value``>`
    
     `</``Color``>`
    
     `<``Color``>`
    
     `<``Name``>Background Color</``Name``>`
    
     `<``Value``>#FFFFFF</``Value``>`
    
     `</``Color``>`
    
     `<``Color``>`
    
     `<``Name``>Text Color</``Name``>`
    
     `<``Value``>#333333</``Value``>`
    
     `</``Color``>`
    
     `</``Colors``>`
    
    `</``Skin``>`
      