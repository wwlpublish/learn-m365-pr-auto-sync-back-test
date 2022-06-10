Microsoft Purview Information Barriers (IB) policies can play an integral part in an organization. However, they can also cause issues if they're improperly configured. For example, an improperly configured IB policy can prevent collaboration when collaboration should be allowed. As such, it's critical that administrators understand the capabilities and consequences of information barrier policies.

Organizations can configure IB using the Microsoft Purview compliance portal or by using Office 365 Security and Compliance PowerShell. For organizations configuring IB for the first time, it's recommended they use the Information barriers solution in the compliance portal. However, if you're managing an existing IB configuration and you're comfortable using PowerShell, you still have this option.

### Configuration concepts

When an organization configures information barriers, it must be familiar with the following objects and concepts:

 -  **User account attributes**. These attributes are defined in Azure Active Directory (or Exchange Online). These attributes can include department, job title, location, team name, and other job profile details. You'll assign users or groups to segments with these attributes. See the list of [IB supported attributes](/microsoft-365/compliance/information-barriers-attributes?azure-portal=true) for details.
 -  **Segments**. Segments are attributes that an administrator uses to define the IB policy for a group. These attributes are taken from the list of attributes that a group is part of. For example, a segment called HR is defined using a value in the Department attribute. Defining segments doesn't affect users. It just sets the stage for defining and applying information barrier policies.
 -  **Information barrier policies**. IB policies determine communication limits or restrictions. When you define IB policies, you choose from two kinds of policies:
     -  **Block policies**. Prevent one segment from communicating with another segment.
     -  **Allow policies**. Allow one segment to communicate with only certain other segments.
        
        > [!NOTE]
        > For allow policies, non-IB groups and users won't be visible to users included in IB segments and policies. If you need non-IB groups and users to be visible to users included in IB segments and policies, you must use block policies.
 -  **Policy application**. Policies must be applied after all IB policies are defined, and you're ready to apply them in your organization.
 -  **Visibility of non-IB users and groups**. Non-IB users and groups are users and groups excluded from IB segments and policies. Depending on the type of IB policies (block or allow), the behavior for these users and group will differ in Microsoft Teams, SharePoint, OneDrive, and in your global address list.
     -  For users defined in allow policies, non-IB groups and users won't be visible to users included in IB segments and policies.
     -  For users defined in block policies, non-IB groups and users will be visible to users included in IB segments and policies.
 -  **Group support**. Only Modern Groups are currently supported in IB. Distribution Lists/Security Groups are treated as non-IB groups.
 -  **Hidden/disabled user accounts**. For hidden/disabled accounts in an organization, the **HiddenFromAddressListEnabled** parameter is automatically set to **True** when the users' accounts are hidden or disabled. In IB-enabled organizations, these accounts are prevented from communicating with all other user accounts. In Microsoft Teams, all chats including these accounts are locked or the users are automatically removed from conversations.

### Planning information barrier policies

Organizations must consider the following questions before configuring information barrier policies:

 -  What are the legal or industry regulations regarding the groups inside your organization?
 -  Are there any groups who should be prevented from communicating with another group?
 -  Are there any groups that should be allowed to communicate only with one or two other groups?

These questions can help an organization get a picture on what IB policies they must implement inside their organization. Once they begin creating policies, they can separate the policies into two types:

 -  **Block policies.** These policies prevent one group from communicating with another group.
 -  **Allow policies.** These policies allow a group to communicate with only certain groups.

When determining how to segment the groups, create a list of policies for each of these two types. Then create a list of segments for your organization. Users who will be included in information barrier policies should belong to a segment.

> [!IMPORTANT]
> Plan your segments carefully because a user can only be in one segment. Also, each segment can have only one information barrier policy applied.

### Configure information barriers for Microsoft 365

Use the following steps to configure information barriers for your organization.

:::image type="content" source="../media/configure-information-barriers-4ed133be.png" alt-text="diagram showing the steps required to configure information barriers that are covered in the following table":::


The following table provides a summarized view of each step along with other resources.

| **Step**                                                                                                                                                                                       | **What's involved**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Step 1: [Make sure prerequisites are met](/microsoft-365/compliance/information-barriers-policies?azure-portal=true#prerequisites).                                  | - Verify that you have the [required licenses and permissions](/microsoft-365/compliance/information-barriers?azure-portal=true).<br>\- Verify that your directory includes data for segmenting users.<br>\- Enable [search by name for Microsoft Teams](/microsoftteams/teams-scoped-directory-search?azure-portal=true).<br>\- Make sure audit logging is turned on.<br>\- Make sure no Exchange address book policies are in place.<br>\- Use PowerShell.<br>\- Provide admin consent for Microsoft Teams.<br> |
| Step 2: [Segment users in your organization](/microsoft-365/compliance/information-barriers-policies?azure-portal=true#part-1-segment-users).                        | - Determine what policies are needed.<br>\- Make a list of segments to define.<br>\- Identify which attributes to use.<br>\- Define segments in terms of policy filters.<br>                                                                                                                                                                                                                                                                                                                                                                                          |
| Step 3: [Define information barrier policies](/microsoft-365/compliance/information-barriers-policies?azure-portal=true#part-2-define-information-barrier-policies). | - Define your policies (don't apply yet).<br>\- Choose from two kinds (block or allow).<br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Step 4: [Apply information barrier policies](/microsoft-365/compliance/information-barriers-policies?azure-portal=true#part-3-apply-information-barrier-policies).   | - Set policies to active status.<br>\- Run the policy application.<br>\- View policy status.<br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Step 5: [Configuration for information barriers on SharePoint and OneDrive (optional)](/microsoft-365/compliance/information-barriers-policies?azure-portal=true).   | - Configure IB for SharePoint and OneDrive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Step 6: [Information barriers modes (optional)](/microsoft-365/compliance/information-barriers-policies?azure-portal=true).                                          | - Update IB modes if applicable.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

### Identify segments

In addition to an organization's initial list of policies, it should make a list of segments. Users who will be included in IB policies should belong to a segment. Organizations should plan its segments carefully as a user can only be in one segment. Each segment can have only one IB policy applied.

An organization should identify the attributes in its directory data that will be used to define segments. For example, it can use **Department,MemberOf,** or any of the supported IB attributes. The organization should ensure that it has values in the attribute it selects for users. If an organization's directory data doesn't have values for the attributes it wants to use, then the user accounts must be updated to include that information before it can proceed with configuring IB. For more information, see the [supported attributes for IB](/microsoft-365/compliance/information-barriers-attributes?azure-portal=true).

### Create IB policies

When an organization creates IB policies, it must determine whether it needs to prevent communications between certain segments or limit communications to certain segments. Ideally, an organization will use the minimum number of IB policies to ensure it's compliant with internal, legal, and industry requirements. Organizations can use the Microsoft Purview compliance portal or PowerShell to create and apply IB policies.

> [!TIP]
> For user experience consistency, we recommend using Block policies for most scenarios if possible.

Once an organization has defined its list of user segments and the IB policies it wants to define, it should select a scenario and then follow the corresponding steps.

 -  [Scenario 1: Block communications between segments](/microsoft-365/compliance/information-barriers-policies?azure-portal=true)
 -  [Scenario 2: Allow a segment to communicate only with one other segment](/microsoft-365/compliance/information-barriers-policies?azure-portal=true)

> [!IMPORTANT]
> An organization should ensure that as it defines policies, it doesn't assign more than one policy to a segment. For example, if it defines one policy for a segment called **Sales**, it shouldn't define an additional policy for the **Sales** segment. And as it defines IB policies, the organization should ensure that it sets those policies to **Inactive** status until it's ready to apply them. Defining (or editing) policies doesn't affect users until those policies are set to **Active** status and then applied.
