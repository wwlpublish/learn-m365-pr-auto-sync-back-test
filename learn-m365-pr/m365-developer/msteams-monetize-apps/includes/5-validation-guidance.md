In this unit, we'll cover policies and include some guidance on the app, offer verification process, and look at some common scenarios for creating a Microsoft Teams app and a transactable SaaS offer.

## Purchase experiences on mobile

To avoid violating third-party App Store policies, you should refrain from providing direct links to subscription purchases within your mobile and tablet Microsoft Teams app.

It's OK to call out that a feature may require a paid subscription but your Microsoft Teams app can't provide a link to purchases.

This policy is similar to other popular mobile app store policies.

This is defined in the policy [1140.4.8 Mobile experience](/legal/marketplace/certification-policies#114048-mobile-experience).

## Common reasons for validation failures

Let's look at some of the common reasons for validation failures.

### Missed Policy Requirements

Review and ensure your transactable SaaS offer adheres to [Microsoft’s Commercial marketplace listing policies for SaaS offers](/legal/marketplace/certification-policies#1000-software-as-a-service-saas).

### Unsupported License Models

Microsoft Teams monetization was designed to support licenses assigned on a named, per-user basis.

If your SaaS offer is built with another method, you should indicate this in “Notes for Certification” for your submission.

### Mismatched Details Between Offer, App and/or Publisher

Ensure your publisher and offer described in Partner Center clearly match the description and details of the app to which you're linking.

Ensure you've published your offer in Partner Center (that is, it’s live in the marketplace) before submitting app for validation.

### Insufficient Details to Set up App Environment and Test

If setup of your app for testing purposes is complex or non-intuitive, please provide an end-to-end functional document, linked SaaS offer configuration steps, and instructions for license and user management as part of your “Notes for Certification”.

> [!TIP]
> Add a video recording of how your app and license management works to assist the team for testing.

### Offers That Have Potential to Confuse Users

Ensure any annual price listed is calculated for 12 months, not a reduced price per month.

If you're offering different plans (for example, free versus basic paid), ensure app experience reflects this in terms of what they purchased (or didn’t). This could come in the form of a banner highlighting the need to buy a subscription, reduced functionality within the application, and/or differentiated experiences for free versus paid.

## Common scenarios for Microsoft Teams app and transactable SaaS offers

The previous section covered some of the common reasons for validation issues. These are more related to your overall submission for your Microsoft Teams app and your SaaS offer.

But what are some of the common scenarios for Microsoft Teams apps and transactable SaaS offers? Think about this as different aspects.

### Scenario: Partner has an existing Microsoft Teams app and an existing transactable SaaS offer

You'll need to submit an updated Microsoft Teams manifest with the SaaS Offer ID included. This will trigger full functional validation for monetization workflows and existing app workflows.

In parallel, you can also link transactable SaaS offer with the Microsoft Teams app.

### Scenario: Partner has an existing Teams app and NO existing transactable SaaS offer

You can create a new SaaS offer and publish it to AppSource. This will trigger validation of SaaS offer.

After the SaaS offer goes live, you'll need to submit an updated Microsoft Teams manifest with SaaS offer ID included. This will trigger full functional validation for monetization workflows and existing app workflows.

In parallel, you can also link the transactable SaaS offer with the Microsoft Teams app.

### Scenario: Partner has NO existing Teams app and an existing transactable SaaS offer

You can create a new Microsoft Teams app and publish it to Microsoft Teams App Store along with SaaS offer ID included in manifest. This will trigger full functional validation for monetization workflows and all app workflows.

In parallel, you can also link transactable SaaS offer with Teams app.

### Scenario: Partner has NO existing Teams app and NO existing transactable SaaS offer

You can create a new SaaS offer and publish it to AppSource. This will trigger validation of SaaS offer monetization workflows.

After the SaaS offer goes live, you can create a new Microsoft Teams app and publish it to the Microsoft Teams app store along with SaaS offer ID included in manifest.

In parallel, you can also link transactable SaaS offer with Teams app.

## Support channels

When you're building your transactable SaaS offer, Microsoft's Partner Center is your best friend.

### Self-service support for your partners via Partner Center

Partners in need of support should always begin by submitting a support ticket through [Partner Center Support](https://aka.ms/partnercentersupport).

Once received, the partner will receive a ticket/case number, and the operations team will triage the ticket and assign to the respective subject matter expert.

For more information on how to contact support, see: [Get support for the commercial marketplace program in Partner Center](/azure/marketplace/support).

### Self-service support for your partners for Teams app submissions

Partners in need of support for their Microsoft Teams app submissions should reach out to teamsubm@microsoft.com after they've submitted their application and heard from the team.

For more information, see [Resolve issues with your store submission](/microsoftteams/platform/concepts/deploy-and-publish/appsource/resolve-submission-issues).

In this unit, we covered policies and include some guidance on the app, reviewed the  verification process, and looked at some common scenarios for creating a Microsoft Teams app and a transactable SaaS offer.
