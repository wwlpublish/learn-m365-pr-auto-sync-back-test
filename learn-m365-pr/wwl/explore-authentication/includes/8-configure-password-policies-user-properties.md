In an organizational environment, password policies define the configuration of user passwords. AD DS stores user accounts, which are managed by network administrators or other support staff, such as help-desk employees.

:::image type="content" source="../media/account-password-policies-4a64a7a6.jpg" alt-text="Screenshot of the user properties screen showing where password policies are set.":::


### Using Group Policy to configure password policies

Although domain administrators configure password policies, you should know the available password-policy options so that you recognize when they affect the user’s ability to sign in. You configure password policies by using Group Policy, which contains settings for account lockout. When you enable account lockout, a user who attempts to sign in by using an incorrect password is locked out after the number of attempts that you configure. Remember that account lockouts can occur based on sign-in attempts to any system that authenticates users to AD DS. The most common scenario is users signing in at workstations, but account lockout also applies to applications such as Microsoft Outlook Web App.

The following table lists important Group Policy settings that can affect the user sign-in process. These settings are located at Computer Configuration\\Windows Settings\\Security Settings\\Account Policies.

:::row:::
  :::column:::
    **Setting**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **Default setting**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Password Policy\\Enforce password history
  :::column-end:::
  :::column:::
    When you turn on **enforce password history**, users cannot reuse passwords.
  :::column-end:::
  :::column:::
    By default, Group Policy remembers 24 passwords.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Password Policy\\Maximum password age
  :::column-end:::
  :::column:::
    **Maximum password age** is the longest span of time that a password can exist before a user must change it.
  :::column-end:::
  :::column:::
    By default, users must change their password every 42 days.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Password Policy\\Minimum password age
  :::column-end:::
  :::column:::
    **Minimum password age** is the minimum amount of time that a user must keep a password.
  :::column-end:::
  :::column:::
    By default, a user must keep a password for one day. This prevents users from cycling quickly through a list of passwords and defeating the password history requirement.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Password Policy\\Minimum password length
  :::column-end:::
  :::column:::
    **Minimum password length** is the minimum number of characters required for a password that domain users create.
  :::column-end:::
  :::column:::
    By default, a minimum length of seven characters is required.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Password Policy\\Passwords must meet complexity requirements
  :::column-end:::
  :::column:::
    If you turn on this setting, passwords must meet specific complexity requirements. Users must create complex passwords by using specific elements, including uppercase and lowercase characters, numbers, and symbols.
  :::column-end:::
  :::column:::
    Three of the four complexity elements must be present. This is enabled by default.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Account Lockout Policy\\Account lockout threshold
  :::column-end:::
  :::column:::
    This defines the number of invalid sign-in attempts that users can make before Windows locks their account. When you enable **Account Lockout threshold**, you can define the period within which the invalid attempts must occur, and how long the account remains locked.
  :::column-end:::
  :::column:::
    The default value is 0, which means accounts never lock.
  :::column-end:::
:::row-end:::


### **User account settings that can affect the sign-in process**

Each user account has settings that are relevant to the sign-in process. You need to be aware of these settings so that you can identify them as potential sources of sign-in issues, and then escalate the issue to the appropriate group in your organization.

:::row:::
  :::column:::
    **Setting**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    User logon name
  :::column-end:::
  :::column:::
    This is the user name that users should use when signing in.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Unlock account
  :::column-end:::
  :::column:::
    If a user locks an account because of invalid sign-in attempts, use this check box to unlock the account.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    User must change password at next logon
  :::column-end:::
  :::column:::
    When you enable on this setting, the user must change their password during the next sign-in. If the user does not change their password, he or she might not be able to sign in.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    User cannot change password
  :::column-end:::
  :::column:::
    If you enable this setting, the user cannot change their password. This setting overrides any requirements to change a password in the domain password policy. You typically use this setting only for service accounts.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Password never expires
  :::column-end:::
  :::column:::
    When you enable this setting, users are not required to change their password. This setting overrides any requirements to change a password in the domain password policy. You typically use this setting for service accounts, and you also might use it for users who are exempt from changing passwords.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Account is disabled
  :::column-end:::
  :::column:::
    Enabling this setting prevents users from signing in and using this account. You typically use this setting when an employee is out of the office for a long period, or when your organization terminates an employee.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Smart card is required for interactive logon
  :::column-end:::
  :::column:::
    When you enable this setting, a user is required to use a smart card to perform sign-ins. Requiring a smart card enhances security in environments with infrastructure to support smart card-based sign-ins.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Account expires
  :::column-end:::
  :::column:::
    This setting allows configuration of a date after which an account is disabled. You typically use this setting only for contract employees or other temporary staff.
  :::column-end:::
:::row-end:::
