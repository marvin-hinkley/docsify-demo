
      ---
      title: SSL
      ---

      The shopping cart software fully supports SSL certificates, and we highly recommend that all sites purchase one. Even if CC information is not being stored, it is a very good idea to secure your site. Many customers will not go through a checkout process they do not feel is secure, and some of the payment gateways actually require that SSL be used (check with your gateway on this).  
  
\[Company Name\] staff cannot assist with the installation of the certificate on your site. Questions of that nature should be directed to your host, or the certificate authority you purchased the cert from. Before trying to enable SSL in the cart, ensure that the certificate is properly installed by going to https://www.yoursite.com. If the page loads without any warnings (on https), the cert is functioning.  
  
There are several things to remember when purchasing an SSL certificate:

\- Our software does not support shared certificates  
\- Some of the 3rd-party services our software interacts with (such as Google Checkout) have lists of certificate authorities that they will accept. Purchasing an SSL certificate from a company not on that list will lead to issues. Be sure you purchase a certificate from a large, reputable company to avoid this type of issue.

In order to use SSL on multiple site domains (MultiStore), a certificate that supports multiple domains is required, or multiple single site certificates. You will also need to create a new LiveServer setting for each store and set it to the appropriate domain.  

Enabling SSL
============

Once the SSL certificate is installed on the site and working, follow these steps to make the shopping cart use it:

1.  Set the **UseSSL** Setting to true.
2.  Set the **LiveServer** Setting to 'yourdomain.com' (no www).
3.  If customers must access your site at www.yourdomain.com instead of just yourdomain.com for the SSL to work, set the **RedirectLiveToWWW** Setting  to true.
4.  If you want the cart to go non-secure again on pages that don't need to be secured (product pages, home page, etc), set the **GoNonSecureAgain** Setting to true.
      