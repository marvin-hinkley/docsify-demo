
      ---
      title: Customer
      ---

      ### Description:

This node allows you to add new customers, or update, delete, or nuke existing ones.

### Full Syntax:

<Customer Action="Add|Update|Delete|Nuke|Lookup" GUID="uniqueidentifier" ID="integer" EMail="string">  
<CustomerLevelID>integer</CustomerLevelID>  
<RegisterDate>datetime</RegisterDate>  
<EMail>string</EMail>  
<FirstName>string</FirstName>  
<LastName>string</LastName>  
<Phone>string</Phone>  
<OkToEMail>boolean</OkToEMail>  
<IsAdmin>integer</IsAdmin>  
<LocaleSetting>string</LocaleSetting>  
<MicroPayBalance>decimal</MicroPayBalance>  
<RecurringShippingMethodID>integer</RecurringShippingMethodID>  
<BillingAddress ID="integer" GUID="uniqueidentifier"/>  
<ShippingAddress ID="integer" GUID="uniqueidentifier"/>  
<CODCompanyCheckAllowed>boolean</CODCompanyCheckAllowed>  
<CODNet30Allowed>boolean</CODNet30Allowed>  
<Over13Checked>boolean</Over13Checked>  
<StoreCCInDB>boolean</StoreCCInDB>  
<StoreID>integer</StoreID>  
<AdminCanViewCC>boolean</AdminCanViewCC>  
<IsRegistered>boolean</IsRegistered>  
<LockedUntil>datetime</LockedUntil>  
<BadLoginCount>integer</BadLoginCount>  
<PwdChangeRequired>boolean</PwdChangeRequired>  
<Active>boolean</Active>  
<VATSetting>integer</VATSetting>  
<VATRegistrationID>string</VATRegistrationID>  
<Notes>string</Notes>  
<ExtensionData>string</ExtensionData>  
<Addresses AutoCleanup="true|false">  
<Address Action="Add|Update|Delete|Nuke|Lookup" GUID="uniqueidentifier" ID="integer">  
<NickName>string</NickName>  
<FirstName>string</FirstName>  
<LastName>string</LastName>  
<Company>string</Company>  
<Address1>string</Address1>  
<Address2>string</Address2>  
<Suite>string</Suite>  
<City>string</City>  
<State>string</State>  
<Zip>string</Zip>  
<Country>string</Country>  
<ResidenceType>integer</ResidenceType>  
<Phone>string</Phone>  
<Email>string</Email>  
<ExtensionData>string</ExtensionData>  
</Address>  
<Address Action="Add|Update|Delete|Nuke|Lookup" GUID="uniqueidentifier" ID="integer">  
<NickName>string</NickName>  
<FirstName>string</FirstName>  
<LastName>string</LastName>  
<Company>string</Company>  
<Address1>string</Address1>  
<Address2>string</Address2>  
<Suite>string</Suite>  
<City>string</City>  
<State>string</State>  
<Zip>string</Zip>  
<Country>string</Country>  
<ResidenceType>integer</ResidenceType>  
<Phone>string</Phone>  
<Email>string</Email>  
<ExtensionData>string</ExtensionData>  
</Address>  
<Address Action="Add|Update|Delete|Nuke|Lookup" GUID="uniqueidentifier" ID="integer">  
<NickName>string</NickName>  
<FirstName>string</FirstName>  
<LastName>string</LastName>  
<Company>string</Company>  
<Address1>string</Address1>  
<Address2>string</Address2>  
<Suite>string</Suite>  
<City>string</City>  
<State>string</State>  
<Zip>string</Zip>  
<Country>string</Country>  
<ResidenceType>integer</ResidenceType>  
<Phone>string</Phone>  
<Email>string</Email>  
<ExtensionData>string</ExtensionData>  
</Address>  
</Addresses>  
</Customer>

### Notes:

*   IsAdmin: 0=normal user, 1=admin user, 3=superadmin user
*   Customer identifiers should always be system-generated, do not try to force specific IDs or GUIDs
*   A <Password></Password> node with a password in plain text is required for the format above. For PCI compliance, if customer records are being imported in bulk, it is best to assign no password (or a random one) and force the customer to reset the password on their first login. If a <Password></Password> node is provided, the password will be salted and encrypted during the import.
*   WSI is aware of your 'AllowCustomerDuplicateEmailAddress' settings. Customers in your import with duplicate email addresses will not be imported if you don't allow that.
*   IsRegistered: Integer values are required 0=False/No 1=True/Yes.

### Warnings:

Customer data ties into a lot of different parts of the database. Be careful of the kinds of updates you make, especially nukes/deletes. Any field that customers would not normally be able to set themselves should normally be left blank during an import, and be updated either by an admin user later on, or allowed to be set during the normal operation of the site.
      