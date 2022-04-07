---
# required metadata

title: Erase a macOS device
titleSuffix: Microsoft Intune
description: Learn how to erase all data, including the operating system, from a macOS device.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Erase all data from a macOS device

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

You can erase all data from a macOS device, including the operating system. The device will also be removed from Intune management. No warning will be given to the end user.

1. In [Intune in the Azure portal](https://aka.ms/intuneportal), choose **Devices** > **All devices** > choose the device you want to erase.
![Screenshot](./media/device-erase/choosedevice.png)
2. Click **More** > **Erase** > provide a 6-digit number for the **Recovery Pin**. This is the pin that you must give to the user so that they can reinstall the operating system on their device. Be sure to make a note of this pin because it won't be visible after the erase action completes.
![Screenshot](./media/device-erase/providepin.png)
3. Click **OK** to erase the device.
