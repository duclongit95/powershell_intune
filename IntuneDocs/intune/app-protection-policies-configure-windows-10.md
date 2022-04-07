---
# required metadata

title: Get ready to configure app protection policies for Windows 10 
titleSuffix: Microsoft Intune
description: Setup mobile application management (MAM) provider in Azure AD.
keywords:
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/21/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Get ready to configure app protection policies for Windows 10 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Enable mobile application management (MAM) for Windows 10 by setting the MAM provider in Azure AD. Setting a MAM provider in Azure AD allows you to define the enrollment state when creating a new Windows Information Protection (WIP) policy with Intune. The enrollment state can be either MAM or mobile device management (MDM).

> [!NOTE]
> Devices with a MAM enrollment state are required to be Azure AD joined.

## To configure the MAM provider

1. Sign in to the Azure portal, and choose **Azure Active Directory.**

2. Choose **Mobility (MDM and MAM)** in the **Manage** group.

3. Click **Microsoft Intune**.

4. Configure the settings in the  **Restore default MAM URLs** group on the **Configure** blade.

   **MAM user scope**  
   Use MAM auto-enrollment to manage enterprise data on your employees' Windows devices. MAM auto-enrollment will be configured for bring your own device scenarios.<ul><li>**None**<br>Select if no users can be enrolled in MAM.</li><li>**Some**<br>Select Azure AD groups that contain users who will be enrolled in MAM.</li><li>**All**<br>Select if all users can be enrolled in MAM.</li></ul>

   **MAM terms of use URL**  
   The MAM terms of use URL is not supported for Microsoft Intune. This input box must be left blank for protection policies to apply.

   **MAM discovery URL**  
   The URL of the enrollment endpoint of the MAM service. The enrollment endpoint is used to enroll devices for management with the MAM service.

   **MAM compliance URL**  
   The MAM compliance URL is not supported for Microsoft Intune. This input box must be left blank for protection policies to apply. 

5.  Click **Save**.

## Next steps

[Create a WIP app protection policy](windows-information-protection-policy-create.md)
