Microsoft Teams scoped directory search allows organizations to create virtual boundaries that control how users can find and communicate with other users in their organization. 

Microsoft Teams lets organizations provide custom views of the directory to their users. Microsoft Teams uses Information Barrier policies to support these custom views. Enabling scope directory search is a prerequisite to use information barriers.

Once the policies are enabled, the results returned by searches for other users will be scoped according to the configured policies. Users will not be able to search or discover any teams when scoped search is in effect. But existing members in those teams can add users, as allowed by active Information Barrier policies.

## When should you use scoped directory searches?

You may use the scoped directory search, when:

* Your organization has multiple companies within its tenant that you want to keep separate.

* Your school wants to limit chats between faculty and students.

Address book policies provide only a virtual separation of users from directory perspective. Any user data that had already been cached, prior to the enforcement of new, or updated address book policies, will remain available to users for up to 30 days.

## Turn on scoped directory search

1. Sign in to the Teams Admin center.

2. Navigate to **Org-wide settings** > **Teams settings**.

3. Scroll down to **Search by name** and turn the slider behind **Scope directory search using an Exchange address book policy** to **On**.

    :::image type="content" source="../media/scoped-directory-search.png" alt-text="Scoped Directory Search":::

This change can take a few hours to replicate.
