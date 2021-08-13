You've learned how to assess your security posture and identify vulnerabilities. Now you can look at how to use Microsoft Defender for Endpoint to improve your security posture.

Here, you'll learn how to remediate vulnerabilities, track remediations, how to handle zero-day vulnerabilities, and more.

## Remediate vulnerabilities

The vulnerabilities discovered on your organization's endpoints are mapped against matching security recommendations to remediate them. These recommendations are also prioritized for you based on their impact.

Each security recommendation includes detailed steps that you can take to remediate a security issue. Security recommendations are intelligent and can change over time based on the information that is continuously collected across your organization, together with the status of the vulnerability, and the changing threat landscape.

The security recommendations pane in the portal lists all the recommendations for your organization and is accessible from the navigation pane under **Recommendations**:

:::image type="content" source="../media/5-recommendations-list-inline.png" lightbox="../media/5-recommendations-list-expanded.png" alt-text="Security recommendations list.":::

You can select any recommendation to find more information about it and understand how to implement it:

:::image type="content" source="../media/5-select-security-recommendation-inline.png" lightbox="../media/5-select-security-recommendation-expanded.png" alt-text="Security recommendation details.":::

**Request remediation** initiates a remediation request.

:::image type="content" source="../media/5-remediation-request-inline.png" lightbox="../media/5-remediation-request-expanded.png" alt-text="Remediation request.":::

With remediation requests, you can send a request to a relevant team to implement the security recommendation and address the issue at hand.

### Use exceptions

Alternatively, you might decide that a recommendation might not be relevant or you might have unique or special circumstances.. In these situations, you can create an exception for any recommendation. To create an exception, you select the **Exception options** next to **Request remediation** in the security recommendation's detail pane. When you create an exception, you specify a justification and duration for the exception to ensure the exception is understood and is restricted to the time period you specify.

:::image type="content" source="../media/5-exception-inline.png" lightbox="../media/5-exception-expanded.png" alt-text="Create an exception.":::

> [!NOTE]
> Only users with the **Threat and vulnerability management - Exception handling** permission can specify exceptions.

### Track remediation

You track remediation requests in the **Remediation** pane, which you can access by selecting **Remediation** in the navigation pane. The **Remediation** pane lists all of the remediation requests (referred to as activities) for your organization. You select a specific remediation activity to view more details about the activity:

:::image type="content" source="../media/5-track-remediation-inline.png" lightbox="../media/5-track-remediation-expanded.png" alt-text="Track remediation activity.":::

You can view the status of the remediation activity, along with other details such as its priority level, and when it's due.

## Identify end-of-support software and software versions

Over time, some software or specific versions of software will stop being supported and will no longer  receive security updates. The software is considered to be at end-of-support (EOS). Software at end-of-support can introduce security vulnerabilities. You must identify EOS software and software versions in order to be able to address these vulnerabilities.

To find EOS software and versions, you can filter the security recommendations list using one or more of the EOS-related tags.

:::image type="content" source="../media/5-tags-inline.png" lightbox="../media/5-tags-expanded.png" alt-text="Filter security recommendations.":::

EOS-related filters are:

- **EOS software**
  - Software that is at end-of-support
- **EOS versions**
  - Versions of a software that are at end-of-support
- **Upcoming EOS versions**
  - Versions that will soon be at end-of-support

The security recommendations are then filtered accordingly:

:::image type="content" source="../media/5-filtered-recommendations-inline.png" lightbox="../media/5-filtered-recommendations-expanded.png" alt-text="Filtered security recommendations.":::

You can then implement the resulting recommendations to address the vulnerable EOS software or software version.

## Address zero-day vulnerabilities

Zero-day vulnerabilities are vulnerabilities that are publicly disclosed and for which there are currently no fixes or patches. These types of vulnerabilities are likely to be of high severity and are potentially actively exploited by attackers.

When a zero-day vulnerability has been identified on your endpoints, you will receive notifications about it across the portal in different areas including:

- The threat and vulnerability main dashboard
- The weaknesses pane
- The software inventory pane
- The security recommendations pane

You can filter your security recommendations pane using the Zero-day tag to see all of the security recommendations for zero-day vulnerabilities:

:::image type="content" source="../media/5-filter-security-recommendations-zero-day-tag-inline.png" lightbox="../media/5-filter-security-recommendations-zero-day-tag-expanded.png" alt-text="Filter the security recommendations using the zero-day tag.":::

To address zero-day vulnerabilities, you can select a recommendation from the list.

:::image type="content" source="../media/5-zero-day-security-recommendation.png" alt-text="Security recommendations for zero-day vulnerabilities." lightbox="../media/5-zero-day-security-recommendation.png":::

You'll get more information and potential workarounds or mitigation options that can help:

:::image type="content" source="../media/5-recommendation-zero-day.png" alt-text="Recommendation for zero-day vulnerabilities." lightbox="../media/5-recommendation-zero-day.png":::

You can use workarounds like these, until a fix becomes available. When a fix is available, the recommendation will be updated with details of the fix.
