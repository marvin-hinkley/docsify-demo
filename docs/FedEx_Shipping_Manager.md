
      ---
      title: FedEx Shipping Manager
      ---

      \[Company Name\] can integrate with FedEx Ship Manager to make shipping and printing of shipping labels much easier.

Installation
============

1.  To install, download the [FedEx Ship Manager software  
      
    ](http://www.fedex.com/us/ship-manager/software/downloads.html)
2.  After the installation, the next step is mapping the FedEx fields to \[Company Name\] table fields. Map the FedEx fields to the **ShippingImportExport** table.  
      
    
3.  Go to the Integration tab at the top of the FedEx Ship Manager Software home screen and begin integrating your shipping information by selecting the FedEx Integration Assistant, a step-by-step wizard. It will guide you through the rest of the integration process. For more help please refer to the [FedEx Ship Manager User Guide  
     ![](images/1416250530987.png)](http://images.fedex.com/ca_english/businesstools/shipsoftware/pdf/FSM2500_UserGuide.pdf) 
4.  Need professional help? Contact your FedEx account executive to arrange for a customized integration solution – FedEx Integrator – for your unique data system. FedEx customer technology consultants will come to you, and provide continuing support.  
      
    
5.  Once you’ve successfully mapped all the required fields, set the **FedexShipManager.Enabled** [Setting](default.aspx?pageid=settings) to **Yes**.

Exporting Order to FedEx Ship Manager for Shipping
==================================================

From the **Orders** Menu in the \[Company Name\] admin console, click **Manage Orders**. Then select an Order, and then click the button **Send To FedexShipManager** within the Delivery Details section. This will send the order information to ShippingImportExport Table. You will now be able to lookup the orders using the FedEx Ship Manager software.  
  
For help on Order Lookup, please refer to the [FedEx Ship Manager User Guide](http://images.fedex.com/ca_english/businesstools/shipsoftware/pdf/FSM2500_UserGuide.pdf)

Tracking an Order after Shipping
================================

1.  The FedEx Ship Manager software will receive shipping tracking number and will be exported to the \[Company Name\] ShippingImportExport table.  
      
    
2.  You need to go back again to **Orders > Manage Orders** and view the Order That Has Been Shipped so that the order will be Mark as Shipped and the order tracking information will be updated in the Orders table.  
      
    
3.  The admin user will also be able to see the link in the Order management page and in Customer Account page for customers that will redirect to FedEx tracking web page.
      