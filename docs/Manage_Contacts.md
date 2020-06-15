
      ---
      title: Manage Contacts
      ---

      From **Contacts** Menu, click **Manage Contacts**.  
  
This page allows store administrators to view and manage existing customers. Customer records can be viewed alphabetically by clicking one of the letter links, or you can search for a specific customer by last name or email address. The records are displayed in a table, with each column containing special information and/or actions, explained below.  
  

 ![](images/1415402841451.png)

  

Customer Account Information
============================

**Column Name**

**Description**

CustomerID

Each customer is assigned a unique customer ID when they register. The ID displayed here is a link, which will take you to the customer's account page (see below in this article for more information). The date displayed is the date the customer registered.

Name

This is the customer's first and last name as they entered it during registration.

Order History

If the customer has placed orders, a 'View' link will appear here which leads to a list of their orders (see below for more details).

Admin

This column displays whether or not the registered account is an admin account, and then provides buttons to either 'promote' them to an admin user (Set Admin or Set Super Admin) or 'demote' them (Clear Admin or Clear Super Admin). See [this page](default.aspx?pageid=manage_admin_users) for more information on admin users.

Level

If the customer belongs to a [customer level](default.aspx?pageid=customer_levels) the level's name is displayed here.

Email

This is the email address the customer provided when they registered.NOTE: If your site allows [anonymous customers](default.aspx?pageid=anonymous_customers) then this column may be blank for some users.

Billing Address

This is the billing address the customer provided when they registered.

Delete Customer

Clicking this button deletes the customer from this list. Note that this does NOT actually remove the customer from the database, it just removes them from the active customer list.

Nuke Customer

Clicking this button permanently removes the customer from the database.This cannot be undone! Be sure this is what you want to do before clicking this button.

Nuke & Ban Customer

If you click this button, the selected customer will be permanently removed from your database. In addition, their last known IP address will be added to a restricted list, and any attempts to visit your site from that IP address will be blocked.It is entirely possible to ban whole companies and/or geographic locations with this action, due to Internet routing configurations beyond your control. This should not be used unless absolutely necessary.

### **

Order History
-------------

**

Clicking the 'View' link in the Order History column brings the store administrator to this page. The customer's previous orders are listed, along with the status of those orders and any customer service notes.  
  
 ![](images/1415403192716.png)
      