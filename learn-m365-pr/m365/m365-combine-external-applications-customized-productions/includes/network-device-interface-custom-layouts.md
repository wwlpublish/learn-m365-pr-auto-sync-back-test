Microsoft Teams can broadcast video and audio output as Network Device Interface (NDI) streams on your network. Producers can mix these streams with output from other cameras and devices to create engaging live content.

You've been reading about video cameras that support NDI and seen demonstrations of their output integrated into rich video presentations. Now, you want to find out whether you can integrate Teams meetings video with this hardware.

## What is NDI?

In a traditional television production environment, directors have several different cameras on different presenters or interviewees, and they can mix the video feeds from these different cameras. For example, they can cut, fade, or wipe from one camera to another or mix a head shot as an insert into a different shot. These cameras must be directly wired to the vision mixer.

:::image type="content" source="../media/network-device-interface-example.png" alt-text="You can use NDI to assemble video streams from multiple sources.":::

NDI makes it easier to connect cameras and other devices for mixing. Instead of connecting them physically, you can connect them though a computer network, such as an Ethernet or Wi-Fi.

:::image type="content" source="../media/network-device-interface-producer.png" alt-text="The meeting producer arranges video streams from multiple sources into a more interesting visual presentation.":::

Teams supports NDI and generates several NDI video streams that you can mix on the same computer or another device over the network to create more engaging content. For example, you can mix two presenters' videos onto a custom layout to simulate a fireside chat.

## Enable NDI in Teams

Before you can use NDI in Teams, an administrator must enable it in the Microsoft 365 tenant. After that, you'll be able to enable it in Teams options.

To enable NDI in the tenant, use this PowerShell command to modify the Teams meeting policy:

```powershell
Set-CsTeamsMeetingPolicy -Identity MEETING_POLICY -AllowNDIStreaming $true
```

Each user must then turn on NDI technology for their client:

1. In Teams, navigate to **Settings > App permissions**.
1. Next to **Network Device Interface (NDI)**, move the slider to the right.

    :::image type="content" source="../media/enable-network-device-interface-teams.png" alt-text="Enabling NDI in Teams options.":::

1. Close the **Settings** dialog.

In-tenant users are included in the streams that Teams generates and have full access to those streams. Other types of user, including federated users, anonymous users, and guests, are included in the streams, but have no access to them.

## NDI streams in Teams

Once you have enabled NDI, you can start NDI broadcasts within any meeting or live event. When you're broadcasting streams, producers can mix your streams into their videos.

Once you've joined a meeting, to start broadcasting, go to the **More actions ...** menu, and then select **Broadcast over NDI**.

:::image type="content" source="../media/broadcast-over-network-device-interface.png" alt-text="Starting broadcasting a meeting over NDI.":::

Now, Teams will broadcast several different streams:

- **Primary speaker.** This stream switches to whoever is actively speaking.
- **Local.** This stream is the audio and video that is sent to the meeting from your local computer, usually the audio from your mic and the image from your webcam.
- **Individual users.** Each user on the meeting will also broadcast an NDI stream.
- **Screen sharing.** This stream is the video that any user has shared with the meeting. This stream is often a user's desktop, an application, or a PowerPoint presentation.
- **Large gallery and Together mode.** Both these display modes broadcast an NDI stream.
