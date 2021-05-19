Information Rights Management (IRM) protection in SharePoint Online is applied to files at the list or library level.

 -  When IRM is enabled for a library, rights management applies to all the files in that library.
 -  When IRM is enabled for a list, rights management applies only to files that are attached to list items, not the actual list items themselves.

When users download files in an IRM-enabled list or library, the files are encrypted so that only authorized people can view them. Each rights-managed file also contains an issuance license that imposes restrictions on the people who view the file. Typical restrictions include making a file read-only, disabling the copying of text, preventing people from saving a local copy, and preventing people from printing the file. Client programs that can read IRM-supported file types use the issuance license within the rights-managed file to enforce these restrictions. This process is how a rights-managed file keeps its protection even after it's downloaded from the server.

The types of restrictions that are applied to a file when it's downloaded from a list or library are based on the individual user's permissions on the site that contains the file. The following table explains how the permissions on sites correspond to IRM permissions.

:::row:::
  :::column:::
    

**Permissions**


  :::column-end:::
  :::column:::
    

**IRM Permissions**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Manage Permissions, Manage Web Site


  :::column-end:::
  :::column:::
    

**Full control** (as defined by the client program): This permission generally allows a user to read, edit, copy, save, and modify permissions of rights-managed content.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Edit Item, Manage Lists, Add and Customize Pages


  :::column-end:::
  :::column:::
    

**Edit**, **Copy**, and **Save**: A user can print a file only if the **Allow users to print documents** check box is selected on the Information Rights Management Settings page for the list or library.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

View Items


  :::column-end:::
  :::column:::
    

**Read**: A user can read the document but can't copy or modify its content. A user can print only if the **Allow users to print documents** check box is selected on the Information Rights Management Settings page for the list or library.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Other


  :::column-end:::
  :::column:::
    

No other permissions correspond directly to IRM permissions.


  :::column-end:::
:::row-end:::


When IRM is enabled for a list or library in SharePoint Online, you can only protect file types in that list or library for which a protector is installed. A protector is a program that controls the encryption and decryption of rights-managed files of a specific file format. SharePoint includes protectors for the following file types:

 -  The 97-2003 file formats for: Word, Excel, and PowerPoint
 -  Office 2010, Office 2013, and Office 2016 created documents
 -  The Office Open XML formats for: Word, Excel, and PowerPoint
 -  The XML Paper Specification (XPS) format
 -  PDF

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”