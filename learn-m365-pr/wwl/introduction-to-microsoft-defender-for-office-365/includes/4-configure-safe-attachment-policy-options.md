When you set up a Safe Attachments policy, you can choose from several options. The following table describes each option and its effect.

:::row:::
  :::column:::
    

**Option**


  :::column-end:::
  :::column:::
    

**Effect**


  :::column-end:::
  :::column:::
    

**Use cases**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Off


  :::column-end:::
  :::column:::
    

Doesn't scan attachments for malware.


Doesn't delay message delivery.


  :::column-end:::
  :::column:::
    

Turn scanning off for internal senders, scanners, faxes, or smart hosts that will only send known, good attachments.


Prevent unnecessary delays in routing internal mail.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Monitor


  :::column-end:::
  :::column:::
    

Delivers messages with attachments and then tracks what happens with detected malware.


  :::column-end:::
  :::column:::
    

See where detected malware goes in your organization.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Block


  :::column-end:::
  :::column:::
    

Prevents messages with detected malware attachments from proceeding.


Sends messages with detected malware to quarantine in Microsoft 365. A security administrator or analyst can then review and release (or delete) those messages.


Blocks future messages and attachments automatically.


  :::column-end:::
  :::column:::
    

Safeguard your organization from repeated attacks using the same malware attachments.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Replace


  :::column-end:::
  :::column:::
    

Removes detected malware attachments.


Notifies recipients that attachments have been removed.


Sends messages with detected malware to quarantine in Microsoft 365. A security administrator or analyst can then review and release (or delete) those messages.


  :::column-end:::
  :::column:::
    

Raise visibility to recipients that attachments were removed because of detected malware.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Dynamic Delivery


  :::column-end:::
  :::column:::
    

Delivers messages immediately.


Replaces attachments with a placeholder file until scanning is complete, and then reattaches the attachments if no malware is detected.


Includes attachment previewing capabilities for most PDFs and Office files during scanning.


Sends messages with detected malware to Quarantine, where a security administrator or analyst can review and release (or delete) those messages.


  :::column-end:::
  :::column:::
    

Avoid message delays while protecting recipients from malicious files.


Enable recipients to preview attachments in safe mode while scanning is taking place.


  :::column-end:::
:::row-end:::
