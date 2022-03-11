Woodgrove has many different applications that it uses for different functions across the environment. Your manager has asked you to explain how your organization can ensure application functionality and compatibility with the update.

## Inputs

You'll need to produce an application portfolio for Woodgrove. The portfolio lists the applications in your environment.  You'll also need to classify the applications listed in the portfolio accordingly, as either critical, important, or not important.
For Woodgrove, you would do it like this:

|Application  |Classification  |
|---------|---------|
|Credit processing application     |Critical|
|Frontline customer service application     |Critical |
|PDF viewer application     |Important|
|Image processing application     | Not important|

## Decisions

Once you've classified the applications, you'll need to make a couple of decisions. You'll define application deployment readiness criteria. You'll define how your organization should deal with issues that might arise for the applications you've classified. Your organization needs to ask how severe and impact would it be for Woodgrove if an app were to have issues during the deployment process? To do this, you'll work with operations and agree on how application failure should be handled based on whether an app has been classified as critical, important, or not important. For example, your organization could agree on the following:

|Application classification  |Severity  |Priority  |Examples of impact  |
|---------|---------|---------|---------|
|Critical|Severity 1 or 2|Priority 1 or 2|- Loss of revenue <br/> - Work stoppage|
|Important|Severity 3 or 4|Priority 3 or 4|- User experience impacted<br/> - Loss of productivity|
|Not important|Severity 4|Priority 4|- Minimal impact on user's productivity<br/> - No impact on the business|

- **Severity 1**: Deployments must be stopped until issue has been resolved.
- **Severity 2**: Deployment is halted for any devices or users that are affected by the issue until it's resolved. But deployment can continue for unaffected users and devices.
- **Severity 3**: Deployment can continue for affected devices, provided that there is a workaround guidance for affected users.
- **Severity 4**: Continue deployment to all devices.

The agreed severity mapping ensures you won't have to work out how individual applications should be handled and prioritized once an importance level has been assigned to them.  For example, you would know that the deployment process should stop for some or all users if any issues arise for any critical application. Once the issues have been resolved, the deployment can continue.

## Tasks

Woodgrove needs to assign an application owner for each application. The application owner will be responsible for putting together a test plan for an application or applications. They also select user acceptance testers. The application owner verifies that the application works with the new update at the end of user acceptance testing.

You'll detail who is responsible for assigning an application owner, and who should be consulted. You'll also detail who should be informed of the decision, like this:

| |End-user computing  |Application developers  |Process manager  |
|---------|---------|---------|---------|
|**Assign application owner**|Responsible|Consulted|Informed|

## Outputs

You're now in a position to be able to create the following artifacts that you can use for the next phase in the workstream:

|Item  |Example format  |Description  |
|---------|---------|---------|
|Compatibility criteria     |Word document|Detail deployment readiness and deployment supportability|
|Priority application and owner List|-Spreadsheet<br/>-Desktop Analytics (recommended)|List and assign owners to:<br/>- Critical applications<br/>- Important applications<br/>- Not important applications|
