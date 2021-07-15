Before you can migrate to Microsoft Teams Direct Routing from your previous telephony system, you must carefully consider some key aspects of the new system, such as the location of the Session Border Controller (SBC).

Suppose that you are a Teams administrator and you beginning the planning phase for implementing Direct Routing. You need to determine where to place the Session Border Controller and how to prepare to cut over to the new system.

Here you will learn where to place the Session Border Controller and prepare for the cut over.

## Migration concepts

You need to consider the source of the migration. Are you migrating to Teams Direct Routing from a legacy private branch exchange (PBX) system, like a Cisco call manager or some other third-party PBX platform? Or are you migrating from an environment such as a Skype for Business Server platform that could be using Enterprise Voice? The reason that's important is that, based on the source of the migration, there's a different set of steps that you have to adapt to.

You also need to understand how to prepare for the cut over. The cut over to Teams with Direct Routing involves enabling the user for Teams and its various features, like Phone System and Direct Routing. But you also need to make some reconfiguration changes to the inbound routing of the particular phone number. This action ensures that the number reaches the correct destination.

## Topology

The placement of your SBCs is important. Consider the following diagram:

:::image type="content" border="false" source="../media/2-topology-diagram.png" alt-text="Topology Diagram":::

On the left side, you have the telephone company connection in the form of a public switched telephone network (PSTN) coming into an SBC. Calls can then be routed to, for example, a Skype for Business Server, shown here as the Mediation Server. Or you could have calls routed to a legacy PBX like a Cisco or Avaya platform. In this unit, we'll be looking at Direct Routing as shown in the diagram above.

## Session Border Controller

To get calls routed to the correct infrastructure, the SBC takes all incoming calls and, based on internal logic, routes them to where the user is located. The user could be on Teams, Skype for Business, or a legacy PBX. The logic in the SBC routes the incoming call to the right location for that user.

You want the SBC near the front of the line, ready to use the telco-provided connection as shown in the diagram above. The SBC can see all of the possible places to route the call, to a legacy PBX, Skype for Business, or Teams.

## Cut over

The cut over to Teams with Direct Routing involves enabling the user for Teams and its various features like Phone System and Direct Routing. But you also need to make some configuration changes to the inbound routing of the particular phone number. This action ensures that it's no longer being passed over to the old PBX or the old Skype for Business environment, but to the new Teams environment.
