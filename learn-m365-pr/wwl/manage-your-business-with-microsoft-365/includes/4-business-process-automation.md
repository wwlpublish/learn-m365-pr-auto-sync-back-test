Every business will have its fair share of time-intensive repetitive tasks that need to be done for the company to operate. These can range from routine email marketing campaigns to the management of employee requests. In today's fast-paced business world, where the customer expects an immediate response to every query, it can be challenging to deliver a quality service. Business process automation gives your organization the ability to automate time-intensive tasks, optimizing operations, and bringing a new level of efficiency to your organization. Process automation allows your employees to use their skills for the jobs they were hired to do instead of routine tasks that may take up valuable time.

Business process automation can be used to streamline a variety of processes, including:

 -  Document management
 -  Workflow automation
 -  Task alerts via email
 -  Email marketing campaigns
 -  Thank you letters
 -  Payment reminders
 -  Document review and approval
 -  Management of employee requests

Microsoft 365 provides several tools, services, or applications to enable automation:

 -  SharePoint
 -  Power Automate
 -  Power Apps

## Use SharePoint to provide business process automation

SharePoint workflows are pre-programmed mini-applications that streamline and automate a wide variety of business processes. Workflows can include collecting signatures, feedback, or approvals for a plan or document to track the current status of a routine procedure. SharePoint workflows are designed to save you time and effort and to bring consistency and efficiency to tasks that you perform regularly.

Here is an example of a typical workflow:

:::image type="content" source="../media/4-sharepoint-workflow-e00e7347.png" alt-text="SharePoint workflow":::


#### Approval

This workflow routes a document or item to a group of people for approval. By default, the Approval workflow is associated with the Document content type, and thus it is automatically available in document libraries.

#### Collect feedback

This workflow routes a document or item to a group of people for feedback. Reviewers can provide feedback, which is then compiled and sent to the person who initiated the workflow. By default, the Collect Feedback workflow is associated with the Document content type, and thus it is automatically available in document libraries.

#### Collect signatures

This workflow routes a Microsoft 365 Office document to a group of people to collect their digital signatures. This workflow must be started in a Microsoft 365 Office application. Participants must complete their signature tasks by adding their digital signature to the document in the relevant Office program. By default, the Collect Signatures workflow is associated with the Document content type, and thus it is automatically available in document libraries. However, the Collect Signatures workflow appears for a document in the document library only if it contains one or more Microsoft 365 Office Signature Lines.

#### Publish approval

This workflow is similar to the Approval workflow in that it automates the routing of content to subject matter experts and stakeholders for review and approval. What makes the publishing approval workflow unique is that it’s designed specifically for publishing sites where the publishing of new and updated web pages is tightly controlled.

#### Three-state

This workflow can be used to manage business processes that require organizations to track a high volume of issues or items, such as customer support issues, sales leads, or project tasks.

## Customize workflows

Each of the above workflows can be customized for your organization in several ways. For example, when you add a workflow to a list, library, or content type to make it available for use on documents or items, you can customize the task lists and history lists where information about the workflow is stored.

When a site user starts a workflow on a document or item, the user may have the option to further customize the workflow by specifying the list of participants, a due date, and task instructions.

## Use Power Automate

Power Automate is an online workflow service that automates actions across the most common apps and services. For example, you can create a flow that adds a lead to Microsoft Dynamics 365 and a record in MailChimp whenever someone with more than 100 followers tweets about your company. You can use Power Automate to automate workflows between your favorite applications and services, sync files, get notifications, collect data, and much more.

For example, you can automate these tasks:

 -  Instantly respond to high-priority notifications or emails.
 -  Capture, track, and follow up with new sales leads.
 -  Copy all email attachments to your OneDrive for Business account.
 -  Collect data about your business and share that information with your team.
 -  Automate approval workflows.

A common use of Power Automate is to receive notifications. For example, you can instantly receive an email or a push notification on your phone whenever a sales lead is added to Dynamics 365 or Salesforce.

Power Automate is one of the pillars of the Power Platform. It provides a low code platform for workflow and process automation. Here's a list of the different types of flows:

:::row:::
  :::column:::
    **Flow type**
  :::column-end:::
  :::column:::
    **Use case**
  :::column-end:::
  :::column:::
    **Target**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Automated flows](/power-automate/get-started-logic-flow)
  :::column-end:::
  :::column:::
    Create a flow that performs one or more tasks automatically after an event triggers it.
  :::column-end:::
  :::column:::
    [Connectors](/connectors/) for cloud or on-premises services.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Button flows](/power-automate/introduction-to-button-flows)
  :::column-end:::
  :::column:::
    Run repetitive tasks from any place, at any time, via your mobile device.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Scheduled flows](/power-automate/run-scheduled-tasks)
  :::column-end:::
  :::column:::
    Create a flow that performs one or more tasks on a schedule.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Business process flows](/power-automate/business-process-flows-overview)
  :::column-end:::
  :::column:::
    Define a set of steps for people to follow to take them to the desired outcome.
  :::column-end:::
  :::column:::
    Human processes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [UI flows](/power-automate/ui-flows/overview)
  :::column-end:::
  :::column:::
    Record and automate the playback of manual steps on legacy software.
  :::column-end:::
  :::column:::
    Desktop and Web applications that do not have APIs available for automation.
  :::column-end:::
:::row-end:::


## Create Power Apps

Power Apps is a suite of apps, services, connectors, and data platforms that provide a rapid application development environment to build custom apps for your business needs. Using Power Apps, you can quickly build custom business apps that connect to your business data stored either in the underlying data platform Common Data Service or in various online and on-premises data sources, for example, SharePoint, Excel, Microsoft 365, Dynamics 365, SQL Server, and so on).

Apps built using Power Apps provide rich business logic and workflow capabilities to transform your manual business processes to digital, automated processes. Further, apps built using Power Apps have a responsive design and can run seamlessly in a browser or on mobile devices (phone or tablet). Power Apps "democratizes" the custom business app building experience by enabling users to build feature-rich, custom business apps without writing code.

Power Apps also provides an extensible platform that lets pro developers programmatically interact with data and metadata, apply business logic, create custom connectors, and integrate with external data.

To create an app, you start with [make.powerapps.com](https://make.powerapps.com/).

 -  **Power Apps Studio** is the app designer used for building canvas apps. The app designer makes creating apps feel more like building a slide deck in Microsoft PowerPoint. More information: Generate an app from data.
 -  **App designer** for model-driven apps lets you define the sitemap and add components to build a model-driven app. More information: Design model-driven apps using app designer.

You can run apps that you created or that someone else created and shared with you, in a browser or on mobile devices (phone or tablet).
