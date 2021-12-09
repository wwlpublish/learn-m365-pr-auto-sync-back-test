Policies are used to control what Teams features are available to users. Organizations have different types of users with unique needs. You can use the Global (Org-wide default) policy or create custom policies for people in your organization. 


A Global (Org-wide default) policy is created by default for each policy type. Global (Org-wide default) policies apply to the largest number of users in your organization. You only have to assign policies to those users that require specialized policies. Custom policies let you tailor policy settings to different sets of users based on their needs. 

## Types of policies

The following policies can be managed with Microsoft Teams.

Policy type | Description | Policies |
------------|------------|---|
Policy packages| A policy package is a collection of predefined policies and settings you can assign to users who have similar roles in your organization.| - Policy package
Meeting policies | A meeting policy is used to control the features that are available to meeting participants for meetings scheduled by users in your organization. | - Meeting policy<br> - Live events policy| 
Voice and calling policies| Voice and calling policies manage these settings through teams such as emergency calling, call routing, and caller ID.|- Call park policy<br> - Calling policy<br> - Caller ID policy<br> - Emergency calling policy<br> - Emergency call routing policy<br> - Dial plan<br> - Voice routing policy|
App policies| App policies are used to control applications in Microsoft Teams, such as allowing or blocking which apps users can install.|- App permission policy<br> - App setup policy|
Chat, teams, and channel policies| Chat, teams, and channel policies control teams and collaboration feature availability.|- Messaging policy<br> - Templates policy<br> - Teams policy|
Teams feature policy |Update policies are used to manage Teams and Office preview users that will see pre-release or preview features in the Teams app. |- Update policy|

## Ways to assign policies

You can assign policies directly to users or via groups (including Microsoft 365 Groups, distribution list, or security group). The option that you choose depends on the number of policies that you're managing and the number of users you're assigning policies to.

- Assign a policy directly to an individual user.
- Assign a policy to a batch of users.
- Assign a policy to a group. 

You can also use policy packages to assign a preset collection of policies to users in your organization who have similar roles. For example, assign the Education (Teacher) policy package to all teachers in the school using batch assignment to give them full access to chats, calling, and meetings. 

- Assign a policy package directly to an individual user.
- Assign a policy package to a batch of users.
- Assign a policy package to a group. 

You can use Teams admin center or PowerShell to assign policies or policy packages. The following table shows a summary of the PowerShell commands. 

|Policy Assignment |Assign a policy|Assign a policy package|
|--|--|--|
|To individual user|Use the ```Grant-``` cmdlet for a given policy type to assign the policy.<br/><br/> For example, use the ```Grant-CsTeamsMeetingPolicy``` cmdlet to assign a Teams meeting policy to users. |Use the ```Grant-CsUserPolicyPackage``` cmdlet to assign a policy package to one or less than 20 users at a time.|
|To a batch of users|Use the ```New-CsBatchPolicyAssignmentOperation``` cmdlet to assign a policy to a batch of users.|Use the ```New-CsBatchPolicyPackageAssignmentOperation``` cmdlet to assign a policy package to  a batch of users in a tenant.|
|To a group|Use the ```New-CsGroupPolicyAssignment``` cmdlet to assign a policy to a group. |Use the ```Grant-CsGroupPolicyPackageAssignment``` cmdlet to assign a policy package to a group.|

Depends on the Teams policy types, some policy assignments aren't available for all Teams policy types. 

* For policy assignment to groups, see [New-CsGroupPolicyAssignment](/powershell/module/teams/new-csgrouppolicyassignment?azure-portal=true) for the list of supported policy types.

* For batch policy assignment, see [New-CsBatchPolicyAssignmentOperation](/powershell/module/teams/new-csbatchpolicyassignmentoperation?azure-portal=true) for the list of supported policy types.


## Policy precedence

A user has one effective policy for each policy type. A user's effective policy is determined according to rules of precedence, as the following order.

1. **User**: If a user is directly assigned a policy (either individually or through a batch assignment), that policy takes precedence.

2. **Group**: If a user isn't directly assigned a policy of a given type, the policy assigned to a group that the user is a member of takes precedence. If a user is a member of multiple groups, the policy that has the highest ranking for the given policy type takes precedence (1 is the highest ranking). 

3. **Org-wide**: If a user isn't directly assigned a policy or isn't a member of any groups that are assigned a policy, the user gets the global (Org-wide default) policy for that policy type.

‎:::image type="content" source="../media/policy-precedence.png" alt-text="The order of policy precedence":::

> [!NOTE]
> * Group policy assignments are only propagated to users who are direct members of the group. The assignments aren't propagated to members of nested groups.
> *  If a user has a policy of a given type that was directly assigned to them, you have to remove that policy from the user before they can inherit a policy of the same type from a group.
> * If you assign policies to batches of more than 20 users through the Microsoft Teams admin center, you can view the status of those policy assignments from the last 30 days in the Activity log (**Teams admin center** > **Dashboard** > **Activity Log**). 


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”