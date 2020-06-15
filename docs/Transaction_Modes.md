
      ---
      title: Transaction Modes
      ---

      The transaction mode for your site determines when the funds for credit card, Google Checkout, and PayPal orders are actually collected. This setting is controlled by the TransactionMode [Setting](default.aspx?pageid=settings). The choices are:

**AUTH** \- Setting TransactionMode to Auth only will instruct the software to verify funds with the merchant gateway, but not actually collect the funds yet. Store admins will have to manually click the 'Capture' button for each order under **Orders > Manage Orders**.

Each gateway has a set time that they will hold authorizations. Once that time period is passed, they will not allow you to collect the funds without running the card again. Check with your gateway to find out how long they allow.

**AUTH CAPTURE** \- This TransactionMode setting tells the software to automatically collect the funds from customers when the order is initially placed. Store admins will not have to click 'Capture' to complete payment of orders.
      