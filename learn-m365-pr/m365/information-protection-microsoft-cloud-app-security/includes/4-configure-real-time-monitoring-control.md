A bring your own device (BYOD) policy is increasingly common in the modern workplace. Furthermore, external users such as customers and temporary workers might connect to your environment. You want to allow these unmanaged devices access to some corporate resources, but want to control what actions they can perform, for example, preventing uploads and downloads, or copy and paste.

## Steps to create a block download policy for guests or external users using unmanaged devices

1. Open a policy configured with Conditional Access App Control in the Azure portal, as seen in the previous unit.
2. Select **Users and groups** and select **All guest and external users**, or select other groups to include or exclude.

    :::image type="content" source="../media/4-users-groups.png" alt-text="Users and groups.":::

3. Select **Cloud apps or actions**, select an app, and select **Select**.

    :::image type="content" source="../media/4-cloud-apps-actions.png" alt-text="Cloud apps or actions.":::

4. Add conditions. For example, to exclude managed devices, select **Conditions**, select **Device state**, select **Yes**, select **Exclude**, and select **Device Hybrid Azure AD joined** and **Device marked as compliant**. Click **Done**.

    :::image type="content" source="../media/4-device-state.png" alt-text="Device state.":::

The following video walks through the steps to configure real-time monitoring and control across cloud apps:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4MsCA]
