Of course, all organizations use information slightly differently. However, the general pathway by which files are created, managed, updated, and destroyed is often broadly similar.

In your legal company, you're concerned that your compliance with regulations might not be as good as it should be. You're investigating file lifecycles to analyze this problem further.

Here, you'll learn about the typical lifecycle of the files in your organization.

## Lifecycle summary

Not all data is created equal. Some data is more sensitive and requires a stronger level of protection and control than other types. The kinds of information that need protecting depends on your internal security requirements and compliance obligations. Because every organization may have different governance or compliance standards, it’s important to allow customization of classification policies. 

For instance, a beverage company needs to protect the secret recipe to its most famous soft drink. However, a finance company's cafeteria recipes are not so critical to everyday business. There are general guidelines for more obvious sensitive data, such as credit card and social security numbers, but no two organizations classify data the same way. 

Let’s look at the journey of a file and discuss how Microsoft technologies can help protect the data within that file.

:::image type="content" source="../media/story-of-file.png" alt-text="Diagram showing how Microsoft technologies protect a file from creation through editing and cloud storage.":::

Now, let's examine these lifecycle stages in more detail.

1. **File is created**

	Regardless of where the file is created, sensitivity labeling in Office apps can enforce information protection based on the labels attached to the data.

1. **User edits the file**

	The label is updated based on the user's changes and the content's sensitivity. This ensure the file has the right protection.

1. **User shares the file with another user in the organization**

	As an additional layer of protection, Data Loss Prevention (DLP) policies help prevent the accidental or inadvertent sharing of sensitive documents and emails.

1. **User opens the file on their phone**

	If a user receives and opens the data on a mobile device, Intune enforces protection of the data.

1. **User uploads the file to another cloud service such as Dropbox**

	If a user uploads the data to other clouds for external sharing, services such as Microsoft Cloud App Security can apply policies based on the data’s labels.
