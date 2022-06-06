When an organization creates a retention policy or retention label policy, it must define the scope of the policy as either adaptive or static.

 -  **Adaptive scope**. An adaptive scope uses a query that you specify. As such, the membership is dynamic rather than static. The reason that it's dynamic is because it runs daily against the attributes or properties that you specify for the selected locations. You can use multiple adaptive scopes with a single policy.
    
    **Example**: Emails and OneDrive documents for executives require a longer retention period than standard users. You create a retention policy with an adaptive scope that uses the Azure AD attribute job title of "Executive". You then select the Exchange email and OneDrive accounts locations for the policy. There's no need to specify email addresses or OneDrive URLs for these users because the adaptive scope automatically retrieves these values. For new executives, there's no need to reconfigure the retention policy because these new users with their corresponding values for email and OneDrive are automatically picked up.
 -  **Static scope**. A static scope doesn't use queries. It's limited in configuration in that it can apply to all instances for a specified location, or use inclusion and exclusions for specific instances for that location. These three choices are sometimes referred to as **org-wide**, **includes**, and **excludes**, respectively.
    
    **Example**: Emails and OneDrive documents for executives require a longer retention period than standard users. You create a retention policy with a static scope that selects the Exchange email and OneDrive accounts locations for the policy. For the Exchange email location, you're able to identify a group that contains just the executives. You then specify this group for the retention policy. The group membership with the respective email addresses is then retrieved when the policy is created. For the OneDrive accounts location, you must identify and then specify individual OneDrive URLs for each executive. For new executives, you must reconfigure the retention policy to add the new email addresses and OneDrive URLs. You must also update the OneDrive URLs anytime there's a change in an executive's UPN.
    
    OneDrive URLs are particularly challenging to reliably specify. Why? Because by default, these URLs aren't created until the user accesses their OneDrive for the first time. And if a user's UPN changes, which you may not know about, their OneDrive URL automatically changes.

### Advantages of using adaptive scopes

Retention policies and retention label policies enjoy the following advantages when using adaptive scopes:

 -  No limits on the number of items per policy. Although adaptive policies are still subject to the [maximum number of policies per tenant](/microsoft-365/compliance/retention-limits?azure-portal=true) limitations, the more flexible configuration will likely result in far fewer policies.
 -  More powerful targeting for your retention requirements. For example, you can assign different retention settings to users according to their geographical location. You do so by using existing Azure AD attributes without the administrative overhead of creating and maintaining groups for this purpose.
 -  Query-based membership provides resilience against business changes that may not be reliably reflected in group membership. It also provides resilience against external processes that rely on cross-department communication.
 -  A single retention policy can include locations for both Microsoft Teams and Yammer. However, when you use a static scope, these locations require their own retention policy.
 -  You can only apply specific retention settings to inactive mailboxes. This configuration isn't possible with a static scope. Why? Because at the time the policy is assigned, static scopes don't support the specific inclusion of recipients with inactive mailboxes.

### Advantages of using static scopes

Retention policies and retention label policies enjoy the following advantages when using adaptive scopes:

 -  Simpler configuration if you want all instances automatically selected for a workload.

    > [!NOTE]
    > For "includes" and "excludes", this choice can be a simpler configuration initially if the numbers of instances that you have to specify are low and don't change. However, when the number of instances starts to increase and you have frequent changes in your organization that require you to reconfigure your policies, adaptive scopes can be simpler to configure and much easier to maintain.

 -  Adaptive scopes aren't supported by Skype for Business public folder locations and Exchange public folder locations. For these locations, you must use a static scope.

**Additional reading**. For more information, see [Configuring adaptive scopes](/microsoft-365/compliance/retention-settings?azure-portal=true).

**Additional viewing**. To watch a recorded webinar (requires registration), visit [Deep Dive on Adaptive Scopes](https://mipc.eventbuilder.com/event/45703?azure-portal=true).

> [!WARNING]
> Currently, adaptive scopes don't support [Preservation Lock to restrict changes to retention policies and retention label policies](/microsoft-365/compliance/retention?azure-portal=true).
