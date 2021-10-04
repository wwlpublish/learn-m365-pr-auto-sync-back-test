Device tags in Microsoft Teams let you group, organize, and easily manage the devices you've deployed in your organization. Device tags are often used in large organizations to be able to sort and filter devices based on something meaningful to the organization, such as a tag for executive devices, contact center devices, or particular categories of meeting rooms you have planned. With the Microsoft Teams admin center, you can add one or more tags to devices, use filters to view devices that match the tag you specify, and then perform actions on the devices that have that tag. To manage device tags, you need a privileged account member of one of the following roles: Global admin, Teams Service admin, or Teams Device admin.

You can add a device tag to more than one device type. However, when you open a device pane in the Microsoft Teams admin center, only the devices of that type are returned. For example, you can assign the "Corporate" tag to both phones and Teams Rooms devices. If you search for the "Corporate" tag while in Devices > Phones, only phones are returned. Similarly, if you search for the "Corporate" tag in Devices > Teams Rooms, only Teams Rooms devices are returned.

## Managing device tags

Using the device tag management panel, you can perform the following management operations:

- See all your device tags.

- Create multiple device tags easily and then assign them to devices later. Tags can be up to 25 characters.

- Remove device tags that are no longer needed. Before you can remove a device tag, you'll need to remove it from all the devices it has been added to.

- Rename device tags. When you rename a device tag, that change is reflected on all the devices it's been added to. Tags can be up to 25 characters.

To manage device tags, sign-in to the Teams Admin Center and navigate to **Devices** and then choose any device pane, such as **Phones**.

- Select **Actions** in the upper-right corner of the page and select **All device tags**.

- To create a device tag, select **+ Add**, provide a value for the device tag, and select the **Save** icon.

- To remove a device tag, select the ellipsis **...** next to the device tag you want to remove, and select **Delete**.

## Finding tagged devices

If you've added device tags to your devices, you can use them to filter the device list to return only the devices that have had a specified tag added to them. This can be helpful if you just want to view all the devices in a specific room, all the devices of a certain type, or any other criteria you used when adding your tags. If you need to perform bulk actions against all phones in a contact center, ensuring they have a tag set, will allow you to do this easily and ensure you don’t apply those changes to executives or receptionists. You can also perform bulk actions on returned devices, such as applying updates in waves, or setting different configuration policies depending on the groups of devices identified using device tags.

- Navigate to the Microsoft Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/)

- Sign in with an account that is member of one of the required privileged roles.

- Navigate to **Devices** and then choose the device pane that contains the devices you want to filter.

- Select the **Filter** icon.

    - If you only want to specify a single tag, or if you want to find devices that have all the tags you specify, select **Match all of these conditions**.

    - If you want to find devices that match one or more device tags, select **Match any one of these conditions**.

- Select the **Tag** field and then specify a device tag name in the **Enter a value** field.

    - If you want to add more device tags, select **Add more** and repeat step 6 for each tag you want to add.

- Select **Apply**.

After you've filtered the devices in your device list, you can perform actions on them as you normally would. For example, you can select them and then assign configurations, edit their settings (if they're Teams Rooms devices), and so on. When you're done, you can remove the filter by selecting the **X** next to the **Tag** filter entry or by selecting **Clear all** on the right side of the list.

