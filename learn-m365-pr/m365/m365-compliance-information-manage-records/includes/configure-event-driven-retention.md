Use event-based retention when you want the retention period to be based on when a specific type of event occurs, rather than when the content was created, last modified or labeled. 

For example, if you associate a label with the event type of "Employment ended", any content with that label applied will be retained until you create an event and specify the type "Employment ended", the ID of the employee who left the company, and the date. 

The event will then detect all items with the label applied that meet the criteria associated with it, and set the expiration date for those items based on the retention period. Here are some other examples of when event-based retention is appropriate:

- **Product lifetime**. Your organization might have retention requirements for product technical specifications. The event that triggers the retention period could be the product release date, or when it was last manufactured.
- **Contract expiration**. Your organization might have a policy that all documents related to a contract must be retained for seven years after the contract expires. The end of the contract triggers the seven-year retention period.

You can only create event-based labels if you choose to "Retain the content" and either "Delete the content automatically" or "Trigger a disposition review". The distinction between an event and an event type is important. The following table helps distinguish them.

| Name  | Definition  |  Example |
|---|---|---|
|  Event type | Description of an event with which to associate the label  | Employment ended  |
|  Event | Specific occurrence of the event type  |Megan Bowen's employment ended   |

Different methods are used to identify the labeled items that trigger the event. Exchange-based content is identified through keyword searches. SharePoint and OneDrive content rely on item properties. Your SharePoint and OneDrive content must have a column containing the identifier to be used to determine when the event type occurrence applies. A column called Asset ID is created and used by default, but you can use a different column and use Keyword Query Language (KQL) to specify it. An example of an asset ID is a column in a document library that includes the employee ID of the individual document, like an employee evaluation, applies to.<!--CE:I don't understand the end of this sentence. What does 'applies to' refer to?-->

Here is the flow to configure event-driven retention:

1. Create retention label with event-based retention period.
1. Publish or auto-apply label.
1. Create an event.

:::image type="content" source="../media/event-driven-retention-configuration.png" alt-text="Event-driven retention configuration" border="false":::

## Step 1: Create a label with event-based retention period

Refer to the retention label configuration unit in this module for the instructions on this step. When you configure the label, select the option to base the retention on an event. 

From there, you select an existing event type or create your own. Multiple retention labels can be associated with a single event type,   and each label might have a different retention period. For example, you could have two labels associated with the event type "Employment ended". 

One label is applied to formal employee reviews and has a retention period of 10 years. A second label is applied to employee awards and has a five-year retention period. Both labels can be associated with the same event type, which results in content being retained for different lengths of time after the employee has left.

## Step 2: Publish or auto-apply the label

Labels don't do anything unless they're published or auto-applied by a policy. Refer to the information governance module in this learning path for instructions on how to publish or auto-apply a label policy. When the label is published, it will be applied to email messages and documents. Remember that the documents the label is being applied to must have a column that's used as an Asset ID.  

## Step 3: Create an event

This step doesn't happen until there's an occurrence of the event type. When an instance of the event type associated with the retention label(s) takes place, an event must be created. In our example, the event type is "Employment ended" and the event is "Megan Bowen's employment ended".  

The process of adding the event triggers the retention period to begin. This is the step where you tell Microsoft 365 that Megan's employment has ended. You now want the retention period to begin on Megan's items with the label(s) associated with the event type "Employment ended". It consists of three steps:

### Step 3.1: Name the event

### Name

Enter a name to describe the event that clearly distinguishes it, such as "Employment ended: Megan Bowen ID: 12345", or "Vendor contract CONTR_6789 closed". After the event is created, you can view its status from the Events page of the records management solution.

### Description

Enter a description of the event.

### Step 3.2: Event settings

### Use event types

Choose the event type associated with labels applied to the items you want to start retaining. The event type should have been created when you produced the retention label. For example, if the event you create is for the end of someone's employment, you choose the event type "Employment ended".

After you identify the items related to this event, records management will find all those items with labels associated with the event type you chose that match the criteria set in this step. It will then set the expiration date for those items based on the labels' retention period(s).

- Keywords for items in Exchange. Use keyword query syntax to identify the items in Exchange you want to retain.
- Asset ID for SharePoint and OneDrive items. Asset ID refers to the specific properties applied to the SharePoint and OneDrive items related to this event. SharePoint and OneDrive properties, also called columns, help group, categorize, and track information in a list or library. 
- When did the event occur? This is the date when the retention period will start for any items identified using Asset ID and keyword searches that have labels associated with the event type you chose.

### Use existing labels

This option is for situations where an event type was not previously defined. Choose all the labels to apply to this event. When you've done that, the rest of the process is identical to the "use event types" branch.

### Step 3.3: Review your settings

The final step in the process is to create the event.

