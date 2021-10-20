Microsoft has developed a tool to import your file plan into Microsoft 365.

Go to **Microsoft 365 compliance center > Records management > File plan > Import** to import your file plan.

:::image type="content" source="../media/import-file-plan.png" alt-text="Screenshot of the Microsoft 365 compliance center showing the import file plan option." lightbox="../media/import-file-plan.png":::

The process consists of the following steps:

1. Download the file plan template.
1. Fill out the file plan.
1. Import the file plan.

Remember that imported file plan labels still need to be published or auto-applied to see any results.

:::image type="content" source="../media/file-plan-import.png" alt-text="Screenshot showing the three step process of file plan importing" border="false" lightbox="../media/file-plan-import.png":::

## Step 1: Download the file plan template

The file plan template is a comma separated value (CSV) file. You download it from the file plan page of the records management solution. Many of your stakeholders will be familiar with using Excel for file plan management. You might be able to use this template to collaborate with stakeholders during file plan and retention schedule development. The template fields won't match your organization's existing file plan and retention schedule, so you'll need to determine how to reconcile the differences. Here's a list of the fields in the file plan template:

- LabelName
- Comment
- Notes
- IsRecordLabel
- RetentionAction
- RetentionDuration
- RetentionType
- ReviewerEmail
- ReferenceId
- DepartmentName
- Category
- SubCategory
- AuthorityType
- CitationName
- CitationUrl
- CitatuionJurisdiction
- Regulatory
- EventType

## Step 2: Fill out the file plan

Next, you complete the file plan template. Because your goal should be to import the file plan into Microsoft 365, don't make any changes to the column headings. You can save the file with whatever name you prefer. You must export the file to CSV format if you convert it to an Excel workbook (XLSX) file, and use rich formatting to facilitate collaboration with stakeholders.

> [!NOTE]
> There's a per-field limit of 64 characters when you import a file plan. If required, you can add more characters to each field after the import.

## Step 3: Import the file plan

You upload the completed plan to Microsoft 365. After you've checked that everything looks as expected, you publish, or auto-apply, the labels to activate them. Refer to the *Information governance* module in this learning path for instructions on how to publish or auto-apply a label policy.

## Learn more

- [Import retention labels into your file plan](/microsoft-365/compliance/file-plan-manager?import-retention-labels-into-your-file-plan?azure-portal=true)
- [Retention label file plan descriptors columns](/microsoft-365/compliance/file-plan-manager?retention-label-file-plan-descriptors-columns?azure-portal=true)
