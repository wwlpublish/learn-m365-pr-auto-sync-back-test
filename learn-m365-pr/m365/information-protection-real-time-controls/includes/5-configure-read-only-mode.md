Business to business (B2B) communication is widespread in organizations today. This brings security challenges because it is difficult to monitor or control external users, however you want to give external users access to internal content.

To solve this problem Microsoft Defender for Cloud Apps can limit external users to read-only access for Microsoft web apps, third party web apps, and custom apps.

To apply read-only mode, you must create a policy to block downloads and another policy to block cutting, copying, or printing.

Before creating the policies, you must create a Conditional Access policy in Azure AD to route traffic to Defender for Cloud Apps.

## Create a policy to block downloads

To create a policy to block downloads, perform the following steps:

1. Navigate to <https://portal.cloudappsecurity.com>.
2. Select **Control** and select **Policies**.

    :::image type="content" source="../media/4-microsoft-cloud-app-security-policies.png" alt-text="Policies":::

3. Select **Create policy** and select **Session policy**.

    :::image type="content" source="../media/5-session-policy.png" alt-text="Session policy":::

4. Enter a name and description in **Policy name** and **Description**.
5. In **Category**, select **DLP** for data loss prevention.
6. In **Session control type**, select **Control file download (with DLP)**.
7. In **Add activity filters to the policy**, enter a name for the external user that you want to control. You can remove the filter for apps if you want the policy to apply to all apps.

    :::image type="content" source="../media/5-activity-filters.png" alt-text="Add activity filters":::

8. In **Actions**, select **Block** and, optionally, add a custom message.

    :::image type="content" source="../media/5-block-message.png" alt-text="Customize block message":::

9. Click **Create**.

## Create a policy to block cut, copy, and print

To create a policy to block cut, copy, and print, perform the following steps:

1. Navigate to <https://portal.cloudappsecurity.com>.
2. Select **Control** and select **Policies**.

    :::image type="content" source="../media/4-microsoft-cloud-app-security-policies.png" alt-text="Policies":::

3. Select **Create policy** and select **Session policy**.

    :::image type="content" source="../media/5-session-policy.png" alt-text="Session policy":::

4. Enter a name and description in **Policy name** and **Description**.
5. In **Category**, select **DLP** for data loss prevention.
6. In **Session control type**, select **Block activities**.
7. In **Add activity filters to the policy**, enter a name for the external user that you want to control. You can remove the filter for apps if you want the policy to apply to all apps.
8. In Activity type, select **Cut/Copy item** and select **Print**.

    :::image type="content" source="../media/5-activity-filters-cut-copy.png" alt-text="Cut, copy, and print":::

9. In **Actions** select **Block** and, optionally, **Customize block message**.
10. Click **Create**.

The following video gives you an overview of how to configure read-only mode for external users apps with Microsoft Defender for Cloud Apps:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyfA5]
