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
