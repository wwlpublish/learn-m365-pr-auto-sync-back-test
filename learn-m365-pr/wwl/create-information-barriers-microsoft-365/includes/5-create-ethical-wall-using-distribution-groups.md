The most common method of implementing an ethical wall, or information barrier, in Exchange Online is to:

1.  Make each affected mailbox a member of one of two distribution groups.
2.  Configure the transport rule to reject any messages sent between members of those two distribution groups.

The following graphic shows how sender restrictions on distribution groups create an ethical wall in Exchange Online between the users of two departments.

:::image type="content" source="../media/sender-restrictions-on-group-email-495161f2.jpg" alt-text="graphic shows how sender restrictions on distribution groups create an ethical wall between the users of two departments.":::


For example, let’s assume an organization wants to enforce an ethical wall that prevents members of the Marketing department and members of the Finance department from exchanging email. When you have two sets of users defined by distribution groups, you can create a rule that prevents e-mail communication between the two groups.

The following table identifies the details used in this example.

:::row:::
  :::column:::
    

**Configuration**


  :::column-end:::
  :::column:::
    

**Value**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Groups that define the users who shouldn't communicate with each other


  :::column-end:::
  :::column:::
    

Marketing and Finance


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Rule name


  :::column-end:::
  :::column:::
    

Marketing-Finance Prohibition


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Block action


  :::column-end:::
  :::column:::
    

For the Block action: Rejection reason.

"Industry regulations prevent direct communication between members of the marketing and finance departments. See your manager for details."


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Moderate action


  :::column-end:::
  :::column:::
    

For the Moderate action: Moderator.

Select one or more moderators. Distribution groups can't be selected as a moderator.


  :::column-end:::
:::row-end:::


Complete the following steps to create this ethical wall in Exchange Online:

1.  Sign in to the Exchange admin center using an admin account.
2.  In the left-hand navigation pane, select **mail flow.**
3.  On the **mail flow** page, the **rules** tab at the top of the page is displayed by default.
4.  In the **rules** tab, select the **plus sign (+)** icon on the menu bar and then select **Restrict messages by sender or recipient**… in the drop-down list.
5.  On the **new rule** page, complete the following steps (in steps c and d, it doesn't matter which group you select first or second):<br>
    
    1.  Enter a **name** for the transport rule.
    2.  Select **The message is between members of these groups**… from the **Apply this if…** drop-down list.
    3.  Select the first instance of **Select people**.... In the **Select Members** window, select **Marketing**, select **Add**, and then select**OK**.
    4.  Select the second instance of **Select people**.... In the **Select Members** window, select **Finance**, select **Add**, and then select **OK**.
6.  Select one of the following actions from the **Do the following…** drop-down list:<br>
    
     -  **Block**. After selecting **Block**, complete the following steps:<br>
        
        1.  Select **Reject the message with the explanation**…
        2.  In the **specify rejection reason** dialog box, type an explanation, such as **Industry regulations prevent direct communication between members of the marketing and finance departments. See your manager for details.**
        3.  Select **OK**.
     -  **Moderate**. After selecting **Moderate**, complete the following steps:<br>
        
        1.  Select **Forward the message for approval to**…
        2.  In the **SelectMembers** window, select a moderator and then select **Add**.
        3.  Select **OK**.
7.  Select **Save**.

> [!NOTE]
> You must be assigned permissions before you can complete this procedure. See the "Transport rules" section in the following article for the list of permissions that are needed: [Messaging Policy and Compliance Permissions](https://docs.microsoft.com/Exchange/permissions/feature-permissions/policy-and-compliance-permissions?azure-portal=true).
