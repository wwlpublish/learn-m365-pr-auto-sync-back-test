Now that we have our host pool deployed, let's create a RemoteApp application group to share an application to a different user in the organization.

## Create and assign remote applications 

### Step 1: Basics

1. [Sign in](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true) to the Azure portal.
1. Use the search box to find **Windows Virtual Desktop**.
1. Select **Application groups** > **Add**.
1. Select the subscription, resource group, host pool, and application type.

   |Field  |Description  |
   |---------|---------|
   |Subscription     |  Subscription where you want the app group to run       |
   |Resource group     | Resource group you've created for Windows Virtual Desktop resources      |
   |Host pool     | wvd-host-pool-1    |
   |Application group type     | RemoteApp    |
   |Application group name | RemoteApp1 |

   :::image type="content" source="../media/4-create-application-group-basics.png" alt-text="Screenshot of the application groups basics tab.":::
1. Select **Next: Assignments**.

### Step 2: Assignments

1. Select **Add Azure AD users or user groups**.

   :::image type="content" source="../media/4-remoteapp-assignment.png" alt-text="Screenshot of the assignments tab with Add Azure AD users or user groups highlighted.":::
1. Select single or multiple users or you can select user groups.
1. Select **Next: Applications**.

### Step 3: Applications

1. Select **Add applications**.

   :::image type="content" source="../media/4-remoteapp-applications.png" alt-text="Screenshot of the applications tab with add applications highlighted.":::
1. Use the information in the following table to help you add an application.

   :::image type="content" source="../media/4-remoteapp-addapplication.png" alt-text="Screenshot that shows Word pad selected.":::

   |Field  |Value  |
   |---------|---------|
   |Application source    |  Start menu |
   |Application    | Wordpad     |
   |Display name    | Wordpad    |
   Accept the rest of the default values.

1. Select **Next: Workspace**.

### Step 3: Workspace

1. For **Register application group**, select **Yes**.

   :::image type="content" source="../media/4-remoteapp-workspace.png" alt-text="Screenshot that shows workspace tab with yes selected.":::
1. Select **Review + create**.
1. Review what you've entered and select **Create**.

## Verify access to application

1. Go to the [Windows Virtual Desktop web client](https://rdweb.wvd.microsoft.com/arm/webclient/index.html).
1. Sign in by using the user credentials for the user you assigned to the RemoteApp application group.
1. You should see the application in the workspace. 