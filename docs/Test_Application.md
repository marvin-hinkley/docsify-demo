
      ---
      title: Test Application
      ---

      Most sites using the WSI feature may need a developer to create an application that interfaces with the WSI service. Those applications will vary from simple import/update tools, to 'middleware' apps that sit between your store site and external sites or applications, allowing integration between the two.

For very simple WSI-based tasks, or just to use as an example for developing your own application, we have provided a basic test program that sends an XML request to your WSI service. The test application can be downloaded [here (C#)](docs/WSITestProgram.zip) or [here (VB)](http://manual.aspdotnetstorefront.com/download/WSIImportTester(VB).zip).

The .zip files that you download contain several test/sample tools. The included Readme.txt file explains the use of several of them, which demonstrate how to use WSI along with the built-in [event handlers](default.aspx?pageid=eventhandler_configuration) feature.

For testing basic WSI functionality, however, we are interested in the WindowsApplication1.exe file located in the WSIEventSampleClient\\WSIImportTester\\WindowsApplication1\\bin\\Debug folder. Run that file, and you should see this screen:

![](http://manual.aspdotnetstorefront.com/images/wsi/test_app_main.png)

There are several parts to using this tool:

**WSI**: Change this to the URL of the ipx.asmx page on your site, ie http://www.youstore.com/ipx.asmx

**USE WSE3 Token Authentication**: If this is checked, the password supplied must be the hashed password copied directly from your admin account's record in the Customer table in your store database. We highly recommend that this method be used.

**E-Mail**: This should be the email address of the admin account you're going to use to authenticate through WSI.

**Password**: If the checkbox described above is checked, use the hashed password for your admin account from the database. If not, enter your admin password here in plain text.

**Top text field**: Place your WSI-formatted XML in this field. Examples of operations that can be performed and how to format the XML can be found throughout this manual.

**GO!**: Clicking this button sends the XML entered above to the web service for processing.

**Show Raw Errors**: Check this box to show more detailed error message information if the application encounters any errors. Clear this box to show 'friendly' error messages.

**Pretty Print XML Above**: Click this button to indent/align the XML you pasted into the top text box. This is a quick test of whether your XML is properly formatted. If your XML fails to align properly there is a problem with your XML.

**Bottom text field**: The bottom text field will contain any results that are returned by WSI after running the XML that you submitted above.
      