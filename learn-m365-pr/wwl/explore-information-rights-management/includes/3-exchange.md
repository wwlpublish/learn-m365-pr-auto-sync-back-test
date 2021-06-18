Every day, people use email to exchange sensitive information, such as confidential information or reports. Because email is accessible from about anywhere, mailboxes have transformed into repositories that contain large amounts of potentially sensitive information. As a result, information leakage can be a serious threat to organizations. To help prevent information leakage, Exchange Server includes Information Rights Management (IRM) features, which provide persistent online and offline protection for email messages and attachments.

### What is information leakage?

Information leakage is the disclosure of sensitive information to unauthorized users. Information leakage can be costly for an organization, and can have a wide-ranging impact on the organization's business, employees, customers, and partners. To avoid violating any applicable regulations, organizations must protect themselves against accidental or intentional information leakage.

Information leakage can result in serious consequences for an organization, including:

 -  **Financial damage.** The organization may incur a loss of business, fines, or adverse media coverage.<br>
 -  **Damage to image and credibility.** Leaked email messages can potentially be a source of embarrassment for the sender and the organization.<br>
 -  **Loss of competitive advantage.** This result of information leakage is one of the most serious. The disclosure of strategic business or merger and acquisition plans can lead to losses in revenue or market capitalization for the organization. Other threats to competitive advantage include the loss of research information, analytical data, and other intellectual property.<br>

Although traditional solutions to information leakage may protect the initial access to data, they often don't provide constant protection. Traditional solutions often lack enforcement tools that apply uniform messaging policies to prevent information leakage. For example, let's assume a user marks a message with **Company Confidential** and **Do Not Forward**. After the message is delivered to the recipient, the sender or the organization no longer has control over the message. The recipient can willfully or accidentally forward the message (using features such as automatic forwarding rules) to external email accounts. This action can subject the organization to substantial information leakage risks.

### IRM in Exchange prevents information leakage

Information Rights Management in Exchange helps prevent information leakage by offering these features:

 -  Prevent an authorized recipient of IRM-protected content from forwarding, modifying, printing, faxing, saving, or cutting and pasting the content.<br>
 -  Protect supported attachment file formats with the same level of protection as the message.<br>
 -  Support expiration of IRM-protected messages and attachments so they can no longer be viewed after the specified period.<br>
 -  Prevent IRM-protected content from being copied using the Snipping Tool in Windows.<br>

However, IRM in Exchange can't prevent the disclosure of information by using these methods:

 -  Third-party screen capture programs.<br>
 -  Photographing IRM-protected content that's displayed on the screen.<br>
 -  Users remembering or manually transcribing the information.<br>

### IRM and Active Directory Rights Management Services

IRM uses Active Directory Rights Management Services (AD RMS). AD RMS is an information protection technology in Windows Server that uses extensible rights markup language (XrML)-based certificates and licenses to certify computers and users, and to protect content. AD RMS can be used to augment the security strategy for your organization by protecting documents using information rights management (IRM).

AD RMS allows individuals and administrators to create IRM policies that specify access permissions to documents, workbooks, and presentations. This process helps prevent sensitive information from being printed, forwarded, or copied by unauthorized people. After permission for a file has been restricted by using IRM, the access and usage restrictions are enforced no matter where the information is. These restrictions are enabled because the permission to a file is stored in the document file itself.

AD RMS and IRM help individuals enforce their personal preferences concerning the transmission of personal or private information. They also help organizations enforce corporate policy governing the control and dissemination of confidential or proprietary information.

IRM solutions that AD RMS enables are used to help provide the following protections:

 -  Persistent usage policies, which remain with the information, no matter where it's moved, sent, or forwarded.<br>
 -  An extra layer of privacy to protect sensitive information—such as financial reports, product specifications, customer data, and confidential e-mail messages—from intentionally or accidentally getting into the wrong hands.<br>
 -  Prevent an authorized recipient of restricted content from forwarding, copying, modifying, printing, faxing, or pasting the content for unauthorized use.<br>
 -  Prevent restricted content from being copied by using the Print Screen feature in Microsoft Windows.<br>
 -  Support file expiration so that content in documents can no longer be viewed after a specified period of time.<br>
 -  Enforce corporate policies that govern the use and dissemination of content within the company.<br>

IRM-based solutions that AD RMS supports can't prevent all types of threats to the security of sensitive documents or prevent disclosure of screen readable information under all circumstances. Some types of document security threats that AD RMS doesn't address or mitigate include:

 -  Content from being erased, stolen, or captured and transmitted by malicious programs such as Trojan horses, keystroke loggers, and certain types of spyware.<br>
 -  Content from being lost or corrupted because of the actions of computer viruses.<br>
 -  Restricted content from being hand-copied or retyped from a display on a recipient's screen.<br>
 -  A recipient from taking a digital photograph of the restricted content displayed on a screen.
 -  Restricted content from being copied by using third-party screen-capture programs.

### Configure and test IRM<br>

You use the Exchange Management Shell to configure IRM features in Exchange. For procedures, see [Managing Rights Protection](/Exchange/information-rights-management-procedures-exchange-2013-help).

After you install and configure a Mailbox server, you can use the **Test-IRMConfiguration** cmdlet to conduct end-to-end tests of your IRM deployment. The cmdlet performs these tests:

 -  Inspects IRM configuration for your Exchange organization.<br>
 -  Checks the AD RMS server for version and hotfix information.<br>
 -  Verifies whether an Exchange server can be activated for AD RMS by retrieving a Rights Account Certificate (RAC) and client licensor certificate.<br>
 -  Acquires AD RMS rights policy templates from the AD RMS server.<br>
 -  Verifies that the specified sender can send IRM-protected messages.<br>
 -  Retrieves a Super User use license for the specified recipient.<br>
 -  Acquires a prelicense for the specified recipient.<br>

**Additional reading.** For more information, see [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).
