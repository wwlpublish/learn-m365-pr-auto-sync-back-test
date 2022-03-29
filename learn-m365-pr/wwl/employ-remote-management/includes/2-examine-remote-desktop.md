Remote Desktop Connection is a useful Windows feature that allows you to access a different PC on your network, or on the Internet, from your own PC. This feature requires that both computers are powered on and connected to Internet. If those conditions are met you can use your PC to fix problems on any other PC remotely. This feature will enable you to get full access to all files that are stored on that PC, and you will see the live desktop.

### How to use Remote Desktop

Use Remote Desktop on your Windows PC or on your Windows, Android, or iOS device to connect to a PC from afar.

1.  First, you will need to set up the remote PC to allow remote connections. On the remote PC, open **Settings** (Gear-shaped Settings icon) and select **System &gt; About**. Note the PC name, you will need this later. Then, under Related settings, select **System info**.
2.  In the left pane of the System window, select **Advanced system settings**.
3.  On the **Remote tab** of the System Properties dialog box, under **Remote Desktop**, select A**llow remote connections to this computer**, and then select **OK**.
4.  Next, in **Settings** (Gear-shaped Settings icon), select **System &gt; Power &amp; sleep** and check to make sure Sleep is set to **Never**.

On the device you wish to connect *from*, do one of the following:

 -  On your local Windows PC: In the search box on the taskbar, type **Remote Desktop Connection**, and then select Remote Desktop Connection. In Remote Desktop Connection, type the full name of the remote PC, and select **Connect**.
 -  On your Windows, Android, or iOS device: Open the Remote Desktop app (available for free from the Microsoft Store, Google Play, or the Apple App Store), and add your remote PC. Select the remote PC, and then wait for the connection to complete.

:::image type="content" source="../media/remote-desktop-connection-3977c16d.jpg" alt-text="Screenshot of remote desktop screen.":::


:::image type="content" source="../media/remote-desktop-window-2e4f1119.jpg" alt-text="Screenshot of a connection to a remote machine.":::


### Using Remote Desktop with Azure AD-joined devices

If the user who joined the PC to Azure AD is the only one who is going to connect remotely, no additional configuration is needed. To allow additional users to connect to the PC, you must allow remote connections for the local **Authenticated Users** group. Specific Azure AD users can be added with the following PowerShell cmdlet:

```
net localgroup "Remote Desktop Users" /add
"AzureAD\\the-UPN-attribute-of-your-user"

```

You can also add other Azure AD users to the **Administrators** group on a device and restrict remote credentials to **Administrators**.
