Federation allows users to communicate with people outside of your tenant, using either Teams or Skype for Business.

## Configure federation policies and domain lists

To configure federation policies, go to the **Microsoft Teams admin center**. From the left-hand navigation, select **Org-wide settings** and select **External access**.

By default, these two options are set to **On**:

- Users can communicate with other Skype for Business and Teams users
- Users can communicate with Skype users

In addition, you can specifically:

1. Add a domain to allow communication with users from that domain.
2. Block a domain, to prevent communication with users from that domain.

Select **Add a domain**, enter the **domain name**, and select whether it should be **allowed** or **blocked**.

:::image type="content" source="../media/external-access-1.png" alt-text="Enabling external access":::

## Configure federation policies and domain lists 

In the following interactive exercise you will step through configuring federation policies and domain lists.

[Troubleshoot federation issues interactive walkthrough](https://edxinteractivepage.blob.core.windows.net/edxpages/M365%20Troubleshoot/Troubleshoot%20federation%20issues/index.html )

## Guests and external access

Guests and external access are both ways of communicating with people outside of your organization or tenant. By default, Teams allows you to communicate with external people. If you are having problems:

- Check that everyone has a paid subscription that includes Teams. Microsoft free licenses do not support external access.
- Check that external access has not been switched off for this client. In Microsoft Teams admin center, verify that:

    - The type of federation is correct.
    - Allowed and blocked domain lists are correct.

Guest access allows a person from outside your organization to work in the same way as users within your organization.

The differences between guest users and external users:

- Guests cannot search for people in other organizations.
- Guests are added to your organization’s Azure Active Directory as a B2B user and must sign-in to Teams using their guest account. They may have to sign out of their own organization to sign-in to your organization.
- External access users cannot share files, see out-of-office messages, or block someone in another organization.

## Troubleshoot chat for federated users in Teams

### Chat is in plain text, with no access to additional formatting options

Users are chatting with an external (federated) user in Microsoft Teams, which limits chat to plain text. Switch users to **Teams Only** upgrade mode to provide additional formatting options, known as “native-Teams chat.” Teams will then prompt the user to use native Teams chat and lock the original chat.

### Formatting options have disappeared part-way through chat

If a user was having a native Teams chat with an external (federated) user, and formatting options disappear, check that someone hasn’t switched out of Teams Only upgrade mode. If one user gets switched out of the **Teams Only** upgrade mode, Teams locks the native Teams chat and gives you a link for a limited, text-only chat. You can still read the native Teams chat, but you can't continue the conversation there.

### Chat is limited to 1:1 only

Users are chatting with external (federated) users in **Teams Only** upgrade mode and cannot add another person to the chat. When chatting to people in other organizations, native Teams chats are limited to 1:1.