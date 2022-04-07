---
# required metadata

title: Remove a user from an iOS device with Microsoft Intune 
titlesuffix:
description: Learn how to remove a user from a shared iOS device with Intune.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: ilwu
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Remove a user from a shared iOS device


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

The **Remove user** action deletes a user that you select from the local cache on a shared iPad device. The iPad device must be set up to manage the iOS Classroom app by using an [iOS education profile](education-settings-configure-ios.md). 

## Supported platforms

- Windows - Not supported
- Windows Phone - Not supported
- iOS - Supported on iOS 9.3 and later (shared iPad devices only)
- macOS - Not supported
- Android - Not supported

## Remove a user

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **All services** > **Intune**. Intune is located in the **Monitoring + Management** section.
3. In the **Intune** pane, select **Devices**.
4. In the **Devices** pane, select **All devices**.
5. In the list of devices that you manage, select an iOS device.
6. In the pane for the device, select **Users**.
7. In the list, right-click the user that you want to remove, and then select **Remove user**.

## Next steps

- To see the status of the **Remove user** action, select **Devices** > **Device actions**.
