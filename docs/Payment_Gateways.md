
      ---
      title: Payment Gateways
      ---

      This page would welcome a sponsor from the \[Company Name\] community.

Supported Gateways
==================

\[Child Page List\]

Backup Payment Gateway Setup
============================

In the event that your primary gateway doesn't respond to transaction requests (ie the gateway is temporarily down, there's a routing issue, etc) the software will 'roll over' to the backup gateway and try the transaction again, to prevent the loss of an order.   
  
Note that this does require that you have a merchant account with both gateways at all times.   
  
To set up a backup payment gateway:  

1.  In the admin console, navigate to [Configuration > Site Setup Wizard](default.aspx?pageid=site_setup_wizard). Scroll to the Payment Processing Solutions section, and click **Configure Per Store and Backup Gateways**.  Edit as desired for the available fields.  
      
    The Primary Gateway Retries and Backup Gateway Retries settings control how many times the software will try to contact the primary and secondary gateways respectively before displaying an error to the customer. Do not set these too high, or the delay may cause customers to give up.  
      
    
2.  Configure the backup payment gateway using the **configure** link to the right of the gateway in the listed Payment Gateways. Do not attempt to set the radio button for the backup gateway.

 Vault/Wallet-type behavior (such as with the Authorize.net CIM integration) does not work on backup gateways.  
To reverse the Backup Payment Gateway Setup, you will need to change the PaymentGatewayBackup [Setting](default.aspx?pageid=settings) directly.
      