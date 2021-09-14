You can create a transport rule to bypass Safe Links just like you could to bypass Safe Attachments. To understand how you create a transport rule that bypasses scanning, review the following steps:

1.  Open a browser and navigate to the Microsoft 365 portal.
2.  On the **Microsoft 365 Home** page, select the **Admin** icon to open the Microsoft 365 Admin center.
3.  On the **Microsoft 365 Admin center**, in the left-hand navigation pane, select **Show all.**
4.  In the left-hand navigation pane, under the **Admin centers** group, select **Exchange**.
5.  In the **Exchange admin center (EAC),** select **mail flow** in the left-hand navigation pane.
6.  On the **mail flow** page, the **rules** tab is displayed by default.
7.  On the **rules** tab, select the **plus sign (+)** icon, and then in the drop-down menu that appears select **Create a new rule**.
8.  In the **new rule** window, enter a name for your new rule.
9.  In the **Apply this rule if…** list, choose an option, such as **The sender is located… > Inside the organization**, and then choose **OK**.

    > [!NOTE]
    > You can choose from several options, such as **The sender is a member of...** or **The sender address includes....** You can also set other criteria, including specifying senders, recipients, distribution group members, and attachment types.

10. Choose **More options....**
11. In the **\*Do the following…** list, select **Modify the message properties… > set a message header**.
12. In the **Set the message header** phrase, select the first **\*Enter text...** phrase, enter **X-MS-Exchange-Organization-SkipSafeLinksProcessing** as the header name, then select **OK**.
13. In the **Set the message header** phrase, select the remaining **\*Enter text...**, and then type something, such as a space, and then select **OK**.

    > [!NOTE]
    > This value isn't used by the system, even though something is required for the rule to work.

14. To save your settings, select **Save**.
