
      ---
      title: Downloadable Products
      ---

      This page would welcome a sponsor from the \[Company Name\] community.

  
\[Company Name\] supports products that are digitally delivered through the downloadable product feature. With download products, the setup for the download item is on the variant level. This way you can create a product that has an option of a digital download and a real shippable item.  
  
If a customer purchases only digital products, the shipping page will be skipped during checkout.

Configuring a Download Product
==============================

1.  Configure the Variant for download: To enable the download feature on a Variant, set the **Is Download** option to **Yes**.
2.  Limit access to a number of days: You can optionally set **Download is Valid for Number of Days** to limit the number of days the customer has access to the download. If you leave this field blank, the download will be available to the customer indefinitely. When the number of days has been exceeded, the download will show up in their **Expired** tab on the downloads page and they will no longer have access to download the file.
3.  Set a download location: The download location can be a location on your web server, such as **/mydownloads/downloadname.mp4** or a location on an external website such as **http://mystore.com/somefile.pdf**.   
      
    You can optionally leave the download location blank and set the download location manually after the order has been placed. The download will remain in a pending state until you specify the location and release it on the order in the admin console. If you have the **Download.ReleaseOnAction** [Setting](default.aspx?pageid=settings) set to anything other than manual, you will be sent a notification that the download item was not released and needs the file location specified.

Configuration Options
=====================

*   Release of the download item: Download items have three states that are visible to the customer on the https://yourstorename.com/downloads.aspx page: _Available, Pending & Expired_. Before an item is released, it shows up in the **Pending** tab of the page, so the customer can see that their order went through but their download is in a pending state. Once it is released, it shows up in their **Available** tab and they are able to download the item. They also receive an email when their download item is released.  
      
    You have three options for how a download will be released and it can be configured via the [Setting](default.aspx?pageid=settings) **Download.ReleaseOnAction**: Valid configurations are (MANUAL, CAPTURE, AUTO). _MANUAL_ will require admin to release on the order page. _CAPTURE_ will release on payment capture status. _AUTO_ will release the download without any requirements.  
      
    If the configuration is set to _CAPTURE_ and the payment type is not a credit card, the download will be placed in the Pending status and will need to be released manually on the order after payment is received.  
      
    
*   Streaming Download Files: The Setting **Download.StreamFile** (Yes/No) - If **Yes**, the file will be streamed and delivered on a button click instead of providing a URL to the file location. Otherwise, a link to the file will be displayed.  
      
    If this configuration is set to **No** and links are displayed, there is nothing keeping customers from sharing the link with others. The advantage for the configuration being set to **Yes** and streaming the files instead, is that customers must log into a secure page to download their file. That means the link to the file on the server cannot be shared with others and is not exposed to the customer. This should be considered before setting this configuration to **No**.  
      
    NOTE: If you are using any external file links (not from within your site files), then you must set this option to NO, as an error will occur.
  
*   Optionally copy files for each order: The Setting **Download.CopyFileForEachOrder (Yes/No)** – If **Yes**, the software will create a separate copy of each file that is purchased in a subfolder of {root}/orderdownloads. This copy will be completed when the order is released, and the path/name of the file will be stored in the Orders\_ShoppingCart table at that time.  
      
    If the configuration is set to copy the file ([Setting](default.aspx?pageid=settings): **Download.CopyFileForEachOrder**) and the file is not hosted on a different server for the website, the copying logic will be performed.  
      
    This feature can quickly use up disk space on a web server if files being copied are large. This should be considered before enabling this feature.  
      
    
*   Related Products on the Downloads page: The [Setting](default.aspx?pageid=settings) **Download.ShowRelatedProducts** - If **Yes**, the product downloads page will display related items based on the download items the customer has purchased. This configuration will honor the **DynamicRelatedProducts.Enabled** [Setting](default.aspx?pageid=settings).

Topics
------

*   **Downloads.Information:** Edit to display content and information for your customers on the download page.
*   **Download.EmailHeader:** Edit to display content at the top of the email notification that gets sent to the customer when the download is released.
*   **Download.EmailFooter:** Edit to display content at the bottom of the email notification that gets sent to the customer when the download is released.
*   **Download.MobilePageContent:** Edit to change the message the customer sees when they attempt to access the downloads page from a mobile device.

Releasing Downloads in the Admin Console
========================================

In the admin console under **[Orders > Manage Orders](default.aspx?pageid=view_manage_orders)**, the download items will appear in the General section for an order. If the order was released while the payment was finalized (due to CAPTURE, or Auto-release) then you will see a summary of the items to be released. Otherwise, if the item is pending release, you can optionally edit the download location for each download item ordered and release the item to the customer.  

Download items after the order is placed
========================================

After the order is placed, all information about a download is stored on the customer’s order record. If a download product changes, is unpublished or deleted the download item will still remain the same for the customer (product name, download location, category).
      