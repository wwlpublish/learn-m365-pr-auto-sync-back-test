Now we have a host pool and workspace that we can use to deploy a remote app.  Let's create a RemoteApp application group to share an application to a different user in the organization.

To complete the exercise, you'll need the credentials for a different non-administrative user account that's in Active Directory.

## Create and assign remote applications

### Step 1: Basics

1. [Sign in](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true) to the Azure portal.
1. Use the search box to find **Azure Virtual Desktop**.
1. Select **Application groups** > **Create**.
1. Select the subscription, resource group, host pool, and application type.

   :::image type="content" source="../media/4-create-application-group-basics.png" alt-text="Screenshot of the application groups basics tab filled out using values from table.":::

   |Field  |Description  |
   |---------|---------|
   |Subscription     |  Subscription where you want the app group to run       |
   |Resource group     | Resource group you've created for Azure Virtual Desktop resources      |
   |Host pool     | wvd-host-pool-1    |
   |Application group type     | RemoteApp    |
   |Application group name | RemoteApp1 |
1. Select **Next: Applications**.

### Step 2: Applications

1. Select **Add applications**.

   :::image type="content" source="../media/4-remoteapp-applications.png" alt-text="Screenshot of the applications tab with add applications highlighted.":::
1. Use the information in the following table to help you add an application. Accept the rest of the default values where not listed in the table.

   :::image type="content" source="../media/4-remoteapp-add-application.png" alt-text="Screenshot that shows WordPad selected.":::

   |Field  |Value  |
   |---------|---------|
   |Application source    |  Start menu |
   |Application    | WordPad   |
   |Display name    | WordPad  |

1. Select **Next: Assignments**.

### Step 3: Assignments

1. Select **Add Azure AD users or user groups**.

   :::image type="content" source="../media/4-remoteapp-assignment.png" alt-text="Screenshot of the assignments tab with Add Azure AD users or user groups highlighted.":::
1. Select single or multiple users or you can select user groups.
1. Select **Next: Workspace**.

### Step 3: Workspace

1. For **Register application group**, select **Yes**.

   :::image type="content" source="../media/4-remoteapp-workspace.png" alt-text="Screenshot that shows workspace tab with yes selected.":::
1. Select **Review + create**.
1. Review what you've entered and select **Create**.

## Verify access to application

1. Go to the [Azure Virtual Desktop web client](https://rdweb.wvd.microsoft.com/arm/webclient/index.html).
1. Sign in by using the user credentials for the user you assigned to the RemoteApp application group.
1. You should see the application in the workspace.
