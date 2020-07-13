Privileged access management allows granular access control over privileged admin tasks in Microsoft 365. It can help protect your organization from breaches that use existing privileged admin accounts with standing access to sensitive data or access to critical configuration settings.

Enabling privileged access management in Microsoft 365 allows your organization to operate with **zero standing access**, this means that users who need privileged access, must request permissions for access, and once received it's just-in-time and just-enough access to perform the job at hand. Zero standing access provides a layer of defense against standing administrative access vulnerabilities.

Privileged access management requires users to request just-in-time access to complete elevated and privileged tasks through a highly scoped and time-bounded approval workflow.

At a high level, the steps to setup and use privileged access are:

1. Create an approvers group - Before you start using privileged access, determine who needs approval authority for incoming requests for access to elevated and privileged tasks. Any user who is part of the Approvers' group is able to approve access requests.
1. Enable privileged access - Privileged access must be explicitly enabled in Office 365 with the default approver group, including a set of system accounts that you want excluded from the privileged access management access control,
1. Create an access policy - Creating an approval policy allows you to define the specific approval requirements scoped at individual tasks.
1. Submit/approve privileged access requests - Once enabled, privileged access requires approvals for any task that has an associated approval policy defined. For tasks included in an approval policy, users must request and be granted access approval to have permissions necessary to execute the task.

After approval is granted, the requesting user can execute the intended task and privileged access will authorize and execute the task on behalf of the user. The approval remains valid for the requested duration (default duration is 4 hours), during which the requester can execute the intended task multiple times. All such executions are logged and made available for security and compliance auditing.

Watch this 6-minute video to get a tour of Privileged Access management:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4xqtC]

In the video, you watched a tour of scoped, just-in-time controls for granting admin role and task privileges.
