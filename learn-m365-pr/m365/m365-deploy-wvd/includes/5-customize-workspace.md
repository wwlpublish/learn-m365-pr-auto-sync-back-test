

## Change the name of your workspace

1. [Sign in](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true) to the Azure portal.
1. Use the search box to find **Windows Virtual Desktop**.
1. Select **Workspace**.
1. Select the workspace you want to customize.
1. Under **Settings**, select **Properties**.
1. Update the **Friendly name**.

   :::image type="content" source="../media/5-workspace-properties.png" alt-text="Screenshot that shows workspace tab with yes selected.":::

## Change the name of your virtual desktops

1. In **Windows Virtual Desktop**, select **Application groups**.
1. Select the application group you want to customize.
1. Under **Settings**, select **Properties**.
1. Update the **Friendly name**.

   :::image type="content" source="../media/5-appgroup-properties.png" alt-text="Screenshot that shows workspace tab with yes selected.":::

## Configure RDP properties 

1. In **Windows Virtual Desktop**, select **Host pools**.
1. Select the host pool you want to configure.
1. Under **Settings**, select **Properties**.
1. Select **RDP Settings**.
1. When you're done, select **Save**.

   :::image type="content" source="../media/5-hostpool-settings-rdp.png" alt-text="Screenshot that shows workspace tab with yes selected.":::

## Install the Windows Virtual Desktop Client for Windows

In the previous units, we used the browser to connect to the Windows Virtual Desktop workspace. That option is helpful when you need to do some work and don't have your device with you. But for the best experience, we recommend you run Windows Virtual Desktop directly from your device.

1. [Download the Windows Virtual Desktop Client](https://aka.ms/wvd/clients/windows) and install it.
2. Launch the Windows Virtual Desktop Client Desktop app.

   :::image type="content" source="../media/5-wvd-app-get-started.png" alt-text="Screenshot that shows workspace tab with yes selected.":::
1. Select **Subscribe with an alternate URL**.
1. Enter the URL https://rdweb.wvd.microsoft.com/api/arm/feeddiscovery.
 
    :::image type="content" source="../media/5-subscribe-workspace.png" alt-text="Screenshot that shows workspace tab with yes selected.":::
1. Select Next.
1. Use sign-in credentials for a user that has the desktop or apps group assigned.
1. You should see the app you added to the remoteapp application group.

   :::image type="content" source="../media/5-remote-desktop-workspace.png" alt-text="Screenshot that shows workspace tab with yes selected.":::
