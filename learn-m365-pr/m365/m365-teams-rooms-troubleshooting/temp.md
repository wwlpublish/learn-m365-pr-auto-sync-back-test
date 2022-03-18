# Adopt, maintain, and troubleshoot Microsoft Teams Rooms

# Unit 1: Introduction

In this module, you'll learn about available Microsoft Teams Rooms end-user adoption tools and how you can educate your users on the benefits of Teams Rooms. You'll learn how to operate and manage Teams Rooms in a production environment. Finally, you'll learn to troubleshoot common issues with Teams Rooms.

## Learning objectives

In this module, you'll learn:

- Ideas for end-user training and adoption materials.
- Operation and maintenance techniques for Teams Rooms.
- Common issues with Teams Rooms and how to troubleshoot them.

## Prerequisites

- Familiarity with Microsoft Teams deployment and resource accounts
- Familiarity with Microsoft Teams devices
- Familiarity with Windows 10 management tools

# Unit 2: Help your organization adopt Teams Rooms

No matter how good your Teams Rooms deployment is, it's only as good as the ability of your users to use the systems you've put in front of them.

To help, here are some links that might assist you with end-user training. You can share these links with your users through an e-mail campaign and post them on your internal support sites.

| Topic  |  Link |
|---|---|
| End-user help  |  aka.ms/TeamsRoomsHelp |
|  Introductory Teams Rooms video |  aka.ms/TeamsRoomsVideo |
| Interactive end-user training  | aka.ms/MicrosoftTeamsRoomsDemo |
Teams Rooms administrator video training | aka.ms/TeamsRoomsLearning |

In-room signage can be important. You can create documents like the one seen here, laminate them, and leave them in the rooms.

![Get your meeting started](../media/get-your-meeting-started.png)

As users walk into their first meetings, they'll quickly see how to join a meeting and that they can share content from their desktop. This is just a sample and you can use your imagination to make your own interesting Teams Rooms signage.

Another creative idea is to make a smaller sign and secure it directly onto the console. In this sample, the sign would be folded along the red dotted line and then attached to the console. This provides additional end-user support directly on the console.

![Here's how to join a Teams meeting](../media/teams-meetings-coming-soon.png)

# Unit 3: Operate and maintain Teams Rooms

What are the day-to-day operations that you should consider to keep Teams Rooms in great shape?

## Consider day-to-day operations

- Always make sure that Windows and the Teams Rooms app are set to auto update. This is handled automatically every morning starting at 2:01 via a scheduled task. 
- Firmware updates may require manual effort, but work with your OEM to see if they have tools to automate the download and update of firmware for their devices.
- Teams admin center can be used to view statistics on the reliability of your meetings and the availability of your devices. Teams admin center can show if a device is unreachable and then you can work to resolve the issue.
- You can use Microsoft Endpoint Manager or System Center Operations Manager to keep track of your devices.
- It's a good idea to inspect the rooms to validate that the equipment is still working as expected. When inspecting the rooms, make sure that cabling is still tightly connected and things haven't come loose. Are the cameras connected and functional? Make test calls in each room to make sure the audio and video is working as expected.
- You should confirm that Teams Rooms is signed in. You can do that simply by looking at the console and making sure it's ready to join a meeting.
- Be sure to wipe down the console touchscreen to keep it clean and clear from fingerprints.
- Also take this time to check if HDMI ingress cables are damaged. These cables can be used many times a day and can degrade over time.

# Unit 4: Troubleshoot Teams Rooms

Despite being a reliable, self-managed system, issues can pop up in Teams Rooms. Here's some common scenarios and how to troubleshoot them.

## What are common Teams Rooms app issues?

### Issue: The Teams Room app is not up to date

- Sign into Windows Settings as admin, and manually update the app via the Microsoft Store. If the app won't update, you can use the Microsoft Teams recovery tool.

### Issue: The resource account can't sign into Microsoft Teams

- Sign into Windows Settings as admin and attempt to sign into Microsoft Teams through the web browser. If you can't, then it's a sign that the account either has a wrong password or there's a typo in the username.
- If you're able to sign into Teams via the web browser and you signed into the Teams Rooms device using a domain account, it's possible proxy authentication is the issue. Teams Rooms devices sign in with a local Skype user account that is not a domain account. It's possible that a proxy server is looking for an Active Directory domain account in order to authenticate proxy server access. Make sure that Teams Rooms are approved for proxy authentication bypass.
- If you're in Teams-only mode, make sure you have the Skype for Business Online DNS records configured. Teams still leverages many Skype for Business Online features and if DNS settings are missing, those features could prevent proper operation.
- For a Skype for Business on-premises environment, make sure that you've imported the enterprise root certificate from your certificate authority.

### Issue: The local Skype account doesn't automatically sign in

- Make sure that a policy isn't applied that disables auto login.  Teams Rooms devices should be put in their own custom groups, whether Active Directory, Group Policy, or Intune. It's possible a Group Policy setting was applied to your Teams Rooms device that's preventing the Skype account from logging in automatically.
- Make sure that the password is still blank.
- Make sure that a password expiration policy hasn't been applied.

## What are common video display issues?

### Issue: Video image is blurry, colors aren't accurate, or it just doesn't look right

- Make sure you're using the correct cabling as required by the manufacturer.
- Make sure you're using high-quality HDMI cables.
- Verify that cables are tightly connected and that the cable hasn't come loose. Inspect the cable to make sure that it isn't broken or damaged in any way.
- You may need to update firmware on the compute module or update the video driver.
- Verify that the front of room displays don't have burn-in or they're simply old and don't show a strong image anymore.

### Issue: Displays don't turn on automatically

- All displays should support either HDMI Consumer Electronic Control (CEC) or PC Power On commands. Teams Rooms supports HDMI CEC, but many of the compute modules Don't, meaning the HDMI ports on compute modules are not pinned correctly to send the CEC signal. In this case, you may need to add a CEC injector.

## What are common network issues?

### Issues: Video is choppy or low resolution, the resource account keeps signing in and out, or audio has echoes, stutters, or drops

- Bypass the proxy server. Don't perform break or inspect analysis on Teams media. Verify that appropriate firewall ports are open for Microsoft Teams.
- Don't use wireless networking. It's unsupported with Teams Rooms. If you are using wireless networking, switch to a physical ethernet cable.
- Make sure that your network is configured for local internet and DNS access.
- When signed into Windows Settings as admin, go to connectivity.office.com from the web browser and validate that the results don't show any network issues with connecting to Microsoft 365.
- For Skype for Business on-premises, check if you have call quality diagnostics installed and enabled. If so, check the values there to see if you can get any additional information for what's happening.
- Check the cabling and switch port and other networking components, making sure that the network cable isn't loose or damaged.
- Validate that the network switch port hasn't been misconfigured.
- If necessary, enable Quality of Service (QoS) on your network for Teams media.

## What are some possible general Issues?

### Issue: Performance is poor

- This usually has to do with unnecessary Intune or Group Policy Objects (GPO) being applied to Teams Rooms. Be sure that the Teams Rooms computer account and resource account are in dedicated Organizational Units and block inheritance of other GPOs.
- Uninstall unnecessary or redundant antivirus and malware software, VPN clients, and additional security agents that are not required on Teams Rooms.
- Be sure Teams Rooms is restarting every night
- Update the BIOS and firmware on the compute module to make sure that there aren't any core hardware issues.

## Learn more

- [Microsoft Teams Rooms recovery tool](/MicrosoftTeams/rooms/recovery-tool?azure-portal=true)

# Unit 5: Check your knowledge

## Questions

    - **content:** "Why is end user adoption important?"
      **choices:**
      - **content:** "To make sure users know how to use Teams Rooms to help conduct effective meetings."
        **isCorrect:** true
        **explanation:** "Correct! Just because you installed Teams Rooms doesn’t mean your users will know how to use the console and access the features."
      - **content:** "It isn’t because Teams Rooms is self-explanatory."
        **isCorrect:** false
        **explanation:** "Incorrect. Teams Rooms is indeed very easy to use to join and control meetings. However, not every user will know how to use Teams Rooms effectively without having some training first."
      - **content:** "So that users will know about the meeting lifecycle."
        **isCorrect:** false
        **explanation:** "Incorrect. Microsoft Teams is an important tool to track the lifecycle of meetings. However, Teams Rooms is only a portion of the meeting lifecycle. If users Don't know how to use Teams Rooms, the investments made will not have a great return."

    - **content:** "Why should you routinely review the Teams Rooms equipment in your meeting rooms?"
      **choices:**
      - **content:** "To make sure they are showing up correctly in Teams Admin Center."
        **isCorrect:** false
        **explanation:** "Incorrect. You walk the rooms every week or so to make sure that they are still functioning correctly and to spot any issues before they arise."
      - **content:** "To make sure everything is working correctly and spot any issues before it affects meetings."
        **isCorrect:** true
        **explanation:** "Correct! You walk the rooms every week or so to make sure that they are still functioning correctly and to spot any issues before they arise."
      - **content:** "To prepare the room for the next meeting."
        **isCorrect:** false
        **explanation:** "Incorrect. You walk the rooms every week or so to make sure that they are still functioning correctly and to spot any issues before they arise."
      
    - **content:** "If video and audio performance are choppy, what steps would help fix this issue?"
      **choices:**
      - **content:** "Add an HDMI CEC adapter."
        **isCorrect:** false
        **explanation:** "Incorrect. An HDMI CEC adapter is used to wake up a display at the start of the meeting. They don't help with choppy audio or video performance."
      - **content:** "Use the Microsoft Teams Rooms recovery tool."
        **isCorrect:** false
        **explanation:** "Incorrect. The Teams Rooms recovery tool can help update the Teams Rooms app if it's having trouble updating."
      - **content:** "Bypass the proxy server and disable break/inspect on Teams media traffic."
        **isCorrect:** true
        **explanation:** "Correct! Proxies and break/inspect are known to cause problems with Microsoft Teams media."
      
# Unit 6: Summary

In this module, you learned about the available Microsoft Teams end-user adoption tools and how to educate your users on their benefits. You also learned how to operate and manage Teams Rooms in a production environment and how to troubleshoot common issues with Microsoft Teams Rooms.

Now that you have finished this module, you learned:
  
- Ideas for end-user training and adoption materials.
- Operation and maintenance techniques for Teams Rooms.
- Common issues with Teams Rooms and how to troubleshoot them.
