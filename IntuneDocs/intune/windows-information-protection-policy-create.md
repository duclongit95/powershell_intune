---
# required metadata

title: Create and deploy Windows Information Protection (WIP) app protection policy
titlesuffix: Microsoft Intune
description: Create and deploy Windows Information Protection (WIP) app protection policy with Microsoft Intune
keywords:
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Create and deploy Windows Information Protection (WIP) app protection policy with Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

You can use app protection policies with Windows 10 apps to protect apps without device enrollment.

## Before you begin

You must understand a few concepts when adding a WIP policy:

### List of allowed and exempt apps

-   **Protected apps:** These apps are the apps that need to adhere to this policy.

-   **Exempt apps:** These apps are exempt from this policy and can access corporate data without restrictions.

### Types of apps

-   **Recommended apps:** A pre-populated list of (mostly Microsoft Office) apps that allow you easily import into policy.
-   **Store apps:** You can add any app from the Windows store to the policy.
-   **Windows desktop apps:** You can add any traditional Windows desktop apps to the policy (for example, .exe, .dll)

## Prerequisites

You must configure the MAM provider before you can create a WIP app protection policy. Learn more about [how to configure your MAM provider with Intune](app-protection-policies-configure-windows-10.md).

Additionally, you need to have the following license and update:

-   [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) license
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP does not support multi-identity, only one managed identity can exist at a time.

## To add a WIP app protection policy

After you set up Intune in your organization, you can create a WIP-specific policy.

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Choose **All Services** > **Intune**.
3. Select **Mobile apps** on the **Microsoft Intune** blade.
4. Select **App protection policies** on the **Mobile apps** blade.
5. Select **Add a policy** to display the **Add a policy** blade.
6. Add the following values:
    - **Name:** Type a name (required) for your new policy.
    - **Description:** (Optional) Type a description.
    - **Platform:** Choose **Windows 10** as the supported platform for your app protection policy.
    - **Enrollment state:** Choose **Without enrollment** as the enrollment state for your policy.
7.  Choose **Create**. The policy is created and appears in the table on the **App protection policies** blade.

## To add recommended apps to your protected apps list

1. Select **Mobile apps** on the **Microsoft Intune** blade.
2. Select **App protection policies** on the **Mobile apps** blade.
3. On the **App protection policies** blade, choose the policy you want to modify. The **Intune App Protection** blade is displayed.
4. Choose **Protected apps** from the **Intune App Protection** blade. The **Protected apps** blade opens showing you all apps that are already included in the list for this app protection policy.
5. Select **Add apps**. The **Add apps** information shows you a filtered list of apps. The list at the top of the blade allows you to change the list filter.
6. Select each app that you want to allow access your corporate data.
7. Click **OK**. The **Protected apps** blade is updated showing all selected apps.
8. Click **Save**.

## Add a Store app to your protected apps list

**To add a Store app**
1. Select **Mobile apps** on the **Microsoft Intune** blade.
2. Select **App protection policies** on the **Mobile apps** blade.
3. On the **App protection policies** blade, choose the policy you want to modify. The **Intune App Protection** blade is displayed.
4. Choose **Protected apps** from the **Intune App Protection** blade. The **Protected apps** blade opens showing you all apps that are already included in the list for this app protection policy.
5. Select **Add apps**. The **Add apps** information shows you a filtered list of apps. The list at the top of the blade allows you to change the list filter.
6. From the list, select **Store apps**.
7. Enter values for **Name**, **Pubisher**, **Product Name**, and **Action**. Be sure to set the **Action** value to **Allow**, so that the app will have access to your corporate data.
9. Click **OK**. The **Protected apps** blade is updated showing all selected apps.
10. Click **Save**.

## Add a desktop app to your protected apps list

**To add a desktop app**
1. Select **Mobile apps** on the **Microsoft Intune** blade.
2. Select **App protection policies** on the **Mobile apps** blade.
3. On the **App protection policies** blade, choose the policy you want to modify. The **Intune App Protection** blade is displayed.
4. Choose **Protected apps** from the **Intune App Protection** blade. The **Protected apps** blade opens showing you all apps that are already included in the list for this app protection policy.
5. Select **Add apps**. The **Add apps** information shows you a filtered list of apps. The list at the top of the blade allows you to change the list filter.
6. From the list, select **Desktop apps**.
7. Enter values for **Name**, **Pubisher**, **Product Name**, **File**, **Min Version**, **Max Version**, and **Action**. Be sure to set the **Action** value to **Allow**, so that the app will have access to your corporate data.
9. Click **OK**. The **Protected apps** blade is updated showing all selected apps.
10. Click **Save**.

## WIP Learning
After you add the apps you want to protect with WIP, you need to apply a protection mode by using **WIP Learning**.

### Before you begin

WIP Learning is a report that allows you to monitor your WIP-enabled apps and WIP-unknown apps. The unknown apps are the ones not deployed by your organization???s IT department. You can export these apps from the report and add them to your WIP policies to avoid productivity disruption before they enforce WIP in ???Block??? mode.

<!-- 1631908 -->
In addition to viewing information about WIP-enabled apps, you can view a summary of the devices that have shared work data with websites. With this information, you can determine which websites should be added to group and user WIP policies. The summary shows which website URLs are accessed by WIP-enabled apps.

When working with WIP-enabled apps and WIP-unknown apps, we recommend that you start with **Silent** or **Allow Overrides** while verifying with a small group that you have the right apps on your protected apps list. After you're done, you can change to your final enforcement policy, **Block**.

### What are the protection modes?

#### Block
WIP looks for inappropriate data sharing practices and stops the user from completing the action. This can include sharing info across non-corporate-protected apps, and sharing corporate data between other people and devices outside of your organization.

#### Allow Overrides
WIP looks for inappropriate data sharing, warning users when they do something deemed potentially unsafe. However, this mode lets the user override the policy and share the data, logging the action to your audit log.

#### Silent
WIP runs silently, logging inappropriate data sharing, without blocking anything that would have been prompted for employee interaction while in Allow Override mode. Unallowed actions, like apps inappropriately trying to access a network resource or WIP-protected data, are still stopped.

#### Off (not recommended)
WIP is turned off and doesn't help to protect or audit your data.

After you turn off WIP, an attempt is made to decrypt any WIP-tagged files on the locally attached drives. Note that previous decryption and policy info isn???t automatically reapplied if you turn WIP protection back on.

### Add a protection mode

1.  From the **App policy** blade, choose the name of your policy, then choose **Required settings**.

	![Learning Mode screen-shot](./media/learning-mode-sc1.png)

1.  Select a setting and then choose **Save**.

### Use WIP Learning

1. Open the [Azure portal](https://portal.azure.com). Choose **All services**. Type **Intune** in the text box filter.

3. Choose **Intune** > **Mobile Apps**.

4. Choose **App protection status** > **Reports** > **Windows Information Protection learning**.  

    Once you have the apps showing up in the WIP Learning logging report, you can add them to your app protection policies.

## Allow Windows Search Indexer to search encrypted items
Allows or disallows the indexing of items. This switch is for the Windows Search Indexer, which controls whether it indexes items that are encrypted, such as the Windows Information Protection (WIP) protected files.

This app protection policy option is in the **Advanced settings** of the Windows Information Protection policy. The app protection policy must be set to the *Windows 10* platform and the app policy **Enrollment state** must be set to **With enrollment**.

When the policy is enabled, WIP protected items are indexed and the metadata about them are stored in an unencrypted location. The metadata includes things like file path and date modified.

When the policy is disabled, the WIP protected items are not indexed and do not show up in the results in Cortana or file explorer. There may also be a performance impact on photos and Groove apps if there are many WIP protected media files on the device.

## Add encrypted file extensions

In addition to setting the **Allow Windows Search Indexer to search encrypted items** option, you can specify a list of file extensions. Files with these extensions are encrypted when copying from a Server Message Block (SMB) share within the corporate boundary as defined in the network location list. When this policy is not specified, the existing auto-encryption behavior is applied. When this policy is configured, only files with the extensions in the list will be encrypted.

## Deploy your WIP app protection policy

> [!IMPORTANT]
> This information applies for WIP without device enrollment.

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

After you created your WIP app protection policy, you need to deploy it to your organization using MAM.

1.  On the **App policy** blade, choose your newly created app protection policy, choose **User groups** > **Add user group**.

	A list of user groups, made up of all the security groups in your Azure Active Directory, opens in the **Add user group** blade.

2.  Choose the group you want your policy to apply to, then choose **Select** to deploy the policy.

## Next steps

Learn more about Windows Information Protection, see [Protect your enterprise data using Windows Information Protection (WIP)](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip).
