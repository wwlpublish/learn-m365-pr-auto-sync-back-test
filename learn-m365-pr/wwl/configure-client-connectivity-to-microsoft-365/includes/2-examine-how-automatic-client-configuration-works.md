Microsoft Outlook includes an Autodiscover feature that automatically configures Outlook to connect to Exchange Online. It does so without the need to manually configure user connection settings. Depending upon their configuration, Outlook users receive their required connection settings from either Exchange Online or Exchange Server on-premises the first time they sign in with their email address and password.

The process for an Outlook client to connect to Exchange Online for the first time is described below:

1.  An Outlook user enters their email address and password.
2.  Based on the email address information and Autodiscover record on the Internet-located DNS, the client locates the Autodiscover service in Microsoft 365.
3.  The client provides its SMTP address and password to authenticate with the Autodiscover service in Microsoft 365.
4.  The client then asks for the appropriate connection settings.
5.  Microsoft 365 provides the connection settings in an XML configuration information format.
6.  Outlook downloads the information and applies it to its connection settings.
7.  Outlook connects to Exchange Online in Microsoft 365.
