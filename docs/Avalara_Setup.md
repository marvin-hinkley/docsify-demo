
      ---
      title: Avalara Setup
      ---

      While AspDotNetStorefront supports [manually configuring tax rates for your store](default.aspx?pageid=taxes), many stores will not want to take the time to set up and manage tax rates for all the areas they sell in. To help with this, we have integrated with the AvaTax service, from [Avalara](http://www.avalara.com/). With AvaTax, you can spend a few minutes setting up your taxes and then forget about them. Avalara handles all of the tax rate setup and updates for you.  
  

### **

Installing the AddIn
====================

**

1.  First, you'll need to [get an account with Avalara](http://www.avalara.com/Contact-Us). The service \[Company Name\] integrates with is called 'AvaTax OnDemand', so make sure that's what you sign up for.  
      
    
2.  Configure the following [Settings](default.aspx?pageid=settings) with information from your new Avalara account:
    *   AvalaraTax.Account - This is your account number. It shows at the top left of the page while logged into your Avalara account.
    *   AvalaraTax.License - This is the license key given to you by Avalara when you first sign up for your account.
    *   AvalaraTax.ServiceUrl - This is the web service URL provided by Avalara that the system should call for live rates. The dev/test URL is [https://development.avalara.net](https://development.avalara.net/)
    *   AvalaraTax.CompanyCode - This is the the company code you create within your Avalara account, under the 'Organization' tab.
    *   AvalaraTax.Enabled - This setting turns the Avalara integration on and off.
3.   Set the RTShipping.Origin Settings to the address you want to use as your 'origin' address when computing taxes. Note that if you are using realtime shipping rates, this step will already have been done.  
      
    
4.  Set the Tax Code value to "FR" for the Shipping tax class on [Configuration > Tax Classes](default.aspx?pageid=product_tax_classes) page.  
     ![](images/1415230963391.png) 
    
5.  Click the **Refresh Store** button in the admin console.
    

  
  
The character length of your [Customer Level](default.aspx?pageid=customer_levels) names (if used) must not exceed 25 including spaces. Exceeding this length will throw an error when retrieving Avalara rates.  

### **

Configuring your Avalara Account
================================

**

1.  Login to your Admin Console. For testing purposes you can use this site: [https://admin-development.avalara.net](https://admin-development.avalara.net/). Once there, click on the **Organization** tab.  
      
    Next, we're going to need to setup an Organization from which to base our taxes on. This entity will possess quite a few possible configurations, depending on your company and business model. If at any time you are not sure about a specific value or configuration options, please consult a tax specialist or Avalara's support team to alleviate any unwanted side effects of incorrect taxation. **AspDotNetStorefront cannot advise on the taxes you need to collect or how to configure your Avalara account.  
    **
2.  Click the 'New' button, which will begin a 'Company Setup Wizard'. Run through these prompts, entering the information for your company. Once that is complete, you should end up back on the Organizations tab, with an entry for the company you just set up.  
      
    
3.  Click on the green N button under the 'Nexus' column for your new company, and you'll see the 'Edit' button. Click that, and you‟ll be taken to an area which allows you to choose which countries you'd like to apply tax for. By adding the United States (Check the box and save), you'll now have access to all 50 states and the ability to apply a nexus in each of them.  
      
    
4.  Click the 'United States' hyperlink on the (AvaTax/GlobalNexus/NexusCountryList.aspx) page, and you'll be taken to this URL (AvaTax/GlobalNexus/NexusRegionList.aspx?CountryId=US). Click the 'Edit' button once more, and you will see a list of the US states.  
      
    
5.  Check the states you'd like to have a nexus in and then save your selections.  
      
    
6.  At this point, your Avalara Account should be configured for proper use.

  
**You have now successfully installed the AvalaraTax AddIn. You can test it by going through the checkout process, and checking the tax values that are being returned for the Nexus regions you enabled.**  
  

You can map products to specific Avalara tax codes using the "Tax Code" field on the [Product Tax Classes](default.aspx?pageid=product_tax_classes) page.
      