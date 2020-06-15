
      ---
      title: Require Login
      ---

      Store administrators can force users to login/register before viewing the store contents.   
All [anonymous users](default.aspx?pageid=anonymous_customers) must be denied from viewing the web store.

1.  In the web.config find:  
     ![](images/1415405210597.png)  
      
    
2.  Change allow users="\*" to deny users="?". By changing this, we're denying any anonymous user access to the site except the signin.aspx page. Access to this page is given in the beginning of the web.config under the forms authentication control.  
     ![](images/1415405220032.png)  
      
    
3.  If you want anonymous visitors to be able to register a new account, to the createaccount.aspx page must be allowed. To do this, add the highlighted snippet under the forms authentication control section:  
     ![](images/1415405230205.png)
      