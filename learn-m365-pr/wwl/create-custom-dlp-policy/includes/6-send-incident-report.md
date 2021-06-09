The previous unit examined the steps required to assign user overrides to an existing policy. This unit continues the update process. It focuses on a user's ability to generate an incident report when a DLP event occurs.

Administrators can configure an action to generate incident reports if a DLP event occurs. These incident reports help track events in real time. Reports are generated in real time and sent to a chosen mailbox, such as the mailbox for a compliance officer. The figure below shows a sample incident report.

:::image type="content" source="../media/sample-incident-report-b2e7b3f5.png" alt-text="graphic showing sample incident report":::


Incident reports are similar to user overrides in that both are generated and sent by default in the **High volume of content detected** rule. They're not generated and sent by default in the **Low volume of content detected** rule. The last step in customizing our continuing policy will be to enable the incident reports setting. You'll also configure it so that reports are sent to the compliance officer.

29. In the list of tabs across the top of the **Low volume of content detected** window, select **Incident reports.**
30. In the **Incident reports** section, select the **Use email incident reports to notify you when a policy match occurs** toggle switch to turn it **On**.
31. By default, incident reports are sent to the global administrator. You can modify this setting to add or remove individuals in the organization. To do so, select the **Add or remove people** link.<br><br>:::image type="content" source="../media/inicident-reports-on-off-setting-909f561e.png" alt-text="screenshot of incident reports setting to turn on and off":::
    
32. Once you have finished assigning users to receive this report, select **Save**. All the modifications that you've made to this **Low volume of content detected** policy will be saved.
33. On the **Editing Policy settings** window, select **Save** to save all the policy settings changes.
34. Select **Close** on the **U.S. Personally Identifiable Information (PII) Data** window.
