
      ---
      title: Shipping Zones
      ---

      From **Configuration** Menu, click **Shipping Calculation**.  
  
Zone-based shipping methods calculate shipping costs based on the zip code that the customer registered with. On this page, store administrators can create the zip code ranges they want to specify prices for, or modify/delete existing ranges. These can be large ranges that cover a large portion of the country, or individual zip codes, whatever is necessary for the site's shipping model.

Zone-based shipping is designed for US orders only! For shipping purposes, the software can only handle numeric zip codes and is not suitable for most overseas zip code formats.   
  
 Zone-based shipping requires one of the Zone-type shipping calculations in the Shipping Rates Table (Calculate Shipping By Weight & Zone or Calculate Shipping By Total & Zone).

### **Adding a Zone**

To create a new zone, click the **Go here to setup your zones** link in the Custom Shipping Calculations By Zone section on the Shipping Calculation page.  
Click the **Create** button and fill in a name for the zone and the zip code range. Keep the following things in mind for your zip codes:

*   By default the software only uses the first 3 digits of each zip code when performing its matching, so do not enter full zip codes. This can be changed with the **ZipCodePrefixLength** [Setting](default.aspx?pageid=settings) if necessary. 
*   Do not put spaces between zones or zone ranges, just commas and hypens. EX: 123,456,789-321 
*   Do not leave any trailing commas at the end of your zip code lists

 ![](images/1416268830712.png)
      