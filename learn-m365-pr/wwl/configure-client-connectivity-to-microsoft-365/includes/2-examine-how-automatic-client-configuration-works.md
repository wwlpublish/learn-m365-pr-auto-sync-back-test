Microsoft Outlook includes an Autodiscover feature that automatically configures Outlook to connect to Exchange Online without the need to manually configure user connection settings. Depending upon their configuration, Outlook users receive their required connection settings from either Exchange Online or Exchange Server on-premises the first time they sign in with their email address and password.

The process for an Outlook client to connect to Exchange Online for the first time is described below:

1.  An Outlook user enters their email address and password.
2.  Based on the email address information and Autodiscover record on the Internet-located DNS, the client locates the Autodiscover service in Microsoft 365.
3.  The client provides its SMTP address and password to authenticate with the Autodiscover service in Microsoft 365 and asks for appropriate connection settings.
4.  Microsoft 365 then provides the connection settings in an XML configuration information format that Outlook downloads and applies to its connection settings.
5.  Outlook connects to Exchange Online in Microsoft 365.
