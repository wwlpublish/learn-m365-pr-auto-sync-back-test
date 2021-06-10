Some of the most common issues that businesses struggle with are conflicts of interest and insider trading with intercommunication and collaborations between certain groups within the organization. Microsoft 365 addresses these types of issues by implementing information barriers.

### What are information barriers?

Information barriers (IB) are policies that restrict communication between certain groups within an organization. Information barrier policies only apply to SharePoint Online, Microsoft Teams, and OneDrive services. Information barrier policies can be used in different kinds of scenarios, including:

 -  Prohibiting communication or file sharing between users on different teams.
 -  Prohibiting calling or online chat between users in certain groups within the organization<br>
 -  Restricting a user to only call or chat online with a specific team.
 -  Restricting file sharing or access to a certain site by anyone outside a specific team.

> [!NOTE]
> Information barriers only support two-way restrictions. With this type of restriction, users from team A can't initiate communication with team B, and users from team B can't initiate communication with team A. One-way restrictions (where users from team A can't initiate communications with team B, but users from team B can initiate communication with team A) aren't supported.

Whenever users who are covered by information barrier policies attempt to communicate and collaborate with others in Microsoft Teams, SharePoint Online, or OneDrive, checks are done to prevent (or allow) communication and collaboration (as defined by the information barrier policies).

The following illustration is a visual representation of how an information barrier policy works. An IB policy has been put in place to stop the Investment banker team from communicating or collaborating with the Financial advisor team. However, they can still both communicate with other teams, such as the HR group.

:::image type="content" source="../media/information-barriers-87323634.png" alt-text="visual representation of how an information barrier policy works":::


The primary driver for information barriers has traditionally come from the Financial Services industry. The Financial Industry Regulatory Authority (FINRA) reviews IBs and conflicts of interest within member firms. It then provides guidance about managing such conflicts (such as FINRA 2241, [Debt Research Regulatory Notice 15-31](https://www.finra.org/sites/default/files/Regulatory-Notice-15-31_0.pdf?azure-portal=true)).

### How do information barrier policies work?<br>

When information barrier policies are in place, people who shouldn't communicate or share files with other specific users can't find, select, chat, or call those users. With information barriers, checks are in place to prevent these types of unauthorized communication and collaboration. These checks are known as segments.

Information barriers apply to Microsoft Teams (chats and channels), SharePoint Online, and OneDrive. In Microsoft Teams, information barrier policies determine and prevent the following types of unauthorized communications:

 -  Searching for a user.
 -  Adding a member to a team.
 -  Starting a chat session with someone.
 -  Starting a group chat.
 -  Inviting someone to join a meeting.
 -  Sharing a screen.
 -  Placing a call.
 -  Sharing a file with another user.
 -  Access to file through sharing link.

If the people involved in an activity are specified in an information barrier policy that prevents the activity, they won't be allowed to continue. Potentially, everyone included in an information barrier policy can be blocked from communicating with others in Microsoft Teams. When people affected by information barrier policies are part of the same team or group chat, they may be removed from those chat sessions and further communication with the group may not be allowed.

In SharePoint Online and OneDrive, information barrier policies determine and prevent the following types of unauthorized collaborations:<br>

 -  Adding a member to a site.
 -  Accessing site or content by a user.
 -  Sharing site or content with another user.
 -  Searching a site.

### Using segments in information barriers<br>

Segments are attributes that an administrator uses to define the IB policy for a group. These attributes are taken from the list of attributes that a group is part of. For example, a segment called HR is defined using a value in the Department attribute. Defining segments doesn't affect users. It just sets the stage for defining and applying information barrier policies.

**Additional reading.** For more information, see [Attributes for information barrier policies](/microsoft-365/compliance/information-barriers-attributes).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”