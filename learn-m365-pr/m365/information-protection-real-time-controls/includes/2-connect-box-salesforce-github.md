Microsoft Cloud App Security is often used to protect Microsoft apps and services such as Office 365 and Azure, but Cloud App Security threat detection policies can also be used for non-Microsoft cloud apps.

Cloud App Security uses APIs from the cloud provider to have visibility and control of the non-Microsoft services. Because these APIs are provided by the cloud provider, the capabilities of each API can differ, and the time taken to perform tasks such as scanning all files might take hours or days.

When a connection is made to a cloud app provider, Cloud App Security will scan users, files, and activities. After this initial scan, Cloud App Security periodically scans users, groups, activities, and files. Once a connection is made, you can create Cloud App Security policies.

For more information on the capabilities of Cloud App Security to manage connected apps, see **Connect your Favorite Apps to Microsoft Cloud App Security** in the **Summary** unit of this module.

The steps to connect each cloud app provider to Cloud App Security are similar and the following example uses Box:

## Connect Box to Cloud App Security

To connect Box to Cloud App Security, perform the following steps:

1. Navigate to <https://app.box.com> and sign in.

2. Select **Admin Console**.

    :::image type="content" source="../media/2-box-admin-console.png" alt-text="Admin console":::

3. Select **Apps**.

    :::image type="content" source="../media/2-box-apps.png" alt-text="Box apps":::

4. Select **Custom Apps** and select **Settings**.

    :::image type="content" source="../media/2-box-custom-apps.png" alt-text="Box custom apps":::

5. Ensure that **Disable unpublished apps by default** is disabled or enter the API key from [Connect Box to Cloud App Security \| Microsoft Docs](https://docs.microsoft.com/cloud-app-security/connect-box-to-microsoft-cloud-app-security).

6. Navigate to <https://portal.cloudappsecurity.com>.

7. Select **Investigate**, and select **Add an app**.

    :::image type="content" source="../media/2-microsoft-cloud-app-security-portal.png" alt-text="Add an app":::

8. Select **+** and select **Box**.

    :::image type="content" source="../media/2-connected-apps.png" alt-text="Connected apps":::

9. Type a name for your Box instance and select **Connect Box**.

10. Select **follow this link**.

    :::image type="content" source="../media/2-follow-this-link.png" alt-text="Follow this link":::

11. Enter your Box credentials.

12. Select **Grant access to Box**.

    :::image type="content" source="../media/2-grant-box-access.png" alt-text="Grant access to Box":::

13. Box is now being protected by Microsoft Cloud App Security.

The following video gives you an overview of connecting Box to Microsoft Cloud App Security:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyaJP]
