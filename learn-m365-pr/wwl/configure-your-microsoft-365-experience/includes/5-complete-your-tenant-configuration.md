It's highly recommended that an organization's enterprise administrators compile a list of tasks that must be done to complete their tenant configuration. They should use this checklist to guide their final configuration efforts and ensure that all necessary tasks have been performed.

While the checklist will be unique to each organization per its deployment requirements, the following list of goals should typically be included:

 -  Have all the users been moved over to Microsoft 365?
 -  Do the users have a functional mailbox and has their data been migrated to their account?
 -  Have all the resources been created?
 -  Have all permissions been established?
 -  Has the vanity domain(s) been moved successfully?
 -  Have all Windows 10 devices been enrolled to Intune?
 -  If the company had SCCM, has co-management been established with Intune?
 -  Has your company established proper governance policies for mobile devices?
 -  Have the DNS records been updated and published globally?
 -  If Azure Active Directory Connect is in place, is the connector properly configured?
 -  If multi-factor authentication is employed, has it been properly configured?
 -  Are the mailing policies in place to protect inbound and outbound mail flow?
 -  Is the Organizational profile set up with the correct information?

These questions help organizations determine if the basic setup has been completed and configured correctly. When an organization feels that its environment is ready to go-live, it can use tools such as the Remote Connectivity Analyzer and the Support and Recovery Assistant (SARA) to confirm its readiness. These tools check DNS records and mail flow to test whether mailing policies are working properly. They also test local connectivity from Outlook and other Office apps.
