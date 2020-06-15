
      ---
      title: SecureNetV4
      ---

      To enable the SecureNetV4 gateway:

1.  In the \[Company Name\] admin console, go to **Configuration > Site Setup Wizard**.  
      
    
2.  In the Payment Gateway section, click the **configure** link next to the **SecureNetV4** entry.  
      
    
3.  Enter the values you obtained from SecureNet for the **SecureNet ID** and **SecureNet Key**.  
      
    
4.  Click **Save and Close**.  
      
    
5.  Finally, click the radio button next to **SecureNetV4** and then click the **Save** button.

SecureNet Vault
===============

The SecureNet Vault allows customers to store credit card information, and then re-use that to check out later without having to re-enter the payment details. Your site does not need to be [storing CC info](default.aspx?pageid=storing_credit_card_information) for this to work. Your site has to be using SecureNetV4 as the main payment gateway to use the Vault service.

**

Enabling the Vault
------------------

**

To enable the Vault, simply follow the steps above to enable SecureNetV4, and on step 3 set **Vault Enabled** to **Yes**.

**

Adding saved credit cards
-------------------------

**

Customers can add saved credit cards 2 ways:

1.  On the account page:  
    ![](images/1415639412607.png)  
      
    
2.  During checkout, any new credit card entered will be saved if the 'Save My Credit Card Info' box is checked on the account page. Note that when using the SecureNetV4 gateway with Vault, this will _not_ store the credit card information locally unless your [StoreCCInDB](default.aspx?pageid=storing_credit_card_information) Setting is also enabled.  
    ![](images/1415639540028.png)

**

Using the Vault
---------------

**

To use a saved credit card from the Vault, customers simply choose the 'Stored Payment Methods' option during checkout, and choose the card they want to use.  
  
![](images/1415640151076.png)

  
  

The 'Stored Payment Methods' text can be changed by editing the 'checkoutpayment.aspx.36' [prompt](default.aspx?pageid=prompts).
      