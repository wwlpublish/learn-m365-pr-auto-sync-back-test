Email address policies assign email addresses to recipients in your Exchange organization. You use the Exchange admin center (EAC) to configure email address policies in Exchange Server.

## Create email address policies
After you create an email address policy, you need to apply the policy to recipients. 

1.	In the EAC, go to **Mail flow > Email address policies**, and then click **Add**.
2.	Configure the following email address policy settings:
   - **Policy name**: Enter a unique, descriptive name for the policy.
   - **Email address format**: Click **Add** to configure an email address template. After you add the first template to define the primary SMTP email address, you can add additional templates for proxy email addresses (SMTP or otherwise). Click **Edit** to modify an existing template.

   You can also click **Remove** to delete existing templates.
>[!NOTE]
> - The first SMTP email address template that you create here defines the primary (**Reply-To:**) SMTP email address. This template has the **Type** value **SMTP**, while other SMTP templates for proxy addresses have the **Type** value **smtp**.
> - You can't delete the email address template that defines the primary SMTP email address in the policy. Instead, you can add or modify another template, configure it to as the primary email address, and then delete the original template.
> - **Run this policy in this sequence with other policies**: The value that you can select here depends on how many other email address policies you've manually created. For example, for the first email address policy that you create, the only available value is 1. If you create another policy, you can select 1 or 2. Remember, the first email address policy that identifies a recipient configures the recipient's email addresses. All other policies are ignored, even if the first policy is unapplied and can't configure the recipient's email addresses.


When you're finished, click **Save**. You'll receive a warning message that tells you to click **Apply** to apply the policy to recipients. 

## Modify email address policies

For the default email address policy, you can't modify the name, priority, or recipient filter settings. You can only modify the email address templates.

After you modify an email address policy, you need to apply the policy to recipients.

If you created an email address policy in the Exchange Management Shell that uses a custom recipient filter, you can't modify the recipient filter in the EAC. You need to use the Exchange Management Shell:


You can't use the EAC or the Exchange Management Shell to replace a custom recipient filter with a precanned recipient filter or vice-versa in an existing email address policy.

### Modify email address policies in the EAC
The same settings are available as when you created the policy, although the settings are now located on separate tabs.

1.	In the EAC, go to **Mail flow > Email address policies**, select the policy from the list, and then click **Edit**.
2.	Configure the settings on the following tabs:
   - **General**
   - **Policy name**: A unique, descriptive name for the policy.
   - **Run this policy in this sequence with other policies**: Remember, the first email address policy that identifies a recipient configures the recipient's email addresses. All other policies are ignored, even if the first policy is unapplied and can't configure the recipient's email addresses.
   - **Email address format**

   You can also click **Remove** to delete existing email address templates.

   >[!NOTE]
   >- The **Type** value **SMTP** indicates the primary SMTP email address, and the value smtp (not bold and lowercase) indicates a proxy address.
   >- You can't delete the email address template that defines the primary SMTP email address in the policy. Instead, you can add or modify another template, configure it to define the primary email address, and then delete the original template.
   >- Even if you configured a custom recipient filter in the Exchange Management Shell, you can still select **Preview recipients the policy applies to** here.
3.	When you're finished, click **Save**. You'll receive a warning message that tells you to click **Apply** in the details pane to apply the policy to recipients. 

### Apply email address policies to recipients by using the EAC
1.	In the EAC, go to **Mail flow > Email address policies**.
2.	Select the email address policy that you want to apply (one of the polciies with the status *Unapplied*).
3.	Click **Apply**.
4.	Click **Yes** on the warning message to apply the policy

## Remove email address policies
You can remove most policies through the EAC. (You can't delete the default email address policy regardless of what tool you use.)

If you have a policy assigned to more than 3000 recipients, you'll need to use the Exchange Management Shell to remove it. It takes a long time to remove a policy like this from all of the recipients, and you won't be able to do anything else in the EAC until the removal is done. The recipient updates will take a long time, and they will prevent you from using the EAC session until the updates are finished. It's OK to use the EAC for policies that apply to fewer than 3000 recipients.

### Use the EAC to remove email address policies
1.	In the EAC, go to **Mail flow > Email address policies**.
2.	Select the email address policy that you want to delete, and then click **Remove**.
3.	Click **Yes** in the warning message that appears. A progress bar allows you to monitor the recipient update process. When updates are complete, click **Close**.

### Use the Exchange Management Shell to remove email address policies
To remove an email address policy, run the following command:

```PowerShell
Remove-EmailAddressPolicy -Identity <EmailAddressPolicyIdentity>
```
## Learn more

- [Manage email address policies](https://docs.microsoft.com/exchange/email-addresses-and-address-books/email-address-policies/eap-procedures?view=exchserver-2019?azure-portal=true)
- [Email address format window in the EAC](https://docs.microsoft.com/exchange/email-addresses-and-address-books/email-address-policies/eap-procedures?view=exchserver-2019#email-address-format-window-in-the-eac?azure-portal=true)
- [Recipient filters in the EAC](https://docs.microsoft.com/exchange/email-addresses-and-address-books/email-address-policies/eap-procedures?view=exchserver-2019#recipient-filters-in-the-eac?azure-portal=true)
- [Address types](https://docs.microsoft.com/Exchange/email-addresses-and-address-books/email-address-policies/email-address-policies?view=exchserver-2016#address-types?azure-portal=true)
- [PowerShell command reference library](https://docs.microsoft.com/powershell/windows/get-started?view=win10-ps?azure-portal=true)