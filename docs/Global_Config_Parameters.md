
      ---
      title: Global Config Parameters
      ---

      This page would welcome a sponsor from the \[Company Name\] community.  

  

From the **Configuration** menu, click **Global Config Parameters**.  
  
These settings affect how _ALL_ stores in the MultiStore install function. See [this page](default.aspx?pageid=varying_settings_by_store) for information on settings that can vary by store.  

**GlobalConfig Name**

**Description**

AllowAffiliateFiltering

This setting determines whether [Affiliates](default.aspx?pageid=manage_affiliates) function on all stores or if they can be mapped per store. If this is set to **Yes**, Affiliates can be mapped specifically to stores.

AllowCouponFiltering

This setting determines whether Promotions function on all stores or if they can be mapped per store. If this is set to **Yes**, promotions can be mapped per store, and customers will receive an 'Invalid Promotion' message if they try to use a coupon/promotion on a store it is not mapped to. See [this page](default.aspx?pageid=promotions) for information about Promotions. Mapping information can be found [here](default.aspx?pageid=store_mappings).

AllowCustomerDuplicateEMailAddresses

This setting determines whether customers' email addresses must be unique, or can be re-used. Allowing duplicate email addresses can cause confusion between purchases, and make accounting more complicated as multiple customer records may have the same email. We almost _always_ recommend that this be set to **No**, unless **AllowCustomerFiltering** (see below) is set to **Yes**.

AllowCustomerFiltering

If this is set to **No** (recommended), a customer that registers on one of your MultiStore sites also becomes registered on all other stores in that instance. Their login, addresses, order history, etc will be shared across all of the stores. If set to **Yes**, the customer must register independently on every store. Setting this to **Yes** requires that **AllowCustomerDuplicateEmailAddresses** be set to **Yes** as well.

AllowEntityFiltering

If this is set to **Yes**, entities (categories, manufacturers, departments, etc) will only show up on the stores that they are mapped to. See [this page](default.aspx?pageid=store_mappings) for more details.

AllowGiftCardFiltering

This setting determines whether [Gift Cards](default.aspx?pageid=gift_card_management) function on all stores or if they can be mapped per store. If this is set to **Yes**, Gift Cards can be mapped per store, and customers will receive an 'Invalid Gift Card' message if they try to use a Gift Card on a store it is not mapped to. See [this page](default.aspx?pageid=store_mappings) for more details.

AllowNewsFiltering

If this is set to **Yes**, [News Articles](default.aspx?pageid=news) will only show up on the stores that they are mapped to. See [this page](default.aspx?pageid=store_mappings) for more details.

AllowOrderOptionFiltering

If this is set to **Yes**, [Cart Upsells](default.aspx?pageid=order_options) will only show up on the stores that they are mapped to. See [this page](default.aspx?pageid=store_mappings) for more details.

AllowProductFiltering

If this is set to **Yes**, Products will only show up on the stores that they are mapped to. See [](http://manual.aspdotnetstorefront.com/p-1086-mapping-products-to-stores.aspx)[this page](default.aspx?pageid=store_mappings) for more details.

AllowRatingFiltering

If this is set to **Yes**, customer product [Ratings](default.aspx?pageid=manage_ratings) will only appear on the store they were created on, even if the product is mapped to multiple stores.

AllowShippingFiltering

If this is set to **Yes**, fixed [Shipping Methods](default.aspx?pageid=shipping_methods) will only appear on the stores they are mapped to. If this is set to **Yes**, _make sure that every store has at least one shipping method mapped to it_ or customers will be unable to check out on stores without a mapped shipping method! [Real Time Shipping](default.aspx?pageid=real_time_shipping_rates) rates cannot be mapped per store!

AllowShoppingcartFiltering

If this is set to **No**, customers can add products from multiple stores to a single cart, and check out on any of those stores. Note that **AllowCustomerFiltering** must also be set to **No** for this to function.

AllowTemplateSwitchingByLocale

If this setting is set to **Yes**, the stores in this install will be able to [switch to another skin](default.aspx?pageid=varying_the_skin_within_a_site) when a customer [chooses a locale](default.aspx?pageid=locale_settings).

AllowTopicFiltering

If this is set to **Yes**, [Topics](default.aspx?pageid=topics) will only show up on the stores that they are mapped to. See [](http://manual.aspdotnetstorefront.com/p-1374-mapping-topics-to-stores.aspx)[this page](default.aspx?pageid=store_mappings) for more details.

LicenseKey

This value should not be changed unless directed by support staff.

Anonymous.AllowAlreadyRegisteredEmail

This setting determines whether email addresses that are already used on a registered account can be used for anonymous purchases. If **Yes** anonymous users will be able to checkout with email addresses that are already in use. If **AllowCustomerDuplicateEMailAddresses** is **Yes** this setting has no effect.

BuySafe.Enabled

To enable buySAFE set this to **Yes**. If this is set to **No**, buySAFE will be disabled. 

BuySafe.EndPoint

The buySAFE API endpoint. Please do not change this setting.

BuySafe.GMS

Your buySAFE GMS (Gross Monthly Sales average).

BuySafe.Hash

The buySAFE Hash value is the unique identifier for your buySAFE account. Please contact [buySAFE](https://www.buysafe.com/about_us/contact_us.html) if you have any questions.

BuySafe.RollOverJSLocation

The buySAFE javascript location. Do not change this value.

BuySafe.TrialStartDate

The date on which your 30 day BuySAFE trial started. This is for your reference only and changing this value will have no effect on the trial period.

BuySafe.UserName

Your buySAFE user name. This will be populated automatically when starting the free trial.
      