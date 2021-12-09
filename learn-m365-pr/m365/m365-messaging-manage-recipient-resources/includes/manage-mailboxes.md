Not all mailboxes are the same. Most mailboxes are used by your employees for their mail. But there are others that we'll discuss in this unit, such as the archive mailbox type and the resource mailbox type.

To complete any of the actions or procedures mentioned in this unit, you'll need to ensure the account you're using has the **Recipient Management** permission.  

## Understand the archive mailbox type

Microsoft Exchange Online Archiving is a Microsoft 365 cloud-based, enterprise archiving solution. It's a solution for organizations that have deployed Microsoft Exchange Server 2019, Microsoft Exchange Server 2016, Microsoft Exchange Server 2013, Microsoft Exchange Server 2010 (SP2 and later), or subscribe to certain Exchange Online or Microsoft 365 plans. Exchange Online Archiving assists with archiving, compliance, regulatory, and eDiscovery challenges while simplifying on-premises infrastructure. Exchange Online Archiving helps reduce your costs and eases IT burdens.

As a Microsoft online service, Exchange Online Archiving is designed to help meet the need for robust security, reliability, and user productivity.

You can use Exchange Online Archiving for Exchange Server with user mailboxes on Exchange Server 2019, Exchange Server 2016, Exchange Server 2013, or Exchange Server 2010 (SP2 or later).

### Select an Exchange Online Archiving plan

Exchange Online Archiving is available through the following plans:

- Exchange Online Archiving for Exchange Server
- Exchange Online Archiving for Exchange Server (via Enterprise CAL Suite)
- Exchange Online Archiving for Exchange Online

### Understand user subscriptions

Each user who uses the Exchange Online Archiving service must have an Exchange Online Archiving subscription. Each email archive subscription can be used to store only one user's messaging data.

### Unlimited archive storage quota

The unlimited archiving feature (called *auto-expanding archiving*) provides additional storage space in archive mailboxes. Each Exchange Online Archiving subscriber initially receives 100 GB of storage in the archive mailbox. When auto-expanding archiving is turned on, additional storage space is automatically added when the 100-GB storage capacity is reached.

## Understand different resource mailbox types

Let's look at two of the resource mailbox types that are available.

A **room mailbox** is a resource mailbox that's assigned to a physical location, such as a conference room, an auditorium, or a training room. After you create room mailboxes, users can reserve rooms by including the specific room mailbox in a meeting request.

An **equipment mailbox** is a resource mailbox assigned to a resource that's not location-specific, such as a portable computer, projector, microphone, or a company car. After you create an equipment mailbox, users can reserve the associated piece of equipment by including its equipment mailbox in a meeting request.

### Create a room mailbox using the Exchange admin center

1. In the Exchange admin center, go to **Recipients > Resources**.
2. To create a room mailbox, select **New +**, and then select **Room mailbox**.
3. Specify the room name, email address, location, phone, and capacity for the new resource mailbox.
4. When you're finished, select **Save** to create the room mailbox.  

### Create a room mailbox using Exchange Online PowerShell

This example creates a room mailbox with the following configuration:

- The name of the mailbox is *ConfRoom1*; this name is used in the room's email address.
- The display name in the Exchange admin center and the address book will be *Conference Room 1*.
- The mailbox is a **room** mailbox (specified using the **Room** switch.)

```PowerShell
New-Mailbox -Name ConfRoom1 -DisplayName "Conference Room 1" -Room 
```

### Create a room list

If you have more than 100 rooms, you can use a room list to help organize your rooms. You can only create room lists using Exchange Online PowerShell.

This example creates a room list for building 32:

```PowerShell
New-DistributionGroup -Name "Building 32 Conference Rooms" -OrganizationalUnit "contoso.com/rooms" -RoomList 
```

### Create an equipment mailbox using the Exchange admin center

1. In the Exchange admin center, go to **Recipients > Resources**.
2. To create an equipment mailbox, select **New**, and then select **Equipment mailbox**.  
3. Specify the equipment name, display name, and an email address for the new resource mailbox.
4. When you're finished, select **Save** to create the equipment mailbox.  

After you've create your equipment mailbox, you can edit it to update information about booking options, MailTips, and delegates.

### Create an equipment mailbox using Exchange Online PowerShell  

This example creates an equipment mailbox with the following configuration:

- The equipment mailbox resides on **Mailbox Database 1**.
- The equipment's name is **MotorVehicle2**, and it will show up in the GAL as "Motor Vehicle 2."
- The email address is **MotorVehicle2@contoso.com**.
- The mailbox is in the **Equipment** organizational unit.
- The mailbox is an equipment mailbox (as specified with the **Equipment** switch.)

```PowerShell
New-Mailbox -Database "Mailbox Database 1" -Name MotorVehicle2 -OrganizationalUnit Equipment -DisplayName "Motor Vehicle 2" -Equipment 
```

## Learn more

- [Exchange Online Archiving service](/office365/servicedescriptions/exchange-online-archiving-service-description/exchange-online-archiving-service-description)
- [Exchange Online Archiving plans](/office365/servicedescriptions/exchange-online-archiving-service-description/exchange-online-archiving-service-description#exchange-online-archiving-plans)
- [Feature sets for Exchange Online Archiving plans](/office365/servicedescriptions/exchange-online-archiving-service-description/exchange-online-archiving-service-description#feature-availability-across-exchange-online-archiving-plans)
