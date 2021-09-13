Sometimes it's useful to allow mail with attachments to flow without delay from internal senders or from trusted scanners, faxes, and smart hosts. An organization may decide that if the mail is from a trusted source, any attachments are assumed to be safe.

If an organization wants to implement such a policy, it can create a transport rule, also known as a mail flow rule, in the Exchange admin center. The purpose of this rule would be to bypass Safe Attachments scanning.

To create a transport rule that bypasses scanning, complete the following steps:

1.  Open a browser and navigate to the **Microsoft 365 portal**.
2.  On the **Microsoft 365 Home** page, select the **Admin** icon to open the **Microsoft 365 admin center**.
3.  In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Show all.**
4.  In the left-hand navigation pane, under the **Admin centers** group, select **Exchange**.
5.  In the **Exchange admin center (EAC)**, select **mail flow** in the left-hand navigation pane.
6.  On the **mail flow** page, the **rules** tab is selected at the top of the page by default. On the **rules** tab, select the **plus sign (+)** icon. In the drop-down menu that appears, select **Create a new rule**.
7.  In the **new rule** window, enter a name for your new rule.
8.  In the **Apply this rule if…** drop-down menu, select an option, such as **The sender is located… > Inside the organization**, and then select **OK**.

> [!NOTE]
> You can choose from several options, such as **The sender is a member of...** or **The sender address includes....** You can also set other criteria, including specifying senders, recipients, distribution group members, and attachment types.

9.  Choose **More options....**
10. In the **Do the following…** list, select **Modify the message properties… > set a message header**.
11. In the **Set the message header to this value** phrase, select the first instance of **\*Enter text...**, enter **X-MS-Exchange-Organization-SkipSafeAttachmentProcessing** as the header name, and then select **OK**.
12. In the **Set the message header to this value** phrase, select the remaining **\*Enter text...,** and then type something, such as a space, and then choose **OK**.

> [!NOTE]
> This value isn't used by the system, even though something is required for the rule to work.

13. To save your settings, select **Save**.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”