---
# required metadata

title: Enroll devices using a device enrollment manager account
titlesuffix: "Microsoft Intune"
description: Use the device enrollment manager account to enroll devices in Intune. "
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: damionw
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure
---

# Enroll devices by using a device enrollment manager account

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Organizations can use Intune to manage large numbers of mobile devices with a single user account. The *device enrollment manager* (DEM) account is a special user account that can enroll up to 1,000 devices. You add existing users to the DEM account to give them the special DEM capabilities. Each enrolled device uses a single license. We recommend that you use devices enrolled through this account as shared devices rather than personal ("BYOD") devices.  

Users must exist in the [Azure portal](https://portal.azure.com) to be added as device enrollment managers. For optimal security, the DEM user should not also be an Intune admin.

>[!NOTE]
>The DEM enrollment method can't be used with these other enrollment methods: [Apple Configurator with Setup Assistant](apple-configurator-setup-assistant-enroll-ios.md), [Apple Configurator with direct enrollment](apple-configurator-direct-enroll-ios.md), [Apple School Manager (ASM)](apple-school-manager-set-up-ios.md), or [Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md).

## Example of a device enrollment manager scenario

A restaurant wants to provide 50 point-of-sale tablets for its wait staff, and order monitors for its kitchen staff. The employees never need to access company data or sign in as users. The Intune admin creates a device enrollment manager account and adds a restaurant supervisor to the DEM account. The supervisor now has DEM capabilities. The supervisor can now enroll the 50 tablets devices by using the DEM credentials.

Only users in the [Azure portal](https://portal.azure.com) can be device enrollment managers. The device enrollment manager user cannot be an Intune admin.

The DEM user can:

-   Enroll up to 1000 devices in Intune
-   Sign in to the Company Portal to get company apps
-   Configure access to company data by deploying role-specific apps to the tablets

## Limitations of devices that are enrolled with a DEM account

Devices that are enrolled with a device enrollment manager account have the following limitations:

  - No per-user access. Because devices don't have an assigned user, the device has no email or company data access. VPN configurations, for example, could still be used to provide device apps with access to data.
  - The DEM user can't unenroll DEM-enrolled devices on the device itself by using the Company Portal. The Intune admin can do unenroll.
  - Only the local device appears in the Company Portal app or website.
  - Users can???t use Apple Volume Purchase Program (VPP) apps with user licenses because of per-user Apple ID requirements for app management.
  - (iOS only) If you use DEM to enroll iOS devices, you can't use the Apple Configurator, Apple Device Enrollment Program (DEP), or Apple School Manager (ASM) to enroll devices.
  - (Android only) There is a limit to the number of Android for Work devices that can be enrolled with a single DEM account. A maximum of 10 Android work profile devices may be enrolled per DEM account. This limitation does not apply to legacy Android enrollment.
  - Devices can install VPP apps if they have device licenses.
  - Each device requires a device license. Learn more about [user and device licenses](licenses-assign.md#how-user-and-device-licenses-affect-access-to-services).


> [!NOTE]
> You can deploy company apps to devices that are managed by the device enrollment manager. Deploy the Company Portal app as a **Required Install** to the device enrollment manager's user account.
> To improve performance, viewing the Company Portal app on a DEM device shows only the local device. Remote management of other DEM devices can only be done from the Intune admin console.


## Add a device enrollment manager

1.  In [Intune in the Azure portal](https://aka.ms/intuneportal), choose **Device enrollment** > **Device enrollment managers**.

2.  Select **Add**.

3.  On the **Add User** blade, enter a user principal name for the DEM user, and select **Add**. The DEM user is added to the list of DEM users.

## Permissions for DEM

Global or Intune Service Administrator Azure AD roles are required to perform tasks that are related to DEM enrollment in the Admin Portal. These roles are also required to see all DEM users despite RBAC permissions being listed and available under the custom User role. A user without the Global Administrator or Intune Service Administrator role assigned, but who has read permissions for the Device Enrollment Managers role, can see only the DEM users they created. RBAC role support for these features will be announced in the future.

If a user does not have the Global Administrator or Intune Service Administrator role assigned to them but has read permissions enabled for the Device Enrollment Managers role assigned to them, they???ll be able to see only the DEM users they have created.

## Remove a device enrollment manager

Removing a device enrollment manager does not affect enrolled devices. When a device enrollment manager is removed:

-   Enrolled devices are unaffected and continue to be fully managed.
-   The removed device enrollment manager account credentials remain valid.
-   The removed device enrollment manager still cannot wipe or retire devices.
-   The removed device enrollment manager can only enroll a number of devices up to the per-user limit configured by the Intune admin.

**To remove a device enrollment manager**

1. In [Intune in the Azure portal](https://aka.ms/intuneportal), choose **Device enrollment**, and then choose **Device enrollment managers**.
2. On the **Device enrollment managers** blade, select the DEM user, and select **Delete**.

## View the properties of a device enrollment manager

1. In the [Azure portal](https://portal.azure.com), choose **Device enrollment**, and then choose **Device enrollment managers**.
2. On the **Device enrollment managers** blade, right-click the DEM user, and select **Properties**.
