
      ---
      title: AppConfig
      ---

      ### Description:

Add, Update, or Delete an AppConfig value. AppConfigs are also referred to as Settings in the \[Company Name\] admin console.

### Full Syntax:

<AppConfig Action="Add|Update|Delete|Lookup" Name="string" Description="string" ConfigValue="string" SuperOnly="boolean"/>

### Notes:

*   You should issue a <ResetCache Confirm="true"/> at the end of any document that updates AppConfig values if you want those values to go into effect immediately.
*   If doing an Update, you must provide an ID or GUID to lookup the AppConfig. For adds, a GUID will be created if one is not provided.

### Warnings:

This node should be used with extreme care. It is entirely possible to bring the site down entirely by putting invalid values in AppConfigs, whether through the admin console or through WSI.

### Example(s):

**Add a new AppConfig:**  
<AppConfig Action="Add" Name="ComicBookSize" ConfigValue="4"/>
      