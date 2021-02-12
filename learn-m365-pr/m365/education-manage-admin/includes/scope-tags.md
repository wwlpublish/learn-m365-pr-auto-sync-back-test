## What is a scope tag?

Scope tags define which objects admins can see. Each object can have up to 100 scope tags defined.

To assign a scope tag to an object, you would typically select the scope tags in the properties of the object.

## Create a scope tag

To create a scope tag, perform the following steps:

1. Open Microsoft Endpoint Manager admin center.
1. Select **Tenant administration**, select **Roles**, and select **Scope (Tags)**.
1. On the **Basics** page, enter a **Name** and select **Next**.
1. On the **Assignments** page, select the device groups that you want to assign and select **Next**.
1. On the **Review + create** page, select **Create**.

## Assign a scope tag to a role

You create assignments to define the admins that will have permissions, the groups that they'll have permissions for, and the scope tags that will be visible to this assignment.

To assign a scope tag to a role, perform the following steps:

1. Open Microsoft Endpoint Manager admin center.
1. Select **Tenant administration**, select **Roles**, select **All roles**, select the role that you want to assign, select **Assignments**, and select **Assign**.
1. On the **Basics** page, enter an **Assignment name** and **Description** and select **Next**.
1. On the **Admin Groups** page, select **Select groups to include**, and select the groups that will be part of this assignment. Select **Next**.
1. On the **Scope Groups** page, select the groups with the users or devices that you want the assignment to manage, or select **All users**, **All devices**, or **All users and all devices**. Select **Next**.
1. On the **Scope tags** page, select the tags that you want to add to this role. Select **Next**.
1. On the **Review + create** page, select **Create**.
