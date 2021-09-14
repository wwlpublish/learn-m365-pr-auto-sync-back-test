
Upgrading from Skype for Business on-premises is a bit more complicated. The process includes configuring hybrid connectivity with your Microsoft 365 tenant so those users can communicate and interoperate with existing Teams users.

## Step 1: Configure hybrid connectivity

The key prerequisite for upgrading your on-premises users to Teams is to configure hybrid connectivity for your Skype for Business Server on-premises deployment.

## Step 2: Set transitional coexistence mode (optional)

Teams Upgrade modes define the coexistence and interoperability between Skype for Business and Teams clients and users. TeamsOnly mode is the final destination for each user.

The purpose of the coexistence modes is to provide a predictable experience for end users as organizations transition to Teams.

Depending on your requirements, you can assign the appropriate coexistence mode based on the upgrade path that your organization has chosen.

## Step 3: Move users between Skype for Business on-premises to TeamsOnly

When a user is moved from on premises to Teams Only, the user’s Skype for Business home is moved from on premises to online and the user is assigned TeamsUpgradePolicy with mode=TeamsOnly. After a user is moved from on-premises to TeamsOnly mode:

* All incoming calls and chats from other users (whether sent from Skype for Business or Teams), will land in the user’s Teams client.

* The user will be able to interoperate with other users who use Skype for Business.

* The user will be able to communicate with users in federated organizations.

* New meetings scheduled by that user are Teams meetings.

* User can still join any Skype for Business meetings.

* The user’s pre-existing meetings scheduled for the future will be migrated from on-premises to Teams.

* Contacts that existed on-premises are available in Teams shortly after the user logs on for the first time.

* Users cannot initiate calls or chats from Skype for Business, nor can they schedule new meetings in Skype for Business. If they attempt to open the Skype for Business client, they will be redirected to use Teams as shown below. If the Teams client is not installed, they will be directed to the web version of Teams using their browser.

    :::image type="content" source="../media/go-to-teams-page.png" alt-text="Screenshot of go to Teams page from SfB client":::

## Step 4: Disable hybrid to complete your migration to the cloud

After you have moved all users from on-premises to the cloud, you can decommission the on-premises Skype for Business deployment.

For more information, see:

* [Upgrade from Skype for Business on-premises to Teams](/microsoftteams/upgrade-to-teams-execute-skypeforbusinesshybridonprem?azure-portal=true)

* [Plan hybrid connectivity](/SkypeForBusiness/hybrid/plan-hybrid-connectivity?azure-portal=true)

* [Configure hybrid connectivity](/skypeforbusiness/hybrid/configure-hybrid-connectivity?azure-portal=true)

* [Move users between on-premises and the cloud](/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud?azure-portal=true)

* [Move users from on-premises to Teams](/skypeforbusiness/hybrid/move-users-from-on-premises-to-teams?azure-portal=true)

* [Disable hybrid to complete migration to the cloud](/skypeforbusiness/hybrid/cloud-consolidation-disabling-hybrid?azure-portal=true)
