By connecting Microsoft and non-Microsoft applications to Microsoft Defender for Cloud Apps you can extend the monitoring and protection capabilities of Microsoft Defender for Cloud Apps to your applications. Each cloud app provider determines the available activities and actions that Microsoft Defender for Cloud Apps can consume via the API.

## Prerequisites

To use Microsoft Defender for Cloud Apps, the following prerequisites should be met:

- Your organization must have a license to use Defender for Cloud Apps. For pricing details, see the Defender for Cloud Apps licensing datasheet.
- To set up Defender for Cloud Apps, you must be a Global Administrator or a Security Administrator in Azure Active Directory or Office 365.
- To run the Defender for Cloud Apps portal, use Internet Explorer 11, Microsoft Edge (latest), Google Chrome (latest), Mozilla Firefox (latest), or Apple Safari (latest).

## Steps to configure Defender for Cloud Apps

These are the steps to configure Defender for Cloud Apps settings, using file monitoring as an example.

1. Navigate to the [Defender for Cloud Apps portal](https://portal.cloudappsecurity.com) and log on to your account.
2. In the Defender for Cloud Apps portal, select **Settings**, and select **Settings**.
3. In **Information Protection**, select **Files**.
4. In **Files**, select **Enable file monitoring** and select **Save**.

    :::image type="content" source="../media/2-settings.png" alt-text="Defender for Cloud Apps settings.":::

## Steps to connect an application to Defender for Cloud Apps

These are the steps to connect Office 365 to Defender for Cloud Apps, as an example. Note that file monitoring has already been enabled.

1. In the Defender for Cloud Apps portal, select **Settings**, and select **App connectors**.

    :::image type="content" source="../media/2-app-connectors.png" alt-text="App connectors." lightbox="../media/2-app-connectors-menu.png":::

2. Select **+** and select **Office 365**.

    :::image type="content" source="../media/2-office-365.png" alt-text="Office 365.":::

3. Select **Connect Office 365**. Once the connection is successfully made, you can click **Close**.

    :::image type="content" source="../media/2-connect-office-365.png" alt-text="Connect Office 365.":::

4. To select the components that will be included, select **Actions** and select **Edit settings**.

    :::image type="content" source="../media/2-edit-settings.png" alt-text="Edit settings.":::

5. Select the relevant components, select **Connect**, and select **Close**.

    :::image type="content" source="../media/2-connect-office-365.png" alt-text="Connect Office 365.":::

6. Once the application is connected, Microsoft Defender for Cloud Apps will scan the application.

The following video walks through the steps to connect an application to Defender for Cloud Apps:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4MDaX]
