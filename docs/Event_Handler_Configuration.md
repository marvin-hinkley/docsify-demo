
      ---
      title: Event Handler Configuration
      ---

      Event Handlers are a system of callouts in the \[Company Name\] software that can post information to endpoint URLs when certain events happen on the site, making integration with 3rd-party applications easier. The software has several handlers built in, and store admins with the source code can add new events if desired.

This is an advanced tool and will require a developer to set up. Stores without source code access will only be able to use the built-in handlers. Please note that Event Handlers will not function in medium trust hosting environments!

Also, please be aware that when creating a listener page to consume the posts made by EventHandlers, you must disable validation on the page if it is written in .NET. EventHandlers post XML-formatted data, which .NET's validation flags as invalid/unsafe.

### **

Built in Event Handlers
=======================

**

From the Configuration menu, click EventHandler Configuration. \[Company Name\] includes 18 EventHandlers by default. To enable an event handler, click the **Edit** button, check the **Active** checkbox, and specify a callback URL.

The URL specified for the callback is a separate URL that a developer must create, this is not part of the \[Company Name\] software.  
  
 ![](images/1415378909656.png)

The built in event handlers are:

*   ViewProductPage 
*   ViewEntityPage 
*   AddToCart 
*   BeginCheckout 
*   RemoveFromCart 
*   CreateCustomer 
*   UpdateCustomer 
*   DeleteCustomer 
*   NukeCustomer 
*   CreateAccount 
*   CheckoutShipping 
*   CheckoutPayment 
*   CheckoutReview 
*   NewOrder 
*   OrderDeleted 
*   OrderVoided 
*   OrderShipped 
*   OrderRefunded

### **

Adding Event Handlers
=====================

**

To add a custom event handler, first add it through the admin site with the **Add New** form on the Event Handler Configuration page.

 ![](images/1415378993096.png)

  

Next, add the following code wherever you want the handler to fire within the source code:

`AppLogic.eventHandler(“CustomEventName”).CallEvent(“SomeRuntimeParams”);`

**CustomEventName** is the exact EventName specified in the admin console when the event was created

**RunTimeParams** is an ampersand-delimited string (e.g. “someparam1=sometext&someparam2=othertext”). These are included in the **Runtime** section of the package data document.
      