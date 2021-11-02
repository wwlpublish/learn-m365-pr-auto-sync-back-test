Some users in your organization might find it difficult to focus during video meetings and calls because of movement, light, and other distractions in participants' backgrounds. Whether users are neurodiverse and prefer to control distractions in their environment, or are hard of hearing and need to lipread to understand what other participants are saying, you need to ensure these users can control distractions and participate fully.

:::image type="content" source="../media/background-image-add-image.png" alt-text="Screenshot showing how you can add a background image through Teams.":::

## Enable background effects

Microsoft Teams makes it possible for users to activate background effects for videos during meetings and calls. Background effects can be fun for most users. But for some users, they're critical to making calls and meetings more inclusive.

Background effects can help people focus on the speaker rather than on the speaker's background. Microsoft Teams provides a library of backgrounds, and users can also upload their own. Users can use simple backgrounds to help them focus on the speaker, or they can use any of those already included in Microsoft Teams.

### Enable background blur

Background blur helps provide improved visibility and focus when in meetings or calls. For some users, background blur allows users to blur their own background in meetings and calls but keep themselves in focus.

:::image type="content" source="../media/enable-background-blur.png" alt-text="Screenshot showing background blur applied to a video call.":::

As the admin, you can enable Background blur by configuring a meeting policy setting in PowerShell.  For example, to enable Background blur for all users along with the ability to use default backgrounds, you can update the global policy by using the **Set-CsTeamsMeetingPolicy** cmdlet, and set the *VideoFiltersMode* parameter to **BlurandDefaultBackgrounds**:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -VideoFiltersMode BlurAndDefaultBackgrounds
```

You can set the *VideoFiltersMode* parameter to any of the following values to enable or disable background blur:

| Value                     | Description                                              |
| ----------------------------- | ------------------------------------------------------------ |
| **NoFilters**                 | Disable all background effects.                              |
| **BlurOnly**                  | Users can enable background blur only.                       |
| **BlurandDefaultBackgrounds** | Users can blur their video background or choose from default images to use as background. |
| **AllFilters**                | Users can blur their video background or choose from default images to  use as a background, or they can upload images to use as their background. |

After you've enabled Background blur for your users, they can use it by selecting **Apply background effects** during meetings or calls:

:::image type="content" source="../media/teams-apply-background-effects.png" alt-text="Screenshot showing the Teams menu where you can apply background effects.":::

The blur effect is then available in the list of background effects that appear:

:::image type="content" source="../media/teams-select-blur-effect-background.png" alt-text="Screenshot showing the Teams menu with the blur background selected.":::

> [!NOTE]
> In the **Learn more** section of this unit, you can find an article about empathy and innovation that also explains how background blur was initially developed by a Microsoft engineer who is deaf and uses lip reading!

## Allow users to turn off incoming video

Some users who are neurodiverse may find video feeds and varying personal background choices distracting. Your users can choose to turn off incoming video and create a personalized and simpler meeting view that they control.

When a user chooses to turn off incoming video, other users will still be able to view the video feeds of the meeting participants. Only the user who selected to turn off incoming video will no longer see incoming video.

:::image type="content" source="../media/teams-turn-off-incoming-video.png" alt-text="Screenshot showing the Teams menu where you can turn off incoming video.":::

## Enable noise suppression

Background noise can happen for many reasons, whether it's ambient noise from a user's environment, loud typing in an office space, or noises from the outside like construction work. Background noise can be distracting and make it difficult for some users to focus on and understand others.  Your users can enable noise suppression in their Teams Settings.

To enable noise suppression for all calls, in Teams Settings select **Devices** and then choose a suppression level from the **Noise suppression** drop-down list:

- **Auto** Teams changes the amount of suppression it applies depending on the amount of noise it detects. This is the default setting.
- **High** Teams removes all noise other than speech. This setting requires intensive use of processing power and a processor that support Advanced Vector Extensions 2. You can't use this setting if the meeting is being recorded or if live captions are switched on.
- **Low** Teams surpresses low levels of persistent background noise.
- **None** Teams doesn't surpress any noise.

:::image type="content" source="../media/teams-settings-noise-suppression.png" alt-text="Screenshot showing the noise suppression setting in Teams.":::

## Learn more

- [Empathy and innovation: How Microsoft's cultural shift is leading to new product development](https://news.microsoft.com/innovation-stories/empathy-innovation-accessibility/)
