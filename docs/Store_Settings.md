
      ---
      title: Store Settings
      ---

      From the **Configuration** menu, click **Settings**.  

Find a Setting
==============

Settings are used to control much of how the software functions. The search box within the **Filter** section at the top of the page is the easiest way to find the Setting you'd like to change. Simply type the name into the **Search All Fields** box and click **Submit**. This is also a good way to find settings if you're not sure of the name. As a rule, \[Company Name\] makes the Setting names as relevant to their function as possible. For instance, if you want to change settings for how product ratings work, a simple search for 'ratings' will return the applicable settings. Settings are also broken down into groups of settings that affect similar functions - ADMIN, GATEWAY, etc. Choosing a **Setting Group** from the dropdown list will narrow down the list of settings presented to help focus your search.   
 ![](images/1415216984653.png) 

Edit a Setting
==============

1.  Click a Setting name to edit the setting value.  
    Note that to the left of each AppConfig name, in the Store column, you will see the word "Default" to begin with. Each MultiStore install begins with Settings defined only for a single store. When checking an Setting, the software will look to see if there is a store-specific copy of that Setting. If so, that value will be used. If not, the software 'falls back' to the Default value.  
    ![](images/1415217040482.png)  
      
    
2.  Each setting includes the following fields, which are described below. Values can be displayed in dropdown menus, radio buttons, or text boxes. Edit the Value(s) as desired, and click **Save**.  
    ![](images/1415217093860.png)  
      
    
     **Name**
    
    The name of the Setting, this is used by the software and is not editable.
    
     **Value**
    
    The setting value - this can either be in a dropdown list, text box, or radio buttons. If multiple stores are in use, there will be options to configure the setting differently for each store. When setting values vary by store, a copy of the Setting is created with a unique value, and is assigned to each store individually.  You can also set the value in the Default for All Stores and it will apply to all stores.
    
     **Description**
    
    A brief description of the setting that will instruct administrators how the setting will be used.
    
     **Group**
    
    The group classification of the setting, used by the Setting Group filter on the Settings page.
    
     **SuperAdmin Only**
    
    If set to Yes, only administrators set to SuperAdmin will be permitted to edit the Setting.
    
     **Value Type**
    
    The type of the Setting. These should only be used when adding new Settings.
    
     **Allowed Values**
    
    Used by some Settings to determine what the available options are for the value.
    

Value Types
===========

Setting values are each assigned a value type. These types allow technical administrators to assign predefined values that are allowable for each Setting (if desired). This allows users who are less familiar with the technical side of the software to easily make changes without risking setting something incorrectly. Typed Settings also reduce the number of accidentally mis-set values (for example entering 'flase' instead of 'false').  
  
The supported AppConfig types are:   

**Type**

**Description**

String

String values can be any text that you wish, up to 1000 characters. Use this for passwords, URLs, etc

Boolean

Boolean values are for AppConfigs that should only ever be true or false.

Integer

Integer AppConfigs are for whole values, for example inventory limits.

Decimal

Decimal type AppConfigs can hold numbers with decimal places. This is a good setting to use for AppConfigs involving dollar amounts.

Double

This is a good type to use for numerical values that may be set very high.

Enumeration

Enumeration AppConfigs have a list of allowable values, which the admin can set once and then choose from later. Only one value can be selected at a time.

Multi-Select

These types of AppConfigs allow admins to set a list of allowable values, but multiple choices can be selected. A good example would be payment methods that are allowed.

Dynamic Invoke

This type of AppConfig pulls from values set in the code. This type can only be used along with some development work.

  

Add a New Setting
=================

To create a new setting, click the **Add Setting**  button from the Settings page.  
  
 ![](images/1415221447237.png)  
  
Simply fill in the Name, Description, and Value,  then assign a Group, and set the Value Type if necessary. When finished, click **Save**. Additional development work may be necessary for your new Setting to have any effect on store operation.  ![](images/1415221621878.png) 

### Allowed Values 

Appropriate for the following value types: Enumeration,  Multi-Select, Dynamic Invoke.  
Make this a comma separated list (or, for Dynamic Invoke ... well, if you're smart enough to be using this feature, you can most likely figure the rest out for yourself.)
      