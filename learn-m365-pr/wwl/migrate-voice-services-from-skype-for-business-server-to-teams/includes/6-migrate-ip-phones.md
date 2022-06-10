After migrating Skype for Business Server users enabled for Enterprise Voice, and common area phones, you may need to migrate Skype for Business IP phones to Microsoft Teams.

Before migrating Skype for Business Server IP phones, ensure you have validated compatibility with Microsoft Teams.

Some Skype for Business IP phones are upgradable to native Microsoft Teams functionality. These phones are known as Teams-capable Phones.

Skype for Business IP phones with standard SIP firmware, Cisco IP phones with multi-platform SIP firmware, or SIP devices from vendors such as Poly, Yealink, and AudioCodes will continue to work with Microsoft Teams with a specific set of functionalities, as these phones access Teams via a SIP Gateway.

If you have Teams-capable phones, consult your vendor for recommendations on upgrading the existing Skype for Business compatible firmware to Teams native firmware. You should plan and align the upgrade to the Teams user interface on the phone to coincide with the migration of the user or common area phone to Teams.

For IP phones certified for Skype for Business, the Skype for Business phones support a limited number of core functionalities listed below.<br>

| **Authentication**| **Calling**| **Calendar and Presence**| **Meetings**| **Device Update and Management**|
| :--- | :--- | :--- | :--- | :--- | :--- |
| Sign in with user credentials/Web Sign in| Incoming/Outgoing P2P calls from/to Teams users|  Calendar Access and Meeting Details| One-click Join for Pre-Scheduled Teams Meeting| Device Update|
| Modern Authentication| In-call controls via UI<br>(Mute/unmute, hold/resume, blind transfer, end call)| Presence Integration| Meeting Call controls<br>(Mute/unmute, hold/resume, hang up,<br>Add/remove participant)| In-band provisioning|
| Phone lock/unlock| PSTN calls| Exchange Calendar Integration| Meeting Reminders| QoE & Log Upload|
| Hot-desking Support| Visual Voicemail| Contact Picture Integration| Add Skype for Business participant to ongoing meeting| Common Area Phone Support|
|| **911 support**| **Corporate Directory Access**|||
||| Visual Voicemail|||

Both Skype for Business IP phones and Teams Capable Phones should expect users or common area phones to sign in after the account is migrated to Microsoft Teams. For Teams Capable Phones, they may be able to support remote provisioning functionality described later in the module Configure, deploy, and manage Teams devices.

