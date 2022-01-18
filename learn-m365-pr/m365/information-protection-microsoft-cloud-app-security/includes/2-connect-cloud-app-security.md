By connecting Microsoft and non-Microsoft applications to Microsoft Cloud App Security you can extend the monitoring and protection capabilities of Microsoft Cloud App Security to your applications. Each cloud app provider determines the available activities and actions that Microsoft Cloud App Security can consume via the API.

## Prerequisites

To use Microsoft Cloud App Security, the following prerequisites should be met:

- Your organization must have a license to use Cloud App Security. For pricing details, see the Cloud App Security licensing datasheet.
- To set up Cloud App Security, you must be a Global Administrator or a Security Administrator in Azure Active Directory or Office 365.
- To run the Cloud App Security portal, use Internet Explorer 11, Microsoft Edge (latest), Google Chrome (latest), Mozilla Firefox (latest), or Apple Safari (latest).

## Steps to configure Cloud App Security

These are the steps to configure Cloud App Security settings, using file monitoring as an example.

1. Navigate to the [Cloud App Security portal](https://portal.cloudappsecurity.com) and log on to your account.
2. In the Cloud App Security portal, select **Settings**, and select **Settings**.
3. In **Information Protection**, select **Files**.
4. In **Files**, select **Enable file monitoring** and select **Save**.

    :::image type="content" source="../media/2-settings.png" alt-text="Cloud App Security settings.":::

## Steps to connect an application to Cloud App Security

These are the steps to connect Office 365 to Cloud App Security, as an example. Note that file monitoring has already been enabled.

1. In the Cloud App Security portal, select **Settings**, and select **App connectors**.

    :::image type="content" source="../media/2-app-connectors.png" alt-text="App connectors." lightbox="../media/2-app-connectors-menu.png":::

2. Select **+** and select **Office 365**.

    :::image type="content" source="../media/2-office-365.png" alt-text="Office 365.":::

3. Select **Connect Office 365**. Once the connection is successfully made, you can click **Close**.

    :::image type="content" source="../media/2-connect-office-365.png" alt-text="Connect Office 365.":::

4. To select the components that will be included, select **Actions** and select **Edit settings**.

    :::image type="content" source="../media/2-edit-settings.png" alt-text="Edit settings.":::

5. Select the relevant components, select **Connect**, and select **Close**.

    :::image type="content" source="../media/2-connect-office-365.png" alt-text="Connect Office 365.":::

6. Once the application is connected, Microsoft Cloud App Security will scan the application.

The following video walks through the steps to connect an application to Cloud App Security:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4MDaX]
