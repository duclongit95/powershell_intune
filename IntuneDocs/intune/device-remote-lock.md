---
# required metadata

title: Lock devices with Microsoft Intune - Azure | Microsoft Docs
description: Use the Remote lock action in Microsoft Intune to lock a device that is protected by a PIN or password. 
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: ilwu
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Remotely lock devices with Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

The **Remote lock** device action locks the device. To unlock the device, the device owner enters their passcode. You can remotely lock devices that have a PIN or password set. Devices that don't have a PIN or password can't be remotely locked.

## Supported platforms

**Remote lock** is supported for the following platforms:

- Android
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 and later

**Remote lock** is *not* supported for:
- Windows 10 desktop

> [!NOTE]
> For macOS devices, you set a 6-digit recovery PIN. When the device is locked, the **Device overview** displays the PIN until another device action is sent.

## Remote lock a device

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **All services**, filter on **Intune**, and then select **Microsoft Intune**.
3. Select **Devices** > **All devices**.
4. In the list of devices, select a device, and then select the **Remote lock** action.

## Next steps

- To see the status of this action, select **Microsoft Intune** > **Devices** > **Device actions**. 
- For more actions that can help you manage your devices, see [Available actions](device-management.md).
