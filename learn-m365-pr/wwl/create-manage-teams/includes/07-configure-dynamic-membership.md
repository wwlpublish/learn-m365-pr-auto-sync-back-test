Microsoft Teams supports teams associated with Microsoft 365 Groups by using dynamic membership. 

You can use dynamic membership to define members of a team by one or more rules that check for certain user attributes in Azure Active Directory (Azure AD). Users are automatically removed or added to the designated teams as user attributes change or users join and leave the tenant. Possible scenarios include:  

- A hospital can create distinct teams for nurses, doctors, and surgeons to broadcast communications. This capability is especially important if the hospital relies on temp employees.  
- A university can create a team for all faculty within a college, including an adjunct faculty that changes frequently.  
- An airline wants to create a team for a frequently changing flight crew automatically assigned or removed as needed.

Using this feature, a given team's members update automatically based on a specific set of criteria, instead of manually managing membership. 

> [!NOTE]
> Using dynamic groups requires Azure AD Premium P1 licenses for any users in scope. 
 
It may take anywhere from a few minutes to up to hours to reflect dynamic membership changes once they take effect in the Microsoft 365 Group for a team. For dynamic group membership in teams, you must consider the following:  
‎
- Rules can define who is a team member of a team, but not who is a team owner.
- Owners won't be able to add or remove users as members of the team, since members are defined by dynamic group rules.  
- Members won't be able to leave teams backed by dynamic groups.

## Enable dynamic membership

To enable dynamic membership in a Team, you must modify the underlying Microsoft 365 group membership rule using the **Azure AD portal** or **PowerShell**. The references to the group won't be changed if you modify the membership. If the group is used for access every member added by the dynamic membership rule will have access to the resources of the group.

There currently isn't a way to create a team with dynamic membership directly. You can either create a team then change the membership rule of the associated Microsoft 365 group or create a Microsoft 365 group with dynamic user membership type then create a team from the existing Microsoft 365 Group. 

> [!WARNING]
> When changing an existing static group to a dynamic group, all existing members are removed from the group, and then the membership rule is processed to add new members. If the group is used to control access to apps or resources, be aware that the original members might lose access until the membership rule is fully processed. You should test the new membership rule beforehand to make sure that the membership in the group is as expected.
 
## Azure AD Portal

Do the following steps to change the group membership of an existing team to a rule based dynamic membership.

1. Sign into the Azure AD admin center with an account that is a global administrator or a user administrator in your tenant.
2. Select the search bar from the top of the page, type **Azure Active Directory** and select it.
3. In the left-pane menu, select **Groups**.
4. From the **All groups** list, open the group that you want to change.
5. Select **Properties**.
6. On the Properties page for your selected group, select a Membership type of Dynamic User.
:::image type="content" source="../media/membership-type.png" alt-text="Membership type in AAD":::

7. Select **Add dynamic query**, and then provide the rule.
:::image type="content" source="../media/add-dynamic-query.png" alt-text="Adding dynamic query in AAD":::

8. After creating the rule, select **Add query** at the lower end of the page.
9. Select **Save** on the **Properties** page for the group to save your changes. The **Membership type** of the group is immediately updated in the group list.

 

## PowerShell

To change the membership type of a group using PowerShell, you can use the AzureAD PowerShell module.

You'll provide a group ID to the cmdlet for it to find the correct Microsoft 365 Group to modify. You can use the Exchange PowerShell module:

```powershell
$groupId = (Get-UnifiedGroup <group_mailaddress>).ExternalDirectoryObjectID
$dynamicMembershipRule = ‘user.department -eq "Sales"’
```

Use the following command to switch the group to dynamic membership:


```powershell
Set-AzureAdMsGroup -Id $groupId -GroupTypes $groupTypes.ToArray() -MembershipRuleProcessingState "On" -MembershipRule $dynamicMembershipRule
```

To create the ```$groupTypes``` variable you have to get the group types of the existing group and add the String "dynamicMembership" to it.

 

```powershell
groupTypes = (Get-AzureAdMsGroup -Id $groupId).GroupTypes
$groupTypes.Add("DynamicMembership")
```

## Create a dynamic membership rule

You can build a rule from one or more expressions. A single expression has the format **Property Operator Value**. For example: ```user.department -eq "Sales"```. If you want to add multiple expressions to a single rule, you can use the same operators to combine them and keep every expression in its own parenthesis:

```(user.department -eq "Sales") -and (user.department -eq "Marketing")```


There are three types of properties that can be used to construct a membership rule.

- Boolean

- String

- String collection

 

The supported operators are:

| **Operator**| **Syntax** |
| - |-|
| Not Equals| -ne |
| Equals| -eq |
| Not Starts With| -notStartsWith |
| Starts With| -startsWith |
| Not Contains| -notContains |
| Contains| -contains |
| Not Match| -notMatch |
| Match| -match |
| In| -in |
| Not In| -notIn |


 

The values used in an expression may consist of several types, including:

- Strings

- Boolean – true, false

- Numbers

- Arrays – number array, string array

 

When specifying a value within an expression, it's important to use the correct syntax to avoid errors. Some syntax tips include:

- Double quotes are optional unless the value is a string.

- String and regex operations are not case-sensitive.

- When a string value contains double quotes, both quotes should be escaped using the  character (\"), for example, ```user.department -eq "Sales" ``` is the proper syntax when "Sales" is the value.

- You can also do Null checks, using null as a value, for example, ```user.department -eq null```.

 

For more information, see [Dynamic membership rules for groups in Azure Active Directory](/azure/active-directory/users-groups-roles/groups-dynamic-membership?azure-portal=true). 

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”