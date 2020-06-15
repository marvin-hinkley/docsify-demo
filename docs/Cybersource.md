
      ---
      title: Cybersource
      ---

      For the CyberSource gateway to work you must have the following System Requirements installed:

*   CyberSource Simple Order API for .NET Framework 2.0 SDK
*   Microsoft Web Services Enhancements (WSE) 3.0

Cybersource SDK Installation
============================

1.  Download the 'Simple API' SDK for .NET 2.0 (.NET2.0 .NET net2.0 v.5.0.2) from [CyberSource](http://www.cybersource.com/developers/integration_methods/simple_order_and_soap_toolkit_api/dot_net_2_0/) and install it. You also need to download and install the WSE 3.0 components from [Microsoft](http://www.microsoft.com/downloads/details.aspx?familyid=018a09fd-3a74-43c5-8ec1-8d789091255d&displaylang=en).  
      
    
2.  Set the application pool your site is running in to allow 32 bit applications.  Consult your host or whoever maintains your server for information on doing this.
  
4.  Log in to your [CyberSource](https://businesscenter.cybersource.com/sbc/login/Login.do) merchant account. NOTE: That you may need to use Firefox or other browser that supports the Java security applet.  
      
    
5.  Go to Account Management, then Transaction Security Keys. In the Transaction Security Keys page click on Security Keys for the Simple Order API link.  
      
    
6.  Click on the 2048-Bit Key button. NOTE: There should be a Java security applet visible and functional on the New Security Key page you are taken to. If there is not, please try using a different browser such as Firefox.  
      
    
7.  Then click the Generate Certificate Request button.  
      
    
8.  Once the key has been generated, copy it to your sdk directory under the keys folder. The extension of the key must be .p12 and the filename should be the same as your merchant ID.  
      
    ![](http://manual.aspdotnetstorefront.com/images/product/ml8/cybersource18.jpg)

Admin Console Setup
===================

1.  In the \[Company Name\] admin console, go to **Configuration > Site Setup Wizard**.  
      
    
2.  In the Payment Gateway section, click the **configure** link next to the Cybersource entry.  
      
    
3.  Enter the value you obtained from Cybersource for the **Merchant ID**.  
      
    
4.  Enter the filename (with extension) that you saved in step 7 above for the **Key Filename** and the full path to the SDK folder you saved that key in for the Keys Directory (end it with a backslash such as ...\\keys\\ ).  
     ![](images/1415640681391.png)  
      
    
5.  Click **Save and Close**.  
      
    
6.  Finally, click the radio button next to **Cybersource** and then click the **Save** button.

Frequently Asked Questions
==========================

Q: **What CyberSource API should I use for transaction keys?**   
A: Security Keys for the Simple Order API (SOAP).   
  
Q: **I keep getting this error: Failed to sign the request with error code N\`1862' and message N \`IO error'**   
A: The CyberSource application interface was not able to sign the request with the key file.

Here are a few things to check:

1.  Verify that these Settings have the proper value:  
    CYBERSOURCE.keysDirectory – should be the absolute path of your SOAP Security Keys.  
    (e.g. C:\\Program Files\\CyberSource Corporation\\simapi-net-2.0-5.0.2\\keys\\)  
      
    CYBERSOURCE.keyFilename – your SOAP security key filename  
    (e.g. filename.p12)  
      
    
2.  Does the ASP.NET or NETWORK SERVICE user have read access permission to the key file?

  
Q: **When I try to void a transaction, it always fails with the following error even if the capture has not been done: “The capture or credit is not voidable because the capture or credit information has already been submitted to your processor. Or, you requested a void for a type of transaction that cannot be voided.”**   
A: A transaction can only be voided if CyberSource has not yet submitted the debit or credit information to your processor. Usually CyberSource submits that type of information to your processor once a day, so your window for successfully performing a void is relatively small. CyberSource will decline your void request if the debit or credit information has already been sent to the processor.   
CyberSource supports the void service for the following processors:

*   Chase Paymentech Solutions 
*   TeleCheck

When you void a transaction, the transaction is at the end of its life. You cannot undo a void, and you cannot perform a follow-on credit for a debit that has been voided.

Q: **Why won't Cybersource work on my 64-bit server?**   
A: The 3rd party DLLs required for Cybersource to work don't support 64 bit environments. Unfortunately, there is nothing AspDotNetStorefront can do to alleviate this limitation.   
  
Q: **Can I use my Bank of America account through Cybersource?**   
A: Yes, Cybersource supports Bank of America accounts. See [here](http://www.cybersource.com/bankofamerica/) for more information.   
  
For more information about CyberSource error messages, go to the [CyberSource page](https://support.cybersource.com/cybskb/index?page=content&id=C156&pmv=print&impressions=false) where they have a list of reason codes for the errors and contact CyberSource support directly if you are experiencing these, they should be able to assist you further.
      