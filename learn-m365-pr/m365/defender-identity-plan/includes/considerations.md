You've learned about the architecture of Microsoft Defender for Identity. But to get decision makers on board, you'll need to identify key information that must be considered to implement Microsoft Defender for Identity for your organization.

## Identify the requirements

To inform decision makers in your organization about how you'll implement Microsoft Defender for Identity successfully, you'll need to look into its requirements. These requirements cover a range of categories, including requirements for using the portal to access Microsoft Defender for Identity, requirements for sensors, and more. Details of prerequisites are out of scope for this module. But you can use the link in the **Learn more** section for the latest information on them.

## Use capacity planning

It's also important to consider capacity planning. Capacity planning is when you determine the number of Microsoft Defender for Identity sensors you'll need for your organization. To plan for the number of sensors you need, you can use the Microsoft Defender for Identity Sizing Tool, or if using this tool is not possible, perform a domain controller traffic estimation. Use the _Plan capacity for Microsoft Defender for Identity_ link in the **Learn more** section for details on how to use the sizing tool or perform a domain controller traffic estimation.

## Understand the setup process

You also need to understand the setup process for Microsoft Defender for Identity, so that you can explain the procedure to decision makers in your organization. The setup process for Microsoft Defender for Identity consists of the following high-level tasks:

1. Create and connect your Microsoft Defender for Identity instance to Active Directory.
      - Here, you create an instance for Microsoft Defender for Identity in the Microsoft 365 Defender portal, and configure an Active Directory username to connect with your Active Directory.
1. Download and install Microsoft Defender for Identity sensors.
      - After you've created your instance, you can set up your sensors. You do this configuration task by downloading a setup package from the portal. This package consists of files that you will use to install a sensor on machines like your domain controller or Active Directory Federation Services server.
  
Once you've completed the setup process, Microsoft Defender for Identity will begin to collect information and monitor for suspicious activity across your organization's identities.

## Learn more

- [Microsoft Defender for Identity prerequisites](/defender-for-identity/prerequisites)
- [Plan capacity for Microsoft Defender for Identity](/defender-for-identity/capacity-planning)
