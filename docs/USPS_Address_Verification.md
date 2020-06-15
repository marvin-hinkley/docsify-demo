
      ---
      title: USPS Address Verification
      ---

      USPS's Address Verification service can help ensure that every address entered by a customer is a real address. This check is made when the customer creates an address, either on the registration page when first signing up, or through the account page later on. To get access to the USPS Address Information APIs that are required for address validation, do the following steps:

1\. If you already have a USPS Web Tools ID (for real time Rate Calculators) then skip directly to step 2, otherwise register for [USPS Web Tools](https://secure.shippingapis.com/registration/)

![](http://manual.aspdotnetstorefront.com/images/product/ML8/usps_addverify_form.jpg)

2\. Once you have your Web Tools ID, submit this form to request access to the [Address Information APIs](https://www.usps.com/business/webtools-address-information.htm) page.

![](http://manual.aspdotnetstorefront.com/images/product/ML8/usps_addverify_web.jpg)

3\. The check box on the form that applies to you should be "U.S. Postal Service package shipments."

**Setting USPS Web Tools ID.**
==============================

1\. Go to Configuration → Advanced → Settings  
2\. Set VerifyAddressesProvider.USPS.UserID appconfig to your USPS Web Tools ID.  
3\. Set VerifyAddressesProvider appconfig to ‘USPS’.

​

NOTE: You will notice that the service returned a valid response when the address is set in full UPPERCASE.

**Limitations**
===============

1\. The addresses are not validated on the one page checkout when Checkout.UseOnePageCheckout appconfig is set to true.

2\. The addresses are not validated for shipping addresses added during checkout when ‘AllowMultipleShippingAddressPerOrder’ appconfig is set to true.

3\. The addresses are not validated for shipping addresses added during checkout with the Smart One Page Checkout.
      