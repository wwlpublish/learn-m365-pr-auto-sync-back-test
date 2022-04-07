A second use for connectors in Exchange Online is to control and secure communications with partner organizations.

## Secure email exchange

Internet email is exchanged by using SMTP through port 25. Most of the time, emails are sent in plain text and the source of an email is not checked. This open approach reduces barriers to communication but can be exploited by malicious users. For example, it's easy to intercept and read emails sent in plain text. You can also claim a different identity from your own by setting a fake From address on an email and there are many other attacks. Many phishing attacks begin with such a spoofed identity. To help prevent such problems from your most sensitive internet emails, you can use connectors to require encryption or identity checking.

Transport Layer Security (TLS) is a protocol that is widely used on the internet and elsewhere to encrypt communications between servers. The protocol works like this:

1. The source email server connects to the destination server and negotiates the best level of encryption that both servers support. This negotiation is called opportunistic TLS. If one server doesn't support TLS at all, emails are sent in plain text, unless you require encryption on the connector.
2. The destination server sends its digital certificate, which includes its public encryption key, to the source server. The source server checks the digital certificate to make sure it comes from a trusted certificate authority and correctly identifies the destination server.
3. The source server creates a symmetric encryption key and uses the destination server's public key to encrypt it. The encrypted symmetric key is sent to the destination server, which decrypts it using its private key. 
4. Now that both servers have the symmetric key, they use it to encrypt all communications in the session, including the emails that are exchanged.

Notice the following points about this protocol:

- Emails are only encrypted as they are sent across the network. TLS does not ensure that emails are protected after they have been received at the destination. Think of TLS as an encrypted tunnel, through which emails are sent. When they reach the end of the tunnel, TLS no longer protects them. If you want a message to always remain encrypted, you can use a technology such as Office Message Encryption.
- A certificate, that is trusted by both parties, is required on the destination server. This certificate includes a DNS domain name, and you can require that this domain matches the DNS domain name of the destination server.

Another restriction you can apply to the connector is to require that all email is sent from or to a specific IP address or range of addresses. This technique is another way to prevent email address spoofing and other attacks.

## Create a connector to secure email transfer from your partner organization to Microsoft 365

In this example, let's create a connector that will secure emails from your partner wholesaler to your Exchange Online organization:

1. In the Exchange admin center, select **mail flow**, and then select **connectors**.
2. Click the plus symbol (**+**) to create a new connector.
3. Set **From** to **Partner organization**, and set **To** to **Office 365**. Click **Next**.
    :::image type="content" source="../media/4-partner-org-m365.png" alt-text="A screenshot of the From and To fields in the new connector wizard." border="false":::

4. On the **How do you want to identify the partner organization?** page, select **Use the sender's domain**.
    :::image type="content" source="../media/4-identify-partner-org.png" alt-text="A screenshot of the How do you want to identify the partner organization page in the new connector wizard." border="false":::
5. Click the **+** to add a new domain. Enter the domain name for your partner, and then click **ok**.
    :::image type="content" source="../media/4-add-partner-domain.png" alt-text="The add domains page of the new connector wizard, with the plus sign highlighted." border="false":::

6. To require encryption, select **Reject email messages if they aren't sent over TLS**.
    :::image type="content" source="../media/4-apply-security-restrictions.png" alt-text="The security restrictions page of the new connector wizard, highlighting the Reject e Mail messages option." border="false":::
7. If, instead, you select **And require that the subject name on the certificate that the partner uses to authenticate with Office 365 matches this domain name**, Exchange will check that the connection is from the same DNS domain and that listed in the certificate. This check helps to prevent spoofing.

Now that you have the connector, it's a good idea to contact an administrator at your partner company and ask them to send an email to a valid mailbox in your Exchange Online system. If the email arrives, you can be confident that your new connector works.

## Learn more

- [Configure mail flow using connectors](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow?azure-portal=true)
- [Set up connectors to route mail between Office 365 and your own email servers](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail?azure-portal=true)
- [Set up connectors for secure mail flow with a partner organization](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner?azure-portal=true)
