---
# required metadata

title: Configure device restriction settings in Microsoft Intune - Azure | Microsoft Docs
description: Add a device profile to restrict features on Android, macOS, iOS, Windows Phone, and Windows 10 devices in Microsoft Intune
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Configure device restriction settings in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Device restrictions let you control a wide range of settings and features you manage across a range of categories such as:
- Security
- Browser
- Hardware
- Data sharing settings

For example, you can create a device restriction profile that prevents users of iOS devices from accessing the device camera.

Learn device restriction profile basics, and then read further articles for each platform to learn about device specifics.

## Create a device profile containing device restriction settings

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **All services**, filter on **Intune**, and select **Microsoft Intune**.
3. Select **Device configuration** > **Profiles** > **Create profile**.
4. Enter a **Name** and **Description** for the device restriction profile.
5. From the **Platform** drop-down list, select the device platform to which you want to apply custom settings. Currently, you can choose one of the following platforms for device restriction settings:
	- **Android**
	- **iOS**
	- **macOS**
	- **Windows Phone 8.1**
	- **Windows 8.1 and later**
	- **Windows 10 and later**
6. From the **Profile type** drop-down list, choose **Device restrictions**. If you want to create a device restrictions profile for Windows 10 Team devices like a Surface Hub, choose **Device restrictions (Windows 10 Team)**.
7. Depending on the platform you chose, the settings you can configure are different. Go to one of the following topics for detailed settings for each platform:
	- [Android settings](device-restrictions-android.md)
	- [iOS settings](device-restrictions-ios.md)
	- [macOS settings](device-restrictions-macos.md)
	- [Windows Phone 8.1 settings](device-restrictions-windows-phone-8-1.md)
	- [Windows 8.1](device-restrictions-windows-8-1.md)
	- [Windows 10 settings](device-restrictions-windows-10.md)
	- [Windows 10 Team settings](device-restrictions-windows-10-teams.md)
	- [Windows Holographic for Business settings](device-restrictions-windows-holographic.md)
	- [Android for Work settings](device-restrictions-android-for-work.md)
8. When you're done, go back to the **Create profile** page, and click **Create**.

The profile is created and appears on the profiles list page.
If you want to go ahead and assign this profile to groups, see [How to assign device profiles](device-profile-assign.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
