Most users use the Teams desktop client to connect to Teams. It’s therefore important that you know how to troubleshoot client startup and configuration. 

## Troubleshoot Teams desktop client startup 

If your users report a problem when they start the Teams desktop client, determine if the issue is related to the desktop client or the Teams service. Instruct the user to open Microsoft Edge and use the [Teams web app](https://www.microsoft.com/microsoft-teams/log-in?azure-portal=true) to sign in. If they can successfully use Teams in their browser, you can assume the problem relates to the desktop client. 

> [!TIP]
> If the user experiences problems connecting with a browser, then check service health in the Microsoft 365 admin center.

To troubleshoot the Teams desktop client, use the following high-level procedure:

1. Examine the **SquirrelSetup.log** file located in the **%LocalAppData%\Microsoft\Teams** folder. Go to the end of the file and verify if any errors are displayed. 
2. Delete the Teams client cache: 

   1. Close Teams, and if necessary, use Task Manager to ensure all Teams processes are ended. 
   2. In File Explorer, navigate to **%appdata%\Microsoft\Teams**.
   3. Open the **Cache** folder and delete its contents.
   4. Restart Teams and try to sign in. 
   5. If that doesn’t resolve the issue, in **%appdata%\Microsoft\Teams**, consider deleting the contents of the following subfolders:

       - \application cache\cache
       - \blob_storage
       - \databases
       - \GPUcache
       - \IndexedDB
       - \Local Storage
       - \tmp

   6. Restart Teams and try to sign in.

3. If clearing the cache doesn’t help, consider installing the latest updates. 
4. Finally, consider reinstalling the Teams desktop client.

## Install and troubleshoot the Teams Meeting add-in

The Teams Meeting add-in in Outlook enables users to schedule meetings from within Outlook. When the add-in is installed, in the Calendar feature in Outlook, the Teams Meeting add-in displays two tiles in the ribbon: 

- Meet Now 
- New Teams Meeting

:::image type="content" source="../media/teams-add-for-outlook.png" alt-text="A screenshot displays a portion of the Outlook ribbon in calendar view. Meet Now and New Teams Meeting tiles are displayed.":::

In addition, if a user creates a new appointment, in the **untitled – Appointment** window, the add-in displays the **Teams Meeting** tile on the ribbon. 

### Install the Teams Meeting add-in

The Teams Meeting add-in is automatically installed for users that have Microsoft Teams and either Office 2013 and newer installed on their Windows 10 computer. 

> [!IMPORTANT]
> If your users deployed Office Outlook from the Microsoft Store, the Teams Meeting add-in isn't supported. 

If users can’t see the Teams Meeting add-in, they must:

1. Close both Outlook and Teams
2. Restart the Teams client and sign in to Teams.
3. Restart the Outlook client.

> [!NOTE]
> There is no specific and separate installation method for the Teams Meeting add-in. 

### Configure required policy settings

In order for the Teams Meeting add-in to deploy, you must configure Teams meeting policies. To configure the required meeting policy setting, you can use the Microsoft Teams admin center. To do this, in the Microsoft Teams admin center:

1. Select **Meetings**, and then select **Meeting policies**. 
2. In the details pane, select the appropriate policy. 
3. Review and modify the required settings. 
4. When you’ve configured the desired settings, select **Save**. 

If your users are unable to use the Teams Meeting add-in, review the policy settings in the **General** section of the meetings policy, displayed in the following screenshot. Specifically, review the settings described in the following table.

:::image type="content" source="../media/general-settings.png" alt-text="A screenshot that displays the details page for a Meeting policy. Default settings are displayed for General.":::


| Setting                                | Description                                                  |
| -------------------------------------- | ------------------------------------------------------------ |
| **Allow the  Outlook add-in**          | Determines if  a user can schedule meetings from Outlook.    |
| **Allow  scheduling private meetings** | Determines if  users can schedule private meetings in Teams. A meeting is private if it's  not published to a channel in a team. |

Enabling the **Allow scheduling private meetings** setting enables the deployment of the add-in. 

> [!NOTE]
> The Teams client installs the correct add-in by determining if users need the 32-bit or 64-bit version.

### Troubleshoot the Teams Meeting add-in

If you experience problems with using the add-in after making the required policy changes, verify that the add-in is installed and not disabled:

1. From Outlook, select **File** and then select **Options**.
2. Select **Add-ins**.
3. Verify the presence of the **Microsoft Teams Meeting Add-in for Microsoft Outlook** in the **Active Application Add-ins** list. 
4. If the add-in appears in the **Disabled Application Add-ins** list, in **Manage**, select **COM Add-ins** and then select **Go**…
5. Set the checkbox next to **Microsoft Teams Meeting Add-in for Microsoft Office**.
6. Select **OK** on all dialog boxes and restart Outlook.

:::image type="content" source="../media/add-ins.png" alt-text="A screenshot that displays the Outlook Options window. The administrator has selected the Add-ins tab. The Microsoft Teams Meeting Add-in for Microsoft Outlook is displayed.":::

If the add-in is not installed, consider running the [Microsoft Support Recovery Assistant](https://support.microsoft.com/office/about-the-microsoft-support-and-recovery-assistant-e90bb691-c2a7-4697-a94f-88836856c72f?azure-portal=true). This tool will check for common problems, and make appropriate suggestions to resolve issues it discovers. 

If you prefer, you can perform the following tasks instead of running the Microsoft Support Recovery Assistant: 

1. Verify the user is assigned a policy that enables both **Allow the Outlook add-in** and **Allow scheduling private meetings** settings.
2. Verify the user has permission to execute regsvr32.exe.
3. Check that all available updates for Outlook desktop client have been applied.
4. Complete the following steps:

   1. Restart Teams desktop client.
   2. Sign out and then sign back in to the Teams desktop client.
   3. Restart the Outlook desktop client. 
