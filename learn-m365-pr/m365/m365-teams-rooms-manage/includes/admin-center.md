Here are some of the tasks you can do in the Teams admin center:

- See an inventory of all your rooms, their status, and performance statistics.
- Remotely restart Teams Rooms.
- Collect logs.

You can see below that all the rooms are listed in the left-hand column. You can also quickly see that there's one unhealthy room and there's one that's offline.  You can also see a healthy meetings metric. 99% of the meetings have not had any quality issues.

From this overview page, you can also select several Team Rooms and change their settings. This is an easier approach than having to manually create a SkypeSettings.xml file and copying it to each one.

 :::image type="content" source="../media/teams-admin-center-overview.png" alt-text="Teams admin center overview page." lightbox="../media/teams-admin-center-overview.png" border="false":::

You can click directly on a device to get more information.

After you click on a Teams Room, you'll see call metrics and the status of connected peripherals scoped to that room. You can download device logs via Teams admin center.

:::image type="content" source="../media/call-metrics-peripheral-status.png" alt-text="Call metrics and peripherals status for a room." border="false":::

You can also see actions that have been taken via Teams admin center against your Teams Rooms. In this example, Teams Rooms was remotely restarted and logs were downloaded.

:::image type="content" source="../media/teams-admin-actions-history.png" alt-text="See Teams admin center actions history." border="false":::

You can see every call and every meeting that has happened in that room. You can also see the quality of the call and troubleshoot it from here. To troubleshoot the call in the image below, you would click on the value in the Start time (UTC) column of the row marked **Poor**.

:::image type="content" source="../media/troubleshoot-call-quality-1.png" alt-text="Click on the value in the Start time column of the row marked Poor." lightbox="../media/troubleshoot-call-quality-1-lightbox.png" border="false":::

After you click on the date and time, you get summary information on the call and a list of participants. You can see which participant had poor audio quality. Clicking on the Session start time column for that call lets you see diagnostic info for that participant.

:::image type="content" source="../media/troubleshoot-call-quality-2.png" alt-text="You can see summary information on the call and a list of participants." lightbox="../media/troubleshoot-call-quality-2-lightbox.png" border="false":::

You can see that the poor call was caused by the network.  Below the message are a few options to see more data on this call, such as Device and System. In this case, you should click on **Network** as that is what the error message is referencing.

:::image type="content" source="../media/troubleshoot-call-quality-3.png" alt-text="Click on Network as the poor call quality cause." lightbox="../media/troubleshoot-call-quality-3-lightbox.png" border="false":::

After clicking on **Network,** you can see that the average round-trip time was 784 milliseconds and the maximum round-trip time was almost two seconds.

:::image type="content" source="../media/troubleshoot-call-quality-4.png" alt-text="View the round-trip time." lightbox="../media/troubleshoot-call-quality-4-lightbox.png" border="false":::

Almost 55 percent of all the packets were lost. This is well below Microsoft's recommended metrics for media. How can you determine what the cause was for this poor network performance?

Click on the **System** icon to learn more about what hardware the participant was using. In the image below, you can see that it was an Android phone. You can now presume that the participant was either traveling and driving through tunnels or a parking garage, took the call and went into an elevator, or was just in a poor coverage area. It seems likely that the issue was not with Teams Rooms or with your network, but with the participant and their device.

:::image type="content" source="../media/troubleshoot-call-quality-5.png" alt-text="See what hardware the participant was using from the System icon." lightbox="../media/troubleshoot-call-quality-5-lightbox.png" border="false":::

## Learn more

- [Network performance requirements from a Skype for Business client to Microsoft network Edge](/skypeforbusiness/optimizing-your-network/media-quality-and-network-connectivity-performance#network-performance-requirements-from-a-skype-for-business-client-to-microsoft-network-edge)
