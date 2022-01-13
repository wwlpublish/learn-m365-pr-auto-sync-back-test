Files in cloud storage can store sensitive information that might not be adequately protected. Using Microsoft Defender for Cloud Apps, you can scan these files and apply actions for the file. You can choose to be notified of the file matching your policy, or you can choose to automatically quarantine the file. By using quarantine, the file can be reviewed and restored if it is found to be safe. So that users know what actions have been taken, a tombstone file is uploaded in place of the quarantined file.

The available actions that can be performed on the file depend on the cloud file storage solution. For example Box can place a file into admin quarantine, and Microsoft OneDrive for Business and Microsoft SharePoint can place a file into admin quarantine once a folder has been configured.

The following example configures an admin quarantine policy for payment card information, but many other templates can be used for alternative policies.

## Configure an admin quarantine policy for payment card information

To configure an admin quarantine policy for payment card information, perform the following steps:

1. Navigate to <https://portal.cloudappsecurity.com>.
2. Select **Control** and select **Policies**.

    :::image type="content" source="../media/4-microsoft-cloud-app-security-policies.png" alt-text="Policies":::

3. Select **Create policy** and select **File policy**.
4. In **Policy template**, select **File containing PCI detected in the cloud (built-in DLP engine)**.
5. Select **Apply template**.
6. Enter a name and description in **Policy name** and **Description**.
7. In **Create a filter for the files this policy will act on** and the **Apply to** fields add any filters that you require.
8. If you want to automatically quarantine the files, in **Governance actions**, select **Put in admin quarantine**. If you are using OneDrive for Business or SharePoint, you will first need to select **Configure a quarantine folder**.

    :::image type="content" source="../media/7-governance-actions.png" alt-text="Configure a quarantine folder":::

9. Select **Create**.
