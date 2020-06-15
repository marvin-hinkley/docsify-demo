
      ---
      title: Sage Pay
      ---

      Sage Pay provides secure credit card and debit card payment solution for thousands of online and mail order businesses across the UK. Payment solutions are provided for both e-commerce payments and Telephone Order/Mail Order payments. Payments can either be processed in real-time or can be delayed with deferred payment options.

Setting up the Sage Pay Account to Use the Simulator
====================================================

In order to use Sage Pay as your payment gateway, you must first obtain an simulator account with them. A VSP Simulator basically emulates the Sage Pay Test and Live systems. So you need an account to test your website before you sign up for their services. To sign up for a free account go to their [website](https://support.sagepay.com/apply/requestsimaccount.aspx).   
  
Once you have signed up for an account, log in to their [site](https://test.sagepay.com/simulator/).  
  
![](images/protx03.jpg)

You will then be redirected to the VSP Simulator Main Menu, once in that page click on the VSP Direct button.  
  
![](images/protx04.jpg)

• In the VSP Direct page, choose the option that you want for Response to Authorisation POSTS and Results of AVS and CV2 Checks.   
• Click the Update button to save the configuration.   
• Then click the Back button to return to the previous page.  
  
![](images/protx05.jpg)

• This time click the Account button.  
• Once in the Administrative Functions page, fill up the Account Settings part, make sure that "Simulate VSP Direct" is checked.   
• Also choose your desired Transaction Type and the Account Types.   
• Then you must provide your IP address by filling up "Add New IP" and clicking the Add button.   
• Finally, add your valid currency. For additional information on adding a valid currency, further discussion can be found at the bottom of the page.

Note: You may also change your password in this page  
  
![](images/protx06.jpg)

For more information on the VSP Simulator, check out their [website](https://ukvpstest.protx.com/vspsimulator/).   
  
After you're done testing and everything works well, apply for a [live account](https://support.protx.com/apply/).   

Enabling Sage Pay in the Admin Console
======================================

1.  In the \[Company Name\] admin console, go to **Configuration > Site Setup Wizard**.  
      
    
2.  In the Payment Gateway section, click the **configure** link next to the **Sage Pay** entry.  
      
    
3.  Enter the value you obtained from Sage Pay for the **Vendor Name**.  
      
    
4.  Set **Use Simulator** to **Yes** while testing.  
     ![](images/1415655355899.png)  
      
    
5.  Click **Save and Close**.  
      
    
6.  Finally, click the radio button next to **Sage Pay** and then click the **Save** button.

Setting up Sage Pay to go Live
------------------------------

After testing with the simulator you will be provided with a unique Sage Pay account. This is the account you will use when you go live. You will need to test your code against the [Test Server](https://support.protx.com/apply/) in the same fashion as you have tested against the Simulator. The Simulator should have helped debug any possible errors so your migration to live should be straightforward.

1.  After using the VSP Simulator, you need to have your account activated. The test account will be created based on the [online application form](https://support.protx.com/apply/) submitted to Sage Pay. The details of the test account will be emailed to you within 48 hours. The merchant number will also be confirmed with the merchant bank if it is correct and they will make sure that it is set up for Sage Pay use.  
      
    
2.  Perform the shopping cart integration by following the [set up guide](http://techsupport.protx.com/aspstorefrontcartguide.asp) for the admin site.  
      
    Make sure that the following [Settings](default.aspx?pageid=settings) are configured correctly:  
    UseLiveTransactions = No  
    SagePayUK.UseSimulator = No  
      
    
3.  Perform testing.  
    Log into [VSP Admin](https://ukvpstest.protx.com/vspadmin/).  
    Enter the following details:
    
    √ Vendor Name = VSP Vendor Name   
    √ User Name = VSP Vendor Name   
    √ Password = VSP Admin password
    
    • Create a new user by clicking the Add button.   
    • Enter a user name and password of your choice and click the Add button. Next time you log in to the test server use the User Name and Password you created.   
    • Now process a test transaction in your website to check if the integration has worked.
    
    √ You will need to use the [test card numbers](http://techsupport.protx.com/cardtypes.asp#howcardtest) found below.   
    √ You must also provide an Expiry Date   
    √ You should enter the value for the CV2 as 123, Billing Address Number as 88 and Billing Post Code Numbers as 412.
    
    These are the only values that will return as Matched, any other value will return a Not Matched.
    
    ![](images/testcardnumbers.jpg)
    
4.  Go Live by logging in to your [Live VSP Admin](https://ukvps.protx.com/vspadmin/) account.
    
    In your admin store site make sure that the following appconfigs are set correctly:
    
    • UseLiveTransactions = Yes   
    • SagePayUK.UseSimulator = No
    
    You need to test your Live account to make sure that you are able to process transactions with the banks. You have to use real credit / debit card numbers to test transactions. The transactions will then be sent to the bank for authorization. You will be able to [void or refund](http://techsupport.protx.com/paymentrefunds.asp#howdorefundadmin) the transaction later on. In order to make sure that the Live account is working, please make transactions for both the credit and debit cards.   
      
    

Here's a checklist on what to set up in your Sage Pay account:

√ Make sure you have set up the right IP address. If you don't know your IP address you may check it out at this [site](http://whatismyipaddress.com/).   
√ The transaction or payment type is either AUTH (this will send DEFERRED requests to Sage Pay) or AUTH CAPTURE (which will send PAYMENT requests to Sage Pay). Please note that if you choose AUTH (DEFERRED), the primary contact on the account needs to email the [Sage Pay support team](mailto:support@protx.com).   
√ By default the currency is set to GBP, but this can be changed to the currency set up as your store's default currency. Sage Pay will check if your merchant number is capable of transactions in that specific currency, so check with your merchant bank. Take note that you can only have one currency set up, and it should match your store's default currency. You can check your store's default currency in the Configuration Wizard of your store's admin site.

  
For more information, you may check out the following pages:   
[http://techsupport.protx.com/vsptestadmin.asp](http://techsupport.protx.com/vsptestadmin.asp)   
[http://techsupport.protx.com/vspdirectcart.asp](http://techsupport.protx.com/vspdirectcart.asp)   
  
If you need additional help in setting up your SagePay account, contact their [support](http://www.protx.com/contact.asp).
      