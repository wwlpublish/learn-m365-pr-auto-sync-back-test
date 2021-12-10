To provide the best experience for your Azure Virtual Desktop users, use FSLogix profiles. FSLogix is designed to roam profiles in remote computing environments, such as Azure Virtual Desktop. User profiles are stored in per-user VHD or VHDX files.  At sign-in, this profile container is dynamically attached to the computing environment. The user profile is immediately available and appears in the system exactly like a native user profile.

## What is FSLogix?

FSLogix is a set of solutions that decouples the local user profile from a single Windows desktop and enables it to roam between multiple Windows machines.

A user profile contains data elements about an individual, including configuration information like desktop settings, persistent network connections, and application settings. A remote user profile provides a partition between user data and the operating system.

- With FSLogix solutions you can:
- Maintain user context in pooled desktop environments
- Minimize sign in times for pooled desktop environments
- Optimize file IO between session host and remote profile store

## Create FSLogix profile for Azure Virtual Desktop users

To use FSLogix to separate user profiles from the session host virtual machines (VM), we’ll need to configure Azure Storage and create an FSLogix profile share. These steps vary depending on the storage type and whether you’re using Azure Active Directory Domain Services (Azure AD DS) or Active Directory Domain Services (AD DS). The following steps cover how to configure Azure Files with Azure AD DS. The steps for AD DS are the same except for the “Enable Azure Active Directory authentication” section. The differences are called out in that section.

## Create the storage account

1. Sign in to the [Azure Portal](https://ms.portal.azure.com/?azure-portal=truey#home).
1. Search for **Storage accounts** by using the Azure portal search box.
1. In the Storage Accounts command bar, select Create. The Create a storage account page appears.
1. Under *Project Details* select the **Subscription**, and then select or create a **Resource group** to contain your storage resources.
1. Under *Instance details*, enter a unique name for your Storage account.
1. Select the same Region as the AVD host pool.
1. For performance, select **Premium**.
1. For Premium Account type select File shares.
1. Leave **Redundancy** set to **Locally-redundant storage (LRS)**.
1. Select **Review + create** to validate your inputs, and then select **Create**.
1. Wait for the deployment to complete. This may take a minute.
1. Select **Go to resource**. The **Storage account** page displays details about your storage account.

## Enable Azure Active Directory authentication

1. Go to the [Azure Virtual Desktop web client](https://rdweb.wvd.microsoft.com/arm/webclient/index.html).

1. Sign in by using the credentials for the user you assigned to the RemoteApp application group.

1. You should see the application in the workspace.

Provide users a local profile experience, which can eliminate many compatibility issues with solutions that rely on folder redirection

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
