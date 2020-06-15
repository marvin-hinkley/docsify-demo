
      ---
      title: Quickbooks Merchant Services
      ---

      ### **

Obtaining Gateway Credentials From Intuit
=========================================

**

The storefront software needs 3 pieces of account information from Intuit/Quickbooks to connect to the QBMS gateway (see below). The steps to obtain that information are as shown below. Please be aware - the Intuit/QBMS registration process is long and complex, and changes frequently without notice. While \[Company Name\] attempts to stay up to date with their procedures so that we can be as helpful as possible, providing store admins with the ApplicationID and Connection Ticket is ultimately Intuit's responsibility. If any problems are encountered with the first section of the directions below, please contact Intuit's gateway support.

1.  Visit [http://appreg.intuit.com/](http://appreg.intuit.com/) and click the **Join Now** link.  
    ![](images/qb_1.jpg)  
      
    
2.  Enter the personal information requested, then select the **QuickBooks Merchant Services** checkbox. If you will be the only person working on the QBMS account, click **Individual Registration**. If multiple people will be registering applications and creating connection tickets (this should almost never be the case), click **Company Registration**.  
    ![](images/qb_2.jpg)  
      
    
3.  Fill in the address information and click **Next**.  
    ![](images/qb_3.jpg)  
      
    
4.  You will be shown a screen indicating that registration was successful.  
    ![](images/qb_4.jpg)  
      
    
5.  You will be sent an email with a temporary password and a link to click to log in. Click the link, and you'll be able to set a new password.  
    ![](images/qb_5.jpg)  
      
    
6.  Navigate back to [http://appreg.intuit.com/](http://appreg.intuit.com/) and log in with the account created in steps 2-5. The screen below will appear. Click **Add**.  
    ![](images/qb_6.jpg)  
      
    
7.  Populate the fields displayed and click **Save**.  
    Domain Name - Your site's domain (with www if you use it to access your site)  
    App Name - Your store's name  
    App Login - Will be created for you  
    Application Description - A short description of your store  
    Tech Contact Email - Where Intuit will send tech-related (password changes, API info, etc) information regarding this account. Can be different than the account used to register.  
    Target Application - This must be set to QBMS.  
    Environment - If this is for your live site, choose 'Production'. If you are generating an AppID and Connection Ticket for testing, choose 'IDNBeta'.  
    Application Type - This must be set to 'desktop'.  
    ![](images/qb_7.jpg)  
      
    
8.  You will be emailed a verification code to enter to complete the process. Copy/paste the code into this field and click **Verify**. You will be taken to the final registration page.  
    ![](images/qb_8.jpg)  
      
    
9.  Navigate back to [http://appreg.intuit.com/](http://appreg.intuit.com/) and your **AppID** and **AppLogin** will be displayed. Copy these down.  
    ![](images/qb_9.jpg)  
      
    
10.  Navigate to [https://merchantaccount.quickbooks.com/j/sdkconnection?appid=<app\_id>&sessionEnabled=false](https://merchantaccount.quickbooks.com/j/sdkconnection?appid=%3Capp_id%3E&sessionEnabled=false)replacing <app\_id> with the **AppID** obtained in step 9. You will see the page below.  
    ![](images/intuit.jpg)  
      
    
11.  Login with the merchant account information you created with Intuit. For a test account, [click here](https://merchant.ptcfe.intuit.com/signup/start.wsp) to signup for an account, and then visit [this page](https://ipp.developer.intuit.com/0085_QuickBooks_Windows_SDK/qbms/0030_Get_Set_Up) for test instructions, and [this page](https://ipp.developer.intuit.com/0085_QuickBooks_Windows_SDK/qbms/0060_Documentation/Testing) for additional testing procedures and test credit card information. Be sure to set the Setting: **UseLiveTransactions** to **No** when using the test account.  
      
    
12.  You will be shown your Connection Ticket, specific to the **AppID** created above. Copy this down as it will be needed later.  
    ![](images/qb_13.jpg)

### **

Configuring QBMS in the Storefront
==================================

**

1.  In the \[Company Name\] admin console, go to **Configuration > Site Setup Wizard**.  
      
    
2.  In the Payment Gateway section, click the **configure** link next to the **QuickBooks Merchant Services** entry.  
      
    
3.  Enter the values you obtained from QuickBooks Merchant Services for the **Application ID**, **Application Login**, and **Connection Ticket**.  
     ![](images/1415647009297.png)  
      
    
4.  Click **Save and Close**.  
      
    
5.  Finally, click the radio button next to **QuickBooks Merchant Services** and then click the **Save** button.
      