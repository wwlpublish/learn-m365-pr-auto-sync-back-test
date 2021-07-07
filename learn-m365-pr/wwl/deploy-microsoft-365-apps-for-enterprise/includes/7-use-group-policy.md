Group Policy can be used to manage general Office settings and application-specific settings, such as managed add-ins. At the application level, Group Policy can be used to control the user's first-run experience.

For example, the following steps show how to use group policy to remove all first-run experiences, which will result in a no-prompt deployment:<br>

1.  In the **Group Policy Editor**, expand the **User Configuration** to the following path: User Configuration\\Administrative Templates\\Microsoft Office 2016\\First Run
2.  Set the following settings:
    
     -  **Disable First Run Movie:** Enabled
     -  **Disable Office First Run on application boot:** Enabled
3.  Then expand the **User Configuration** to the following path: User Configuration\\Administrative Templates\\Microsoft Office 2016\\Privacy\\Trust Center
4.  Set the following settings:
    
     -  **Disable Opt-in Wizard on first run:** Enabled
     -  **Enable Customer Experience Improvement Program:** Disabled
     -  **Allow, including screenshot with Office Feedback:** Disabled
     -  **Send Office Feedback:** Disabled
     -  **Automatically receive small updates to improve reliability:** Disabled
