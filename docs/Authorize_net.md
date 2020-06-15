
      ---
      title: Authorize.net
      ---

      Obtaining your API Login and Transaction Key
============================================

1.  Login to your [Authorize.Net](https://account.authorize.net/) account.  
      
    
2.  Navigate to Account - Settings - Security Settings - API Login and Transaction Key.  
      
     ![](images/1415640101641.png)  
      
    
3.  Obtain your API Login ID and generate a Transaction Key if you have not already been provided one from Authorize.Net.  
      
     ![](images/1415640127861.png)

Enabling the Authorize.Net Gateway
==================================

1.  In the \[Company Name\] admin console, go to **Configuration > Site Setup Wizard**.  
      
    
2.  In the Payment Gateway section, click the **configure** link next to the Authorize.Net entry.  
      
    
3.  Enter the values you obtained from Authorize.Net for the **Login** and **Transaction Key**.  
      
     ![](images/1415639263684.png)  
      
    
4.  Click **Save and Close**.  
      
    
5.  Finally, click the radio button next to Authorize.Net and then click the **Save** button.

Authorize.Net Wallet
====================

The \[Company Name\] software is also integrated with Authorize.Net's [Customer Information Manager (CIM)](http://www.authorize.net/solutions/merchantsolutions/merchantservices/cim/) service. This allows customers to store their credit card information in the Authorize.net 'Wallet', which is stored on Authorize.Net's servers. Customers can access this stored credit card information to check out without having to re-enter their payment information each time. This will work even if your store is not [storing credit card information](default.aspx?pageid=storing_credit_card_information).

**

Enabling the Wallet
-------------------

**

To enable the Wallet, simply follow the steps above to enable Authorize.Net, and on step 3 set **CIM Enabled** to **Yes**.

**

Adding saved credit cards
-------------------------

**

Customers can add saved credit cards 2 ways:

1.  On the account page  
     ![](images/1415639412607.png)  
      
    
2.  During checkout, any new credit card entered will be saved if the **Save to your wallet?** box is checked. Note that when using the Authorize.Net gateway with CIM enabled, this will _not_ store the credit card information locally unless your [StoreCCInDB Setting](default.aspx?pageid=storing_credit_card_information) is also enabled.  
     ![](images/1415639540028.png)

  

  
**

Using the Wallet
----------------

**

To use a saved credit card from the Wallet, customers simply choose the 'Stored Payment Methods' option during checkout, and choose the card they want to use.  
 ![](images/1415640151076.png)

The 'Stored Payment Methods' text can be changed by editing the 'checkoutpayment.aspx.36' [prompt](default.aspx?pageid=prompts).

**

Troubleshooting
---------------

**

*   Authorize.Net CIM requires a unique customer ID per gateway account for each customer that it is saving data for. Those IDs come from your storefront. This means that if you are testing this functionality on multiple sites with different databases, you must use a different customer for testing on each site.
*   CIM will only work on an Authorize.Net account that is set to live mode. You can enable CIM testing by setting the AUTHORIZENET\_Cim\_UseSandbox Setting to true, but the main account must be live. You can do this in your Authorize.Net Account - Settings - Security Settings - General Security Settings - Test Mode.
      