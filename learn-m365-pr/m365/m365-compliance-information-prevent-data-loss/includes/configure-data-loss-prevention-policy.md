Data loss prevention policies help identify and protect your organization's sensitive information. For example, you can set up policies to help make sure information in email and documents are not shared with the wrong people.

Now that you understand the basics of data loss policies, it's time to create your first policy.

## Start the policy creation workflow
Here are the steps involved in the DLP policy creation workflow:
- Choose the information to protect
- Name your policy
- Choose locations
- Policy settings
- Review your settings

The image below shows the steps in the policy creation workflow.

:::image type="content" source="../media/data-loss-prevention-policy-configuration.png" alt-text="A workflow diagram shows the steps through DLP policy configuration: Choose information, name your policy, choose locations, set policy settings, and finally, review the settings.":::

You can access the data loss prevention solution in several ways. One way to get started creating a DLP policy is by following these steps:

1. In the **Microsoft 365 compliance center** left menu, select **Show all** if it is visible, then select **Data loss prevention**.
2. In the **Policies** tab, click **Create Policy**.

## Choose a template to use for your policy

The DLP solution includes policy templates to help create DLP policies that meet the needs of specific categories and industries. For this scenario, you'll use one of the Financial templates to create a policy about UK financial data.

1. On the **Choose the information to protect** page, select **Financial**.
2. Select the **U.K. Financial Data** template, and then select **Next**.

## Name the policy

The next step is to give your policy a name and description. The default name and description are taken from the policy template selected in the Choose information to protect step. They can be used as-is or changed to meet your business requirements. DLP policy names must be unique and can't be changed once created. If you are using a custom policy, review a few of the policy template names and descriptions to get a feel for meaningful DLP policy names and descriptions. 

The image below shows the default name and description from the U.K. Financial Data DLP policy template. 

:::image type="content" source="../media/name-your-policy.png" alt-text="A screenshot of the Name your policy section of the DLP solution.":::

## Choose locations to apply the policy 
Locations refer to the places or services to which your policy will apply. They include:
- Exchange Online email
- SharePoint Online sites
- OneDrive for Business accounts
- Teams chat and channel messages
- Windows 10 devices
- Third-party applications and services (via integration with Microsoft Cloud App Security)

You can further refine the scope for the policy via inclusion or exclusion settings. For example, if you want to enable a small group of users, like the commodities trading desk, to exchange financial data without triggering a data loss prevention policy, you can exclude a distribution group to which they all belong from policy enforcement. As you are learning about all the options available when defining policy settings, consider creating a policy that includes a single location. That way, you can see all the configuration options available to you that might not appear when selecting more than one location at a time. Policy settings are described next.

The image below shows all the locations selected and all data in each location included in the policy. Notice that the inclusion and exclusion settings vary by location. For Exchange, it is distribution groups, while it is sites for SharePoint.
 
 source="../media/choose-locations.png" alt-text="A screenshot of the locations section of the DLP solution, with all the options selected.":::

In the next step, you'll choose which policy workflow (simple vs advanced) to use and, if needed, make changes to the policy to match your environment.