Organizations create custom management role groups if the built-in RBAC management role groups don't provide sufficient permissions for all their company job roles. However, before creating new management roles, you should always remember the following best practices:

 -  **Don’t change the existing built-in role groups.** If you change the default groups, you'll most likely end up in a situation where your organization can no longer receive support involving role group issues because you've modified the default roles.
 -  **Don’t create new roles and role groups from the scratch.** An organization's custom roles and role groups should fit into the existing permission structure. Creating new roles and role groups from scratch creates a new hierarchy of permission roles in parallel to the built-in roles.

Rather than changing the existing built-in role groups and creating new roles and role groups from scratch, you should:

1.  Find an existing role group that closely matches your needs.
2.  Copy this role group as a new custom role group.
3.  Add or remove roles to this new role group until it meets your business requirements.

This process uses existing roles and role groups as a starting point for new custom roles and role groups. This design keeps the custom roles and role groups in Microsoft 365's existing hierarchy of permission roles.

### Plan and implement your management role groups

Before you begin creating any roles or role groups, you should match your business job roles with the built-in roles. If you have any job roles that couldn't be matched to a built-in role, you should then answer the following questions:

 -  **How many role groups do you need?** Always start with a single role group. Only add another role group if the first role group isn't enough.
 -  **What roles will you add to each role group?** Decide what roles you want to add to the custom role group. Try to use the built-in roles, and create custom roles only if the built-in roles aren't suitable.
 -  **What scopes do you require for each role group?** Define a scope, such as a database scope, only if you need it.

As soon as you finished matching all job roles to built-in and custom roles, you can then begin creating the custom management roles and role groups that will map to your unmatched job roles.

To manage your permissions using role groups in Exchange, you can use the Exchange Management Shell or the EAC. Because assigning roles with PowerShell is different from working with the EAC, it’s recommended that you use the EAC to manage your role groups.

For your new role group, you must complete the following steps:

1.  Choose a name for your role group.
2.  Select the roles you want to add to the role group.
3.  Add members to the role group.
4.  Save the role group.

If there's an existing role group that has some of the permissions you need, you can copy it as a new role group and then make your necessary changes to the new role group. Copying an existing role group lets you create a customized version of the role group without affecting the original role group. When you copy the existing role group, you can:

 -  Assign a new name and description to the new group.
 -  Add roles to the new role group.
 -  Remove roles from the new role group.
 -  Add new members.

Existing role groups can also be modified. You can add and remove roles from existing role groups and add and remove members from it at the same time using an EAC dialog box like the one in the preceding figure. By adding and removing roles to and from role groups, you turn on and off administrative features for members of that role group.<br>

After you create a new, custom role group, you'll manage it like any other role group.

### Management role assignments

A management role assignment is the link between a management role and a role assignee. A role assignee is a role group, role assignment policy, user, or universal security group (USG). A role must be assigned to a role assignee for it to take effect.

You can create the following types of role assignments:

 -  Regular and delegating role assignments
 -  Exclusive role assignments

When you change role assignments, the changes you make will probably be between role groups and role assignment policies. By adding, removing, or modifying role assignments to or from these role assignees, you can control what permissions are given to your administrators and users, in effect turning on and off management of related features.

You can also assign roles directly to users or USGs. Assigning roles is a more advanced task that enables you to define at a granular level what permissions your users are given. Although this design provides you with flexibility, it also increases the complexity of your permissions model. For example, if the user changes jobs, you may need to manually reassign that user's roles to another user.

> [!TIP]
> For this reason, it's recommended that you use role groups and role assignment policies to give permissions to your users. You can assign the roles to a role group or role assignment policy, and then just add or remove members of the role group or change role assignment policies as needed.

When managing role assignments, you can:

 -  Add, remove, and enable role assignments.
 -  Modify the management scope on an existing role assignment.
 -  Move role assignments to other role assignees.

Roles can be assigned to role groups, role assignment policies, users, and USGs. The process of assigning roles is largely the same for each role assignee. However, there are exceptions, including:

 -  Role assignment policies can only be assigned end-user management roles.
 -  Role assignment policies can't be assigned delegating role assignments.
 -  You can't specify a management scope when creating a role assignment to role assignment policies.

Role assignment policies for end-user roles will be covered in other training.

Two types of role assignments are available:

 -  **Regular and delegating role assignments.** Regular role assignments enable the role assignee to access the management role entries made available by the associated management role. If multiple management roles are assigned to a role assignee, the management role entries from each management role are aggregated and applied.
 -  **Exclusive role assignments.** Exclusive role assignments are created when you associate an exclusive scope with a role assignment. Exclusive scopes work like regular scopes and enable role assignees to manage recipients that match the exclusive scope. However, unlike regular scopes, all other role assignees are denied the ability to manage the recipient, even if the recipient matches scopes applied to their role assignments.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.