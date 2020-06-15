
      ---
      title: GetGUID
      ---

      ### Description:

This node returns a specified number of GUIDs that are compatible with the storefront software, which you can use for creating new objects. If your interface application is capable of generating its own SQL GUIDs, then you won't need to use this.

### Full Syntax:

<GetGUID Count="integer"/>

### Notes:

*   You cannot generate these GUIDs and use them in the same WSI call. Your application would need to send this request to WSI, get the GUIDs back, and then insert them into a separate XML call which you can then send to WSI.

### Warnings:

None

### Example(s):

**This returns 10 GUIDs**  
<GetGUID Count="10 "/>
      