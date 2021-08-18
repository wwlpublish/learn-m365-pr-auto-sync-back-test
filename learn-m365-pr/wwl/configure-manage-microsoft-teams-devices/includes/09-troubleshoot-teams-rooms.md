Even though Teams Rooms is a reliable, self-managed system, issues can still appear. This unit examines some common situations that may occur and how to troubleshoot them.

## Sign in issues

### Issue: The Teams Room app isn't up to date

- Sign into Windows Settings as admin and manually update the app through the Microsoft Store. If the app won't update, you can use the Microsoft Teams recovery tool. 

### Issue: The resource account can’t sign into Microsoft Teams

- Use [Azure AD sign in logs](/azure/active-directory/reports-monitoring/concept-sign-ins) to verify the account signs in to the Teams Meeting Room. 
- Sign into Windows Settings as admin and attempt to sign into Microsoft Teams through the web browser. If you can’t sign in, then it's an indication the account either has an incorrect password or there's a typo in the username. 
- If you can sign into Teams through the web browser and you signed into the Teams Rooms device using a domain account, then proxy authentication may be the issue. Teams Rooms devices sign in with a local Skype user account that's not a domain account. It's possible that a proxy server is looking for an Active Directory domain account to authenticate proxy server access. Ensure that Teams Rooms are approved for proxy authentication bypass.
- If you're in Teams-only mode, verify you have the Skype for Business Online DNS records configured. Teams still uses many Skype for Business Online features. If DNS settings are missing, those features could prevent proper operation. 
- For a Skype for Business on-premises environment, verify that you've imported the enterprise root certificate from your certificate authority.


## Video display issues

### Issue: Video image is blurry, colors aren’t correct, or it just doesn’t look right

- Verify you’re using the correct cabling as required by the manufacturer.
- Verify you're using high-quality HDMI cables. 
- Verify that cables are tightly connected and the cable hasn't come loose. Inspect the cable to verify that it isn't broken or damaged in any way. 
- You may need to update firmware on the compute module or update the video driver. 
- Verify the monitors at the front of the room don't have burn-in. Also verify whether they no longer display a strong image, often because of age.

### Issue: Displays don’t turn on automatically

- All displays should support either HDMI Consumer Electronic Control (CEC) or PC Power On commands. Teams Rooms supports HDMI CEC, but many of the compute modules don't. As a result, the HDMI ports on compute modules aren't pinned correctly to send the CEC signal. In this case, you may need to add a CEC injector.

## Network issues

### Issues: Video is choppy or low resolution, the resource account keeps signing in and out, or audio has echoes, stutters, or drops

- Bypass the proxy server. Don’t conduct break or inspect analysis on Teams media. Verify that appropriate firewall ports are open for Microsoft Teams.
- Don't use wireless networking because it's unsupported with Teams Rooms. If you're using wireless networking, switch to a physical ethernet cable.
- Verify that your network is configured for local internet and DNS access.
- When signed into Windows Settings as an admin, go to **connectivity.office.com** from the web browser. Validate the results don't show any network issues when connecting to Microsoft 365.
- For Skype for Business on-premises, verify whether you have call quality diagnostics installed and enabled. If so, check the values to see if you can get any other information for what's happening.
- Check the cabling and switch port and other networking components. Verify the network cable isn't loose or damaged.
- Examine the network switch port to verify that it hasn't been misconfigured. 
- If necessary, enable Quality of Service (QoS) on your network for Teams media.

## General issues

### Issue: Performance is poor

- Poor performance is usually the result of unnecessary Intune or Group Policy Objects (GPO) being applied to Teams Rooms. Verify the Teams Rooms computer account and resource account are in dedicated Organizational Units and block inheritance of other GPOs.
- Uninstall unnecessary or redundant antivirus and malware software, VPN clients, and other security agents that aren't required on Teams Rooms.
- Be sure Teams Rooms is restarting every night.
- Update the BIOS and firmware on the compute module to verify there aren't any core hardware issues.

For more information, see [Microsoft Teams Rooms recovery tool](/MicrosoftTeams/rooms/recovery-tool).