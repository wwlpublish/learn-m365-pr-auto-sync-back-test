When a user selects a link in an email and the target web site is later identified as malicious, the Safe Links process automatically warns the user. Here's a summary of how Safe Links works in email:

1.  Someone sends a user an email message that contains a URL to a web site.
2.  The message flows through the anti-malware pipeline. Assuming the message passes through all the initial checks, it eventually arrives in the recipient’s inbox.
3.  The user opens the message and selects the link.
4.  When the user selects the link, the URL is redirected to a secure server that checks the URL against a blocklist of known malicious web sites.
    
     -  If the link is safe, the user’s browser navigates to the target web site.
     -  If the link is malicious, the user’s browser displays a warning page.

Now consider the scenario when a user receives a message from an external sender that contains two URLs, one to the malicious `www.spamlink.contoso.com` site and another to the legitimate **www.bing.com** site.

1.  The user selects the `www.spamlink.contoso.com` link. The user doesn't know that this URL is a phishing link that was previously identified by the service as malicious.
2.  The organization’s Safe Links policy detects the link and redirects it to the secure server in Microsoft 365. The secure server determines the URL is malicious.
3.  Because the link is malicious, the user is redirected to a protective shell. The shell alerts the user about the classification of the URL (see the following graphic).
    
    :::image type="content" source="../media/malicious-website-warning-cc2435da.png" alt-text="Screenshot of warning message saying the website is malicious.":::
    
4.  The policy is selective enough to remove only the malicious link. When the user selects the link to **www.bing.com**, the user is successfully able to navigate to Bing.com as expected.

> [!NOTE]
> The sample web page above includes the option to **Continue to this web site**. This text indicates the administrator who created the policy selected this option to let users select through to the original URL. Had the administrator not selected this option, this text wouldn't have appeared on the page.

### URL detonation end-user experience

URL detonation combines elements of Safe Links and Safe Attachments into a single feature. This feature is designed to protect users in the event a URL points to a malicious file on a web site.

When you select the link, the file is downloaded into the Safe Attachments sandbox environment and detonated just like an attachment. During this process, the recipient is redirected to a warning page like the one in the following screenshot, which lets the user know the file is being scanned.

:::image type="content" source="../media/link-being-scanned-warning-message-d6484fab.png" alt-text="Screenshot of warning message saying the link is being scanned.":::


If the file is ultimately determined to be malicious, the user is redirected to the warning page like the one in the previous screenshot. The warning page advises the user the site is malicious.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”