All auto attendants and call queues require an associated resource account. Resource accounts may also be assigned service telephone numbers. This design enables organizations to assign phone numbers to auto attendants and call queues, which allows callers from outside Teams to reach the auto attendant or call queue. 

> [!NOTE]
> Teams resource accounts aren't the same as Microsoft 365 resource accounts. Microsoft 365 resource accounts are tied to an Exchange Online mailbox and enable booking of shared resources, such as rooms.

Before creating a Teams resource account and configuring it, ensure you've done the following:

* **Service numbers** - For any auto attendant or call queue that you want to be reachable directly by a service number, you must have a resource account with an associated service number.

* **Resource Account licenses** - Resource accounts that require a phone number need either a free **Microsoft Teams Phone Resource Account** license or a paid **Teams Phone Standard** user license before a phone number can be applied to the resource account.

	Your organization is allotted **Microsoft Teams Phone Resource Account** licenses depending on its overall size. Any organization that has at least one license with Teams  Phone features, including **Teams Phone Standard** and **Teams Phone with Calling Plan** licenses, has 25 Resource Account licenses available at no cost. For more information, see [Resource Account license allocation](/microsoftteams/teams-add-on-licensing/virtual-user?azure-portal=true#resource-account-license-allocation).

## Create a resource account

You can create a resource account in the Teams admin center by completing the following steps:

1. In the Teams admin center, in the left-hand navigation pane, select **Voice**, and then select **Resource accounts**.

2. Select **+ Add**.

3. In the **Add resource account** pane, enter the **Display name** and **Username** fields, and then select the appropriate **Resource account type** value. The resource account type can be either **Auto attendant** or **Call queue**, depending on how you intend to use this resource account.

	:::image type="content" source="../media/resource-options.png" alt-text="Screenshot of add resource account user interface.":::

4. Select **Save**.

	:::image type="content" source="../media/resource-accounts-page.png" alt-text="Screenshot of a list of resource accounts.":::

## Assign a license

Each resource account requires a license to work with auto attendants and call queues. You can assign a **Microsoft Teams Phone Resource Account** or **Microsoft Teams Phone Standard** to the resource account.

1. In the Microsoft 365 admin center, select the resource account to which you want to assign a license.

2. On the **Licenses and Apps** tab, under **Licenses**, select **Microsoft Teams Phone Standard**.

3. Select **Save changes**.

	:::image type="content" source="../media/resource-account-assign-virtual-user-license.png" alt-text="Screenshot of assign licenses user interface in the Microsoft 365 admin center.":::

## Assign a service number

Service numbers are optional for auto attendants and call queues. However, an organization must have at least one service number for callers to reach its auto attendant and call queue configuration.

Resource accounts can use either toll or toll-free service numbers.

If you're planning to use the resource account with an auto attendant or call queue that requires a service number, complete the following steps to assign a number to the resource account:

1. In the Teams admin center, on the **Resource accounts** page, select the resource account to which you want to assign a service number, and then select **Assign/unassign**.

2. In the **Phone number type** dropdown menu, choose the type of number that you want to use.

3. In the **Assigned phone number** box, search for the number you want to use and select **Add**.

4. Select **Save**.

	:::image type="content" source="../media/assign-number.png" alt-text="Screenshot of the assign service number user interface.":::

## Manage resource accounts 

Complete the following steps to manage resource accounts using the Microsoft Teams Admin Center:

1. In the **Teams Admin Center**, navigate to **Voice** > **Resource accounts**.
2. Select the account you want to modify.
3. Select **Edit**.
4. Modify the following options:

	- **Display name**
	- **Call queue** or **Auto attendant.** The options displayed depend on the selection made at time the resource account was created.

5. Select **Save** to apply the changes.
