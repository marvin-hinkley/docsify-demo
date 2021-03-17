---
title: 3D Secure
---
# What is 3D Secure?

\*\*

3D Secure stands for Three Domain Secure which is an XML-based protocl that is used as an added layer of security for online credit and debit card transactions. This has been developed by major card companies. Visa calls their version 'Verified by Visa' while MasterCard call theirs 'MasterCard SecureCode'. Both are referred to as 3D Secure.   

Basically, internet transactions are classed as 'cardholder not present' (CNP) transactions, which makes it hard to identify and confirm that the legitimate cardholder is the one entering the card details. 3D Secure technology was developed to reduce the frequency of fraudulent card use by authenticating the cardholder at the time of the transaction. In turn, this will reduce the incidence of disputed transactions and chargebacks.

### \*\*

# How it works

\*\*

The protocol aims to integrate the financial authorization process with the online gateway authentication. This is based on a three domain model made up of the Acquirer Domain (the merchant and the bank to which money is being paid), the Issuer Domain (the bank which issued the card being used) and finally the Interoperability Domain (the infrastructure provided by the credit card scheme to support the 3D Secure protocol). It uses XML messages sent over SSL connections with client authentication.   

A transaction using 3D Secure will be redirected to the website of the card issuing bank, where the cardholder will go through an authentication method. The authentication method is not covered by the protocol, but it is usually a password-based method. The main difference between Visa and MasterCard implementation is the method to generate the AAV (Accountholder Authentication Value). For MasterCard, they use UCAF (Universal Cardholder Authentication Field). Visa uses CAVV (Cardholder Authentication Verification Value).  

In simple terms, the behavior you will see is as such: **If** the bank that issued the customer's credit card is a member of the 3D Secure/VBV scheme a pop-up window *may* appear either asking the customer to register their card, or if they have already registered asking the customer for a password to enable them to identify themselves.   

### \*\*

# How to configure

\*\*

To configure 3D Secure go to [the Settings page](default.aspx?pageid=settings) and search for 3dSecure.CreditCardTypeIDs, then enter the [Credit Card Type IDs](default.aspx?pageid=credit_card_types) you want to use 3D secure on.   

\*\*

## The following gateways support 3D Secure Natively:

\*\*

\- [Cybersource](default.aspx?pageid=cybersource)\

* [SagePay](default.aspx?pageid=sage_pay)  

\*\*

## The following gateways use [Cardinal Commerce](default.aspx?pageid=cardinal_commerce) to obtain CAVV and ECI:

\*\*

\- [Authorize.net](default.aspx?pageid=authorize_net)\

* [eProcessingNetwork](default.aspx?pageid=e_processing_network)\
* [PayPal PayFlow Pro](default.aspx?pageid=paypal_payflow_pro)\
  - [SecureNetV4](default.aspx?pageid=securenetv4)