You can apply your company branding to customize the look of your organization's email messages and the encryption portal. You'll need to apply global administrator permissions to your work or school account before you can get started. Once you have these permissions, use the **Get-OMEConfiguration** and **Set-OMEConfiguration** Windows PowerShell cmdlets to customize these parts of encrypted email messages:

 -  Introductory text.
 -  Disclaimer text.
 -  URL for Your organization's privacy statement.
 -  Text in the message encryption portal.
 -  Logo that appears in the email message and encryption portal, or whether to use a logo at all.
 -  Background color in the email message and encryption portal.

You can also revert back to the default look and feel at any time.

If you'd like more control, use Microsoft Purview Advanced Message Encryption to create multiple templates for encrypted emails originating from your organization. Use these templates to control parts of the end-user experience. For example, specify whether recipients can use Google, Yahoo, and Microsoft Accounts to sign in to the encryption portal. Use templates to fulfill several use cases, such as:

 -  Individual departments, such as Finance, Sales, and so on.
 -  Different products.
 -  Different geographical regions or countries.
 -  Whether you want to allow emails to be revoked.
 -  Whether you want emails sent to external recipients to expire after a specified number of days.

Once you've created the templates, you can apply them to encrypted emails by using Exchange mail flow rules. If you have Microsoft Purview Advanced Message Encryption, you can revoke any email that you've branded by using these templates.

### Work with Microsoft Purview Message Encryption branding templates

You can modify several features within a branding template. You can modify, but not remove, the default template. If you have Microsoft Purview Advanced Message Encryption, you can also create, modify, and remove custom templates.

To work with one branding template at a time, use the following Windows PowerShell cmdlets:

 -  **Set-OMEConfiguration**. Modify the default branding template or a custom branding template that you created.
 -  **New-OMEConfiguration**. Create a new branding template.
 -  **Remove-OMEConfiguration**. Remove a custom branding template. You can't delete the default branding template. This cmdlet only works with Microsoft Purview Advanced Message Encryption.

### Modify a Microsoft Purview Message Encryption branding template

Organizations must use Windows PowerShell to modify one branding template at a time. If you have Advanced Message Encryption, you can also create, modify, and remove custom templates. Complete the following steps to modify a branding template:

1.  Using a work or school account that has global administrator permissions in your organization, start a Windows PowerShell session and connect to Exchange Online.
2.  Use the **Set-OMEConfiguration** cmdlet. Refer to the following graphic and table for guidance on what parameters to include in this command. The parameters are based on the type of customization you want to make.
    
    :::image type="content" source="../media/message-encryption-template-0805f33e.png" alt-text="Diagram showing a message encryption branding template with all the features highlighted that can be customized.":::
    

:::row:::
  :::column:::
    **To customize this feature of the encryption experience:**
  :::column-end:::
  :::column:::
    **Use these PowerShell commands:**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Background color:
  :::column-end:::
  :::column:::
    **Set-OMEConfiguration -Identity "&lt;OMEConfigurationName&gt;" -BackgroundColor "&lt;\#RRGGBB hexadecimal color code or name value&gt;"**Example:

Set-OMEConfiguration -Identity "Branding Template 1" -BackgroundColor "\#ffffff"

For more information about background colors, see [Background colors](/microsoft-365/compliance/add-your-organization-brand-to-encrypted-messages?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Logo:
  :::column-end:::
  :::column:::
    **Set-OMEConfiguration -Identity "&lt;OMEConfigurationName&gt;" -Image &lt;Byte\[\]&gt;**

Example:

Set-OMEConfiguration -Identity "Branding Template 1" -Image (\[System.IO.File\]::ReadAllBytes('C:\\Temp\\contosologo.png'))

Supported file formats: .png, .jpg, .bmp, .tiff

Optimal size of logo file: less than 40 KB

Optimal size of logo image: 170x70 pixels. If your image exceeds these dimensions, the service resizes your logo for display in the portal. The service doesn't modify the graphic file itself. For best results, use the optimal size.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Text next to the sender's name and email address:
  :::column-end:::
  :::column:::
    **Set-OMEConfiguration -Identity "&lt;OMEConfigurationName&gt;" -IntroductionText "&lt;String up to 1024 characters&gt;"**

Example:

Set-OMEConfiguration -Identity "Branding Template 1" -IntroductionText "has sent you a secure message."
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Text that appears on the "Read Message" button:
  :::column-end:::
  :::column:::
    **Set-OMEConfiguration -Identity "&lt;OMEConfigurationName&gt;" -ReadButtonText "&lt;String up to 1024 characters&gt;"**

Example:

Set-OMEConfiguration -Identity "OME Configuration" -ReadButtonText "Read Secure Message"
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Text that appears below the "Read Message" button:
  :::column-end:::
  :::column:::
    **Set-OMEConfiguration -Identity "&lt;OMEConfigurationName&gt;" -EmailText "&lt;String up to 1024 characters&gt;"**

Example:

Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system."
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    URL for the Privacy Statement link:
  :::column-end:::
  :::column:::
    **Set-OMEConfiguration -Identity "&lt;OMEConfigurationName&gt;" -PrivacyStatementURL "&lt;URL&gt;"**

Example:

Set-OMEConfiguration -Identity "Branding Template 1" -PrivacyStatementURL "https://contoso.com/privacystatement.html"
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Disclaimer statement in the email that contains the encrypted message:
  :::column-end:::
  :::column:::
    **Set-OMEConfiguration -Identity "&lt;OMEConfigurationName&gt;" -DisclaimerText "&lt;Disclaimer statement. String of up to 1024 characters.&gt;"**

Example:

Set-OMEConfiguration -Identity "Branding Template 1" -DisclaimerText "This message is confidential for the use of the addressee only."
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Text that appears at the top of the encrypted mail viewing portal:
  :::column-end:::
  :::column:::
    **Set-OMEConfiguration -Identity "&lt;OMEConfigurationName&gt;" -PortalText "&lt;Text for your portal. String of up to 128 characters.&gt;"**

Example:

Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal"
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    To enable or disable authentication with a one-time pass code for this custom template:
  :::column-end:::
  :::column:::
    **Set-OMEConfiguration -Identity "&lt;OMEConfigurationName&gt;" -OTPEnabled &lt;$true\|$false&gt;**

Examples:

To enable one-time passcodes for this custom template:

Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $true

To disable one-time passcodes for this custom template:

Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $false
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    To enable or disable authentication with Microsoft, Google, or Yahoo identities for this custom template:
  :::column-end:::
  :::column:::
    **Set-OMEConfiguration -Identity "&lt;OMEConfigurationName&gt;" -SocialIdSignIn &lt;$true\|$false&gt;**

Examples:

To enable social IDs for this custom template:

Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $true

To disable social IDs for this custom template:

Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $false
  :::column-end:::
:::row-end:::


### Create an Exchange mail flow rule that applies your custom branding to encrypted emails

> [!WARNING]
> Third-party applications that scan and modify mail can prevent Microsoft Purview Message Encryption branding from being applied correctly.

After you've either modified the default template or created new branding templates, you can create Exchange mail flow rules to apply your custom branding based on certain conditions. Most importantly, the email must be encrypted. Such a rule will apply custom branding in the following scenarios:

 -  The email was manually encrypted by the end user using Outlook or Outlook on the web (formerly Outlook Web App).
 -  The email was automatically encrypted by an Exchange mail flow rule or a Microsoft Purview Data Loss Prevention policy.

To ensure Microsoft Purview Message Encryption applies your custom branding, set up a mail flow rule to encrypt your email messages. The priority of the encryption rule should be higher than the branding rule. By doing so, the encryption rule is processed first. By default, if you create the encryption rule before the branding rule, then the encryption rule will have a higher priority.

1.  In a web browser, using a work or school account that has been granted global administrator permissions, sign in to Microsoft 365.
2.  On the **Office 365 Home** page, select the **Admin** tile.
3.  In the **Microsoft 365 admin center**, select **Admin centers** in the navigation pane, and then select **Exchange**.
4.  In the **Exchange admin center**, in the navigation pane, select **Mail flow**, and then select **Rules**.
5.  On the **Rules** page, select **New+**, then select **Create a new rule** from the drop-down list**.**
6.  In the **Name** field, type a name for the rule, such as **Branding for Sales department**.
7.  In **Apply this rule if**, select the condition **The sender is located inside the organization.** Then select any other conditions you want from the list of available conditions. For example, you may want to apply a particular branding template to:
     -  All encrypted emails sent from members of the Finance department.
     -  Encrypted emails sent with a certain keyword such as **External** or **Partner**.
     -  Encrypted emails sent to a particular domain.
8.  If you've already defined a mail flow rule to apply encryption, skip this step. Otherwise, to configure the mail flow rule to apply encryption, from **Do the following**, select **Modify the message security**, and then select **Apply Office 365 Message Encryption and rights protection**. Select an RMS template from the list and then select **add action**.
    
    The list of templates includes default templates and options and any custom templates you create. If the list is empty, ensure that you've set up Microsoft Purview Message Encryption.
9.  From **Do the following**, select **Modify the message security**, then select **Apply custom branding to OME messages**. From the drop-down list that appears, select a branding template.
    
    Select **add action** if you want to specify another action, or select **Save**, and then select **OK**.

**Additional reading**. For more information on mail flow rules, see the following links:

 -  For more information on how to create an Exchange mail flow rule that applies encryption, see [Define mail flow rules to encrypt email messages in Office 365](/microsoft-365/compliance/define-mail-flow-rules-to-encrypt-email?azure-portal=true).
 -  For more information on setting the priority of a mail flow rule, see [Manage mail flow rules](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#set-the-priority-of-a-mail-flow-rule?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”