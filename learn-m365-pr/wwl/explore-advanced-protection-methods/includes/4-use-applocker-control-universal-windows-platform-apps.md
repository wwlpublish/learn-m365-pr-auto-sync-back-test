To enable AppLocker restrictions for the Universal Windows apps, you must configure the appropriate Group Policy settings by performing the following procedure:

1.  Open the **Local Group Policy editor** (gpedit.msc).
2.  Under **Local Computer Policy**, in the left pane, navigate to **Computer Configuration\\Windows Settings\\Security Settings\\Application Control Policies\\AppLocker**, and then select **Packaged app Rules**.
3.  Right-click **Packaged app Rules**, and then select **Create New Rule**.
4.  Use the **Create Packaged App Rules Wizard** to configure the application restriction policy with the following settings:
    
     -  Configure the permissions to allow or deny the app.
     -  Select an app publisher. You can select an installed app as a reference.
     -  Modify the rule by making the rule apply to:
        
         -  Only the specific version of the app that you select.
         -  Any apps from the publisher.
         -  Any apps from any publisher.
     -  Define exceptions.
     -  Name the policy.

5.  Create the default rule. This default rule has a lower precedence, but it enables all signed packaged apps to run. To create the default rule, right-click **Packaged app Rules**, and then select **Create Default Rules**.
6.  Select the enforcement level. By default, policies are enforced. You can change the policy to audit policies only. To do this:
    
     -  Right-click the **AppLocker** node, and then select **Properties**.
     -  In the **AppLocker Properties** dialog box, select the **Configured** check box adjacent to **Packaged app rules**. In the list, depending on your requirements select either **Enforce rules** or **Audit only**, and then select **OK**.

:::image type="content" source="../media/app-locker-access-5e95ab0d.jpg" alt-text="AppLocker window":::


### Enabling the Application Identity service

Enforcement of AppLocker rules requires that the Application Identity service must run on all computers affected by your AppLocker policy. This service identifies applications, and then processes the AppLocker policies against the identified applications. You can enable this service by opening Services.msc, and then selecting the Application Identity service. Configure the service for automatic startup, and then start the service manually. You also can start the service by configuring the setting through a GPO.
