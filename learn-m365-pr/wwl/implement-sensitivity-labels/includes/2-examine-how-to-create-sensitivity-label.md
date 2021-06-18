When an organization is ready to start protecting its data by using sensitivity labels, it must complete the following high-level steps to create and publish labels:<br>

1.  **Create sensitivity labels.** Create and name your sensitivity labels according to your organization's classification taxonomy for different sensitivity levels of content. Use common names or terms that make sense to your users. The next unit explores how to create a Data Classification framework to establish a taxonomy that fits your organization's needs. If your organization doesn't have an established taxonomy, consider starting with basic label names such as Personal, Public, General, Confidential, and Highly Confidential. You can then use sublabels to group similar labels by category. When creating a label, use the tooltip text to help users select the appropriate label.<br>
2.  **Define what each sensitivity label can do.** Configure the protection settings you want associated with each label. For example, you may want lower sensitivity content (such as a "General" label) to have just a header or footer applied. Conversely, you may want your higher sensitivity content (such as a "Highly Confidential" label) to have a watermark and encryption.<br>
3.  **Publish the sensitivity labels.** After configuring your sensitivity labels, publish them by using a label policy. Decide which users and groups should have the labels and what policy settings to use. A single label is reusable—you define it once, and then you can include it in several label policies assigned to different users. For example, you could pilot your sensitivity labels by assigning a label policy to just a few users. Then when you're ready to roll out the labels across your organization, you can create a new label policy for your labels and this time, specify all users.<br>

The following diagram shows the basic flow for deploying and applying sensitivity labels. The three steps described above encompass the first task in this workflow diagram. This task focuses on the administrative steps required to create and publish sensitivity labels.

:::image type="content" source="../media/sensitivity-label-flow-1163508f.png" alt-text="graphic showing the basic flow for deploying and applying sensitivity labels":::


### Subscription and licensing requirements for sensitivity labels

Many different subscriptions support sensitivity labels. The licensing requirements for users depend on the features you use.

To see the options for licensing your users to benefit from Microsoft 365 compliance features, see the [Microsoft 365 licensing guidance for security &amp; compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). For sensitivity labels, see the [Information Protection](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection?azure-portal=true) section and related PDF or Excel download.

### Permissions required to create and manage sensitivity labels

Members of your compliance team who will create sensitivity labels need permissions to the Microsoft 365 compliance center, or to the older Security &amp; Compliance Center.

By default, global administrators for an organization's Microsoft 365 tenant have complete access to these admin centers. They can give access to compliance officers and other people, without giving them all of the permissions of a tenant admin. For this delegated limited admin access, add users to the Compliance Data Administrator, Compliance Administrator, or Security Administrator role group.

Besides using default roles, you can also create a new role group and add either Sensitivity Label Administrator or Organization Configuration roles to this group. For a read-only role, use Sensitivity Label Reader. These permissions are only required to create and configure sensitivity labels and their label policies. They aren't required to apply the labels in apps or services.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”