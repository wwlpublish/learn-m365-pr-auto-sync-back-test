Sensitive data presents significant risk to a company if it's stolen, inadvertently shared, or exposed through a breach. Risk factors include reputational damage, financial effect, and loss of competitive advantage. Protecting the data and information a business manages is a top priority for all organizations. However, some may find it difficult to know if their efforts are truly effective, given the amount of content it maintains.

In addition to volume, an organization's content may range in importance from highly sensitive and impactful to trivial and transient. It can also be under the purview of various regulatory compliance requirements. Knowing what to prioritize and where to apply controls can be a challenge.

Organizations address these concerns by implementing data classification. Data classification is a specialized term used in the fields of cybersecurity and information governance. It describes the process of identifying, categorizing, and protecting content according to its sensitivity or impact level. In its most basic form, data classification is a means of protecting an organization's data from unauthorized disclosure, alteration, or destruction based on how sensitive or impactful it is.

Data is classified in an organization in many ways, including:

 -  Sensitivity labels
 -  Retention labels
 -  Sensitive information types
 -  Trainable classifiers

### What is a data classification framework?

Organizations often codify a data classification framework (sometimes called a 'data classification policy') in a formal, enterprise-wide policy. Data classification frameworks are typically comprised of three to five classification levels. These levels usually include three elements: a name, description, and real-world examples.

Microsoft recommends no more than five top-level parent labels, each with a maximum of five sublabels (25 total) to keep the user interface (UI) manageable. Levels are typically arranged from least to most sensitive, such as:

 -  Public
 -  Internal
 -  Confidential
 -  Highly Confidential

Other level name variations you may encounter include:

 -  Restricted
 -  Unrestricted
 -  Consumer Protected

Microsoft recommends label names that are self-descriptive and that highlight their relative sensitivity clearly. For example, **Confidential** and **Restricted** may leave users guessing which label is appropriate. By comparison, **Confidential** and **Highly Confidential** are clearer on which is more sensitive.

The following table shows an example of a **Highly Confidential** data classification framework level:

| **Classification level** | **Description**                                                                                                                                                                                                                                                                                     | **Examples**                                                                                                       |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Highly Confidential      | Highly Confidential data is the most sensitive type of data stored or managed by the enterprise and may require legal notifications if breached or otherwise disclosed.<br><br>Restricted Data requires the highest level of control and security, and access should be limited to "need-to- know." | - Personal user information<br>\- Cardholder Data<br>\- Protected Health Information (PHI)<br>\- Bank Account Data |

> [!TIP]
> Microsoft's corporate data classification framework originally used a category and label named 'Internal'. However, during the pilot phase, it found there were legitimate reasons for a document to be shared externally. As such, it shifted to using the label 'General' instead of 'Internal'.

Another important component of a data classification framework is the controls associated with each level. Data classification levels by themselves are simply labels (or tags) that indicate the value or sensitivity of the content. To protect that content, data classification frameworks define the controls that should be in place for each data classification level. These controls may include requirements related to:

 -  Storage type and location
 -  Encryption
 -  Access control
 -  Data destruction
 -  Data loss prevention
 -  Public disclosure
 -  Logging and tracking access
 -  Other control objectives, as needed

An organization's security controls will vary by data classification level. For example, protective measures defined in an organization's framework may increase commensurate with the sensitivity of its content. In other case, an organization's data storage control requirements will vary depending upon the media that's being used, and the classification level applied to a given piece of content.

The following table shows an example of data classification controls for a specific storage type.

| **Storage type**  | **Confidential** | **Internal**                | **Unrestricted**    |
| ----------------- | ---------------- | --------------------------- | ------------------- |
| Removable Storage | Prohibited       | Prohibited unless encrypted | No control required |

Correctly applying the right level of data classification can be complex in real-life situations. As such, it may sometimes overwhelm end users. Once a policy or standard has been created that defines the required levels of data classification, it's important to guide end users on how to bring this framework to life in their daily work. This area is where data classification handling rules or guidelines come in.

Data classification handling guidelines will help end users with specific guidance on how to handle each level of data appropriately, for different storage media throughout their lifecycle. These guidelines also help end users correctly apply rules in practice. For example, when sharing documents, sending emails, or collaborating across different platforms and organizations.

Microsoft customers indicate that approximately 50% of an Information Protection project is business focused rather than technical. As such, end-user training and communication are critical to success.

### Create a well-designed data classification framework

As organizations develop, revamp, or refine their data classification frameworks, they should consider the following leading practices:

 -  **Don't expect to go from 0-100 on day 1**. Microsoft recommends a crawl-walk-run approach. Features critical to the organization should be prioritized and mapped against a timeline. Complete the first step, ensure it was successful, and then move on to the next phase, applying lessons learned. Remember that your organization may still be exposed to risk while you design your data classification framework. As such, it's okay to start small with just a few classification levels and expand later as needed.
 -  **You aren't just writing for cybersecurity professionals**. Data classification frameworks are meant for a broad audience. It may include your average staff member, your legal and compliance teams, and your IT team. It's important to write clear, easy-to-understand definitions for your data classification levels. Provide real-world examples wherever possible. Try to avoid jargon, and consider a glossary for acronyms and highly technical terms.
 -  **Data classification frameworks are meant to be implemented**. For data classification frameworks to be successful, they must be implemented. It's especially relevant when crafting the control requirements for each data classification level. Make sure requirements are clearly defined. They should also anticipate and address any ambiguity that may arise during implementation. For example, if you have a control around personal customer information, make sure to spell out exactly what that control means, such as Social Security or passport number.
 -  **Only go granular if you need to**. Data classification frameworks typically contain anywhere from 3-5 data classification levels. But just because you ***can*** include five levels doesn't mean you ***should***. Consider the following criteria when deciding on the number of classification levels you need:
     -  Your industry and your associated regulatory obligations (highly regulated industries tend to need more classification levels).
     -  The operational overhead required to maintain a more complex framework.
     -  Your users and their ability to comply with the increased complexity and nuance associated with more classification levels.
     -  User experience and accessibility when seeking to apply manual classification across multiple device types.
 -  **Get the right people involved**. Having a senior stakeholder is critical for success. Many projects struggle to start or take longer without senior management backing. Data classification frameworks are typically owned by information technology teams. However, they may have legal, compliance, privacy, and change management implications. To ensure you're creating a framework that helps protect your business, be sure to include privacy and legal stakeholders such as your Chief Privacy Officer and the Office of General Counsel in the development of your policy. If your organization has a Compliance division, information governance professionals, or a records management team, they may also have valuable input. As your framework is rolled out to the business, your Communications department also has a key role to play for internal messaging and adoption.
 -  **Balance security against convenience**. A common mistake is to draft a secure but overly restrictive data classification framework. This type of framework may have been designed with security in mind, but they can be difficult to implement in practice. If users must follow complex, rigid, and time-consuming procedures to apply the framework in their daily lives, there's always a risk they may no longer believe in its value. When this scenario occurs, users typically stop following procedures. This risk exists at all levels of the organization, including executive-level (C-suite) managers within the organization. A good balance of security against convenience alongside easy-to-use tools usually leads to wider user adoption and use. If there are gaps in your framework, don't wait until everything is perfect to start implementation. Instead, assess the risk or gap, create a plan to mitigate, and continue moving forward. Remember that information protection is a journey, it isn't something that's activated overnight and then done. Plan, implement some capabilities, confirm success, and iterate to the next milestone as tools evolve and users gain maturity and experience.

Also, keep in mind that a data classification framework only addresses ***what*** your organization should do to protect sensitive data. Data classification frameworks are often accompanied by data handling rules or guidelines that define ***how*** to put these policies in place from a technical and technology perspective.

### Pain points in creating a data classification framework

Data classification efforts are, by nature, wide-reaching. They touch nearly every business function within an enterprise. Because of this broad scope and the complexity of managing content in modern digital environments, companies often face challenges in knowing where to start, how to manage a successful implementation, and how to measure their progress. Organizations often encounter common pain points when they:

 -  Design a robust and easy-to-understand data classification framework, including determining classification levels and associated security controls.
 -  Develop an implementation plan that includes confirming the appropriate technology solution, aligning the plan to existing business processes, and identifying its effect on the workforce.
 -  Set up a data classification framework within the chosen technology solution.
 -  Address any gaps between the technology capabilities of the tool and the framework itself.
 -  Establish a governance structure that oversees the on-going maintenance and health of data classification efforts.
 -  Identify specific key performance indicators (KPIs) to monitor and measure progress.
 -  Increase awareness and understanding of data classification policies, why they're important, and how to comply with them.
 -  Comply with internal audit reviews that target data loss and cybersecurity controls.
 -  Train and engage users so they become mindful of the need for correct classification in their daily work and apply the right classification measures.

### Governance and maintenance

After an organization has developed and implemented its data classification framework, ongoing governance and maintenance will be critical to its success. In addition to tracking how sensitivity labels are used in practice, organizations must update their control requirements based on changes in regulations, cybersecurity leading practices, and the nature of the content they manage.

Governance and maintenance efforts may include:

 -  Establishing a governance body dedicated to data classification, or adding a data classification responsibility to the charter of an existing information security body.
 -  Defining roles and responsibilities for users overseeing data classification.
 -  Establishing KPIs to monitor and measure progress.
 -  Tracking cybersecurity leading practices and regulatory changes.
 -  Developing standard operating procedures that support and enforce a data classification framework.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”