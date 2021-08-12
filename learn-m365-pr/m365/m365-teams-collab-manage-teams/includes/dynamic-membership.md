Microsoft Teams supports teams associated with Microsoft 365 Groups by using dynamic membership. Dynamic membership enables the membership of a team to be defined by one or more rules that check for certain user attributes in Azure Active Directory (Azure AD). When an attribute changes for a user or device, all dynamic group rules in the organization are processed for membership changes. Users are added or removed if they meet the conditions for a group.

> [!NOTE]
> Dynamic groups for users cannot contain devices.

## What is dynamic membership?

With dynamic membership, users are automatically added to or removed from the correct teams as user attributes change or users join and leave the tenant. You can set up teams for certain cohorts of users in your organization. A hospital could create distinct teams for nurses, doctors, and surgeons to broadcast communications; this is especially important if the hospital relies on temporary employees.

Since a team's members update automatically based on specific criteria instead of manually managing membership, this feature requires Azure AD Premium P1 licenses. Team membership is assigned by a tenant administrator to any user's Azure AD properties.

You can create a dynamic group by using the Azure AD admin center. To do this, you must have an account that is in the Global Administrator, Intune Administrator, or User Administrator role in the tenant.

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Overview of dynamic membership for teams](/MicrosoftTeams/dynamic-memberships)
