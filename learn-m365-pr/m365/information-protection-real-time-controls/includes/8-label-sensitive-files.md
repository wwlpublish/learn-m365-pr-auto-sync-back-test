An Azure Information Protection classification label is metadata that is stored in a file. This information can be used by a data loss prevention (DLP) solution, such as Microsoft Defender for Cloud Apps, to limit access to, and actions that can be performed on, this file. The classification labels are retained if the file is exported.

With Defender for Cloud Apps, you can automatically apply labels using a file policy that could then be used to protect the file, for example, by applying encryption to the file.

## Create a policy to set up data protection

To create a policy to set up data protection on files that contain credit card information, perform the following steps:

1. Navigate to <https://portal.cloudappsecurity.com>.
2. Select **Control** and select **Policies**.

    :::image type="content" source="../media/4-microsoft-cloud-app-security-policies.png" alt-text="Policies":::

3. Select **Create policy** and select **File policy**.

    :::image type="content" source="../media/8-file-policy.png" alt-text="File policy":::

4. Enter a name and description in **Policy name** and **Description**.
5. In **Create a filter for the files this policy will act on** and the **Apply to** fields add any filters that you require to target your sensitive files.
6. In **Inspection method**, select **Built-in DLP**, select **Include files that match a preset expression**, and select **All countries: Finance: Credit cards number**.

    :::image type="content" source="../media/8-inspection-method.png" alt-text="Credit card search":::

7. In **Governance**, expand your cloud file storage solution, select **Apply classification label** and select the label that you want to apply. For example, select **Confidential**.

8. Select **Create**.
