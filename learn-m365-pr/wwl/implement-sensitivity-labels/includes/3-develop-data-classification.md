  Implementing sensitivity labels must begin with determining the terms that will be used to classify an organization's documents and emails. This process is referred to as Data Classification, which is a specialized term used in the fields of cybersecurity and information governance. It's used to describe the process of identifying, categorizing, and protecting content according to its sensitivity or impact level. In its most basic form, data classification is a means of protecting your data from unauthorized disclosure, alteration, or destruction based on how sensitive or impactful it is.

Often codified in a formal, enterprise-wide policy, a Data Classification framework typically includes three to five classification levels. Each level usually includes three elements: a name, description, and real-world examples. It's recommended that organizations identify no more than five top-level parent labels, each with five sublabels (25 total) to keep the User Interface (UI) manageable. Levels are typically arranged from least to most sensitive such as Public, Internal, Confidential, and Highly Confidential. Other level name variations you may encounter include Restricted, Unrestricted, and Consumer Protected.

It's recommended that label names be self-descriptive and clearly highlight their relative sensitivity. For instance, Confidential and Restricted may leave users guessing which is appropriate, while Confidential and Highly Confidential are clearer on which is more sensitive.

The following table displays an example of a Data Classification framework level.

:::row:::
  :::column:::
    **Classification level**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **Examples**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Highly Confidential
  :::column-end:::
  :::column:::
    

Highly Confidential data is the most sensitive type of data stored or managed by the enterprise. It may require legal notifications if breached or otherwise revealed.

Restricted Data requires the highest level of control and security, and access should be limited to "need-to-know."


  :::column-end:::
  :::column:::
    

 -  Sensitive Personal Information
 -  Cardholder Data
 -  Protected Health Information (PHI)
 -  Bank Account Data


  :::column-end:::
:::row-end:::


> [!TIP]
> Microsoft’s corporate data classification framework originally used a category and label named ‘Internal’. However, during its pilot phase of implementing sensitivity labels, Microsoft but found that there were legitimate reasons for a document to be shared externally and shifted to using ‘General’.

Another important component of a Data Classification framework is the controls associated with each level. Data Classification levels by themselves are simply labels (or tags) that indicate the value or sensitivity of the content. To actually protect that content, Data Classification frameworks define the controls that should be in place for each of your data classification levels. These controls may include requirements related to:

 -  Storage Type and Location
 -  Encryption
 -  Access Control
 -  Data Destruction
 -  Data Loss Prevention
 -  Public Disclosure
 -  Logging and Tracking Access
 -  Other control objectives, as needed

Your security controls will vary by data classification level, such that the protective measures defined in your framework increase commensurate with the sensitivity of your content. For example, your data storage control requirements will vary depending upon the media that's being used, and upon the classification level applied to a given piece of content.

Correctly applying the right level of data classification can be complex in real-life situations and may sometimes overwhelm end users. As a result, once a policy or standard has been created that defines the required levels of data classification, it remains important to also guide end users on how to bring this framework to life in their daily work. This situation is where data classification handling rules or guidelines come in.

Data classification handling guidelines will help end users with specific guidance on how to handle each level of data appropriately, for different storage media throughout their lifecycle. These guidelines help end users to correctly apply rules in practice, for instance when sharing documents, sending emails, or collaborating across different platforms and organizations.

> [!NOTE]
> Microsoft customers indicate that approximately 50% of an Information Protection project is business focused rather than technical, so end-user training and communication are critical to success.

### Pain points in creating a Data Classification framework

Data Classification efforts are by nature wide-reaching, touching nearly every business function within an enterprise. Because of this broad scope and the complexity of managing content in modern digital environments, companies often face challenges in knowing where to start, how to manage a successful implementation, and how to measure their progress.

Common pain points include:

 -  Designing a robust and easy-to-understand Data Classification framework, including determining classification levels and associated security controls.
 -  Developing an implementation plan that includes confirming the appropriate technology solution, aligning the plan to existing business processes, and identifying impact to the workforce.
 -  Setting up a Data Classification framework within technology solution and addressing any gaps between the technology capabilities of the tool and the framework itself.
 -  Establishing a governance structure that oversees the on-going maintenance and health of Data Classification efforts
 -  Identifying key performance indicators to monitor and measure progress.
 -  Increasing awareness and understanding of Data Classification policies, why they're important, and how to follow them.
 -  Following suggestions from internal audit reviews that target data loss and cybersecurity controls.
 -  Training and engaging end users so they become mindful of the need for correct classification in their daily work and apply the right measures as necessary.

### Creating a well-designed Data Classification framework

As you develop, revamp, or refine your Data Classification framework, consider the following leading practices:

 -  **Don’t expect to go from 0-100 on day 1.** It's recommended that organization take a crawl-walk-run approach, prioritizing features critical to the organization and mapping them against a timeline. Complete the first step, ensure it was successful, and then move on to the next phase applying lessons learned. Remember that your organization may still be exposed to risk while you design your Data Classification framework, so it’s ok to start small with just a few classification levels and expand later as needed.
 -  **You’re not just writing for cybersecurity professionals.** Data Classifications frameworks are meant for a broad audience, including your average staff member, your legal and compliance team, and your IT team. As such, it's imperative to write clear, easy-to-understand definitions for your Data Classification levels, providing real-world examples wherever possible. Also try to avoid jargon and consider a glossary for acronyms and highly technical terms.
 -  **Data Classification frameworks are meant to be implemented.** For Data Classification frameworks to be successful, they must be implemented. Planning for a successful implementation of sensitivity labels should be a key goal when crafting the control requirements for each Data Classification level. Make sure requirements are clearly spelled out. Expect and address any ambiguity that may arise during implementation. For example, if you have a control around Personal Information, make sure to spell out exactly what it means, such as Social Security Number or Passport Number.
 -  **Only go granular if you need to.** As previously mentioned, Data Classification frameworks typically contain anywhere from three to five Data Classification levels. But just because you can include five levels doesn’t mean you should. Consider the following criteria when deciding on the number of classification levels you need:
    
     -  Your industry and your associated regulatory obligations (highly regulated industries tend to need more classification levels).
     -  The operational overhead required to maintain a more complex framework.
     -  Your users and their ability to follow the increased complexity and nuance associated with more classification levels.
     -  User experience and accessibility when seeking to apply manual classification across multiple device types.
 -  **Get the right people involved.** Having a senior stakeholder is critical for success, as many projects struggle to start or take much longer to finish without senior management backing. Data Classification frameworks are typically owned by an organization's Security team, but they also have legal, compliance, privacy, and change management implications. To ensure you’re creating a framework that truly protects your business, be sure to include privacy and legal stakeholders such as your Chief Privacy Officer and the Office of General Counsel in the development of your policy. If your organization has a Compliance division, Information Governance professionals, or a Records Management team, they'll have valuable insights to add as well. As your framework is rolled out to the business, your Communications department also has a key role to play from a messaging and adoption perspective.
 -  **Balance security against convenience.** A common mistake is to draft a secure but restrictive data classification framework that's been designed with security in mind, but is difficult to implement in practice. If end users need to follow complex, rigid, and time-consuming procedures to apply the framework in their daily lives, there's always a risk the end users will end up no longer believing in its value and stop following procedures. This risk exists at all levels of the organization, including C-suite executives.<br><br>A good balance of security against convenience alongside easy-to-use tools will lead to wider end-user support. Also, if there are gaps in your framework, don’t wait until everything is perfect to start implementation. Instead, assess the risk or gap, create a plan to mitigate, and continue with the implementation. Remember that Information Protection is a journey. It’s not something that's activated overnight and then done.

    > [!IMPORTANT]
    > Plan, implement some capabilities, confirm success, and iterate to the next milestone as tools evolve and users gain maturity and experience.

Also keep in mind that a Data Classification framework only addresses what your organization should do to protect sensitive data. Data Classification frameworks are often accompanied by data handling rules or guidelines that define how to put these policies in place from a technical and technology perspective.
