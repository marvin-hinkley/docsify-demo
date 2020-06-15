
      ---
      title: ResetPassword
      ---

      ### Description:

This node can reset the password for any non admin user to an explicit or new randomly generated password.

### Full Syntax:

<ResetPassword PasswordType="ClearText|Random" CustomerID="integer" CustomerGUID="uniqueidentifier" CustomerEMail="string" SendEMailToCustomer="Boolean">new password here in clear text if not doing random reset</CustomerPasswordChange>

### Notes:

*   If SendEMailToCustomer=true, then the customer will also be e-mailed their new password.
*   Use ClearText if you are assigning a new password explicitely. Use Random to have the customer's password get reset to a random password that matches store policies.
*   At least one of CustomerID, CustomerGUID or CustomerEMail must be specified to locate the customer record. If using CustomerEMail for lookup, remember that the store MAY have the allow duplicate e-mail AppConfig enabled, so if that is true, then CustomerEMail may not be a unique customer record locator.
*   This element cannot be used inside a transaction. If it is used inside a transaction, the transaction state is ignored and this node still executes.
*   If specifying a password, it must meet the password policies in effect on your site (UseStrongPwd, NewPwdAllowedChars, etc).
*   This node cannot be used to reset an admin or super admin's password.

### Warnings:

PCI / PA-DSS compliance has special rules regarding how password resets are handled, who is allowed to do them, and who is allowed to know what the passwords are set to. Be sure that your company is following all of the required guidelines!
      