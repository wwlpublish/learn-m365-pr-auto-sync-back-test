Now that you understand what DLP is and how you can use it in Teams, let's create a new DLP policy to protect sensitive information in Teams chat and channels. By creating DLP policies, admins can help prevent sensitive information from unintentionally being shared or leaked—either inside or outside of the organization.

> [!NOTE]
> When creating a policy for use with Teams, you must include other technologies that Teams uses; Exchange email, SharePoint sites, and OneDrive accounts as you will see in this section.

Account information: For all of the walkthroughs in this learning path, you will need to open a browser and connect to <https://compliance.microsoft.com>. Sign in to the Compliance Center using your own admin account. You will need proper licensing to access the Compliance Center.

## Create a new policy using an existing template

1. In the left navigation of the Microsoft 365 Compliance, at the bottom of the page under Solutions, select **Show all**.
:::image type="content" source="../media/5-show-all-inline.png" lightbox="../media/5-show-all-expanded.png" alt-text="Show all.":::
1. Under **Solutions** select **Data loss prevention**, and then select **+ Create policy**.
:::image type="content" source="../media/5-data-loss-prevention-inline.png" lightbox="../media/5-data-loss-prevention-expanded.png" alt-text="Create policy.":::
1. On the **Start with a template or create a custom policy page**, under **Categories**, select **Medical and health**.
1. In the **Templates** list, select **U.S. Health Insurance Act (HIPAA)**.
1. Review the U.S. Health Insurance Act (HIPAA) template description and then select **Next**.
:::image type="content" source="../media/5-start-template-hipaa-inline.png" lightbox="../media/5-start-template-hipaa-expanded.png" alt-text="Start HIPAA template.":::
1. On the **Name your DLP policy** page, review the default name and description and then select **Next**.
1. On the **Choose locations to apply the policy page**, select **Exchange email, SharePoint sites, OneDrive accounts, Teams chat and channel messages**.
:::image type="content" source="../media/5-template-locations-inline.png" lightbox="../media/5-template-locations-expanded.png" alt-text="Choose locations.":::

## Customize the policy

In this part, you will customize the DLP policy by excluding this policy from everyone in the Leadership team. By excluding members of the Leadership team from this policy, you are free to create a policy just for those users that can be tailored for their needs. For example, you could create a policy with different tip information that they can take action upon.

1. On the **Choose locations to apply the policy** page, to the right of **Teams chat and messages**, select **Exclude account**.
:::image type="content" source="../media/5-template-exclude-account-inline.png" lightbox="../media/5-template-exclude-account-expanded.png" alt-text="Exclude account.":::
1. On the **Teams chat and channel messages** page, select **Leadership**, and then select **Done**.
:::image type="content" source="../media/5-exclude-leadership-team-inline.png" lightbox="../media/5-exclude-leadership-team-expanded.png" alt-text="Exclude leadership team.":::
1. On the **Choose locations to apply the policy** page, select **Next**.
1. On the **Define policy settings** page, confirm the **Review and customize default settings from the template** radio button is selected and then select **Next**.
1. On the **Info to protect** page, under **Detect when this content is shared from Microsoft 365**, select **Only with people inside my organization**, and then select **Next**.
:::image type="content" source="../media/5-info-to-protect-inline.png" lightbox="../media/5-info-to-protect-expanded.png" alt-text="Information to protect.":::
1. On the **Protection actions** page, under **When content matches the policy conditions, show policy tips to users and send them an email notification**, select **Customize the tip and email**.
1. On the **Customize policy tips and email notifications** page, select **Add or remove people** and add the email address for the HIPAA officer (or equivalent) in your organization, and then select **Save**.
:::image type="content" source="../media/5-customize-tip-and-email-inline.png" lightbox="../media/5-customize-tip-and-email-expanded.png" alt-text="Customize policy tip and email.":::

    > [!NOTE]
    > This is the page where you can optionally customize the email and policy tip that will be generated when the DLP policy detects sensitive information. You can add information for the user to help them properly deal with the alert.

1. On the **Protection actions** page, select **Next**.
1. On the **Customize access and override setting** page, select options to restrict third-party apps using Microsoft Defender for Cloud Apps, and then select **Next**.
1. On the **Test or turn on the policy** page, leave the **I'd like to test it out first** radio button selected and select the **Show policy tips while in test mode** check box, and then select **Next**.
:::image type="content" source="../media/5-test-turn-on-policy-inline.png" lightbox="../media/5-test-turn-on-policy-expanded.png" alt-text="Test or turn on the policy.":::
1. Review the policy settings and then select **Submit**. After a few seconds, the **New policy created** page will be displayed. Select **Done**.
