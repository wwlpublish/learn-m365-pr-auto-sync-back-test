Windows Virtual Desktop uses app groups to share RemoteApps with users. When you share an app, the user sees and can use only the application window, not the entire desktop.  

## Create and assign remote applications 

### Step 1: Basics

1. [Sign in](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true) to the Azure portal.
1. Use the search box to find **Windows Virtual Desktop**.
1. Select **Application groups** > **Add**.
1. Select the subscription, resource group, host pool, and application type.

   |Field  |Description  |
   |---------|---------|
   |Subscription     |  Subscription where you want the app group to run.       |
   |Resource group     | Create a new resource group or select an existing resource group.    |
   |Host pool     | Host pool to be associated with the application group.     |
   |Application group type     | Select RemoteApp to create an application group to publish applications. A Desktop Application Group was created when you provisioned Windows Virtual Desktop in the previous unit.   |
   |Application group name | enter a name for your RemoteApp. |

   :::image type="content" source="../media/3-create-application-group-basics.png" alt-text="Screenshot of the application groups basics tab.":::
1. Select **Next: Assignments**.

### Step 2: Assignments

1. Select **Add Azure AD users or user groups**.
1. Select single or multiple users or you can select user groups.
1. Select **Next: Applications**.

### Step 3: Applications

1. Use the information in the following table to help you add an application. 

   |Field  |Description  |
   |---------|---------|
   |Application source    |  You can select an application from the start menu or from a file path.       |
    |Application path    |  If you selected, **Application source** > **File path**, add the path to the application on the session host that's registered with the associated host pool.    |
   |Application    | If you selected **Application source** > **Start menu**, choose the application.     |
   |Display name    | If you selected **Application source** > **Start menu**, add an application name that's shown to the user on their client.     |
   |Description    | Description of the application.    |
   |Icon path    |  Path to the application icon.    |
   |Icon index    |   ???   |
   |Show in web feed    |    ??  |
   |Require command line    |  ??    |

1. Select **Next: Workspace**.

### Step 3: Workspace

1. For **Register application group**, select **Yes**.
1. For **Register application group**, select an existing workspace to register your app group to.
1. Select **Review + create** > **Create**.

## Validate the new app group

Sign in to [Windows Virtual Desktop](https://aka.ms/wvdweb) using user credentials (not your admin credentials). You should see **Word** and any other apps you added. When you select the app, only the app window opens, hiding the rest of the Windows desktop. 

To assign both full desktops with RemoteApps to a user, provision a second host pool and use the default **Desktop Application Group**.