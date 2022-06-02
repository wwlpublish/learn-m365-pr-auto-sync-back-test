As an administrator that manages Exchange Online, you can create mail flow rules (also known as transport rules) to help protect email messages you send and receive. For example, you can:

 -  Set up rules to encrypt outgoing email messages.
 -  Remove encryption from encrypted messages coming from inside your organization.
 -  Remove encryption from replies to encrypted messages sent from your organization.

> [!NOTE]
> You can't encrypt inbound mail from senders outside of your organization.

You can use the Exchange admin center (EAC) or Exchange Online PowerShell to create these rules. In addition to overall encryption rules, you can also choose to enable or disable individual message encryption options for end users.

If you recently migrated from Active Directory RMS to Azure Information Protection, you must:

 -  Set up Microsoft Purview Message Encryption. For more information, see the prior unit in this training.
 -  Review your existing mail flow rules to ensure they continue to work in your new environment.
 -  Update your existing mail flow rules so that you can use Microsoft Purview Message Encryption with Azure Information Protection. Otherwise, your users will continue to receive encrypted mail that uses the previous HTML attachment format instead of the new, seamless experience.

**Additional reading**. For more resources, see the following links:

 -  For information about the components that make up mail flow rules and how mail flow rules work, see [Mail flow rules (transport rules) in Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules?azure-portal=true).
 -  For information about how mail flow rules work with Azure Information Protection, see [Configuring Exchange Online mail flow rules for Azure Information Protection labels](/azure/information-protection/deploy-use/configure-exo-rules?azure-portal=true).

For hybrid Exchange environments, on-premises users can send and receive encrypted mail using message encryption only if email is routed through Exchange Online. To configure message encryption in a hybrid Exchange environment, you should complete the following steps:

1.  [Configure hybrid using the Hybrid Configuration wizard](/Exchange/exchange-hybrid?azure-portal=true).
2.  [Configure mail to flow from Office 365 to your email server](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-1-configure-mail-to-flow-from-office-365-to-your-on-premises-email-server?azure-portal=true).
3.  [Configure mail to flow from your email server to Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365?azure-portal=true).

Once you've configured mail to flow through Microsoft 365, you can configure mail flow rules for message encryption by using this guidance.

### Create mail flow rules to encrypt email messages with Microsoft Purview Message Encryption

You can define mail flow rules for triggering message encryption by using the Exchange admin center.

#### Use the EAC to create a rule for encrypting email messages with Microsoft Purview Message Encryption

1.  In a web browser, using a work or school account that has been granted global administrator permissions, sign in to Microsoft 365.
2.  On the **Office 365 Home** page, select the **Admin** tile.
3.  In the **Microsoft 365 admin center**, select **Admin centers** in the navigation pane, and then select **Exchange**.
4.  In the **Exchange admin center**, in the navigation pane, select **Mail flow**, and then select **Rules**.
5.  On the **Rules** page, select **New+**, then select **Create a new rule** from the drop-down list**.**
6.  In the **Name** field, type a name for the rule.
7.  In **Apply this rule if**, select a condition, and enter a value if necessary. For example, to encrypt messages going to a specific user:
    1.  In **Apply this rule i**f, select **the recipient is**.
    2.  Select an existing name from the contact list or type a new email address in the **check names** box.
         -  To select an existing name, select it from the list and then select **OK**.
         -  To enter a new name, type an email address in the check names box and then select **check names &gt; OK**.
8.  To add more conditions, select **More options** and then select **add condition** and select from the list.
    
    For example, to apply the rule only if the recipient is outside your organization, select **add condition,** select **The recipient is external/internal**, select **Outside the organization**, and then select **OK**.
9.  To enable message encryption, from **Do the following**, select **Modify the message security,** and then select **Apply Office 365 Message Encryption and rights protection**. Select an RMS template from the list, select **Save**, and then select **OK**.

The list of templates includes all default templates and options. It also includes any custom templates you've created for use by Microsoft 365. If the list is empty, ensure that you've set up Microsoft Purview Message Encryption as described in a previous unit in this training.

> [!NOTE]
> You can select the **add action** option if you want to specify another action.

#### Use the EAC to update an existing mail flow rule to use Microsoft Purview Message Encryption

1.  In a web browser, using a work or school account that has been granted global administrator permissions, sign in to Office 365.
2.  On the **Office 365 Home** page, select the **Admin** tile.
3.  In the **Microsoft 365 admin center**, select **Admin centers** in the navigation pane, and then select **Exchange**.
4.  In the **Exchange admin center**, in the navigation pane, select **Mail flow**, and then select **Rules**.
5.  In the list of mail flow rules, select the rule you want to modify to use with Microsoft Purview Message Encryption and then select **Edit** (the pencil icon).
6.  To enable encryption using Microsoft Purview Message Encryption, from **Do the following**, select **Modify the message security**, and then select **Apply Office 365 Message Encryption and rights protection**. Select an RMS template from the list, select **Save**, and then select **OK**.
    
    The list of templates includes all default templates and options. It also includes any custom templates you've created for use by Microsoft 365. If the list is empty, ensure that you've set up Microsoft Purview Message Encryption as described in a previous unit in this training.
    
    You can select the **add action** option if you want to specify another action.
7.  From the **Do the following** list, remove any actions that are assigned to **Modify the message security**, and then select **Apply the previous version of OME**.
8.  Select **Save**.
