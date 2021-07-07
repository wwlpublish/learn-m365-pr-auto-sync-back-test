For each user account that a sender spoofs from your domain, you can view the following information in the Microsoft 365 Security &amp; Compliance Center. Some user information is displayed in the Standard tab of the Anti-Spam portal, while other information is displayed in the Detailed tab.

:::row:::
  :::column:::
    

**Parameter**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Sender


  :::column-end:::
  :::column:::
    

The domain from which the spoof email originates. Microsoft 365 determines the domain of the pointer (PTR) DNS record of the sending IP address that's spoofing your organization. If no domain is found, the report displays the sender's IP address instead.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Spoofed user


  :::column-end:::
  :::column:::
    

Standard tab only. The user account that's being spoofed by the sender.

Detailed tab only. If the sender is spoofing multiple user accounts, then all the accounts are displayed in this field. If the sender is spoofing multiple user accounts, the report lists one row for each user that is spoofed by the sender.


> [!TIP]
> The spoofed user is the From (5322.From) address, which is also the address displayed as the From address by the mail client. This address is sometimes called the **header.from** address. The validity of this address is not checked by SPF.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Number of messages


  :::column-end:::
  :::column:::
    

The number of mail messages sent by the sender to your organization on behalf of the identified spoofed sender or senders within the last 30 days.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Number of user complaints


  :::column-end:::
  :::column:::
    

Complaints filed by users against this sender by your users within the last 30 days. Complaints are usually in the form of junk submissions to Microsoft.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Authentication result


  :::column-end:::
  :::column:::
    

Detailed tab only. This value is Passed if the sender passed Exchange Online Protection (EOP) sender authentication checks, such as SPF or DKIM. The value is Failed if the sender failed EOP sender authentication checks, or Unknown if the result of these checks isn't known.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Decision set by


  :::column-end:::
  :::column:::
    

Detailed tab only. Shows whether the Microsoft 365 administrator or the spoof intelligence policy determined whether the sender is allowed to spoof the user.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Last seen


  :::column-end:::
  :::column:::
    

Detailed tab only. The last date on which a message was received by this sender on behalf of this spoofed user.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Allowed to spoof?


  :::column-end:::
  :::column:::
    

Displays whether this sender is allowed to send email on behalf of the spoofed user. Possible values include:

 -  **Yes.** All spoofed addresses from this spoofing sender will be allowed to spoof your organization.
 -  **No.** Spoofed addresses from this spoofing sender won't be allowed to spoof your organization; instead, messages from this sender will be marked as spam by Microsoft 365.
 -  **Some users.** If a sender is spoofing multiple users, some spoofed addresses from this sender will be allowed to spoof your organization, the rest will be marked as spam. Use the Detailed tab to see the specific addresses.


  :::column-end:::
:::row-end:::


### Manage senders who are spoofing your domain

Complete the following steps to display the list of senders who are spoofing your domain. You can then decide whether each sender is legitimate and should be allowed to do so.

1.  Go to the **Office 365 Security &amp; Compliance Center** and sign in using your work or school account for Microsoft 365.
2.  In the left-hand navigation pane, select **Threat management** and then select **Policy**.
3.  On the **Policy** page, select the **Anti-spam** tile.
4.  On the **Anti-spam settings** page, in the list of anti-spam policies, expand **Spoof intelligence policy**.
5.  To view the list of senders spoofing your domain, select **Review new senders**. If you've already reviewed senders and want to change some of your previous choices, you can choose **Show me senders I already reviewed** instead.
6.  In the tabs at the top of the page, you can view either senders within your domains, or senders from external domains.
7.  Each row represents a sender that is spoofing one or more users in your organization.
8.  If a sender is spoofing multiple users and you want to allow that sender to spoof some users but not others, select **Choose users**. The **Detailed** tab is displayed with the list of users being spoofed. The list is split into individual rows. You can then choose whether to allow or block the sender from spoofing each user individually.
9.  To add a sender to the **allowlist** for a user, choose **Yes** from the **Allowed to spoof?** To add a sender to the **blocklist** for a user, choose **No**.
10. Select **Save** to save any changes.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”