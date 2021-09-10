Call analytics can help organizations troubleshoot call and connection problems with Microsoft Teams. Call Analytics shows detailed information about the devices, networks, and connectivity for the calls and meetings of each user in an organization's Microsoft 365 tenant. If Call Analytics includes building, site, and tenant information, this information will also be shown for each call and session. Information available through Call Analytics can help an organization's Teams administrator determine why a user had a poor call or meeting experience. 

## Permissions to access call analytics

Teams administrators and Teams communication administrators have full access to all the features of Call Analytics and the Teams admin center. An organization can assign the following Azure Active Directory roles to support staff and Helpdesk agents so they can also access per-user call analytics (without having access to the rest of the Teams admin center):

- **Teams communication support specialist role**: This role has a limited view of Call Analytics. Communication support specialists handle basic call-quality problems. They don't investigate issues with meetings; instead, they collect related information and then escalate to a communication support engineer. The communication support specialist role is equivalent to Tier 1 support.

- **Teams communication support engineer role**: This role has access to the full functionality of Call Analytics. Communication support engineers see information in detailed call logs that is hidden from communication support specialists. Users in this role can help troubleshoot problems with both calls and meetings. The communication support engineer role is equivalent to Tier 2 support.

The following table identifies the per-user information that's available for each communications support role.

|Activity|Information|What the communications<br>support *specialist* sees|What the communications<br>support *engineer* sees|
|||||
|**Calls**|Caller name|Only the name of the user the agent searched for.|User name.|
||Recipient name|Shows as Internal User or External User.|Recipient name.|
||Caller phone number|Entire phone number except last three digits are obfuscated with asterisk symbols. For example, 15552823\*\*\*.|The entire phone number except the last three digits are obfuscated with asterisk symbols. For example, 15552823\*\*\*.|
||Recipient phone number|Entire phone number except last three digits are obfuscated with asterisk symbols. For example, 15552823\*\*\*.|The entire phone number except the last three digits are obfuscated with asterisk symbols. For example, 15552823\*\*\*.|
||**Call Details** \> **Advanced** tab|Information not shown.|All details are shown, such as device names, IP address, subnet mapping, and more.|
||**Call Details** \> **Advanced** \> **Debug** tab|Information not shown.|All details shown, such as DNS suffix and SSID.|
|**Meetings**|Participant names|Only the name of the user the agent searched for. Other participants identified as an Internal User or External User.|All names shown.|
||Participant count|Number of participants.|Number of participants.|
||Session details|Session details shown with exceptions. Only the name of the user the agent searched for is shown. Other participants are identified as an Internal User or External User. The last three digits of the telephone number are obfuscated with asterisk symbols.|User names and session details are shown. The last three digits of the telephone number are obfuscated with asterisk symbols.|

## View the call analytics for a user

Complete the following steps to view the call analytics for a user:

1. Sign into Microsoft Teams admin center.
2. From the left-hand navigation pane, select **Users**, and then select a user.
3. On the **User** page, select **Meetings & calls**.

    Call analytics displays all calls and meetings for that user for the past 30 days.

    ‎‎:::image type="content" source="../media/user-call-history.png" alt-text="User Call history":::  
‎
By selecting a session, you can view other information about a given session, including detailed media and networking statistics.

In the session details for each call or meeting, minor issues appear in yellow. An issue highlighted in yellow indicates it's outside the normal range and may be contributing to the problem, but it's unlikely to be the main cause of the problem. An issue highlighted in red indicates it's a significant problem, and it's likely the main cause of the poor call quality for this session.

### Call analytics for calls

Complete the following steps to view the call analytics for a call:

1. On the user's **Meetings & calls** page, select a session with a *Call* activity type.

2. In the **Overall call analytics** page, you can select different phrases for more detailed information.

    ‎:::image type="content" source="../media/call-analytics-overview-tab.png" alt-text="Overview tab":::

3. Select the **Advanced** or **Debug** tabs, and then look for yellow and red items that indicate poor call quality or connection problems.  

    * **Advanced tab**
    ‎:::image type="content" source="../media/call-analytics-advanced-tab.png" alt-text="Advanced tab":::

    * **Debug tab**
    :::image type="content" source="../media/call-analytics-debug-tab.png" alt-text="Debug tab":::

### Call analytics for meetings

Complete the following steps to view the call analytics for a meeting:

1. On the user's **Meetings & calls** page, select a session with a *conference* activity type to review the call analytics for meetings.

2. Select the **Timeline** or **Participant details** tabs for more information about the meeting.

    ‎‎:::image type="content" source="../media/call-analytics-meetings.png" alt-text="Screenshot of the Meetings and Calls page that displays the Timeline tab":::

Rarely is quality of experience data not received for audio sessions. When this situation does occur, it's usually the result of the call dropping and connection with the client ending. When this situation occurs, the session rating is **unavailable**.

For audio sessions that do have quality of experience (QoE) data, the following table describes major issues that qualify a session as **poor**.

| Issue                              | Area    | Description                                                                                                                                                            |
||||
| Call setup                         | Session | The error code Ms-diag 20-29 indicates the call setup failed. The user couldn't join the call or meeting.                                                             |
| Audio network classified poor call | Session | Network quality issues (such as packet loss, jitter, NMOS degradation, RTT, or concealed ratio) occurred.                                                      |
| Device not functioning             | Device  | A device isn't functioning correctly. Device not functioning ratios are: <br/> - DeviceRenderNotFunctioningEventRatio \>= 0.005 <br/> - DeviceCaptureNotFunctioningEventRatio \>= 0.005     |

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”