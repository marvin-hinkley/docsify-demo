
      ---
      title: Prompts
      ---

      Your online store needs to 'talk' to your visitors. You want your reminders, your messages, your labels, and even your errors to carry the personality that goes along with your brand identity.  
  
Within \[Company Name\], 'prompts' are used to generate much of the text that can be viewed on the front end of the site (and, incidentally, also in the admin console). You can use these prompts to make a very real difference - for example the 'out of box' account creation page is shown on the left. The right hand version has had prompts changed:  
  
  
 ![](images/1417521585097.png) ![](images/1417522578539.png)  
  
  
These prompts are stored in your database. They are uploaded from an Excel file, giving you complete control, and without needing any developer skills.  
  
Let's learn about a 'prompt' in detail. We'll experiment with the shopping cart page (that's the name for the 'stopping off' point between your product pages and your checkout. It looks like this:  
  

 ![](images/1417492416018.png) 

  
  
​Test Yourself ... How many 'prompts' do you think there are in the image above? Remember - buttons, reminders, labels, links ... almost all of them are prompts, and therefore totally under the control of the storeowner to adopt his style. Check your answer [here](default.aspx?pageid=miscellany).   
On the shoppingcart page, pictured above, just underneath the "Checkout with PayPal" button there is a string resource.  
  

 ![](images/1417494667978.png) 

  
  
The snippet of code includes this:   
<%$ Tokens:StringResource,shoppingcart.recurring.paypalworks %>  
  
This code snippet shows us that there is a prompt called 'shoppingcart.recurring.paypalworks'. If we go to the \[Company Name\] admin console and go to Content > Manage Prompts, then we can search for 'shoppingcart.recurring.paypalworks'  
  
 ![](images/1417494800626.png)  
  
  
We can see the default value ('Works with recurring payments too!').  
  
Now, imagine that you own a store that doesn't actually offer any items on a 'recurring payment' ... you might still offer PayPal and it might be that you'd sooner remind _your_ shoppers that PayPal lets them pay with all leading credit cards. Simply edit your prompt ...  
  
 ![](images/1417495073457.png)  
  
And now your shopping cart page reflects your own changes ...  
  
  
  

 ![](images/1417495202671.png)

  
   
  
  
As well as allowing you to stamp your brand 'persona' onto your store, it also makes translating your site into other languages extremely easy, as all you have to do is translate the initial Excel file and then upload it to your site. There is more information on localizing your site [here](default.aspx?pageid=locale_settings).   
  
From the **Content** menu, click **Manage** **Prompts**.  

Editing Prompts
===============

1.  Use the **Filters** at the top of the page to locate a prompt to edit. You can enter search terms in the **Name** (ex: signin.aspx.11) and/or **Value** (example: "Please enter your e-mail address") fields. You can also choose a **Locale** and/or **Store** from the available dropdown menus, and filter by prompts that have already been **Modified**.  
      
    Many prompts are named based on the page the prompt is displayed on. If you would like to change a text prompt that displays on the front-end Create Account page (createaccount.aspx), try typing 'createaccount' into the name field in your filter.  
      
    
2.  From the grid at the bottom of the page, click the prompt Name to edit the prompt.  
     ![](images/1415033571372.png)  
      
    
3.  In the **Value** field, type the new prompt, and click Save.  
     ![](images/1415033646001.png)

  

### **

Adding Prompts
==============

**

New prompts can be added to the store from the admin console. Be aware that in order for the string to be displayed, the site's page where you wish the string to be displayed will have to be modified to 'call' that string.  

1.  From the top of the **Prompts** page, click **Add New Prompt**.  
     ![](images/1415033908892.png)  
      
    
2.  Enter the new prompt's **Name**, **Value**, **Locale** and **Store** settings, then click **Save**.  
    The **Name** field is how the prompt is referred to from within the skin or code files. The **Value** field is the actual content of the prompt, that will be visible on the store. 

### **

Reload from Excel file on Server
================================

**

It may become necessary during the setup/maintenance of your site to reload the entire prompt list.  You may want to reset prompts to the default, or you may be installing a new locale (language) etc. This option allows administrators to start again, and pulls the prompts from the spreadsheet called **strings.en-US.xls** (or other similarly named files - strings.fr-FR.xls, etc). These spreadsheets are found in the **/StringResources** folder on the server where the software is installed.  
  

1.  From the Prompts page, click **Reload from Excel file on Server**, then click OK at the dialog box prompting for confirmation.  
     ![](images/1415034273469.png)  
      
    
2.  Check the boxes for **Replace Existing**, and/or **Leave my modified prompts**, then click **Reload Review**.
    *   **Replace Existing**: If checked, the software will overwrite existing prompts. Use this option if you are importing a new file that contains some old prompts as well as new prompts and you want to replace them all.
    *   Leave my modified prompts: If checked, the software will leave any prompts which have been modified in their current, modified state. Modified prompts will not be overwritten.  
          
        
3.  The next screen will show a preview of the changes which are going to be made. The status column will indicate whether a prompt will be imported. Click **Begin Reload Processing** to start the import. This may take some time to process, a status screen will display once the process is complete.

  

### **

Reload from an Excel file on your PC
====================================

**

This allows you to upload a string file from the local PC you're working on instead of using one already loaded on the server.  
  
The steps are the same as for reloading from the server (see above), except that you must specify the file to be uploaded first.  

1.  From the Prompts page, click **Reload from Excel file on your PC**.  
    ![](images/1415042299956.png)  
      
    
2.  Click **Choose File** to upload an Excel file from your PC. Check the boxes for **Replace Existing** and/or **Leave my modified prompts** if desired. Click **Upload** to review and start the import.  
     ![](images/1415042431913.png)
      