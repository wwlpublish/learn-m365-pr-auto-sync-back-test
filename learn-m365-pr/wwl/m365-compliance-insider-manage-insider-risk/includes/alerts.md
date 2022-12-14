## Alert dashboard

The insider risk Alert dashboard allows you to view and take action on alerts generated by insider risk policies. The Alert dashboard displays information from the previous 30 days for the following widgets:

- Alerts to review: The total number of alerts needing review and triage are listed, including a breakdown by alert severity.
- Open alerts over the past 30 days: The total number of alerts created by policy matches over the last 30 days, sorted by high, medium, and low alert severity levels.
- Average time to resolve alerts: A summary of useful alert statistics:
  - Average time to resolve high severity alerts, listed in hours, days, or months.
  - Average time to resolve medium severity alerts, listed in hours, days, or months.
  - Average time to resolve low severity alerts, listed in hours, days, or months.

:::image type="content" source="../media/resolve-alerts.png" alt-text="Screenshot of the Alerts tab that shows 3 alerts currently need review in addition to a chart of the open alerts over the past 30 days, and a list of each alert." lightbox="../media/resolve-alerts.png" border="false":::

> [!NOTE]
> Insider risk management uses built-in alert throttling to help protect and optimize your risk investigation and review experience. This throttling guards against issues that might result in an overload of policy alerts, such as misconfigured data connectors or DLP policies. As a result, there might be a delay in displaying new alerts for a user.

## Alert status and severity

As alerts start showing up, you can review them and investigate each by clicking on it and analyzing the signals in the Alert details pane. Once you have analyzed an alert, you can assign it to one of the following statuses:

- **Confirmed.** Creates a case to further investigate the alert.
- **Dismissed.** Identifies it as a false positive. 
- **Needs review.** The alert requires further analysis to define an action.
- **Resolved.** The case to which this alert was assigned has been closed.

Alert risk scores are automatically calculated from several risk activity attributes that include:

- The type of risk activity.
- The number and frequency of the activity occurrence.
- The history of user risk activity.
- The addition of activity risks that may boost the seriousness of the activity.

The alert risk score drives the programmatic assignment of a risk severity level for each alert and cannot be customized. If alerts remain untriaged and risk activities continue to be added to the alert, the risk severity level can increase. Risk analysts and investigators can use the alert risk severity to help triage alerts in accordance to your organization's risk policies and standards.

The alert risk severity levels are:

- **High severity:** The activity and indicators for the alert pose significant risk. The associated risk activities are serious, repetitive, and correlate strongly to other significant risk factors.
- **Medium severity:** The activity and indicators for the alert pose a moderate risk. The associated risk activities are moderate, frequent, and have some correlation to other risk factors.
- **Low severity:** The activity and indicators for the alert pose a minor risk. The associated risk activities are minor, more infrequent, and do not correlate to other significant risk factors.

## Filtering and searching alerts

Depending on the number and type of active insider risk management policies in your organization, reviewing a large queue of alerts can be challenging. Using filters can help analysts and investigators sort alerts by several attributes. Selecting the **Filter** control on the **Alerts** dashboard lets you filter alerts by one or more of the following attributes:

- **Status:** Select one or more status values to filter the alert list. The options are **Confirmed**, **Dismissed**, **Needs review**, and **Resolved**.
- **Severity:** Select one or more alert risk severity levels to filter the alert list. The options are **High**, **Medium**, and **Low**.
- **Time detected:** Select the **start** and **end** dates for when the alert was created.
- **Policy:** Select one or more policies to filter the alerts generated by the selected policies.

To search the alert name for a specific word, select the **Search** control and type the word to search. The search results display any policy alert containing the word defined in the search.
