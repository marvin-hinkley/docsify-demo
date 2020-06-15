
      ---
      title: Email Setup
      ---

      Before your site can send emails - receipts, admin notifications, contact requests, etc - you must give the software your SMTP information. This info is usually obtained from your host, though some hosts do not provide email services. In that case, you can use your business ISP's mail services, Google's mail service, etc.

Still need help getting email?
==============================

**Sign up for Google's G-Suite and save.** Vortx is happy to recommend an E-mail service we've known to work well with the cart. G-Suite is Google's approach to mail hosting, using the very familiar email interface many of you know as Gmail.

G-Suite is capable of hosting small to large business email. Being Google partners we'd love to share our benefits and offer 20% off your first year's service. Come see us in [Live Chat](https://vortx.whoson.com/chat/chatstart.htm?domain=www.aspdotnetstorefront.com&timestamp=1488911175254&session=947-1481588721972) to learn more and for a promo code to save today!

[Learn more and sign-up here!](https://goo.gl/h6sqMd)

Your Store needs Email!
=======================

Your store needs email to send receipts, admin new order notices, distributor notifications and password resets. The Forgot Password feature on login pages is visible and available only if your storefront is properly configured to send email.

Ready to setup email?
=====================

There's more than one way to do it... This article will outline the setup procedures.

  

Site Setup Wizard
=================

In the \[Company Name\] admin console, go to **Configuration > Site Setup Wizard** and click the **Configure Email** link.  
  
 ![](images/1415747021194.png)

  

Email Setup Wizard
==================

In the \[Company Name\] admin console, go to **Configuration > Setup E-mail**.  
  
This page lets you set up and test your email settings to verify that everything is working properly for your outgoing emails. Enter the necessary values and click the test button, and the store will attempt to send outgoing mail. If everything goes well you'll see a message indicating success. If there is a problem, the store will attempt to display any error messages returned by the mail server.

If you receive an error message from the mail server, you will need to contact whoever maintains that mail server for assistance with correcting your email settings. \[Company Name\] cannot advise you on what to change.

Clicking **Send Test** saves the entered values to the \[Company Name\] Settings (see below).  
 ![](images/1415747207501.png)

  

Manual Configuration
====================

If you prefer to configure email manually, it can be done directly through the [Settings](default.aspx?pageid=settings) . Make sure that all of the **GotOrder**, **ReceiptEmail**, and **MailMe** Settings are configured properly for your email accounts and mail servers. These include:

*   MailMe\_Server
*   MailMe\_ToAddress
*   MailMe\_ToName
*   MailMe\_FromAddress
*   MailMe\_User
*   MailMe\_FromName
*   MailMe\_UseSSL (optional)
*   MailMe\_Port (optional)
*   MailMe\_Pwd
*   GotOrderEmailTo
*   GotOrderEmailFrom
*   GotOrderEmailFromName
*   ReceiptEmailFrom
*   ReceiptEmailFromName

Troubleshooting
===============

The software uses System.Net.Mail for outgoing emails. This only supports explicit SSL and will fail if your SMTP is set to use SSL on port 465. Please use TLS/STARTTLS on port 587 instead if possible (you still need to set the **Mail Server Requires SSL** option to **Yes**.)  
  
The best way to troubleshoot email issues is to pull up a test order on the Order page and click the **Resend Receipt Email** button. The software will attempt to send that email, and display any errors encountered on the screen. This will often give an indication of where the issue is.   
If emails are not being sent, check that there are no AppConfigs that are preventing them from being sent. Some of these are:

*   Recurring.SendShippedEmail
*   Recurring.SendOrderEmailToCustomers
*   BulkImportSendsShipmentNotifications
*   SendOrderEmailToCustomer
*   SendWelcomeEmailToCustomer
*   SendShippedEmailToCustomer
*   TurnOffStoreAdminEmailNotifications

Free email accounts like Gmail, Yahoo, and Hotmail often filter out storefront emails, preventing your customers from getting messages you send. Some ways to prevent this are:

*   Ensure your domain/IP is not on a blacklist from these mail providers
*   Ensure your emails are being sent from valid email addresses
*   Implement one of the many ways to verify that you are a legitimate sender
*   Sender Policy Framework, Sender ID, DomainKeys, Identified Mail, etc
*   Verify that reverse DNS lookups resolve to your site properly
*   Disable recursion on your server

\[Company Name\] cannot determine if these are necessary for you or provide any assistance with setting them up. Contact your host/IT department for assist with this.
      