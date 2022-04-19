Microsoft 365 imposes security requirements on Actionable Messages in Outlook senders to prevent unauthorized senders from exploiting users. Microsoft 365 also provides ways for your service to verify that calls to your action endpoints are valid.

## Sender requirements

In addition to the registration requirement discussed in the previous unit, email messages that contain Actionable Messages must meet **one** of the following requirements.

- The email message must originate from a server that implements both DomainKeys Identified Mail (DKIM) and Sender Policy Framework (SPF). These are industry standard ways to prove a sender's identity when sending emails over SMTP. Many companies already implement these standards to secure the emails they are already sending.
- The Actionable Message JSON must be signed using the JSON Web Signature (JWS) standard, using a private key that corresponds to a public key included in your Actionable Message registration.

## Protecting your service

All HTTP POST requests sent to your service by Microsoft 365 include a bearer token in the `Authorization` header. This token is a JSON Web Token (JWT) signed by Microsoft, and it includes important claims that should be verified by the service handling the associated request. By validating this token, you can know that the request is a valid one and that it originated from Microsoft. The token also contains the Azure Active Directory identity of the recipient who initiated the action.

Your service can also require authentication on your action endpoint. You can respond to a POST to your endpoint with an HTTP 401 status and an `ACTION-AUTHENTICATE` header, specifying a login URL. The Outlook client will use that URL to allow the user to login to your system, and your service can associate the user's Azure AD identity with your system.
