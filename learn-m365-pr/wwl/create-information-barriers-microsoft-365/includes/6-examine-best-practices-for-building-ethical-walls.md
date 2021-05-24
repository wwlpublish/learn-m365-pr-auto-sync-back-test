The following chart identifies key best practices that should be considered before implementing transport rules to impose ethical walls.

:::row:::
  :::column:::
    

**Best practices**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Beware of the transport restrictions


  :::column-end:::
  :::column:::
    

The message must not be subject to an administrator-configured transport restriction that prevents delivery of the message. Transport restrictions are global restrictions such as mail size limits and recipient limits. If a transport restriction prevents delivery of a message, the Transport Rules agent can't act on that message.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Define an appropriate scope


  :::column-end:::
  :::column:::
    

Ethical walls can block all messages if you don't define an appropriate scope. When you create a transport rule to enforce an ethical wall, you must specify conditions to define which recipients and senders to prohibit from sending messages to each other. If you don't specify any conditions, you must specify exceptions to narrow the scope of the transport rule. If you don't specify conditions or exceptions, the transport rule will block all messages sent to or from recipients or senders in your organization.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Test transport rules in a test environment first


  :::column-end:::
  :::column:::
    

Before you modify transport rules or create new transport rules in your production environment, it's recommended that you use a test environment to ensure that the modifications or new rules operate as intended.


  :::column-end:::
:::row-end:::


As previously mentioned, using transport rules to implement ethical walls can prevent email between the affected parties. However, Exchange can't prevent individuals from using other methods of communication.

> [!IMPORTANT]
> Consider implementing Exchange transport rules as part of an overall suite of tools or processes that should be deployed throughout your organization. These rules will help enforce a more far-reaching ethical wall policy.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”