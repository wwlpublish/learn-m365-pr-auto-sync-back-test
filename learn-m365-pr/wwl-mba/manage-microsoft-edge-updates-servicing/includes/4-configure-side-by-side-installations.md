
While most users will only need a single installation of Microsoft Edge, there are some instances such as testing and validating capabilities, that require multiple versions installed side-by-side. 

> [!IMPORTANT]
> Running Microsoft Edge Legacy side-by-side with the new version of Microsoft Edge is not recommended for use in production. This configuration should only be used in specific cases where testing with both browser versions is required.
>
> The Microsoft Edge Legacy desktop app will reach end of support on March 9, 2021 in favor of the new Microsoft Edge. This means that Microsoft Edge Legacy will not receive security updates after that date. This change is applicable to all experiences that run in the Microsoft Edge Legacy desktop app.
>
> [Learn more](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

Watch the video below for a brief overview of Microsoft Edge side-by-side installations.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4F999]

### Side-by-side experience with Microsoft Edge Stable Channel and Microsoft Edge Legacy

Installing the Stable Channel of the next version of Microsoft Edge at the system-level will cause the current version (Microsoft Edge Legacy) to be hidden. If you want to let your users see both versions of Microsoft Edge side by side in Windows, you can enable this experience by setting the Allow Microsoft Edge Side by Side browser experience group policy to Enabled.

To do this, follow these steps:

1. Install the Policy Definitions from [Microsoft Edge for Business](https://aka.ms/edgeenterprise).

    - Pick the **CHANNEL/BUILD** and **PLATFORM** you want to use, and then choose **GET POLICY FILES**.
    - Extract the zipped files.
    - Copy msedge.admx and msedgeupdate.admx to the 'C:\Windows\PolicyDefinitions' directory.
    - Copy msedge.adml and msedgeupdate.adml to the 'C:\Windows\PolicyDefinitions\\[APPROPRIATE LANGUAGE/LOCALE]' directory.

2. Open the Group Policy Editor (gpedit.msc).

3. Under Computer Configuration, go to *Administrative Templates &gt; Microsoft Edge Update &gt; Applications*.

    > [!NOTE]
    > If you don't see the Microsoft Edge Update folder, verify that step 1 was completed correctly.

4. Under Applications, double-click Allow Microsoft Edge Side by Side browser experience.

    > [!NOTE]
    > By default, this group policy is set to "Not configured", which results in Microsoft Edge Legacy being hidden when the new version of Microsoft Edge is installed.

5. Select **Enabled** and then select **OK**.

Setting this policy will set the following Registry Key to '00000001':

- Key: 'Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\EdgeUpdate'
- Value Name: 'Allowsxs'
- Value Type: 'REG_DWORD'

For more information, see:

- [Access Microsoft Edge Legacy after installing the new version of Microsoft Edge](/learn/modules/manage-microsoft-edge-updates-servicing/)
- [Microsoft Edge - Update policies - Allowsxs](/deployedge/microsoft-edge-update-policies#allowsxs)
