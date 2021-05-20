The previous unit examined the steps required to update the rules for a custom DLP policy. These rules let organizations define boundaries, which are low and high thresholds.

This unit continues the update process for the custom DLP policy used in this training scenario. It begins by modifying the conditions for the **Low volume of content detected** setting. You'll then update the corresponding actions that will be performed when the condition is satisfied.

### Modifying conditions

This unit continues with the example from the previous unit in which your organization previously created a DLP policy based on the **U.S. Personally Identifiable Information (PII) Data** template. The default sensitive information types associated with the **U.S. Personally Identifiable Information (PII) Data** policy include:

 -  U.S. Individual Taxpayer Identification Number
 -  U.S. Social Security Number
 -  U.S./U.K. Passport Number

When customizing a rule, you can add any sensitive information type. If necessary, you can also remove any of the default types.

In the continuing example, let’s assume that your organization requires protection of its users’ driver license numbers. To customize your policy, complete the following steps to add this sensitive information type as another condition:

7.  In the prior unit, you left off in the **Low volume of content detected** window. In the list of tabs across the top of the window, select **Conditions**.
8.  The **Conditions** section displays the list of three sensitive information types that were assigned to this policy by default. Below this list, select the **Add** button. This button displays a drop-down menu of data types that you can add to the policy. In the drop-down menu, select **Sensitive info types**.
9.  On the **Sensitive info types** window, select **+ Add**. This option displays the list of sensitive information types that you can choose from.
10. While you can scroll down through the list to the **U.S. Driver's License Number**, it will be quicker to enter **U.S.** in the search box. Entering **U.S.** in the search box will display the list of U.S.-specific information types.
11. Select the **U.S. Driver's License Number** checkbox and then select **Add**.
12. Select **Done**.
13. You should now see **U.S. Driver's License Number** appear as a fourth sensitive information type assigned to this policy.

In the next section, you'll continue updating this policy by modifying the actions to be done when this policy goes into effect.

### Modifying actions

Restricting access is only enforced in the **High volume of content detected** rule. The default action in the **Low volume of content detected** rule is to notify the user. To restrict access despite the total number of sensitive information types, you must modify the action associated with the **Low volume of content detected** rule. Complete the following steps to modify this action:

14. In the list of tabs across the top of the **Low volume of content detected** window, select **Actions**.
15. In the **Actions** section, select the **+ Add an action** button. A drop-down menu will appear. Select **Restrict access or encrypt the content**.
16. If necessary, scroll back to the top of the **Actions** section. Review the settings for the **Restrict access or encrypt the content** action that now appears as part of the rule.
17. The **Block people from sharing and restrict access to shared content** option is selected by default. Don't change this setting. However, since you want to encrypt this sensitive information in emails, select the **Encrypt email messages (applies only to content in Exchange)** option.

You'll continue updating the policy in the next unit, which covers user notifications.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”