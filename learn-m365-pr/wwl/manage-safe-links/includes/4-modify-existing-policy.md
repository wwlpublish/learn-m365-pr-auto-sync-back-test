To modify an existing Safe Links policy, complete the following steps:

1.  In the Security &amp; Compliance Center, in the left-hand navigation pane, select **Threat management** and then select **Policy.**
2.  On the **Policy** page, select the **ATP Safe Links** tile.
3.  On the **Safe Links** page, select a policy from the list and select on it (don't select the check box).
4.  In the policy details fly out that appears, select **Edit policy**.
5.  The available settings in the fly out that appears are identical to those policies described in the earlier unit on creating a Safe Links policy in the SCC.

### Set the priority of Safe Links policies

Safe Links policies are automatically assigned a priority that's based on the order in which they were created. So the first policy you create is assigned priority 0, which is the highest priority policy. The second policy you create (priority 1) has the next priority, and so on. Newer policies have a lower priority than older policies.

A lower priority number indicates a higher priority for the policy (priority 0 is the highest). Policies are processed in priority order (higher priority policies are processed before lower priority policies). No two policies can have the same priority, and policy processing stops after the first policy is applied.

In the Security &amp; Compliance Center, you can only change the priority of the Safe Links policy after you create it. In PowerShell, you can override the default priority when you create the Safe Links rule (which can affect the priority of existing rules).

**Additional reading.** For more information about the order of precedence and how multiple policies are evaluated and applied, see [Order and precedence of email protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/how-policies-and-protections-are-combined?azure-portal=true).
