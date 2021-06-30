Sharing is commonly used in online meetings. The organizer, or another authorized participant, might want to share the following elements:

- An entire screen
- A single application
- PowerPoint slides
- Whiteboard
- Shared notes

When users experience problems with initiating shared content in a meeting, review the meeting policies assigned to the organizer and participants. Also review the meeting settings.

## Review content sharing policy settings

To review the content sharing settings, open the **Microsoft Teams admin center**, and review the **Content sharing** section of the appropriate meeting policy, as shown in the following screenshot.

:::image type="content" source="../media/share-settings.png" alt-text="A screenshot that displays the Content sharing section in a meeting policy. All values displayed are defaults.":::

The following table describes content sharing policy settings.

| Setting                                                      | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Screen  sharing mode**                                     | Enables you  to define the screen sharing mode. Options are **Entire screen** or **Single  application**. Ensure that **Disabled** is not selected. This is a  per-organizer and per-user setting. |
| **Allow a  participant to give or request control**          | Determines  whether a user can give control of the shared desktop to other participants  in the meeting. This per-user setting determines whether the **Give Control**  button is accessible during a meeting. |
| **Allow an  external participant to give or request control** | Determines  whether external participants can be given control or request control of the  sharer's screen. This is a per-user setting. |
| **Allow  PowerPoint sharing**                                | Determines if  a user can share PowerPoint slide decks in a meeting. External users,  including anonymous, guest, and federated users, inherit the policy of the  meeting organizer. This is a per-user setting. |
| **Allow  whiteboard**                                        | Determines if  users can use and share the whiteboard during their meetings. |
| **Allow  shared notes**                                      | Determines if  a user can create and share notes in a meeting. External users, including  anonymous, B2B, and federated users, inherit the policy of the meeting  organizer. This is a per-user setting. |

When considering the effect of policies, remember that per-organizer and per-user policies can sometimes be confusing. Let’s review a couple of examples.

### Screen sharing example

Screen sharing mode is a per-organizer and per-user policy. Let’s imagine your global meeting policy allows for **Entire screen** sharing. However, Adele is assigned a policy with **Disabled** screen sharing. If Alex schedules a meeting, then anyone that joins the meeting can share their screens or apps. If Adele joins, she cannot share her screen or apps. If Adele schedules a meeting, then no one can share their screen or apps. 

### Give or request control example

The **Allow a participant to give or request control** setting is per-user only. Let’s imagine that your global meeting policy has this value **On**. However, Adele is assigned a policy where this value is **Off**. If Alex schedules a meeting, he can give control of the shared desktop to other participants. If Adele schedules a meeting, she cannot give control of the shared desktop to other participants. However, if Alex attends that meeting, he can give control. 

> [!TIP]
> You can use the `Set-CsTeamsMeetingPolicy` PowerShell cmdlet to configure these policy settings.

## Verify network settings

Specific network ports must be accessible for screen sharing in Teams. These can be reviewed or managed in the **Meeting settings** page in the **Microsoft Teams admin center**. For sharing, the default network ports are: 50040 to 50059. 

:::image type="content" source="../media/share-ports.png" alt-text="A screenshot that displays the Network section of Meeting settings. Default values are displayed.":::
