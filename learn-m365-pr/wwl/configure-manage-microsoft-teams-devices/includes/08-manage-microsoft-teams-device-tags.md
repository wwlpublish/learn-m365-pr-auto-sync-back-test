Device tags in Microsoft Teams enable organizations to group, organize, and more easily manage the devices they've deployed. Administrators can use the Microsoft Teams admin center to:

- add one or more tags to devices.
- use filters to view devices that match the tag you specify.
- complete actions on the devices that have that tag. 

Using the device tag management panel, you can:

- See all your device tags.
- Add a device tag to more than one device type. Tags can be up to 25 characters.
- Create multiple device tags and then assign them to devices at a later time. 
- Remove device tags that are no longer needed. Before you can remove a device tag, you must remove it from all the devices it has been added to.
- Rename device tags. When you rename a device tag, that change is reflected on all the devices it's been added to.

## Create, remove, or rename device tags

Complete the following steps to create and maintain device tags:

1. Sign in to [Microsoft Teams admin center](https://admin.teams.microsoft.com?azure-portal=true).
2. In the left-hand navigation pane, select **Devices**, and then select the specific Teams device type that you want to configure (for example, IP phones, Collaboration bars, Teams displays, or Teams panels).
1. In the window that appears for the device type you selected, select **Actions** in the upper-right corner of the page and then select **All device tags**.
1. In the **Manage tags** pane that appears, you can complete any of the following tasks:

    * To create a device tag, select **+ Add**, enter a name for the device tag, and then select the **Save** icon that appears to the right of the name.

    * To remove a device tag, select the ellipsis **...** next to the device tag you want to remove, and then select **Delete**.

    * To rename a device tag, select the ellipsis **...** next to the device tag you want to rename, and then select **Edit**. Provide a new value for the device tag and then select the **Save** icon.

## Add or remove tags on a single device

When you add tags to a device, you can either select an existing tag or create a new one. 

1. Sign in to [Microsoft Teams admin center](https://admin.teams.microsoft.com?azure-portal=true).

2. In the left-hand navigation pane, select **Devices**, and then select the specific Teams device type that you want to configure (for example, IP phones, Collaboration bars, Teams displays, or Teams panels).
1. In the window that appears for the device type you selected, select the device you want to add or remove tags on (do NOT select the device name; instead, select the check mark that appears to the left of the device), and then select **Manage tags**.

    * If you want to add a tag to the selected device:
        1. Start typing the tag name you want to add.
        2. If the tag already exists, select it from the list of tags that are returned.
        3. If the tag doesn't exist, select **Add "\<tag name>" as a new tag**. 
    * If you want to remove a tag, select **X** next to the tag you want to remove.

4. Repeat these steps to add or remove more tags.
5. Select **Apply**.

## Add or remove tags on multiple devices

When you add tags to a device, you can either select an existing tag or create a new one.  If you want to remove a tag from multiple devices, you must select the Teams user that's associated with the device and remove the tag from the user.

1. Sign in to [Microsoft Teams admin center](https://admin.teams.microsoft.com?azure-portal=true).
2. In the left-hand navigation pane, select **Devices**, and then select the specific Teams device type that you want to configure (for example, IP phones, Collaboration bars, Teams displays, or Teams panels).
1. In the window that appears for the device type you selected, select the devices you want to add or remove tags on (do NOT select the device name; instead, select the check mark that appears to the left of the device), and then select **Manage tags**.
    * If you want to add a tag to the selected devices:
        1. Start typing the tag name you want to add in **Manage tags for all devices of Teams users**.
        2. If the tag already exists, select it from the list of tags that are returned.
        3. If the tag doesn't exist, select **Add "\<tag name>" as a new tag**.
    * If you want to remove a tag:
        1. Expand **Select Teams users**.
        2. Expand **\<x> tags** under the name of the Teams user you want to remove tags from.
        3. Select **X** next to the tag you want to remove.
6. Repeat these steps to add or remove more tags.
7. Select **Apply**.

## Use filters to return devices with a specific tag

Device tags can be used to filter the device list to display only the devices that are assigned a specific tag. Using filters can be helpful if you just want to view all the devices in a specific room, all the devices of a certain type, or any other criteria that were used when adding your tags. You can also complete bulk actions on the displayed devices, such as applying updates in waves, or setting different configuration policies depending on the groups of devices identified using device tags.

When you open a device pane in the Teams admin center, only the devices of that type are displayed. For example, you can assign the "Corporate" tag to both phones and Teams Rooms devices. If you search for the "Corporate" tag while in **Devices** > **IP Phones**, only phones are returned. Similarly, if you search for the "Corporate" tag in **Devices** > **Teams Rooms**, only Teams Rooms devices are returned.

Complete the following steps to use filters to return devices with a specific tag:

1. Sign in to [Microsoft Teams admin center](https://admin.teams.microsoft.com?azure-portal=true).
2. In the left-hand navigation pane, select **Devices**, and then select the specific Teams device type that you want to configure (for example, IP phones, Collaboration bars, Teams displays, or Teams panels).
1. In the window that appears for the device type you selected, select the **Filter** icon.
    * If you only want to specify a single tag, or if you want to find devices that have all the tags you specify, select **Match all of these conditions**.
    
    * If you want to find devices that match one or more device tags, select **Match any one of these conditions**.
6. Select the **Tag** field and then specify a device tag name in the **Enter a value** field.
7. If you want to add more device tags, select **Add more** and repeat the previous steps for each tag you want to add.
8. Select **Apply**.

After you've filtered the devices in your device list, you can complete actions on them as you normally would. For example, you can select them and then assign configurations, edit their settings (if they're Teams Rooms devices), and so on. When you're done, you can remove the filter by selecting the **X**  next to the **Tag** filter entry or by selecting **Clear all** on the right side of the list.


:::image type="content" source="../media/admin-2.gif" alt-text="Manage Teams device tags":::  


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”