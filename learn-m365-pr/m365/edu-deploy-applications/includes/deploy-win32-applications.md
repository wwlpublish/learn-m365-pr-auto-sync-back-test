Here, you'll learn how to install applications from the Microsoft Store for Eduction using Intune for Education.

## Use Intune for Education to buy apps from the Microsoft Store for Education

In this example, you'll see how to install a free educational/reference application.

1. Using a browser, connect to Intune for Education at [https://intuneeducation.portal.azure.com](https://intuneeducation.portal.azure.com).
1. In the Intune for Education console, Select **Apps** from the menu on the left.
:::image type="content" source="../media/3-intune-apps-menu.png" alt-text="Intune for Education Apps":::

1. On the Apps screen, Select **New App**, and then Select **New Microsoft Store app**. This will take you to the Microsoft Store for Education portal and you'll already be signed in.
:::image type="content" source="../media/3-intune-new-apps.png" alt-text="Intune for Education New App":::

1. In the Microsoft Store page, check some of the categories for suggested apps or search the Store for a free educational or reference app. Find ones that you haven't already installed during express setup for Intune for Education.

    For example, these apps are free:

    - Duolingo - Learn Languages for Free
    - Flashcards Pro
    - Khan Academy
    - My Study Life

1. Find or select the app you want to install and Select **Get the app**.

1. Repeat steps 3-5 to install another app or move to the next step.

1. In the Microsoft Store for Education portal, select Manage > Apps & software > Manage apps to verify that the apps you purchased appear in your inventory.

For example, if you bought Duolingo, it will show up in your inventory along with the apps that Microsoft automatically provisioned for your education tenant.

:::image type="content" source="../media/3-free-app-in-store.png" alt-text="Duolingo in the store":::

### Install applications for all users

Now that you've bought the apps, use Intune for Education to specify the group to install the apps for. Here, we'll show you how to install the apps you bought for all devices used by all users in your tenant.

1. In the Intune for Education console, Select the **Groups** option from the menu on the left.
:::image type="content" source="../media/3-intue-groups.png" alt-text="Intune for Education Groups":::

1. In the **Groups** page, select **All Users** from the list of groups on the left, and then in **Group member**, Select **Users**.
:::image type="content" source="../media/3-intune-all-users.png" alt-text="Intune for Education All Users":::

1. Under **Apps**, select **Windows apps**, and then select **Edit apps**.

:::image type="content" source="../media/3-intune-windows-apps.png" alt-text="Intune for Education Edit apps":::

1. Select the apps to deploy to the group. A blue check mark will appear next to the apps you select.

:::image type="content" source="../media/3-intune-select-duolingo.png" alt-text="Screenshot showing confirmed app selection":::

1. Once you're done, Select **Save** at the top of the page to deploy the selected apps to the group.

You'll be notified that app assignments are being updated. The updated All Users groups page now includes the apps you selected.

:::image type="content" source="../media/3-intune-duolingo-assigned.png" alt-text="Intune for Education assigned apps":::
