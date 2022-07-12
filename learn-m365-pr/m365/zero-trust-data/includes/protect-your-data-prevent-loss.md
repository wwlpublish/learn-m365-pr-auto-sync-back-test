The aim of a Zero Trust strategy is to enable your organization to protect data in transit, at rest, and in use—particularly for sensitive information. This is done by appropriately identifying your data but also ensuring that you can control and verify any access to it _and_ have effective data loss prevention in place.

## Sensitivity labels

Sensitivity labels facilitate the "verify explicitly" Zero Trust principle for your organization because they provide additional data points that can be used to make security decisions about access to resources. Your organization can automatically apply labels to flag items, such as files and emails, that contain sensitive information. These labels also indicate the sensitivity of a particular item. Here are some examples of common labels:

- **Public** - Business data that is designed for public consumption. For example, a public marketing campaign for a new product.
- **Confidential** - Data that could harm the business if accessed by unauthorized individuals. For example, contracts, and sales accounts.
- **Highly confidential** - Confidential data that should only be accessible to a select group of people. For example, information about an ongoing merger.

Your organization can also apply turnkey labels using cloud security tools or create its own labels.
Turnkey labels are out-of-the-box labels for organizations based on common security requirements. These allow you to easily use labels without having to create your own. When labels are applied to items, they enable your organization to identify the sensitivity of data at a glance. This is because they help your cloud security tools to create detailed charts and derive insights based on sensitivity labels.

Sensitivity labels can also be used to provide protection and data loss prevention because they can be a basis for:

- Encryption
- Content marking
- Data loss prevention policies

We'll learn about these next.

## Encryption and content marking

Your sensitive data should also be protected using encryption and content marking. Encryption is a process by which data is converted into an unrecognizable format that can't be accessed unless decrypted by an authorized user or entity. When an item like an email or a file is encrypted, it:

- Is encrypted both in transit and at rest.
- Stays encrypted even if it's taken outside of the organization.

Your organization can configure encryption and content marking based on sensitivity labels. For instance, confidential and highly confidential items could automatically be encrypted and content marked using a "Confidential – for internal use only" watermark in either the footer or the heading of a document, or email. This way, assets like documents and emails are protected automatically, based on their sensitivity. This means that your organization can ensure that unauthorized users won't be able to open these files or emails, and only authorized users can view them. Content marking also helps to reinforce best practices for users because they can easily see that the document is only meant for confidential use.

This way, your organization enforces Zero Trust principles such as "assume breach"—because items are automatically encrypted—and "verify explicitly", because the items can only be decrypted to be viewed by authorized users.

## Data loss prevention policies (DLP)

In addition to data protection, your organization should also prevent data loss. This can occur through risky behavior or accidental oversharing of sensitive information. Your organization needs to be able to govern and prevent inappropriate transfer and sharing of sensitive data. To achieve this, you can create data loss prevention policies. These are policies that describe what actions should be taken to prevent data from being shared or accessed in an unauthorized manner.

For example, your organization can create a policy that states that all confidential items, such as emails or files, shouldn't be viewed or modified by unauthorized users. The policy could consist of the following general configuration details:

- **Conditions** - You can specify a condition to state that this policy should apply to all items such as emails and documents that have the confidential sensitivity label.
- **Actions** - You can describe actions to take if the condition is matched. For example, blocking users from receiving confidential items like documents or emails, or sending confidential items, or only blocking people from outside of the organization from receiving or viewing confidential items.

Your organization's cloud security tool will then automatically enforce this policy. For instance, suppose a user accidentally attempts to insert a document labeled "confidential" into an email message going to a group that includes some external users. The policy would come into effect, and block the user from sending the email until they've either removed the document, or ensured that no more unauthorized users are in the list of recipients for the message. This way, your organization can enforce the Zero Trust principle "use least privilege access" because only authorized users can access items. You can enforce the "verify explicitly" principle because labels are used  to verify whether users can access items.

All of this means your organization can automatically control access to data and, in turn, prevent data loss caused by inappropriate or unauthorized behavior.  Additionally, because these policies are cloud-based, your organization will benefit from the ability to scale and fine-tune them to make encompassing changes and improvements for data loss prevention.
