Now we have a host pool and workspace that we can use to deploy a remote app.  Let's create a RemoteApp application group to share an application to a different user in the organization.

To complete the exercise, you'll need the credentials for a different non-administrative user account that's in Active Directory.

## Create and assign remote applications

### Step 1: Basics

1. [Sign in](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true) to the Azure portal.
 
1. Use the search box to find **Azure Virtual Desktop**. The Azure Virtual Desktop page appears.

1. From the resource menu under **Manage** category, select **Application groups**. The **Azure Virtual Desktop** *Application groups* pane appears.

1. In the command bar, select **Create**. The **Create an application group** pane appears.

1. On the Basics tab, enter the following values.

   |Field  |Description  |
   |---------|---------|
   |Subscription | Subscription where you want the app group to run |
   |Resource group | Resource group you've created for Azure Virtual Desktop resources |
   |Host pool | wvd-host-pool-1 |
   |Application group type | RemoteApp |
   |Application group name | RemoteApp1 |
   
   
   :::image type="content" source="../media/4-create-application-group-basics.png" alt-text="Screenshot of the application groups basics tab filled out using values from table.":::
   
1. Select **Next: Applications**. The **Create an applications group** pane appears.

### Step 2: Applications

1. The application list is empty. Let's add a few applications. Select **Add applications**. The **Add Applications** tab appears.

   :::image type="content" source="../media/4-remoteapp-applications.png" alt-text="Screenshot of the applications tab with add applications highlighted.":::
   
1. Enter the following values. Accept default values for fields that are not listed in the table.

   |Field  |Value  |
   |---------|---------|
   |Application source |  Start menu |
   |Application | WordPad |
   |Display name  | WordPad  |

   :::image type="content" source="../media/4-remoteapp-add-application.png" alt-text="Screenshot that shows WordPad selected.":::

1. Select **Save**.
1. Select **Next: Assignments**.


### Step 3: Assignments

1. Select **Add Azure AD users or user groups**.

   :::image type="content" source="../media/4-remoteapp-assignment.png" alt-text="Screenshot of the assignments tab with Add Azure AD users or user groups highlighted.":::

1. Select single or multiple users, or you can select user groups. 
1. Select **Next: Workspace**.

### Step 4: Workspace

1. For **Register application group**, select **Yes**.

   :::image type="content" source="../media/4-remoteapp-workspace.png" alt-text="Screenshot that shows workspace tab with yes selected.":::
1. Select **Review + create**.
1. Review what you've entered and select **Create**.

## Verify access to application

1. Go to the [Azure Virtual Desktop web client](https://rdweb.wvd.microsoft.com/arm/webclient/index.html).

1. Sign in by using the credentials for the user you assigned to the RemoteApp application group.

1. You should see the application in the workspace.
