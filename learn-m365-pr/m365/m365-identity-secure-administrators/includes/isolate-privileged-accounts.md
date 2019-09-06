## Isolate privileged accounts

To further protect administrator accounts that access sensitive data, create dedicated accounts for these users solely to perform tasks that require privileged access. Then restrict these accounts from performing non-administrative tasks, such as personal email.

For example, you assign Christina a dedicated account *ChristinaAdmin@contoso.com* to perform her administrative tasks. This account is separate from Christina's non-administrative account, *Christina@contoso.com*, which she uses for non-administrative tasks and communications with partners and clients. In this way, her administrator account credentials are not exposed externally.

![Screenshot of Azure AD Privileged Identity Management dashboard.](../media/privileged-identity-management.png)

*Azure AD Privileged Identity Management dashboard*

You can also use Azure AD PIM to identify accounts that are in privileged roles and then categorize and track those accounts as follows:

- Accounts individually assigned to administrators for non-administrative purposes
- Accounts individually assigned to administrators for administrative tasks only
- Shared roles across multiple users
