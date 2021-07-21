Use event-based retention when you want the retention period to be based on when a specific type of event occurs, rather than when the content was created, last modified or labeled. For example, if you associate a label with the event type of ‘Employment ended', any content with that label applied will be retained until you create an event and specify the event type ‘Employment ended', the ID of the employee who left the company, and the date it occurred. At this point, the event will detect all items with the label applied that meet the criteria associated with it and set the expiration date for those items based on the retention period. Here are some other examples of when event-based retention is appropriate:

- **Product lifetime**. Your organization might have retention requirements for product technical specifications. The event triggering the retention period could be the product release date or when it was last manufactured.
- **Contract expiration**. Your organization may have a policy all documents related to a contract must be retained for seven years after the contract has expired. The contract expiration triggers the 7-year retention period.

You can only create event-based labels if you choose to 'Retain the content' and either 'Delete the content automatically' or 'Trigger a disposition review'. The distinction between an event and an event type is important. The following table helps distinguish them.

| Name  | Definition  |  Example |
|---|---|---|
|  Event type | Description of an event to associate label with  | Employment ended  |
|  Event | Specific occurrence of the event type  |Megan Bowen's employment ended   |

Different methods are used to identify the labeled items that trigger the event. Exchange-based content is identified through keyword searches. SharePoint and OneDrive content rely on item properties. Your SharePoint and OneDrive content must have a column containing the identifier to be used to determine when the event type occurrence applies. A column called Asset ID is created and used by default, but you can use a different column and use Keyword Query Language (KQL) to specify it. An example of an asset ID would a column in a document library that includes the employee ID of the individual document, like an employee evaluation, applies to.

Here is the flow for configuring event-driven retention:

1. Create retention label with event-based retention period
1. Publish or auto-apply label
1. Create an event

![Event-driven retention configuration](../media/event-driven-retention-configuration.png)

## Step 1: Create a label with event-based retention period

Refer to the Retention label configuration unit in this module for the instructions on this step. When configuring the label, select the option to base the retention on an event. From there, you can select an existing event type or create your own. Multiple retention labels can be associated with a single event type   and each label can have a different retention period. For example, you could have two labels associated with the event type of "Employment ended". One label is applied to formal employee reviews and has a retention period of 10 years. A second label is applied to employee awards and has a 5-year retention period. Both labels can be associated with the same event type, resulting in content being retained for different lengths of time after the employee has left the organization.

## Step 2: Publish or auto-apply the label

Labels do not do anything unless they are published or auto-applied by a policy. Refer to the information governance module in this learning path for instructions on publishing or auto-applying a label policy. Once the label is published, it will be applied to email and documents. Keep in mind that the documents the label is being applied to must have column that is used as an Asset ID.  

## Step 3: Create an event

The step does not happen until an occurrence of the event type takes place. When an instance of the event type associated with the retention label(s) takes place, an event must be created. In our example, the event type is ‘Employment ended' and the event is ‘Megan Bowen's employment ended'.  The process of adding the event is what triggers the retention period to begin. This is the step where you tell Microsoft 365 Megan's employment has ended and you want the retention period to begin on Megan's items with the label(s) associated with the event type ‘Employment ended'. It consists of three steps:

### Step 3.1: Name the event

### Name

Enter a name describing the event that clearly distinguishes it, such as "Employment ended: Megan Bowen ID: 12345" or "Vendor contract CONTR_6789 closed". After the event is created, you can view its status from the Events page of the records management solution.

### Description

Enter a description of the event.

### Step 3.2: Event settings

### Use event types

Choose the event type associated with labels applied to the items you want to start retaining. The event type should have been created when you created the retention label. For example, if the event you are creating is for the end of someone's employment, you would choose the event type ‘Employment ended'.

After you identify the items related to this event, records management will find all those items with labels associated with the event type you chose that match the criteria set in this step. It will then set the expiration date for those items based on the labels' retention period(s).

- Keywords for items in Exchange. Use keyword query syntax to identify the items in Exchange you want to retain.
- Asset ID for SharePoint and OneDrive items. Asset ID refers to the specific properties applied to the SharePoint and OneDrive items related to this event. SharePoint and OneDrive properties, also called columns, help group, categorize, and track information in a list or library. 
- When did event occur? This is the date when the retention period will go into effect for any items identified using asset ID and keyword searches that have labels associated with the event type you chose.

### Use existing labels

This option is for situations where an event type was not previously defined. Choose all the labels to apply to this event. Once you have done that, the rest of the process is identical to the use event types branch.

### Step 3.3: Review your settings

The final step in the process is to create the event.

## Learn more

- [Overview of event driven retention](/microsoft-365/compliance/event-driven-retention?azure-portal=true)
- [Automate event-based retention](/microsoft-365/compliance/automate-event-driven-retention?azure-portal=true)
