
      ---
      title: Allow Scripts in HTML Editor
      ---

      When entering HTML into a description (topic, product, etc), script elements may disappear when you save the entry.

  

To save scripts,  you must enable scripts in the RadEditor. Open the file that the RadEditor is being used on (for example **Admin/Controls/TopicEditor.ascx**, **Admin/entityEditProducts.aspx**, etc.) and find this line:

  

    

`<``tcontrol:RadEditor` `runat``=``"server"` `RadControlsDir``=``"rad"` `id``=``"radDescription"``>`

  

...and add the AllowScripts="true" attribute:

  

`<``tcontrol:RadEditor` `runat``=``"server"` `AllowScripts``=``"true"` `RadControlsDir``=``"rad"` `id``=``"radDescription"``>`
      