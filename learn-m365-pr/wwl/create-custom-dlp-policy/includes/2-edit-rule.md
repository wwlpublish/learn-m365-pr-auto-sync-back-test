This unit examines how to take an existing, built-in rule and edit it to create a custom DLP rule. Policy settings control the behavior of rules within a policy. Each policy is automatically created with two rules:

 -  Low volume of content detected
 -  High volume of content detected

The purpose of these rules is to let organizations define boundaries. Boundaries are low and high thresholds.

 -  The default threshold for the **Low volume of content detected** rule is 1 and 9, respectively.
 -  The default threshold for the **High volume of content detected** rule is 10 and Any, respectively.

Let's follow an example of how to create a custom DLP policy rule. In this example, assume your organization previously created a DLP policy based on the **U.S. Personally Identifiable Information (PII) Data** template. You'll now edit a rule in this policy.

Complete the following steps to begin the process of editing one of the rules for this policy:

1.  Go to the [Security &amp; Compliance Center](https://sip.protection.office.com/homepage?azure-portal=true) and sign in using your work or school account.
2.  In the left-hand navigation pane, select **Data loss prevention** and then select **Policy**.<br>
3.  On the **Policy** page, select the **U.S. Personally Identifiable Information (PII) Data** policy that your organization previously created from the built-in DLP policy template. Selecting a policy listed on the **Policy** home page opens a new window with a brief overview of the policy.**<br>**
4.  In the **U.S. Personally Identifiable Information (PII) Data** window, scroll down to the bottom of the window. In the **Policy settings** section, select **Edit**.
5.  In the **Editing Policy settings** page, you can create new rules and modify any existing rules. In this example, let’s modify the **Low volume of content detected** rule by adding the **U.S. Driver’s License Number** sensitive information type. To do so, select the drop-down arrow next to the **Low volume of content detected.**
6.  Select **Edit rule**.

The wizard continues in the next unit, at which point you'll update the conditions for the **Low volume of content detected** setting.
