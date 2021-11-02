The default settings in Exchange allow any mobile device to connect to the company's network if it adheres to the company’s required security policy. Exchange Server lets messaging administrators create allowlists, blocklists, and quarantine lists that specify which mobile devices can access their Exchange mailboxes.

This design enables messaging administrators to identify the devices that can connect to Exchange. For example, devices may only be allowed to connect to Exchange if they're running a specific operating system or they're company-owned.

### Device access state

Identifying the mobile devices that can connect to Exchange is achieved by defining the access state for each device. A device access state is the status of a particular device. A mobile device will behave differently in each access state. A mobile device can be assigned one of the following access states:

 -  **Allowed**. In the Allowed access state, a mobile device can synchronize through Exchange ActiveSync and connect to Exchange to retrieve email and work with calendar information, contacts, tasks, and notes.
 -  **Blocked**. If the device access rule identifies a device that should be blocked, that device can't connect to Exchange Online, and it will receive an HTTP 403 Forbidden (access denied) error. You can block a device for various reasons:
    
     -  You can block a device based on the device family.
     -  You can block a specific device model.
     -  You can block a device because it fails to apply the mobile device mailbox policies.
 -  **Quarantined**. When a mobile device is in a quarantined state, it can connect to Exchange, but with limited access to data. The user can add content to their calendar, contacts, tasks, and notes folders, but Exchange won't allow the device to retrieve any content from the user's mailbox.

In a restrictive organization, the IT department will only choose to allow the devices it supports, and all other devices will be blocked (as shown in the following flowchart).

:::image type="content" source="../media/restrictive-organization-mobile-device-policy-939da179.png" alt-text="Graphic showing restrictive organization mobile device policy.":::


Permissive organizations typically allow all, or most, devices to connect to Exchange. In these cases, the Allow, Block, Quarantine list can help organizations block a particular device or set of devices from connecting. This design is useful if there's a security vulnerability or if the device is putting a heavy load on the Exchange server.

In these cases, the IT department can identify the misbehaving device and block that device until a fix or update for it brings the device into compliance. All other devices, including the unknown devices, are given access (as shown in the following flowchart).

:::image type="content" source="../media/permissive-organization-mobile-device-policy-402eddaf.png" alt-text="Graphic showing permissive organization mobile device policy.":::


Quarantining devices is useful when an IT department wants to monitor new devices connecting to their organization and decide before any company data is synchronized to new devices. Both permissive and restrictive organizations may choose to employ this mechanism.

 -  In a permissive organization, quarantine can be used so that IT administrators know what devices, and which users, are making new connections.
 -  In a restrictive organization, quarantine can be used to see who is trying to work around policy and gauge demand from “Bring Your Own Device” (BYOD) users.

This logic is displayed in the following flowchart. You could also choose to quarantine at the device/device family level if necessary (this scenario isn't shown in the diagram for simplicity sake).

:::image type="content" source="../media/quaranteed-devices-cd0b5737.png" alt-text="Graphic showing quarantined mobile device policy.":::


You can change the default access level from Allow to Quarantine by using the Exchange Admin Center or the **Set-ActiveSyncOrganizationSettings** cmdlet in Exchange Management Shell.

The following example uses the Exchange Management Shell to set the default access level across the Exchange organization to Quarantine. It also sets two administrative email addresses.

```powershell
Set-ActiveSyncOrganizationSettings ‘
-DefaultAccessLevel Quarantine ‘
-AdminMailRecipients will@contoso.com, roger@contoso.com

```

The following example uses the Exchange Management Shell to set the default access level to **Allow** for a specific device type:

```powershell
New-ActiveSyncDeviceAccessRule ‘
–QueryString “Outlook for iOS and Android” ‘
–Characteristic DeviceModel ‘
–AccessLevel Allow

```

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.