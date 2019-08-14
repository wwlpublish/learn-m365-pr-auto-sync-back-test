Microsoft Teams supports teams associated with Office 365 Groups by using dynamic membership. Dynamic membership enables the membership of a team to be defined by one or more rules that check for certain user attributes in Azure AD. When an attribute changes for a user or device, all dynamic group rules in the organization are processed for membership changes. Users are added or removed if they meet the conditions for a group.

> [!NOTE]
> Dynamic groups for users cannot contain devices.

## What is dynamic membership?

With dynamic membership, users are automatically added to or removed from the correct teams as attributes change or they join and leave the tenant. You can set up teams for certain cohorts of users in your organization. For example, a hospital is able to create distinct teams for nurses, doctors, and surgeons to broadcast communications. This is especially important if the hospital relies on temporary employees.

Using this feature, a given team’s members update automatically based on a specific set of criteria as opposed to manually managing membership. Doing this requires Azure AD Premium P1 licenses. Team membership can be assigned by a tenant administrator to any user's Azure AD properties provided the user has a tenant and an administrative account.

You can create a dynamic group by using the Azure AD admin center. To do this, you must have an account that is in the global administrator, Intune administrator, or user administrator role in the tenant.
