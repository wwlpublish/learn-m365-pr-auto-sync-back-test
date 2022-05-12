The threat investigation and response capabilities in Microsoft Defender for Office 365 enable an organization's security team to discover and respond to cybersecurity threats. These threat investigation and response capabilities include Threat Trackers. Threat Trackers are informative widgets and views that provide organizations with intelligence on different cybersecurity issues. For example, you can view information about trending malware campaigns using Threat Trackers.

Most threat tracker pages include:

 -  Trending numbers that are updated periodically.
 -  Widgets that identify which issues are the biggest or have grown the most.
 -  A quick link in the **Actions** column that takes you to Threat Explorer, where you can view more detailed information.

To view and use Threat Trackers, go to the **Microsoft 365 Defender portal**, and then under the **Email and collaboration** section in the navigation pane, select **Threat tracker**.

> [!NOTE]
> To use Threat Trackers, you must be a global administrator, security administrator, or security reader.

Available Threat Trackers include:

 -  Noteworthy trackers
 -  Trending trackers
 -  Tracked queries
 -  Saved queries.

Each of these features is examined in the following sections.

### Noteworthy trackers

Noteworthy trackers are where you'll find large and small threats and risks that Microsoft thinks you should know about. Noteworthy trackers help you find whether these issues exist in your Microsoft 365 environment. These trackers also provide links to articles that give you more details on what's happening, and how they'll affect your organization's use of Microsoft 365.

Whether it's a new threat (for example, Wannacry and Petya) or an existing threat that might create some new challenges (such as Nemucod), Noteworthy trackers is where an organization's security team will find important new items that it should review and examine periodically.

Noteworthy trackers will typically be posted for just a couple of weeks when Microsoft identifies new threats that it feels organizations should be aware of. Once the biggest risk for a threat has passed, Microsoft will remove that Noteworthy item. This way, Microsoft can keep the list fresh and up to date with other relevant new items.

### Trending trackers

Trending trackers (formerly called Campaigns) highlight new threats that haven't been seen in an organization's email in the past week. Trending trackers provide visibility into new threats that organizations should review. In doing so, organizations can ensure their broader corporate environment is prepared against attacks.

:::image type="content" source="../media/trend-trackers-7b564652.png" alt-text="Screenshot showing the Trending Trackers view.":::


Trending trackers give organizations an idea of new threats they should review to ensure their broader corporate environment is prepared against attacks.

### Tracked queries

Tracked queries use an organization's saved queries to periodically assess its Microsoft 365 activity. This feature provides an organization with event trending. Tracked queries run automatically, giving an organization up-to-date information without having to remember to rerun its queries.

:::image type="content" source="../media/tracked-queries-3a0d3666.png" alt-text="Screenshot showing the tracked queries view.":::


### Saved queries

Saved queries are also found in the Trackers section. An organization can use Saved queries to store the common Explorer searches that it wants to get back to quicker and repeatedly, without having to re-create the search every time.

:::image type="content" source="../media/saved-queries-4973a8cb.png" alt-text="Screenshot showing the saved queries view.":::


A Noteworthy tracker query or any of your own Explorer queries can be saved using the **Save query** button at the top of the Explorer page. Anything saved there will show up in the **Saved queries** list on the Tracker page.

### Trackers and Explorer

Whether you're reviewing email, content, or Office activities, Threat Explorer and Threat Trackers work together to help you investigate and track security risks and threats. All together, Threat Trackers provide organizations with information to protect their users by highlighting new, notable, and frequently searched issues. This design helps organizations ensure they're better protected as they move to the cloud.

### Trackers and Microsoft Defender for Office 365

Organizations that have an Office 365 Enterprise E5 tenant should be using Microsoft Defender for Office 365 - it's included in their subscriptions. Microsoft Defender for Office 365 provides value even if you have other security tools filtering email flow with your Office 365 services. However, anti-spam, Safe Attachments, and Safe Links features work best when your main email security solution is through Office 365.

:::image type="content" source="../media/threat-policies-page-53c1a2a0.png" alt-text="Screenshot of the threat policies page.":::


In today's threat-riddled world, running only traditional anti-malware scans means you aren't protected enough against attacks. Today's more sophisticated attackers use common tools to create new, obfuscated, or delayed attacks that won't be recognized by traditional signature-based anti-malware engines. The Safe Attachments feature takes email attachments and detonates them in a virtual environment to determine whether they're safe or malicious. This detonation process opens each file in a virtual computer environment. It then watches what happens after the file is opened. Whether it's a PDF, a compressed file, or an Office document, malicious code can be hidden in a file. The code is only activated when the victim opens the document on their computer. The threat tracking capability in Microsoft Defender for Office 365 detonates and analyzes the file in the email flow. By doing so, it can find these threats based on behaviors, file reputation, and numerous heuristic rules.

The Noteworthy threat filter highlights items that were recently detected through Safe Attachments. These detections represent items that are new malicious files. They weren't previously found by an organization's Microsoft 365 tenant in either its email flow or other customers' email. Organizations should pay particular attention to the items in the Noteworthy Threat Tracker. They should see who was targeted by them and review the detonation details shown on the **Advanced Analysis** tab (found by selecting on the subject of the email in Threat Explorer).

> [!NOTE]
> You'll only find the **Advanced Analysis** tab on emails detected by the Safe Attachments capability. This Noteworthy tracker includes that filter, but you can also use it for other searches in Threat Explorer.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”