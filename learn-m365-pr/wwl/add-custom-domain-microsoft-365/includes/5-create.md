When an organization has a domain name that it wants to add to Microsoft 365, the administrator or Microsoft partner should complete the following steps:

1.  Verify the organization owns the domain. Domain ownership can sometimes be problematic, particularly if a former employee registered the domain with their personal information and has now left the organization. To find out who originally registered the domain, check the WHOIS record for that domain by using an Internet WHOIS register, such as who.is.
2.  Verify the organization has administrative access to manage DNS for the domain. Different DNS hosting providers grant varying levels of access to DNS records for a hosted domain.
3.  Verify the organization can make changes to the DNS records for the domain.
4.  Sign in to the Microsoft 365 admin center and go to the **Domains** tab on the **Settings** menu.
5.  Confirm domain ownership for the domain by completing the following steps:<br>a. Enter the domain name for which you want to confirm domain ownership.<br>b. Add text (TXT) or mail exchanger (MX) records to the DNS zone for the domain according to the information in the Microsoft 365 setup wizard.<br>c. Verify the domain ownership in the Microsoft 365 setup wizard.
6.  Change the default domain to the new domain, so that any new accounts use this domain value rather than the one originally assigned when Microsoft 365 was originally set up (such as the default **.onmicrosoft.com** domain).
7.  Add users and assign licenses (this step is part of the Microsoft 365 setup rather than a DNS‑specific operation).
8.  Set the domain purpose and finish configuring DNS.

You can cancel out of the domain setup process but still verify that you own the domain. The Microsoft 365 admin console will display a message indicating that the setup is in progress. After you verify a domain, you can delete the verification TXT record.

> [!NOTE]
> Each domain (with any attendant subdomains) can only be validated to a single Microsoft 365 tenant account.

The following diagram shows how public domains, managed in their respective provider portals, must point to Microsoft 365 to receive emails and use them in Microsoft 365.

:::image type="content" source="../media/public-domains-pointing-to-m365-e3b21950.jpg" alt-text="diagram depicts how public domains, managed in their respective provider portals, simply must point to Microsoft 365 to receive emails and use them in Microsoft 365":::


### Setting up a custom domain

Complete the following steps to set up a custom domain using the Microsoft 365 admin center and DNS Manager:

1.  In the **Microsoft 365 admin center,** in the left-hand navigation pane, select **Setup** and then select **Domains**.<br>
2.  On the **Domains** page, select **Add domain**.
3.  Enter the name of the domain you want to add and then select **Next**.<br>
4.  Choose how you want to verify that you own the domain.<br>
    
     -  If your domain is registered at GoDaddy or 1&amp;1, choose **Sign in** and Microsoft 365 [will set up your records automatically](https://support.office.com/article/will-set-up-your-records-automatically-ec6f4bd8-5996-4505-ba68-afaf8a141fb9?azure-portal=true).
     -  You can have an email sent to the registered contact for the domain with a verification code. If you don't recognize or have access to the email on record, you can use the next option to use a TXT record to verify your domain.
     -  You can use a TXT record to verify your domain. Select this option and then select **Next** to see instructions on how to add this DNS record to your registrar's website. This process can take up to 30 minutes to verify once you've added the record.<br>
5.  Choose how you want to make the DNS change required for Microsoft 365 to use your domain.<br>
6.  If you chose to add DNS records yourself, select **Next** and you'll see a page with all the records you need to add to your registrar’s website to set up your domain.
    
     -  If the portal doesn't recognize your registrar, you can [follow these general instructions](https://support.office.com/article/follow-these-general-instructions-7b7b075d-79f9-4e37-8a9e-fb60c1d95166?azure-portal=true).
     -  Check the drop-down menu for your DNS hosting provider and follow the instructions to update all the necessary DNS records.
     -  If you don’t know the DNS hosting provider or domain registrar for your domain, [find your domain registrar or DNS hosting provider](https://support.office.com/article/find-your-domain-registrar-or-dns-hosting-provider-b5b633ba-1e56-4a98-8ff5-2acaac63a5c8?azure-portal=true).
