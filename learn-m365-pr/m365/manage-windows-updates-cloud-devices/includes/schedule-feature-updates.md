In the last unit, you learned how to deploy feature updates without specifying a set schedule. As the admin for your organization, you know that following a schedule is a good way to maintain update consistency across devices. So, you want to learn how to schedule feature updates. In this unit, you’ll learn how to use the Microsoft Graph PowerShell SDK to schedule feature updates.

When you deploy an update, you can schedule when your target devices receive the update. You can also schedule a deployment to gradually roll out to groups of devices. You can control the total time it takes to deploy the update by setting an offering rate or an end date that you specify. You can think of a gradual rollout as similar to a recurring calendar event series.

## Create a scheduled deployment

Suppose you need to schedule deployments to groups of devices belonging to different teams in your organization. Both teams require different deployment schedules because of the nature of their work. Team one wants you to deploy updates to their devices at a specific date and time. The other team wants you to deploy updates to their devices gradually over time. To meet the requirements of both teams, you’ll do the following:

### Deploy at a specific date and time

Let’s say team one has asked if you can deploy feature update 21H1 on 14 September at 17:00 PM.  You’ll create a deployment that will meet their needs. To deploy a feature update at a specific date and time, you’ll use the **New-MgWindowsUpdatesDeployment** PowerShell command. To specify your scheduling details, you’ll use the **-Settings** parameter. The final command you’ll run will look like this:

```PowerShell
New-MgWindowsUpdatesDeployment -Content @{
  "@odata.type" = "#microsoft.graph.windowsUpdates.featureUpdateReference";
  "version"= "21H1"
} -Settings @{
  "rollout" = @{    
    "startDateTime" = [DateTime]"2021-14-09T17:00:00Z"
} 
  }
```

Let’s clarify what’s happening here. You use the **New-MgWindowsUpdateDeployment** command, just like when you created a deployment for a feature update that wasn’t scheduled. But now, you’ll use the **-Settings** parameter, to provide a hashtable (object) using **@{}** for your scheduling settings. You then use the **rollout** property in this object to specify your  rollout details. This rollout object contains a **startDateTime** property that you use to provide the start date and time you want the update to be scheduled. In this case, you specify the date and time as 14 September 2021 at 17:00 PM.

### Deploy gradually over time

For team two, you’ll use the **New-MgWindowsUpdatesDeployment** PowerShell command again. But this time, you’ll configure it to deploy the update gradually. To do this, you use the **rollout** property to:

- Specify how many devices you want to deploy to at a time (using a **devicesPerOffer** property)
- Specify the duration between offers (using a **durationBetweenOffer** property)

Let’s say the team has asked you to only deploy to 100 devices per day. This means you’ll configure your deployment accordingly by running the following:

```PowerShell
New-MgWindowsUpdatesDeployment -Content @{
  "@odata.type" = "#microsoft.graph.windowsUpdates.featureUpdateReference";
  "version"= "21H1"
} -Settings @{
  "rollout" = @{
    "devicesPerOffer" = 100;
    "durationBetweenOffers" = "P1D"
    } 
  }
```

Now suppose there’s another team that has seen how well deployments are going for the previous teams and wants your help. This specific team has business policies, which mean that they can only afford to have one device updated at a time. And they need all devices to be updated by end of the year.  To help them, you’ll need to deploy to one device per day until a specific date and time. So how will you do this? Well, you’ll run the following command:

```PowerShell
New-MgWindowsUpdatesDeployment -Content @{
  "@odata.type" = "#microsoft.graph.windowsUpdates.featureUpdateReference";
  "version"= "21H1"
} -Settings @{
  "rollout" = @{
"startDateTime" = [DateTime]"2021-14-09T17:00:00Z"
  "endDateTime" = [DateTime]"2021-12-31T17:00:00Z"
    "durationBetweenOffers" = "P1D"
    } 
  }
```

Here, you use:

- The **startDateTime** property to set a date and time to begin to offer the update to devices. This can be a date you agree with the team. For this scenario, the team wants deployments to start on the 14 September, so you specify this date.
- The **durationBetweenOffers** property to specify how long to wait between offers. In this case, it has to be one day.
- The **endDateTime** property to set the date and time by which all devices should be offered the update. The team needs this by the end of the year, so you’ll set the date to the last day of the year.
