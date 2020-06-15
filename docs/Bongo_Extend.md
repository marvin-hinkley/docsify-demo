
      ---
      title: Bongo Extend
      ---

      [Bongo International](https://bongous.com/) is a 3rd party service that allows customers outside of the United States to sign up for US forwarding addresses, which they can use when shopping on eCommerce sites. During checkout, customers can enter the US address that they got through Bongo, so your site doesn't have to worry about handling overseas shipping! Ship the customer's package to the address they entered, and Bongo will forward it on to the customer overseas.

\[Company Name\] integrates with the [Bongo Extend](https://bongous.com/extend/index.php) service, which allows US stores to tell customers about this great service through the eCommerce site, and easily expand the site's customer base to non-US countries, all at no cost to the site owner!

Once the integration is enabled, customers will see the Bongo logo on the lower left of the store site:  
 ![](images/1416331430173.png)

Customers that click the logo will see an overlay that allows them to go through the entire Bongo registration and signup process without ever leaving your site. When they're done, they can close the Bongo overlay and continue shopping on your site, using their new US address to check out:

 ![](images/1416331459419.png)

Enabling the Bongo Integration
==============================

There are 2 parts to enabling the Bongo integration:

1.  First, set the **Bongo.Extend.Enabled** [Setting](default.aspx?pageid=settings) to **Yes**, and click **Refresh Store**.  
      
    
2.  Next, make sure that the Bongo [skin token](default.aspx?pageid=skinning_tokens) is in your site's skin. It should be formatted like this:

`<``asp:Literal` `ID``=``"litBongoExtend"` `runat``=``"server"` `Text='<%$ Tokens:BongoExtend %>' />`

Once those steps have been followed, make sure you check the front-end of your site to ensure the logo is displaying correctly. The Bongo JavaScript doesn't allow that overlay to be moved, so some small adjustments to the skin might be necessary.
      