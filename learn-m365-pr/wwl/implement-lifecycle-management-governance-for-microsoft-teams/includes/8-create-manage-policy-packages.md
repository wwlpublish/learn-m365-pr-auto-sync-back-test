**Policy packages** in Microsoft Teams let you control Teams features that you want to allow or restrict for specific sets of people across your organization. Policy packages simplify, streamline, and help provide consistency when managing policies for groups of users across your organization.

A policy package is a collection of **predefined policies and policy settings** that you can assign to users who have similar roles in your organization. When you assign a policy package to users, the policies in the package are created and you can then customize the settings of the policies in the package to meet your organization's needs.

## Policy packages
Each policy package in Teams is designed around a user role and includes predefined policies and policy settings that support the collaboration and communication activities that are typical for that role. Each individual policy is given the name of the policy package so you can easily identify the policies that are linked to a policy package. Teams currently includes the following policy packages.

‎:::image type="content" source="../media/policy-packages.png" alt-text="Assign a policy package to one user":::

## View policy packages
View the settings of each policy in a policy package before you assign a package. Make sure that you understand each setting and then decide whether the predefined values are appropriate for your organization or whether you need to change them to be more restrictive or lenient based on your organization's needs.

1. In the left navigation of the Microsoft Teams admin center, select **Policy packages**, and then select a policy package by selecting to the left of the package name.
2. Select the policy you want to view.

The following shows the available predefined policies of different packages:

|**Package name**  |**Messaging policy** |**Meeting policy**|**App setup policy**|**Calling policy**|**Live events policy**|
|--|--|--|--|--|--|
|Education (Higher education student)    |Yes|Yes|Yes|Yes|Yes|
|Education (Primary school student using remote learning)   |Yes|Yes|Yes|Yes|Yes|
|Education (Primary school teacher using remote learning)   |Yes|Yes|Yes|Yes|Yes|
|Education (Primary school student)   |Yes|Yes|Yes|Yes|Yes|
|Education (Secondary school student)    |Yes|Yes|Yes|Yes|Yes|
|Education (Teacher)    |Yes|Yes|Yes|Yes|Yes|
|Frontline manager  |Yes|Yes|Yes|Yes|Yes|
|Frontline worker |Yes|Yes|Yes|Yes|Yes|
|Healthcare clinical worker  |Yes|Yes|Yes|-|-|
|Healthcare information worker  |Yes|Yes|Yes|-|-|
|Healthcare patient room  |Yes|Yes|Yes|Yes|Yes|
|Public safety officer  |Yes|Yes|Yes|Yes|-|
|Small and medium business user (Business Voice) |-|-|Yes|-|-|
|Small and medium business user (without Business Voice) |-|-|Yes|-|-|

## Customize policy packages
You can create a new policy package or customize the settings of policies in the existing policy package to fit the needs of your organization. Any changes you make to policy settings are automatically applied to users who are assigned the package.

You can edit the settings of a policy through the **Policy packages** page or by going directly to the policy page in the Microsoft Teams admin center.

1. In the left navigation of the Microsoft Teams admin center, do one of the following:
    - Select **Policy packages**, and then select the policy package by clicking to the left of the package name.
    - Select the policy type.  For example, select **Messaging policies**.
2. Select the policy you want to edit. Policies that are linked to a policy package have the same name as the policy package.
3. Make the changes that you want, and then select **Save**.

> [!NOTE]
> If a policy is deleted, you can still view the settings but you won't be able to change any settings. A deleted policy is re-created with the predefined settings when you assign the policy package.

## Assign policy packages
Assign the policy package to users. Remember that policies in a policy package aren't created until you assign the package, after which you can change the settings of individual policies in the package.

#### Assign a policy package to one user

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then select the user.
2. On the user's page, select **Policies**, and then next to **Policy package**, select **Edit**.
3. In the **Assign policy package** pane, select the package you want to assign, and then select **Save**.

You can also use ```Grant-CsUserPolicyPackage``` PowerShell cmdlet to assign a policy package to fewer than 20 users at a time.

The example below assigns the Education_PrimaryStudent policy package to two users in the tenant. You can specify users by their object ID or Session Initiation Protocol (SIP) address.

```PowerShell
Grant-CsUserPolicyPackage -Identity 1bc0b35f-095a-4a37-a24c-c4b6049816ab,johndoe@example.com -PackageName Education_PrimaryStudent
```

#### Assign a policy package to multiple users
With batch policy package assignment, you can assign a policy package to large sets of users at a time.

1. In the left navigation of the Microsoft Teams admin center, go to **Policy packages**, and then select the policy package you want to assign by selecting to the left of the package name.
2. Select **Manage users**.
3. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.
4. When you're finished adding users, select **Save**.

You can also use ```New-CsBatchPolicyAssignmentOperation``` PowerShell cmdlet to assign a policy package to multiple users. A batch may contain up to 5,000 users.

The example below assigns the Education_PrimaryStudent policy package to a batch of users. You can specify users by their object ID or Session Initiation Protocol (SIP) address.

```PowerShell
New-CsBatchPolicyPackageAssignmentOperation -Identity 1bc0b35f-095a-4a37-a24c-c4b6049816ab,user1@econtoso.com,user2@contoso.com -PackageName Education_PrimaryStudent
```

#### Assign a policy package to a group
Policy package assignment to groups lets you assign multiple policies to a group of users, such as a security group or distribution list. The policy assignment is propagated to members of the group according to precedence rules. As members are added to or removed from a group, their inherited policy assignments are updated accordingly.

1. Sign in to the Teams admin center.
2. In the left navigation, go to the policy package page.
3. Select the Group policy assignment tab.
4. Select **Add group**, and then in the Assign a policy package to group pane, do the following:

    a. Search for and add the group you want to assign the policy package to.

    b. Select a policy package.

    c. Set the ranking for each policy type.

    d. Select **Apply**.

5. To manage ranking for a specific policy type, navigate to the specific policy page.
6. To reassign a policy package to a group, first remove the group policy assignment. Then, follow the steps above to assign the policy package to a group.

You can also use ```Grant-CsGroupPolicyPackageAssignment``` PowerShell cmdlet to assign a policy package to a group. You can specify a group by using the object ID, SIP address, or email address.

The example below assigns the Education_Teacher policy package to a group with an assignment ranking of 1 for TeamsAppSetupPolicy and TeamsMeetingBroadcastPolicy and a ranking of 2 for TeamsMeetingPolicy.

```PowerShell
Grant-CsGroupPolicyPackageAssignment -GroupId "dae90bb4-120f-4a3e-a15d-30f142e79f69" -PackageName "Education_Teacher" -PolicyRankings "TeamsAppSetupPolicy, 1", "TeamsMeetingBroadcastPolicy, 1", "TeamsMeetingPolicy, 2"
```


