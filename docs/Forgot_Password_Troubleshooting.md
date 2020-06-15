
      ---
      title: Forgot Password Troubleshooting
      ---

      **Symptoms**  
When attempting to retrieve a new temporary password from the storefront account signin page using the 'Forgot Your Password?' email field, the site returns the message "There is no registered user with that e-mail address!" although the user account is valid and active.  
  
**Cause**  
This will occur for any Admin or Super Admin customer account when attempting to retrieve a new password using the storefront account signin page. This is a security feature to prevent errant or malicious resetting of your admin account password on the public account signin page.  
  
**Solution**  
If you need to reset your Admin or Super Admin account password, please use the /admin/signin.aspx page for your site (might be a different folder than /admin).
      