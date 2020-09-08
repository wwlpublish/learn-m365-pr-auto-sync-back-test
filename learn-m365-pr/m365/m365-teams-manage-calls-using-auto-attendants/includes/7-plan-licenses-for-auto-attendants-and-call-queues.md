You can use the Microsoft 365 admin center or PowerShell to assign licenses to users in your organization. You must be a global admin or user management admin to manage licenses.

## Assigning Add-on Licenses

Add-on licenses are licenses for specific Microsoft Teams features. They give you the flexibility to add features only for users in your organization who need them. To add a feature, buy one add-on license for each user who will use it.
While Phone System is part of Microsoft Teams, in order to use it, you'll need to purchase an add-on license.

You can assign licenses to individual users or small sets of users at a time. You can assign licenses on the Licenses page, for up to 20 users at a time, or the Active users page. The method you choose depends on whether you want to manage product licenses for specific users or manage user licenses for specific products.

If you need to assign licenses for a large number of users, such as hundreds or thousands of users, use PowerShell or group-based licensing in Azure Active Directory (Azure AD).

## Licensing

Before you get started adding licenses, consider these points:

- If you're using on-premises public switched telephone network (PSTN) connectivity for hybrid users, you only need to assign a Phone System license. Don't assign a Calling Plan license.
- Because of the latency between Microsoft 365 and Microsoft Teams, it can take up to 24 hours for a user to be assigned a Calling Plan after you assign a license. If the user isn't assigned a Calling Plan after 24 hours, contact support.
- You'll get an error message if you haven't purchased the correct number of licenses. If you need to buy more Calling Plan licenses, choose the option to buy more.
- Even if your users are assigned Enterprise E5 licenses, you still need to assign communications credits licenses to them if they want to make or receive calls from the PSTN.
After you assign Calling Plan or communication credits licenses to your users, you'll need to get phone numbers for your organization, and then assign those numbers to users.## Zero Licensing cost

When using nested auto attendants, as long as they don't have a phone number assigned, you won't need a license.

:::image type="content" border="false" source="../media/7-pstn-routing.png" alt-text="Diagram showing PSTN routing and cost plans":::

## Learn more

- [Assign Teams add-on licenses to user](https://docs.microsoft.com/microsoftteams/teams-add-on-licensing/assign-teams-add-on-licenses)
- [Teams - add on licenses](https://docs.microsoft.com/microsoftteams/teams-add-on-licensing/microsoft-teams-add-on-licensing?tabs=small-business)
