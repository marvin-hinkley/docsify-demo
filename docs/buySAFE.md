
      ---
      title: buySAFE
      ---

      [buySAFE](http://www.buysafe.com/) is a 3rd party service that provides your store's customers with bonds, guaranteeing them:

*   Up to $25,000 insurance on their purchase
*   $10,000 ID Theft Protection for 30 days after the purchase
*   $100 Price Guarantee against changes to prices

Customers get a bond automatically after every purchase, and handle those bonds and claims against them directly with buySAFE.

Displaying the buySAFE seal on your site shows customers that you are a reputable merchant, and increases their confidence in shopping on your site.

Note that the activation steps below being a free 30-day trial. After that, there is a fee for offering buySAFE's seal and guarantee on your site. The fee varies by site. Contact [buySAFE](http://www.buysafe.com/) for pricing information.

Activating buySAFE
==================

To turn buySAFE on, follow these quick easy steps:

1.  Make sure that at least one store with a valid production domain has been created under **Configuration > Manage Stores**.
2.  Make sure that you have configured the [email](default.aspx?pageid=email_setup) on your store.
3.  In the admin console, browse to Configuration > Site Setup Wizard. Select **Yes** next to Increase Sales with buySAFE, and click the link on the right to configure.
4.  Click the orange 'Enable Free Trial' button. 
5.  A 30 day trial account will be created for you, and the credentials will be emailed to the admin address you set up in step 2 above.
6.  Finally, make sure that the buySAFE [skin token](default.aspx?pageid=skinning_tokens) is in your site's skin. This token is 'pre-loaded' in the sample skin that comes with \[Company Name\], but customers who have upgraded or created their own skins will need to add this token manually. It should be formatted like this:

`<``asp:Literal` `ID``=``"litBuySafeSeal"` `runat``=``"server"` `Text='<%$ Tokens:BuySafeSeal %>' />`

That's it! the buySAFE seal will now appear on your site, and customers will be given guarantee numbers when they complete orders.

### Multiple Stores

If you are running multiple stores, buySAFE can track which orders came from which stores. When [adding a new store](default.aspx?pageid=adding_a_morestore), you can check the **Add to buySAFE** box to have that store added to your account automatically. You can also add stores manually through your buySAFE account.

Optional Settings
=================

There are several buySAFE settings which can be adjusted to suit your site's needs:

*   **BuySafe.DisableAddoToCartKicker** \- Setting this to **Yes** will disable the buySAFE guarantee information that is shown to customers on product pages.
*   **BuySafe.KickerType** \- Changing this will change the type of buySAFE guarantee display that is shown to customers throughout your site. There is a list of types you can use at [http://www.buysafe.com/web/general/kickerpreview.aspx](http://www.buysafe.com/web/general/kickerpreview.aspx).

buySAFE Sandbox
===============

Testing buySAFE in sandbox mode is not generally required, as there's no action required for individual items and the first 30 days are free. If desired, however, the integration can be tested against buySAFE's sandbox environment.

1.  Add a new [Setting](default.aspx?pageid=settings) called **BuySafe.UseSandbox** and set it to **Yes**.
2.  Set the **BuySafe.RollOverJSLocation** [GlobalConfig](default.aspx?pageid=global_config_parameters) to “https://sb.buysafe.com/private/rollover/rollover.js”. _Remember to keep a backup of the live value, and change this back when going live!_
      