To modify an existing Safe Links policy, complete the following steps:

1.  In the **Microsoft 365 admin center**, select **Show All** in the left-hand navigation pane, and then under **Admin centers**, select **Security**.<br>
2.  In **Microsoft 365 Defender**, select **Policies & rules** in the left-hand navigation pane.<br>
3.  On the **Policies & rules** page, select **Threat policies**.<br>
4.  On the **Threat policies** page, under the **Policies** section, select **Safe Links.**
5.  On the **Safe Links** page, select a policy from the list and select on it (don't select the check box).
6.  In the policy details pane that appears, edit the settings for each section that must be changed.
7.  The available settings in the detail pane are identical to those policies described in the earlier unit on creating a Safe Links policy in Microsoft 365 Defender.

### Set the priority of Safe Links policies

Safe Links policies are automatically assigned a priority that's based on the order in which they were created. So the first policy you create is assigned priority 0, which is the highest priority policy. The second policy you create (priority 1) has the next priority, and so on. Newer policies have a lower priority than older policies.

A lower priority number indicates a higher priority for the policy (priority 0 is the highest). Policies are processed in priority order (higher priority policies are processed before lower priority policies). No two policies can have the same priority, and policy processing stops after the first policy is applied.

In Microsoft 365 Defender, you can only change the priority of the Safe Links policy after you create it. In PowerShell, you can override the default priority when you create the Safe Links rule (which can affect the priority of existing rules).

**Additional reading.** For more information about the order of precedence and how multiple policies are evaluated and applied, see [Order and precedence of email protection](/microsoft-365/security/office-365-security/how-policies-and-protections-are-combined?azure-portal=true).
