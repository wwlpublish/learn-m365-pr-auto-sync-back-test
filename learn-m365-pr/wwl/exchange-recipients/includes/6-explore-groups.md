Exchange provides different types of groups so that you can group together recipients and make them available in your global address list. This unit focuses on groups that can be used by Exchange to address a group of recipients.

> [!NOTE]
> Exchange also enables organizations to create security groups that aren't mail-enabled and can't be used for distributing email to multiple recipients in Microsoft 365. These groups are commonly used to provide access to resources, such as control access to OneDrive and SharePoint. They can also be used for Mobile Device Management.

The following table identifies the different types of groups that you can create and manage in the Exchange admin center (EAC) portal.

:::row:::
  :::column:::
    **Group Type**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **Membership Management**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Distribution lists

(Distribution Groups)
  :::column-end:::
  :::column:::
    These groups can only be used to distribute messages to a set of recipients.
  :::column-end:::
  :::column:::
    Configure if owner approval is required to join the group (open, closed, or owner approval)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mail-enabled security groups
  :::column-end:::
  :::column:::
    These groups can be used to distribute messages and to provide access to resources, such as control access to OneDrive and SharePoint.
  :::column-end:::
  :::column:::
    Configure if owner approval is required to join.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Dynamic distribution lists

(Dynamic distribution groups)
  :::column-end:::
  :::column:::
    These groups don't have a predefined member list because they use recipient filters and conditions that you define to dynamically determine membership at the time that messages are sent.
  :::column-end:::
  :::column:::
    Membership is dynamic, based on a query against the Azure Active Directory or Active Directory Domain Services.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft 365 groups
  :::column-end:::
  :::column:::
    These groups are available in Microsoft 365 only. They provide distribution list team collaboration functionality for small to medium teams when the requirements include functionality such as conversations, co-authoring of documents, a shared OneNote notebook, or task-based planning.
  :::column-end:::
  :::column:::
    Membership is managed by the administrator or self-managed. This design enables users to search for a Microsoft 365 group and join it. Dynamic group membership is possible but requires an Azure AD Premium license.
  :::column-end:::
:::row-end:::


**Additional reading.** For more information, see [What to create: Office 365 groups, shared mailboxes, security groups, and distribution lists](/microsoft-365/admin/create-groups/compare-groups?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.