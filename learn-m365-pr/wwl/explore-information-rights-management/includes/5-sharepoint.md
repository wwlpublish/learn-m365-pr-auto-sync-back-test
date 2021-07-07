Within SharePoint Online, Information Rights Management (IRM) protection is applied to files at the list and library level. Before your organization can use IRM protection, you must first set up Rights Management. IRM relies on the Azure Rights Management service from Azure Information Protection to encrypt and assign usage restrictions. Some Microsoft 365 plans include Azure Rights Management, but not all.

In SharePoint, IRM enables administrators and content creators to limit the actions that users can take on files that are stored in document libraries. Once IRM has been enabled, site collection administrators can configure individual document libraries to use IRM to protect documents. IRM encrypts the files and limits the set of users and programs that can decrypt these files. IRM can also limit the rights of the users who can read files. This design prohibits users from completing actions such as printing copies of the files or copying text from them.

You can use IRM on lists and libraries to limit the dissemination of sensitive content. For example, let's assume you're creating a document library to share information about upcoming products with selected marketing representatives. You can use IRM to prevent these individuals from sharing this content with other employees in the company.

IRM in SharePoint helps to protect restricted content in the following ways:

 -  Prevents an authorized viewer from copying, modifying, printing, faxing, or copying and pasting the content for unauthorized use.
 -  Prevents an authorized viewer from copying the content by using the Print Screen feature in Microsoft Windows.
 -  Prevents an unauthorized viewer from viewing the content if it's sent in email after it's downloaded from the server.
 -  Restricts access to content to a specified period of time, after which users must confirm their credentials and download the content again.
 -  Enforces corporate policies that govern the use and dissemination of content within your organization.
 -  Blocks the upload of files with content that cannot be protected by IRM.

IRM can't protect restricted content from the following actions:

 -  Erasure, theft, capture, or transmission by malicious programs such as Trojan horses, keystroke loggers, and certain types of spyware.
 -  Loss or corruption because of the actions of computer viruses.
 -  Manual copying or retyping of content that is displayed on a screen.
 -  Digital or film photography of content that is displayed on a screen.
 -  Using third-party screen-capture programs to copy content.
 -  Using third-party screen-capture programs or copy-and-paste action to copy content metadata (column values).

**Additional reading.** For more information, see [How Office applications and services support Azure Rights Management](/azure/information-protection/understand-explore/office-apps-services-support).

### Turn on IRM service using SharePoint admin center

Before an organization can IRM-protect SharePoint lists and libraries, it may need to activate the Azure Rights Management service. To learn whether your organization must activate Azure Rights Management and how to do so, see [Activating Azure Rights Management](/information-protection/deploy-use/activate-service).

After activating the Azure Rights Management service, sign in to the SharePoint admin center to turn on IRM.

1.  Sign in to the SharePoint admin center as a global administrator or SharePoint administrator.<br>
2.  Select the app launcher icon in the upper left of the screen and choose **Admin** to open the Microsoft 365 admin center. (If you don't see the Admin tile, you don't have administrator permissions in your organization.)<br>
3.  In the left pane, choose **Admin centers &gt; SharePoint.**<br>
4.  In the left pane, choose **settings**, and then choose **classic settings page**.<br>
5.  In the **Information Rights Management (IRM)** section, choose **Use the IRM service specified in your configuration**, and then choose **Refresh IRM Settings**.

After you refresh IRM settings, people in your organization can begin using IRM in their SharePoint lists and document libraries. However, the options to do so may take up to an hour to appear in Library Settings and List Settings.<br>

### IRM-enable SharePoint document libraries and lists

After refreshing IRM settings, site owners can IRM-protect their SharePoint lists and document libraries. For more information, see [Apply Information Rights Management to a list or library](/microsoft-365/compliance/apply-irm-to-a-list-or-library).

You can't create or edit documents in an IRM-enabled library using Office in a browser. Instead, one person at a time can download and edit IRM-encrypted files. Use check-in and check-out to manage coauthoring, which is the authoring of a document by multiple users.<br>

When you download a PDF file from an IRM-protected library, Microsoft 365 creates a protected PDF file. The file's extension won't change, but the file is protected. To view this file, you'll need the Azure Information Protection viewer, the full Azure Information Protection client, or another application that supports viewing protected PDF files.

SharePoint Online supports encryption of the following file types:

 -  PDF<br>
 -  The 97-2003 file formats for the following Microsoft Office programs: Word, Excel, and PowerPoint<br>
 -  The Office Open XML formats for the following Microsoft Office programs: Word, Excel, and PowerPoint<br>
 -  The XML Paper Specification (XPS) format<br>

> [!NOTE]
> IRM protection can't be applied to protected documents (like digitally signed PDF files) because SharePoint must open the document on upload.<br>
