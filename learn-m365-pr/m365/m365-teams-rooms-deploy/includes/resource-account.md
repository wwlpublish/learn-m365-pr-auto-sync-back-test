The resource account is a Microsoft Exchange resource mailbox.

When people schedule a room, it is this resource mailbox that they invite to their meeting. This mailbox will - on behalf of the room - accept or decline the meeting invite. This resource account is also the account that signs into the Microsoft Teams Rooms app. It must be enabled for Skype for Business and/or Microsoft Teams.

Try to establish a naming convention, particularly when you move to Azure Active Directory (Azure AD) and the concept of dynamic groups. A resource account can automatically be added to Azure AD groups based on the naming convention. It's recommended that you assign the Teams Rooms Standard or Teams Rooms Premium license to all Teams Rooms resource accounts. The Teams Rooms Standard license is a cost-effective license that includes all the core components needed for Teams Rooms.

The Teams Rooms Premium license adds additional features such as a Microsoft-managed service that will help with everything from planning your rooms to monitoring and troubleshooting them. This license also includes everything in the Standard license. You can find more information about licensing on the [Teams Meeting Room Licensing Update](/MicrosoftTeams/rooms/rooms-licensing?azure-portal=true) page.

![Standard versus Premium licenses](../media/standard-premium-license.png)

> [!IMPORTANT]
> Every Teams Rooms compute module requires its own unique resource account. You cannot share a resource account across multiple rooms. If you do, only one of those accounts will be able to join a meeting and other rooms with the same account will not be able to join any meetings at the same time.

- If you use Skype for Business on-premises, you'll need to assign an Enterprise Client Access license, and if you intend to use Enterprise Voice features of Skype for Business, you'll need to add a Plus Client Access license.
- It's recommended that you create the account well in advance of hardware installation. This is because you may need to open tickets within your IT organization to have them created. You also need to test and review to make sure the accounts were set up correctly.
- If your environment is configured to use modern authentication, Microsoft recommends that you enable it for the resource account. You can use Intune conditional access policies to help control and limit what the resource account has access to. For example, you can limit the account to only sign in on a given subnet.  

> [!IMPORTANT]
> All credentials are secured on the device through a physical TPM chip and are stored in the Windows Vault. Physical TPM chips are required on all compute modules used by Teams Rooms.
>

## What is the workflow for creating a resource account?

1. First identify what room you are going to use with Teams Rooms. Does a resource already exist? It's possible that a resource account for this room was created previously for other purposes.

   - If that is the case, you can then move forward with configuring auto accept.
   - If there is not an existing resource, create a new Exchange resource and then configure auto accept within Exchange.

2. Once the auto-accept parameters for the Exchange mailbox have been configured, you will need to set the password to never expire. *Resource accounts must have their password set to not expire*. Otherwise, the account will not be able to sign in to Teams Rooms when its password has expired and no one will be able to join meetings in that room until someone physically changes the password on the Teams Rooms application.

3. Will you enable this account for Skype for Business?

   - If yes, enable the account for Skype.
   - If not, assign a Teams license.

4. If you have enabled the account for Skype, will you enable it for Teams and for Skype? If yes, assign a Teams license.

    ![Resource account workflow](../media/resource-account-flow.png)

## Learn more

- [Configure accounts for Microsoft Teams Rooms](/MicrosoftTeams/rooms/rooms-configure-accounts?azure-portal=true)
- [Teams Room licensing update](/MicrosoftTeams/rooms/rooms-licensing?azure-portal=true)
