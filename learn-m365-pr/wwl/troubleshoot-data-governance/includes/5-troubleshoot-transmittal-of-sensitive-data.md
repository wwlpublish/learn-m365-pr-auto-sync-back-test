When sensitive data is unexpectedly transmitted despite a policy that has been turned on, it's typically caused by an errant setting in the policy.

The first place to check is the settings of the policy, particularly the status of the policy. Complete the following steps to check these settings:

1.  In the Security and Compliance Center, select **Data loss prevention &gt; Policy**.
2.  Select the desired policy from the list and then select **Edit policy.**
3.  Verify whether the policy is enabled.
4.  Select **Policy settings** and verify the status of each rule.
5.  Select the rule to be enforced. In the figure below, only the **High volume of content detected** rule is being enforced, since the status of the **Low volume of content detected** rule is **Off**.<br><br>:::image type="content" source="../media/policy-window-with-rule-status-f7b34989.png" alt-text="screenshot of the policy settings window showing the status of each rule":::
    <br><br>
6.  To turn on the rule, select the slider in the status line.
7.  Select **Name** on the left pane, decide to select **Yes, turn it on right away,** or to remain in test mode with **I’d like to test it out first** and select the **Show policy tips while in test mode**, and then select **Save**.
