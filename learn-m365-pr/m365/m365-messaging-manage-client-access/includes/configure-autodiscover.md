The Autodiscover service feature automatically configures Outlook to work with Exchange Online. Outlook users get their required profile settings directly from Exchange Online the first time they sign in with their email address and password. These settings automatically update the Outlook client with the information necessary to create and maintain the user's profile. An SSL certificate is required to use the Autodiscover service. This certificate is limited to a single primary SSL domain.

During installation, Exchange creates the virtual directory **autodiscover** in IIS, the frontend Client Access services web site that clients connect to. This lets Outlook discover the Exchange mailbox settings so that users don't have to manually configure any advanced settings.

An SCP object is also created in Active Directory during installation. The SCP stores and provides authoritative URLs of the Autodiscover service for domain-joined computers.

You need to update the SCP object to point to the Exchange server. This is necessary because Exchange servers provide additional Autodiscover information to clients to improve the discovery process. You can use the **Set-ClientAccessService** PowerShell cmdlet to update the SCP object.

## Learn more

[PowerShell Reference Library](/powershell/windows/get-started?azure-portal=true)
