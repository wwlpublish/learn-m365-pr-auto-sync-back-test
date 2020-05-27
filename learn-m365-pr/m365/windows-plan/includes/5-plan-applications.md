Woodgrove has many applications that it uses for different functions across the environment. Your manager wants you to explain how the organization can ensure application functionality and compatibility with the update.

## Inputs

You’ll need to produce an application portfolio for Woodgrove. The portfolio lists the applications in your environment. You’ll also need to classify the applications listed in the portfolio as critical, important, or not important.

For Woodgrove, you would produce the portfolio in the following way:

:::image type="content" border= "false" source="../media/5-applications-classified.png" alt-text="Applications example":::



## Decisions

After you’ve classified the applications, you’ll need to make a couple of decisions.

**Define application deployment readiness criteria**

You’ll define how your organization should deal with issues that might arise for the applications you’ve classified.  Your organization needs to ask how severe an impact it would be if an app had issues during the deployment process. You’ll work with Operations and agree on how application failure should be handled, based on whether an app has been classified as critical, important, or not important.

For example, your organization could agree on the following procedures:

:::image type="content" border= "false" source="../media/5-severity-agreed.png" alt-text="Severity agreed":::

- **Severity 1**: Deployments must be stopped until the issue has been resolved.
- **Severity 2**: Deployment is halted for any devices or users affected by the issue until it’s resolved. But deployment can continue for unaffected users and devices.
- **Severity 3**: Deployment can continue for affected devices, providing there's workaround guidance for affected users.
- **Severity 4**: Continue deployment to all devices. 


The agreed severity mapping ensures you won’t have to work out how individual applications should be handled and prioritized when an importance level has been assigned to them.  For example, you would know that the deployment process should stop for some or all users if issues arise for any critical application. When the issues have been resolved, the deployment can continue.

## Tasks

Woodgrove needs to assign an Application Owner for each application. The Application Owner will be responsible for putting together a test plan for an application or applications. The Application Owner also selects user acceptance testers, and verifies that the application works with the new update at the end of the testing process.

You’ll detail who is responsible for assigning an Application Owner, and who should be consulted. You’ll also specify who should be informed of the decision, like this:

:::image type="content" border= "false" source="../media/5-assign-application-owner.png" alt-text="Application owner assigned":::

## Outputs

You're now in a position to create the following artifacts that you can use for the next phase in the workstream:

:::image type="content" border= "false" source="../media/5-outputs.png" alt-text="Outputs":::