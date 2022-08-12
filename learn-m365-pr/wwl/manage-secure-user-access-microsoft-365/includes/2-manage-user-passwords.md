Microsoft 365 helps provide secure access by requiring users to sign in with a password. It also includes various password management features, including:

 -  Setting password expiration
 -  Changing passwords
 -  Resetting passwords
 -  Eliminating bad passwords

These features are examined in the following sections.

### Setting password expiration

The default password expiration policy in Microsoft 365 includes the following settings:

 -  Users’ passwords aren't set to expire.
 -  Users receive notification of impending password expiration 14 days before it occurs.

The Microsoft 365 admin center enables the Enterprise Administrator to change both of these settings for their organization. To change the password expiration policy, complete the following steps:

1. Sign-in to the Microsoft 365 admin center, navigate to the **Settings** menu, and then select the **Security &amp; privacy** tab.
1. In the **Security &amp; privacy** page, select **Password expiration policy**.
1. Select **Set user passwords to expire after a number of days** and specify the number of days between 14 and 730 for password expiration.
1. Specify the number of days between 1 and 30 for the notification warning of password expiration.
1. Save your settings.

Let's assume an organization changed its password expiration policy so that passwords expire after 60 days. What happens if a user doesn't change their password before the expiration time has elapsed? There are two options:

 -  The user can still change it themselves by using the **Password update** page that appears the next time they sign in.
 -  Their password can be reset for them.

> [!WARNING]
> The **Password update** page also includes an option to set user passwords to never expire. This setting disables password expiration for all users. However, disabling password expiration for all users isn't recommended because of the potential that a password will be hacked or leaked over time.

To disable password expiration for single users using PowerShell, use the **Set-MsolUser** cmdlet with the **-PasswordNeverExpires** parameter.

### Resetting user passwords

If necessary, a password can be reset for one or more users on the **Active users** page. You can choose from the following options:

 -  Assign a new, randomly generated password or a password of your choice.
 -  Select whether users need to change their password at their next sign-in.

### Resetting admin passwords

If an administrator forgets their own password, the two available options are:

 -  **Ask another administrator to reset it for you.** In this case, the other administrator must be either a Global admin, a User Management admin, or a Password admin. However, if the administrator who forgot their password is a Global admin, another Global administrator must reset it for them.
 -  **Reset the password yourself.** On the sign-in page for Microsoft 365, the "**Can’t access your account?"** link enables a user to reset their own password. After following the instructions provided in the link, an email is sent with a link that enables the user to reset their password.

    If a user wants to reset their own password, they must have previously supplied an alternative email address in their account settings. The email address can't be their Microsoft 365 email address. Additionally, if the organization uses a custom domain name or it uses directory synchronization, the user must have supplied a phone number in their account details that can receive text notifications. An automatically generated code will be sent in a text message to their mobile phone. Once they receive the message, they must enter this code on the mobile phone verification page.

> [!CAUTION]
> When resetting the password yourself, the entire admin password reset process must be completed within 10 minutes; otherwise, you must start the process over.

### Eliminating bad passwords

Many security guidance documents recommend that you:

 -  Don't use the same password in multiple places.
 -  Make passwords complex.
 -  Avoid simple passwords like *Password123*.

Organizations can provide its users with [guidance on how to choose passwords](https://www.microsoft.com/research/publication/password-guidance?azure-portal=true). However, weak or insecure passwords are often still used. Azure AD Password Protection detects and blocks known weak passwords and their variants. It can also block other weak terms that are specific to an organization.

With Azure AD Password Protection, default global banned password lists are automatically applied to all users in an Azure AD tenant. To support your own business and security needs, you can also define entries in a custom banned password list. When users change or reset their passwords, these banned password lists are checked to enforce the use of strong passwords.

> [!TIP]
> Organizations shouldn't just rely on strong passwords enforced by Azure AD Password Protection. They should also use other features like Azure AD Multi-Factor Authentication.

#### Global banned password list

The Azure AD Identity Protection team constantly analyzes Azure AD security telemetry data looking for commonly used weak or compromised passwords. Specifically, the analysis looks for base terms that often are used as the basis for weak passwords. When weak terms are found, they're added to the global banned password list. The contents of the global banned password list aren't based on any external data source. Instead, it's based on the results of Azure AD security telemetry and analysis.

When a password is changed or reset for any user in an Azure AD tenant, the current version of the global banned password list is used to validate the strength of the password. This validation check results in stronger passwords for all Azure AD customers.

The global banned password list is automatically applied to all users in an Azure AD tenant. There's nothing to enable or configure, and it can't be disabled. This global banned password list is applied to users when they change or reset their own password through Azure AD.

> [!NOTE]
> Cyber-criminals also use similar strategies in their attacks to identify common weak passwords and variations. To improve security, Microsoft doesn't publish the contents of the global banned password list.

#### Custom banned password list

Some organizations want to improve security and add their own customizations on top of the global banned password list. To add your own entries, you can use the custom banned password list. Terms added to the custom banned password list should be focused on organizational-specific terms. For example:

 -  Brand names.
 -  Product names.
 -  Locations, such as company headquarters.
 -  Company-specific internal terms.
 -  Abbreviations that have specific company meaning.

For example, consider the fictional organization named *Contoso*. The company is based in London. Contoso is a plastics manufacturer whose primary product is known as a "Widget". For this company, it would be wasteful and less secure to try to block specific variations of these terms, such as:

 -  "Contoso!1"
 -  "Contoso@London"
 -  "ContosoWidget"
 -  "!Contoso"
 -  "LondonHQ"

Instead, it would be much more efficient and secure to block only the key base terms, such as:

 -  "Contoso"
 -  "London"
 -  "Widget"

The password validation algorithm then automatically blocks weak variants and combinations.

When terms are added to the custom banned password list, they're combined with the terms in the global banned password list. Password change or reset events are then validated against the combined set of these banned password lists.

The custom banned password list is limited to a maximum of 1000 terms. It's not designed for blocking large lists of passwords. To fully receive the benefits of the custom banned password list, first understand [how passwords are evaluated](/azure/active-directory/authentication/concept-password-ban-bad#how-are-passwords-evaluated?azure-portal=true) before you add terms to the custom banned list. This approach lets you efficiently detect and block large numbers of weak passwords and their variants.

#### Password spray attacks and third-party compromised password lists

Azure AD Password Protection helps you defend against password spray attacks. Most password spray attacks don't attempt to attack any given individual account more than a few times. This behavior would increase the likelihood of detection, either through account lockout or other means.

Instead, most password spray attacks submit only a few of the known weakest passwords against each of the accounts in an enterprise. This technique allows the attacker to quickly search for an easily compromised account and avoid potential detection thresholds.

Azure AD Password Protection efficiently blocks all known weak passwords likely to be used in password spray attacks. This protection is based on real-world security telemetry data from Azure AD to build the global banned password list.

There are some third-party websites that enumerate millions of passwords that have been compromised in previous publicly known security breaches. It's common for third-party password validation products to be based on brute-force comparison against those millions of passwords. However, those techniques aren't the best way to improve overall password strength given the typical strategies used by password spray attackers.

> [!NOTE]
> The global banned password list isn't based on any third-party data sources, including compromised password lists.

Although the global banned list is small in comparison to some third-party bulk lists, it's sourced from real-world security telemetry on actual password spray attacks. This approach improves the overall security and effectiveness, and the password validation algorithm also uses smart fuzzy-matching techniques. As a result, Azure AD Password Protection efficiently detects and blocks millions of the most common weak passwords from being used in your enterprise.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”