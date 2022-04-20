Once the Azure AD Cloud Sync prerequisites are met, organizations must complete the following steps to install Azure AD Connect Cloud Sync:

1.  Install the Azure AD Connect provisioning agent.
2.  Verify the agent is installed.<br>
3.  Verify the agent is running.
4.  Configure Azure AD Connect Cloud Sync provisioning.

Each of these steps is outlined in the following sections.

### Install the Azure AD Connect provisioning agent

This section examines the installation process for the Azure AD Connect provisioning agent and how to initially configure it in the Azure portal.

> [!NOTE]
> This unit deals with installing the provisioning agent by using the Microsoft Azure AD Connect Provisioning Agent wizard. For information on installing the Azure AD Connect provisioning agent by using a command-line interface (CLI), see [Install the Azure AD Connect provisioning agent by using a CLI and PowerShell](/azure/active-directory/cloud-sync/how-to-install-pshell?azure-portal=true).

You should complete the following steps to install the Azure AD Connect provisioning agent:

1.  Sign in to the server you'll use with enterprise admin permissions.
2.  Sign in to the Azure portal, and then go to **Azure Active Directory**.
3.  On the menu on the left, select **Azure AD Connect**.
4.  On the **Provision from Active Directory** window, select **Manage Azure AD cloud sync**.

:::image type="content" source="../media/install-azure-ad-connect-provisioning-agent-5faabdd1.png" alt-text="screenshot of the Provision from Active Directory window showing the Manage Azure AD cloud sync option selected.":::


5.  On the **Azure AD Connect cloud sync** screen, select the **Download agent** option that appears in the menu bar at the top of the page.
6.  On the **Azure AD Provisioning Agent** window that appears, select the **Accept terms &amp; download** button.
7.  Once the agent has completed downloading, select **Open file**. This option will start the installation.
8.  On the **Microsoft Azure AD Connect Provisioning Agent Package** screen, accept the licensing terms and select **Install**.
9.  On the **Welcome to Azure AD Connect provisioning agent configuration wizard** page, select **Next**.
10. Sign in with your Azure AD global administrator account.
11. On the **Configure Service Account** page, select either **Create gMSA**, or **Use custom gMSA**.

:::image type="content" source="../media/configure-gmsa-service-account-6ef48539.png" alt-text="screenshot of the Configure Service Account window showing the Create gMSA option and the Use custom gMSA option.":::


12. If you allow the agent to create the account, enter the domain administrator credentials to create the group managed service account that will be used to run the agent service and then select **Next**. The account that's created will be named **provAgentgMSA$**.
13. If you specify **Use custom gMSA**, you'll be prompted to provide this account.
14. On the **Connect Active Directory** page, select **Next**. Your current domain is automatically displayed. If you wish to add more domains, enter them and select **Add Directory**. Then sign in with an administrator account from that domain.
15. You can optionally manage the preference of domain controllers the agent will use by selecting **Add Directory** and then selecting the **Select domain controller priority** check box. A list of domain controllers will appear. Order the list of domain controllers and then select **OK**.
16. On the **Agent installation** page, confirm the settings and the account that will be created and then select **Confirm**.
17. After this operation finishes, a message should appear that indicates the agent installation is complete. Select **Exit**.
18. If you still see the initial **Microsoft Azure AD Connect Provisioning Agent Package** screen, select **Close**.

### Verify the agent is installed

Agent verification occurs in the Azure portal and on the local server that's running the agent. You should complete the following steps to verify the agent is being seen by Azure:

1.  Sign in to the Azure portal.
2.  In the navigation pane, select **Azure Active Directory &gt; Azure AD Connect**.
3.  On the **Azure AD Connect** page, in the center pane, select **Manage cloud sync**.
4.  On the **Azure AD Connect cloud sync** screen, select the **Review all agents** option that appears on the menu bar.
5.  On the **On-premises provisioning agents** screen, the agents that you installed are displayed. Verify the agent you installed appears and that its **Status** is **active**.

:::image type="content" source="../media/verify-provisioning-agent-51e7f6f0.png" alt-text="screenshot of the On-premises provisioning agents window dowign the newly created agent and its Active status highlighted.":::


### Verify the agent is running

On the local server in which the agent is installed, you should then complete the following steps to verify the agent is running:

1.  Sign in to the server with an administrator account.
2.  Open **Services** by going to it or by selecting **Start &gt; Run &gt; Services.msc**.
3.  Under **Services**, verify **Microsoft Azure AD Connect Agent Updater** and M**icrosoft Azure AD Connect Provisioning Agent** are present. and that their status is **Running**.

:::image type="content" source="../media/screenshot-of-services-window-a09b6169.png" alt-text="screenshot of the Services window showing the Azure AD Connect Agent and Updater services highlighted.":::


### Configure Azure AD Connect Cloud Sync provisioning

Once the agent is installed, it must be configured and enabled before it will start synchronizing users. Complete the following steps to configure the agent:

1.  Sign in to the Azure portal, and then go to **Azure Active Directory**.
2.  On the menu on the left, select **Azure AD Connect**.
3.  On the **Provision from Active Directory** window, select **Manage Azure AD cloud sync**.
4.  Select **New configuration**.
5.  On the **New provisioning configuration** screen, select the domain you want to sync and whether to enable password hash sync. Select **Create**.
6.  The **Edit cloud sync configuration** screen will appear. Update the following sections of this screen to configure the agent:
    
    1.  **Scope**. Configure whether all users are in scope, or configure scoping filters to provision specific users and groups.
    2.  **Manage attributes**. You can map attributes between your on-premises user/group objects and the objects in Azure AD. You can customize the default attribute-mappings according to your business needs. In doing so, you can change or delete existing attribute-mappings, or create new attribute-mappings.
    3.  **Validate (recommended)**. Select the **Provision a user** button. This option verifies that synchronization is working as expected before enabling the configuration. It does so by testing with individual users that you enter after selecting the **Provision a user** button.
    4.  **Settings**. Enter a **Notification email** address. This email will be notified when provisioning isn't healthy. It's recommended that you keep the **Prevent accidental deletion** check box selected. You should also set the **Accidental deletion threshold** to a number that you wish to be notified about.
    5.  **Deploy**. Select **Enable** to sync the users and groups that are in scope as defined in the **Scope** section.

:::image type="content" source="../media/edit-cloud-sync-configuration-screen-a73b1cc6.png" alt-text="screenshot of the Edit cloud sync configuration screen.":::


7.  Move the selector to **Enable** and then select **Save**.
