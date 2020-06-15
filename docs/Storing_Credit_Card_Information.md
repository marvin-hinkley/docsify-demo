
      ---
      title: Storing Credit Card Information
      ---

      By default, the software does not store customer credit card information. This is almost never required anymore when using a live payment gateway, and we **STRONGLY** recommend against it. The only time this information should need to be saved is if store administrators are processing payment through a manual terminal, or when using recurring products (even then, [gateway recurring billing](default.aspx?pageid=gateway_recurring_billing) may remove the need for this depending on the gateway you are using). 

  
If you decide to save credit card information, simply set the **StoreCCInDB** [Setting](default.aspx?pageid=settings) to true.

### **

Viewing Credit Card Information
===============================

**

Full credit card information is only visible within the Payment Details panel, under [Orders > View/Manage Orders](default.aspx?pageid=view_manage_orders):  
 ![](images/1414778439312.png)  
  

Credit card information will only appear to admin accounts that have **Can View Credit Card #s:** checked. You can check this by looking up the account under [Contacts > View/Edit Contacts](default.aspx?pageid=view_edit_contacts).

### **

Customer Options
================

**

VISA PA-DSS requirements state that customers must be able to decline to store their credit card information. In accordance with that rule, if **StoreCCInDB** is set to Yes, the customer account page will show a **Store My Credit Card Info** checkbox. If customers uncheck that box and update their account information, their credit card number will not be stored.  
  
 ![](images/1414778596808.png)
      