
      ---
      title: OrderManagement
      ---

      ### Description:

The OrderManagement node lets you perform almost 30 common order processing functions in bulk.

### Full Syntax:

<OrderManagement Action="Void|Capture|FullRefund|ForceFullRefund|MarkAsFraud|SendReceipt|ClearFraud|BlockIP|AllowIP|SendDownloadNotification|SimulateDownloadNotification|SendDistributorNotification|ChangeOrderEMail|MarkAsReadyToShip|ClearReadyToShip|ClearNewStatus|MarkAsShipped|SetTracking|SetPrivateNotes|SetCustomerServiceNotes|SendToShipRush|SetOrderWeight|SendToFedexShippingMgr|MarkAsPrinted|GetReceipt|GetDistributorNotifications" OrderNumber="integer" Notes="text" NewEMail="text" ShippedCarrier="text" TrackingNumber="text" Weight="decimal" RefundReason="text"/>

### Notes:

*   **Void** \- Voids the specified order.
*   **Capture** \- Captures the specified order.
*   **FullRefund** \- Performs a FullRefund on the specified order, using the reason set in the 'RefundReason' attribute.
*   **ForceFullRefund** \- Does a Force Refund on the specified order.
*   **MarkAsFraud** \- Marks the specified order as fraudulent. Note that this also adds the IP address that the order came from to the blocked list.
*   **SendReceipt** \- Sends the full receipt to the customer.
*   **ClearFraud** \- Clears the fraud flag on the specified order.
*   **BlockIP** \- This adds the IP address the specified order was placed from to the blocked list, without marking the order as fraud.
*   **AllowIP** \- This unblocks the IP address used to place the specified order.
*   **SendDownloadNotification** \- Sends the download notification email for the specified order. THIS IS DEPRECATED FOR MSx9.4.0.0+
*   **SimulateDownloadNotification** \- This action updates the order record to indicate that the download notification was sent (at the time this WSI action processes), but does not actually send the email.
*   **SendDistributorNotification** \- Sends the distributor notification(s) (if any) for the specified order.
*   **ChangeOrderEMail** \- Changes the email address on the specified order to the address specified in the 'NewEmail' attribute on this WSI call.
*   **MarkAsReadyToShip** \- Sets the ready to ship flag to true for the specified order.
*   **ClearReadyToShip** \- Clears the ready to ship flag for the specified order.
*   **ClearNewStatus** \- Removes the IsNew flag from the specified order.
*   **MarkAsShipped** \- Marks the order as shipped by the carrier set in the 'ShippedCarrier' attribute, on the date specified in the 'ShippedOn' attribute if one is provided, or the current time if not.
*   **SetTracking** \- Updates the 'ShippedCarrier' and 'TrackingNumber' values on the specified order.
*   **SetPrivateNotes** \- Sets the note section that customers cannot see to the contents of the 'Notes' attribute.
*   **SetCustomerServiceNotes** \- Sets the note section that customers can see to the contents of the 'Notes' attribute.
*   **SendToShipRush** \- Exports the specified order to ShipRush, if the integration has been set up.
*   **SetOrderWeight** \- Updates the weight on the order to the decimal value in the 'Weight' attribute.
*   **SendToFedexShippingMgr** \- Exports the specified order to FedEx Shipping Manager, if the integration has been set up.
*   **MarkAsPrinted** \- Marks the specified order as printed.
*   **GetReceipt** \- Returns the receipt that the customer was sent as XML, wrapped in a CDATA tag.
*   **GetDistributorNotifications** \- Not currently implemented.
*   **OrderNumber** \- Indicates which order to care out this OrderManagement action on. This is required!
*   **Notes** \- Used with the SetPrivateNotes & SetCustomerServiceNotes actions.
*   **NewEmail** \- Used with the ChangeOrderEMail action.
*   **ShippedCarrier** \- Used with the MarkAsShipped & SetTracking actions.
*   **TrackingNumber** \- Used with the MarkAsShipped & SetTracking actions.
*   **Weight** \- Used with the SetOrderWeight action.
*   **RefundReason** \- Used with the FullRefund action.

### Warnings:

Only one order number can be managed per OrderManagement node. Note that depending on the action being carried out, processing an order can take some time (sending email, calling the gateway, etc).
      