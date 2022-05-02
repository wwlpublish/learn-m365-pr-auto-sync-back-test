Account information: For all of the walkthroughs in this module, you'll need to open a browser and connect to <https://compliance.microsoft.com/homepage> using your admin credentials.

If you're working with content that conflicts with a DLP policy, a policy tip can be presented to help the user understand and resolve the conflict.

To perform this task, you must be assigned a role that has permissions to edit DLP policies. Members of your compliance team who will create DLP policies need permissions to the Microsoft 365 Defender portal. By default, your tenant admin will have access to this location and can give compliance officers and other people access to the Microsoft 365 Defender portal, without giving them all of the permissions of a tenant admin. To do this, we recommend:

1. Create a group in Microsoft 365 and add compliance officers to it.
1. Create a role group on the Permissions page of the Microsoft 365 Defender portal.
1. While creating the role group, use the Choose Roles section to add the following role to the Role Group: DLP Compliance Management.
1. Use the Choose Members section to add the Microsoft 365 group you created before to the role group.

You can also create a role group with view-only privileges to the DLP policies and DLP reports by granting the View-Only DLP Compliance Management role.

These permissions are required only to create and apply a DLP policy. Policy enforcement does not require access to the content.

## Customize a tool tip

In this walkthrough, you'll see how to create a custom tool tip for a rule.

1. In the left navigation of the Microsoft Purview, at the bottom of the page under Solutions, select **Show all**.  
1. Choose **Data loss prevention**.
1. On the **Data loss prevention** page, select the **U.S. Health Insurance Act (HIPAA)** radio button, and then select **Edit Policy**.
:::image type="content" source="../media/6-edit-policy-inline.png" lightbox="../media/6-edit-policy-expanded.png" alt-text="Edit a policy.":::
1. On the **Name your DLP policy** page, select **Next**.
1. On the **Choose locations to apply the policy** page, select **Next**.
1. On the **Customize advanced DLP rules** page, to the right of the **Content matches U.S. Health Insurance Act (HIPAA) rule**, select **Edit**.
:::image type="content" source="../media/6-edit-rule-inline.png" lightbox="../media/6-edit-rule-expanded.png" alt-text="Edit a rule.":::
1. On the **Edit rule** page, scroll down the page and locate **Policy tips**.
1. Under **Policy tips** select the **Customize the policy tip text** checkbox and then enter the text that you want to add for the policy tip text, and then select **Save**.
:::image type="content" source="../media/6-policy-tip-inline.png" lightbox="../media/6-policy-tip-expanded.png" alt-text="Edit policy tip.":::
1. On the **Customize advanced DLP rules** page select **Next**.
1. On the **Test or turn on the policy** page select **Next**.
1. On the Review, your policy and create it page select **Submit**.
1. After a few seconds, the **Policy updated** page will be displayed. Select **Done**.
