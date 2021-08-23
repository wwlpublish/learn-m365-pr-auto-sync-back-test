

Network Planner is designed to assist the admin to determine and organize network requirements for connecting Microsoft Teams users across the whole organization. You can access the tool by going to **Microsoft Teams admin center** > **Planning** > **Network planner**. After providing network details and Teams usage, the Network Planner calculates the network requirements for deploying Teams and cloud voice across the organization’s physical locations.

:::image type="content" source="../media/network-planner.png" alt-text="Network planner":::

With Network Planner you can:

- Create representations of your organization using sites and Microsoft recommended personas (office workers, remote workers, and Teams room system devices).
- Generate reports and calculate bandwidth requirements for Teams usage

To use the Network Planner, you must have one of the following roles: 

- Global administrator
- Teams admin
- Teams communication administrator

## Create a custom persona

To create a custom persona in your network plan, do the following steps:

1. Sign into **Microsoft Teams admin center.**
2. Navigation to **Planning** > **Network Planner**.
3. On the Network Planner page, select the **Personas** section, review the default personas, and then select **Add persona** if you’d like to add a custom persona.
4. On the **Add persona** page, provide the persona name and description. Under the Permissions section, select from the following services: Audio, Video, Screen sharing, File sharing, Conference audio, Conference video, Conference screen sharing and PSTN.
5. Select **Apply**.

:::image type="content" source="../media/network-planner-add-persona.png" alt-text="A screenshot of creating custom personas":::

## Build your plan

To build your network plan, do the following steps:

1. Sign into **Microsoft Teams admin center**.
2. Navigation to **Planning** > **Network Planner**. 
3. On the **Network Planner** page, under **Network Plans** section, select **Add**. 
4. On the **Network Plan name** page, enter the name for the network plan (for example **NY Teams network plan**), a description, and select **Apply**.
5. The newly created network plan will appear under the **Network Plans** section. Select the plan you created.
6. On the plan page, for example **NY Teams network plan**, under **Network Sites** section, select **Add a network site.** 
7. On the **Add a network site** page, enter the following information and then select **Save**.

	- Name of the network site
	- Network site address
	- Network settings – IP address subnet and network range
	- Express route or WAN connection
	- Internet egress
	- Internet link capacity
	- PSTN egress (VoIP only or local).
	- an optional description. 

## Create a report

To create a report based on your network plan, do the following steps:

1. Sign into **Microsoft Teams admin center**.

2. From the left navigation pane, select **Planning,** and then select **Network Planner**.

3. On the **Network Planner** page, under **Network Plans** section, select your network plan (for example, **NY Teams network plan**).

4. On the plan page, select **Report**, and then select **Add report**.

5. On the **Add report** page, enter the report name, and in the **Calculation** section, choose the type of persona, such as Office Worker or Remote Worker and the number of each persona types.

6. Select **Generate report**.

7. On the report page, review the report including Type of service, and required bandwidth for different services, such as Audio, Video, Screenshare, Office 365 server traffic and PSTN.
:::image type="content" source="../media/network-planner-report-output.png" alt-text="A screenshot to run the report of network planner":::
