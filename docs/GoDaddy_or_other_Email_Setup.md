
      ---
      title: GoDaddy (or other) Email Setup
      ---

      Due to restrictions set by GoDaddy (and some other email servers such as those that require SSL over port 465), GoDaddy email settings cannot be directly used to send email (receipts, shipment notifications) from your store. You can work around this restriction by establishing a free Gmail account, and using Gmail settings to "Send As" your GoDaddy (or other) email address. What you need:

*   GoDaddy (or other) email account (sales@yourdomain.com):
    *   Email Address
    *   Password
*   Free Gmail account (yourgmailaddress@gmail.com):
    *   Email Address
    *   Password

First, Log in to your Gmail account.

Click the Gear icon in the top right corner, and select **Settings**:

![](http://manual.aspdotnetstorefront.com/images/product/MSx/1-Gmail-Gear-Settings.jpg "1-Gmail-Gear-Settings") 

Click the **Accounts** tab, and in the Send Mail As: section, click **Add another email address you own**.

![](http://manual.aspdotnetstorefront.com/images/product/MSx/2-Gmail-Accounts.jpg "2-Gmail-Accounts") 

In the pop up box, enter your company name in the Name field.

Enter your GoDaddy (or other) Email address (sales@yourdomain.com)

UN-check the **Treat as an alias** box.

Click **Next Step.**

![](http://manual.aspdotnetstorefront.com/images/product/MSx/3-Gmail-SendMailAs.jpg "3-Gmail-SendMailAs") 

On the next screen, select Send through yourdomain.com SMTP servers.

Enter the following values:

SMTP Server: **smtpout.secureserver.net**  
Username: **sales@yourdomain.com** (Your GoDaddy or other email address)  
Password: \[your GoDaddy or other email password\]  
Select Port **465**.  
Select Secured connection using**SSL**.

Click **Add Account**.

![](http://manual.aspdotnetstorefront.com/images/product/MSx/4-Gmail-SMTP.jpg "4-Gmail-SMTP") 

Gmail will check your credentials, and send an email verification code to your sales@yourdomain.com GoDaddy (or other) email address. Check your GoDaddy (or other) email account and either click the link in the email to verify, or copy the confirmation code, and click **Verify.**

![](http://manual.aspdotnetstorefront.com/images/product/MSx/5-Gmail-Verify.jpg "5-Gmail-Verify")

Next, log in to your AspDotNetStorefront admin console, and navigate to **Configuration > Setup Email**.

Set the following values on the Email configuration page:

Mail Server DNS: **smtp.gmail.com**  
Mail Server Username: **yourgmailaddress@gmail.com**  
Mail Server Password: \[Your Gmail Password\]  
Mail Server TCP Port: **587**  
Mail Server Requires SSL:**Yes**  
Receipt Email sends from (Email Address): **sales@yourdomain.com**  
Receipt Email sends from (Name): **Your Company Name**  
New Order Notifications send to (EMail Address): **sales@yourdomain.com**  
New Order Notifications send to (Name): **Your Company Name**  
New Order Notifications send from (EMail Address): **sales@yourdomain.com**  
New Order Notifications send from (Name): **Your Company Name**

**​**

Click the buttons at the bottom of the page to Test All. If you’ve followed all of the steps, you’ll see a ‘success’ message on the email configuration page. You should also receive a copy of the test email in your inbox, where the ‘From’ email address is your GoDaddy (or other) Email address.

With Google GMAIL, you also need to make sure that the site is allowed to access the SMTP, by following these steps:

1) Log in to your Google account

2) Go to "My Account"

3) Under the section "Sign-in & Security", select "Connected apps & sites"

4) Ensure that "Allow less secure apps" is ON

Still need help getting email?
==============================

**Sign up for Google's G-Suite and save.** Vortx is happy to recommend an E-mail service we've known to work well with the cart. G-Suite is Google's approach to mail hosting, using the very familiar email interface many of you know as Gmail.

G-Suite is capable of hosting small to large business email. Being Google partners we'd love to share our benefits and offer 20% off your first year's service. Come see us in [Live Chat](https://vortx.whoson.com/chat/chatstart.htm?domain=www.aspdotnetstorefront.com&timestamp=1488911175254&session=947-1481588721972) to learn more and for a promo code to save today!

[Learn more and sign-up here!](https://goo.gl/h6sqMd)
      