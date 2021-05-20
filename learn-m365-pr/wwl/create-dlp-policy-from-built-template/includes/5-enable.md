The previous unit examined the steps that must be completed in the New DLP policy wizard to configure policy rules. This unit picks up in the wizard where the previous unit left off.

The last two pages of the New DLP policy wizard ask about the status of the DLP policy after the wizard finishes. They also display a review of the policy's settings.

:::image type="content" source="../media/dlp-policy-wizard-policy-settings-turn-off-on-eeb57b67.png" alt-text="screenshot of new DLP policy window and turn on and off policy settings option":::


When an organization creates its DLP policies, it should consider rolling them out gradually. Doing so enables it to assess their impact and test their effectiveness before fully enforcing them. For example, you don’t want a new DLP policy to unintentionally block access to thousands of documents that people need to access to get their work done.

If you’re creating DLP policies that could potentially have a large impact, the following sequence of activation options is recommended:

 -  **I’d like to test it out first.** Start in test mode without Policy Tips and then use the DLP reports and any incident reports to assess the impact. You can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, you can fine-tune the rules as needed. In test mode, DLP policies won't impact the productivity of people working in your organization.
 -  **Show policy tips while in test mode.** Move to Test mode with notifications and Policy Tips so that you can begin to teach users about your compliance policies and prepare them for the rules that are going to be applied. At this stage, you can also ask users to report false positives so that you can further refine the rules.
 -  **Yes, turn it on right away.** Once testing is complete and you’ve achieved the planned test results, start full enforcement on the policies. This process applies the actions in the rules, and the content’s protected. Continue to monitor the DLP reports and any incident reports or notifications to make sure that the results are what you intend.

This example tests out all features of the DLP rules and immediately activates the policy.<br>

13. Select the **Yes, turn it on right away.**
14. Select **Next**.
15. On the next screen, review all settings of the DLP policy and select **Create** to complete the wizard.

:::image type="content" source="../media/dlp-policy-wizard-review-settings-668e1748.png" alt-text="screenshot of new DLP policy window and review your settings page":::


**Additional reading.** For more information, see [Create a DLP policy from a template](https://support.office.com/article/create-a-dlp-policy-from-a-template-59414438-99f5-488b-975c-5023f2254369?azure-portal=true).
