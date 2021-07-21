When you connect Microsoft Cloud App Security to apps by using API connectors, Cloud App Security enables you to import user groups from those apps. There are two types of user groups.

- Automatic groups
- Imported groups

## What are automatic groups?

Automatic groups are created by Cloud App Security automatically. The following is a list of some of these automatic groups.

- External users
- Office 365 administrator
- Application (Cloud App Security)
- Dropbox administrator
- G Suite administrator
- Box administrator
- All Salesforce standard and custom profiles, for example, Salesforce System Administrator

> [!NOTE]
> The External users automatic group consolidates all users from all connected apps that are external to your organization. These users have access to files in your organization, or performed user activities in your tenant.

## What are imported groups?

You can also import user groups from other connected apps. For example, you could choose to import user groups from your Office 365 tenant. You use imported user groups so that you can search for and identify potential threats in your organization based on group membership, rather than specific user account.

> [!IMPORTANT]
> Only activities performed after importing a user group will be tagged as having been performed by a member of that user group.

### How to import user groups

To import user groups, use the following procedure:

1. Navigate to the [Cloud App Security portal](https://portal.cloudappsecurity.com).
2. Sign in as a Global Admin in your Microsoft 365 tenant.
3. In the portal, select **Settings**. This is the cog next to your profile picture.
4. Select **User groups**. A list of automatic user groups is returned, plus any additional user groups you previously created.
5. On the **User groups** page, select **Import user group**.
6. In the **Import user group** dialog box, in the **Select app** list, select the appropriate connected app.
7. In the **Select user group to import** list, select the group you want to import.
8. The import process can take up to an hour, depending on membership of the group. If you want to be notified on completion, select the **Notify me by email when the import is complete** check box, and then select **Import**.

    > [!TIP]
    > When you're selecting the user group to import, if you have a large number of groups, not all user groups are visible. It's therefore important to know the user group name from your tenant when searching.

    :::image type="content" source="../media/import-group.png" alt-text="A screenshot displays the Import user group dialog box. The administrator has selected the Office 365 (Azure AD) app and the All Employees group.":::

> [!NOTE]
> The maximum number of imported user groups is 500.

After you complete the import, you can review the imported group from the User groups page. To review the properties of a group, whether automatic or imported, select the group from the list.

:::image type="content" source="../media/view-groups.png" alt-text="A screenshot displays the list of User groups. These are All Employees (Imported), and three automatic groups: Office 365 administrator, External users, and Application (Cloud App Security)." lightbox="../media/view-groups.png":::

### Import user groups

The following video demonstrates how to import user groups.

 >[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4MDah]
