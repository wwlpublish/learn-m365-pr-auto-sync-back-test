There are several reasons why a policy tip may not appear as expected. The following chart identifies the most common causes and the corresponding resolution for each issue.

:::row:::
  :::column:::
    

**Cause**


  :::column-end:::
  :::column:::
    

**Resolution**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

The full Microsoft Office 2013, 2016, or 2019 Professional Plus suite isn't installed on the computer. Outlook relies on components from other Office programs. As such, policy tips won't work if you install Outlook separately.

> [!NOTE]
> Policy Tips are only supported in Office 2013 and later.


  :::column-end:::
  :::column:::
    

Install the full Office 2013, 2016, or 2019 Professional Plus suite.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Outlook isn't set up to use policy tips.


  :::column-end:::
  :::column:::
    

Make sure that policy tips are enabled in Outlook by following these steps:

1.  In Outlook, select the **File** tab, select **Options**, and then select **Mail**.
2.  Scroll to the **MailTips** section and then select the **MailTips Options** button.
3.  In the **Select MailTips to be displayed selection** dialog box, ensure the **Policy tip notification** option is selected.
4.  Select **OK** two times to close the File window.
5.  Restart Outlook.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Policy Tip settings are misconfigured.


  :::column-end:::
  :::column:::
    

1.  In the Security and Compliance Center, select **Threat management &gt; Data loss prevention**.
2.  Select the policy and then select the **Edit** icon to edit the policy.
3.  Select **Rules**.
4.  Select a rule and then select the **Edit** icon to open the **DLP RuleEditor**.
5.  Select **Actions** and verify the **Policy Tip content** and **Override options** settings under **Send a notification**.
6.  Select **OK** and repeat the process for any remaining rules in the policy.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Sensitive data threshold for the DLP policy isn't met. As a result, the associated DLP policy tips aren't displayed.


  :::column-end:::
  :::column:::
    

Check and modify, if necessary, the Instance Count of the sensitive information type(s). For example, you may have to adjust the minimum or maximum sensitive item count values or adjust the kind of sensitive data that triggers the policy.

1.  In the Security and Compliance Center, select **Data loss prevention &gt; Policy**.
2.  Select the policy and select the **Edit policy** icon to edit the policy.
3.  Select **Policy settings**.
4.  Select a rule and select the **Edit rule** icon to open the **DLP RuleEditor**.
5.  Select **Conditions** and verify the **Min count** and **Max count** values.
6.  If the values of a sensitive information type must be modified, select the sensitive information type, select the value, enter new values for the **Minimum count** or **Maximum count**, and then select **Save**.
7.  Select the **Save** button again to save the policy.


  :::column-end:::
:::row-end:::
