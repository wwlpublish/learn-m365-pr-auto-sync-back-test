Blocked users are potentially compromised users. They may have exceeded one of their company's outbound sending limits as specified in [the service limits](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options?azure-portal=true). Or, they may have exceeded the sending limits in their company's outbound spam policies (see the prior unit). Sending limits apply to the number of recipients, number of messages, and number of recipients per message that a user can send from their Exchange Online account.

If a user exceeds a sending limit:

 -  The user is added to the **Restricted users** page in the Microsoft 365 Defender portal. Doing so blocks the user from sending email.
 -  The user can still receive email.

When this scenario occurs and the user later tries to send email, the message is returned in a non-delivery report (also known as an NDR, or bounce message) with the error code [5.1.8](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-1-8-in-exchange-online?azure-portal=true) and the following text:

Your message couldn't be delivered because you weren't recognized as a valid sender. The most common reason for this is that your email address is suspected of sending spam and it's no longer allowed to send email. Contact your email admin for assistance. Remote Server returned '550 5.1.8 Access denied, bad outbound sender.

There are two ways in which an admin can unblock a user so they can resume sending email:

 -  Remove the user from the **Restricted users** page in the Microsoft 365 Defender.
 -  Through Exchange Online PowerShell.

> [!IMPORTANT]
> A sender exceeding the outbound email limits is an indicator of a compromised account. Before you remove the user from the **Restricted users** portal, be sure to follow the required steps to regain control of their account. For more information, see [Responding to a compromised email account in Office 365](/microsoft-365/security/office-365-security/responding-to-a-compromised-email-account?azure-portal=true).

### Verify the alert settings for blocked users

The default alert policy named **User restricted from sending email** will automatically notify admins when users are blocked from sending outbound mail. You can verify these settings and add other users to notify. For more information about alert policies, see [Alert policies in Microsoft 365](/microsoft-365/compliance/alert-policies?azure-portal=true).

For alerts to work, audit log search must be turned on. For more information, see [Turn the audit log search on or off](/microsoft-365/compliance/turn-audit-log-search-on-or-off?azure-portal=true).

Complete the following steps to verify the alert settings for blocked users.

1.  In the Microsoft 365 Defender portal at [https://security.microsoft.com](https://security.microsoft.com/), go to **Email &amp; collaboration &gt; Policies &amp; rules &gt; Alert policy**.
2.  On the **Alert policy** page, find and select the alert named **User restricted from sending email**. You can sort the policies by name, or use the **Search** box to find the policy.
3.  In the **User restricted from sending email** pane that appears, verify or configure the following settings:
    
     -  **Status**. Verify the alert is turned **On**.
     -  **Email recipients**. Select **Edit** and verify or configure the following settings in the **Edit recipients** pane that appears:
        
         -  **Send email notifications**. Verify this option is selected (set to On).
         -  **Email recipients**. The default value is **TenantAdmins** (meaning, Global admin members). To add more recipients, select inside the box. A list of recipients will appear, and you can start typing a name to filter and select a recipient. You can remove an existing recipient from the box by selecting the **X** that appears next to their name.
         -  **Daily notification limit**. The default value is **No limit**. However, you can select a limit for the maximum number of notifications per day.

    When you're finished, select **Save**.

4.  On the **User restricted from sending email** pane, select **Close**.

### Unblock a user through the Microsoft 365 Defender portal

A blocked user can be unblocked, which allows them to resume sending email. To do so, it must remove the user from the **Restricted users** list in the Microsoft 365 Defender portal. Complete the following steps to unblock a user:

1.  In the **Microsoft 365 Defender** portal at [https://security.microsoft.com](https://security.microsoft.com/), go to **Email &amp; collaboration &gt; Review &gt; Restricted users**.
2.  On the **Restricted users** page, find and select the user that you want to unblock by selecting the user.
3.  Select the **Unblock** action that appears.
4.  In the **Unblock user** pane that appears, read the details about the restricted account. You should review the recommendations to ensure you're taking the proper actions in case the account is compromised. When you're finished, select **Next**.
5.  The next screen has recommendations to help prevent future compromise. Enabling multifactor authentication and resetting the password are a good defense. When you're finished, select **Submit**.
6.  Select **Yes** to confirm the change.

> [!WARNING]
> It might take up to one hour for all restrictions to be removed from the user.

### Unblock a user using Exchange Online PowerShell

To view this list of users that are restricted from sending email, run the following command:

```powershell
Get-BlockedSenderAddress
```

To view details about a specific user, replace &lt;emailaddress&gt; with their email address and run the following command:

```powershell
Get-BlockedSenderAddress -SenderAddress <emailaddress>
```

To remove a user from the **Restricted users** list, replace &lt;emailaddress&gt; with their email address and run the following command:

```powershell
Remove-BlockedSenderAddress -SenderAddress <emailaddress>
```
