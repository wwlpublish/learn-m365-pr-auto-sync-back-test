Woodgrove has many different applications that it uses for different functions across the environment. Your manager has asked you to explain how your organization can ensure application functionality and compatibility with the update.

## Inputs

You’ll need to produce an application portfolio for Woodgrove. The portfolio lists the applications in your environment.  You’ll also need to classify the applications listed in the portfolio accordingly, as either critical, important, or not important. 
For Woodgrove, you would do this as shown below:

:::image type="content" source="../media/5-applications-classified.png" alt-text="Applications classified":::

## Decisions

Once you’ve classified the applications, you’ll need to make a couple of decisions.

**Define application deployment readiness criteria**

You’ll define how your organization should deal with issues that might arise for the applications you’ve classified. Your organization needs to ask how severe and impact it would be for Woodgrove if an app were to have issues during the deployment process? To do this, you’ll work with Operations and agree on how application failure should be handled based on whether an app has been classified as critical, important, or not important. For example, your organization could agree on the following:

:::image type="content" source="../media/5-severity-agreed.png" alt-text="Severity agreed":::

- **Severity 1**: Deployments must be stopped until issue has been resolved.
- **Severity 2**: Deployment is halted for any devices or users that are affected by the issue until it’s resolved. But deployment can continue for unaffected users and devices.
- **Severity 3**: Deployment can continue for affected devices, provided that there is a workaround guidance for affected users.
- **Severity 4**: Continue deployment to all devices 

The agreed severity mapping ensures you won’t have to work out how individual applications should be handled and prioritized once an importance level as been assigned to them.  For example, you would know that the deployment process should stop for some or all users if any issues arise for any critical application. Once the issues have been resolved, the deployment can continue.

## Tasks

Woodgrove needs to assign an Application Owner for each application. The Application Owner will be responsible for putting together a test plan for an application or applications. They also select user acceptance testers. The Application Owner verifies that the application works with the new update at the end of user acceptance testing. 

You’ll detail who is responsible for assigning an application owner, and who should be consulted. You’ll also detail who should be informed of the decision, like this:

| |End-user computing  |Application Developers  |Process Manager  |
|---------|---------|---------|---------|
|Assign application owner     |Responsible|Consulted|Informed|

## Outputs

You're now in a position to be able to create the following artefacts that you can use for the next phase in the workstream:


|Item  |Example format  |Description  |
|---------|---------|---------|
|Compatibility criteria     |Word Document|Detail Deployment readiness and deployment supportability.|
|Priority Application and Owner List     |-Spreadsheet<br/>-Desktop Analytics (recommended)|List and assign owners to:<br/>- Critical Applications<br/>- Important Applications<br/>- Not important Applications 
|
