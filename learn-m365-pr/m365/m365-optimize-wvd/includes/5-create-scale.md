## Scaling plan

This module will explain what a scaling plan is and will walk you through how to create one in the Azure portal.

## What is a scaling plan and how does it work?

A scaling plan is an Azure Virtual Desktop object that acts as a container for your Autoscale schedules. Scaling plans are designed such that you can apply one to one or more pooled host pools and the associated schedules will take effect for all the assigned host pools. However, only one scaling plan can be assigned to a host pool. A scaling plan can be comprised of one or more schedules that contain the scaling configuration for the selected days of the week.

## Create scaling plan

To create a scaling plan:

1. Sign into the Azure portal at [https://portal.azure.com](https://portal.azure.com)
1. Go to **Azure Virtual Desktop** > **Scaling Plans**, then select **Create**.
1. In the Basics tab, look under Project details and select the name of the subscription you will assign the scaling plan to.
1. If you want to make a new resource group, select Create new. If you want to use an existing resource group, select its name from the drop-down menu.
1. Enter a name for the scaling plan into the Name field.
1. Optionally, you can also add a "friendly" name that will be displayed to your users and a description for your plan.
1. For Region, select a region for your scaling plan. The metadata for the object will be stored in the geography associated with the region. To learn more about regions, see Data locations.
1. For Time zone, select the time zone you'll use with your plan.
1. In Exclusion tags, enter tags for VMs you don't want to include in scaling operations. For example, you might want to use this functionality for maintenance. When you have set VMs on Drain mode use the tag so Autoscale doesn’t override drain mode.
1. Select Next, which should take you to the Schedules tab.

## Create a schedule for your scaling plan

This section will explain what a scaling plan schedule is and will walk you through how to create one in the Azure portal.

### What is a schedule and how does it work?

Schedules are Azure Virtual Desktop proxy resources for scaling plans that contain the information about the scaling configuration. In the schedule, you can configure the days it is applicable to and the start and end times. You can also configure the load balancing algorithm, capacity thresholds, and the minimum percentage of hosts for different points in the day, as well as your preferred ramp down strategy.

In each phase of the schedule, Autoscale only turns off VMs when a session host has no sessions active. The default values you'll see when you try to create a schedule are the suggested values for weekdays, but you can change them as needed.

### Create a schedule

1. In the **Schedules** tab, select **Add schedule**.
1. Enter a name for your schedule into the **Schedule name** field.
1. In the **Repeat on** field, select which days your schedule will repeat on.
1. In the **Ramp up** tab, fill out the following fields:

    - For **Start time**, select a time from the drop-down menu to start preparing VMs for peak business hours.

    - For **Load balancing algorithm**, we recommend selecting **breadth-first algorithm**. Breadth-first load balancing will distribute users across existing VMs to keep access times fast.
    >[!Note]
    >The load balancing preference you select here will override the one you selected for your original host pool settings.

    - For **Minimum percentage of session host VMs**, enter the amount of session host resources you want to use during ramp-up and peak hours. For example, if you choose **10%** and your host pool has 10 session hosts, Autoscale will keep one session host available for user connections at all times during ramp-up and peak hours.

    - For **Capacity threshold**, enter the percentage of host pool usage that will trigger the start of the ramp-up and peak phases. For example, if you choose **60%** for a host pool that can handle 100 sessions, Autoscale will only turn on additional hosts once the host pool goes over 60 sessions.

1. In the Peak hours tab, fill out the following fields:

    - For **Start time**, enter a start time for when your usage rate is highest during the day. Make sure the time is in the same time zone you specified for your scaling plan. This time is also the end time for your ramp-up phase.

    - For **Load balancing**, you can select either breadth-first or depth-first load balancing. Breadth-first load balancing distributes new user sessions across all available sessions in the host pool. Depth-first load balancing distributes new sessions to any available session host with the highest number of connections that hasn't reached its session limit yet. For more information about load-balancing types, see Configure the Azure Virtual Desktop load-balancing method.
    >[!Note]
    >You can't change the capacity threshold here. Instead, the setting you entered in Ramp-up will carry over to this setting.

1. For **Ramp-down**, you'll enter values into similar fields to **Ramp-up**, but this time it will be for when your host pool usage drops off. This will include the following fields:

    - Start time
    - Load-balancing algorithm
    - Minimum percentage of hosts (%)
    - Capacity threshold (%)
    - Force logoff users

    - Likewise, Off-peak hours works the same way as Peak hours:

    - Start time, which is also the end of the ramp-down period.
    - Load-balancing algorithm. We recommend choosing depth-first to gradually reduce the number of session hosts based on sessions on each VM.
    - Just like peak hours, you can't configure the capacity threshold here. Instead, the value you entered in Ramp-down will carry over.
