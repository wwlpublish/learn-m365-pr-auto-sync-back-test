Actionable Messages in Outlook provide a powerful set of capabilities and typically send information outside of the Microsoft 365 service. Because of this, services must register their sender and web API endpoints.

## Actionable Email Developer Dashboard

Developers register their solution in the Actionable Email Developer Dashboard. The developer provides the following information.

- One or more static email addresses that will be used as the sender for Actionable Messages.
- One or more HTTPS URLs that will be invoked by the actions in the message.
- The scope of the submission. Scope dictates the set of recipients that can receive Actionable Messages from the solution.
- Optionally, the developer can provide a logo for their provider.

Once the registration is created, the developer obtains a provider ID, which is included in the Adaptive Card markup in every message sent by the solution.

### Scope of submission

Next steps for the registration process depends on the desired scope of submission.

#### My Mailbox

With this scope, the solution is only allowed to send to the user's mailbox that created the registration. This scope is typically used in the early stages of development, allowing the developer to test the Actionable Message in their own mailbox.

This scope requires no additional information, and is auto-approved.

#### Test Users

With this scope, the solution is only allowed to send to the specified users. These users must be in the same Microsoft 365 organization as the user creating the registration. This scope is typically used in later stages of development, for more formal testing or beta testing.

This scope requires a list of one or more test user email addresses, and is auto-approved.

#### Organization

With this scope, the solution is allowed to send to any user in the same Microsoft 365 organization as the user creating the registration. This scope is typically used by line-of-business applications, such as internal expense reporting solutions.

This scope optionally accepts one or more email addresses of users to add to the new registration notification, along with a comment field. The request is sent to the organization's Exchange administrators for approval.

#### Global

With this scope, the solution is allowed to send to any Microsoft 365 user. This scope is typically used by ISVs or websites that provide services to multiple customers.

This scope requires additional information, including company information, point of contact, a description of the scenario and actions, and detailed instructions for testing and verifying the solution. The request is sent to Microsoft for testing, validation, and approval.
