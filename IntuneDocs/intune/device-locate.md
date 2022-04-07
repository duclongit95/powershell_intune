---
# required metadata

title: Find lost iOS devices with Microsoft Intune - Azure | Microsoft Docs
description: Locate lost or stolen iOS devices by using the locate device feature in Microsoft Intune. Get details on security and privacy information when using the locate device action.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/21/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: ilwu
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Locate lost or stolen iOS devices with Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

To get the location of a lost or stolen iOS device on a map, use the **Locate device** action. The device must be a corporate-owned iOS device, enrolled through the device enrollment program, and be in supervised mode. Before you use this action, be sure the device is in [lost mode](device-lost-mode.md).

## Supported platforms

- iOS 9.3 and later

This feature is not supported for the following systems: 
- Windows
- Windows Phone
- macOS
- Android

## Locate a lost or stolen device

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **All services**, filter on **Intune**, and select **Microsoft Intune**.
3. Select **Devices**, and then select **All devices**.
4. From the list of devices you manage, choose an iOS device, and choose **...More**. Then choose the **Locate device** remote action.
5. After the device is located, its location is shown in **Locate device**.
	![Screenshot of Locate device using Intune in Azure](./media/locate-device.png)

>[!NOTE]
>For privacy reasons, the distance you can zoom into the map is limited to a 300 meter radius.

## Activate lost mode sound alert on an iOS device

If someone has lost their iOS 9.3 or later device, you can remotely trigger the device to play an alert sound so the user can find it. The device must be in [lost mode](device-lost-mode.md).

In the [Intune in the Azure portal](https://aka.ms/intuneportal), choose **Devices** > **All devices** > select an iOS device > **Overview** > **More** > **Play Lost mode sound (supervise only)**.

The sound will continue to play until the user disables the sound on the device or the device is removed from lost mode.


## Security and privacy information for lost mode and locate device actions
- No device location information is sent to Intune until you turn on this action.
- When you use the locate device action, the latitude and longitude coordinates of the device can be retrieved by using the Graph API.
- The data is stored for 24 hours, then removed. You cannot manually remove the location data.
- Location data is encrypted, both while stored and while being transmitted.
- When you configure lost mode, you can customize a message that appears on the lock screen. In this message, to help the person that finds the device, be sure to include specific details to return the lost device.

## Next steps

To see the status of enabling locate device, open **Devices**, and select **Device actions**.
