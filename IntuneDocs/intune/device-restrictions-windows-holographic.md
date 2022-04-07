---
# required metadata

title: Device restrictions for Windows Holographic for Business in Microsoft Intune - Azure | Microsoft Docs
description: Read about and configure device restriction settings in Microsoft Intune for Windows Holographic for Business, including unenrollment, geolocation, passwords, install apps from app store, cookies and pop ups in Edge, Windows Defender, search, cloud and storage, bluetooth connectivity, system time, and usage data in Azure.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/1/2018
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

# Device restriction settings for Windows Holographic for Business in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

The following device restriction settings are supported on devices running Windows Holographic for Business, such as Microsoft Hololens.

## General

- **Manual unenrollment** - Lets the user manually delete the workplace account from the device.
- **Cortana** - Enable or disable the Cortana voice assistant.
- **Geolocation** - Specifies whether the device can use location services information.

## Password
- 	**Password** - Require the end user to enter a password to access the device.
	- 	**Require password when device returns from idle state** - Specifies that the user must enter a password to unlock the device.

## App Store

- 	**Auto-update apps from store** - Allows apps installed from the Microsoft Store to be automatically updated.
- 	**Trusted app installation** - Allows apps signed with a trusted certificate to be sideloaded.
- 	**Developer unlock** - Allow Windows developer settings, such as allowing sideloaded apps to be modified by the end user.

## Edge Browser

- 	**Cookies** - Lets the browser save internet cookies to the device.
- 	**Pop-ups** - Blocks pop-up windows in the browser (applies to Windows 10 desktop only).
- 	**Search suggestions** - Lets your search engine suggest sites as you type search phrases.
- 	**Password Manager** - Enable or disable the Edge Password Manager feature.
- **Send do-not-track headers** - Configures the Edge browser to send do not track headers to websites that users visit.

## Windows Defender Smart Screen

- **SmartScreen for Microsoft Edge** - Enable Edge SmartScreen for accessing site and file downloads.

## Search
- **Search location** -Specify if search can use location. information

## Cloud and Storage
- 	**Microsoft account** - Lets the user associate a Microsoft account with the device.

## Cellular and Connectivity

- 	**Bluetooth** - Controls whether the user can enable and configure Bluetooth on the device.
- 	**Bluetooth discoverability** - Lets the device be discovered by other Bluetooth-enabled devices.
- 	**Bluetooth advertising** - Lets the device receive advertisements over Bluetooth.

## Control Panel and Settings

- **System Time modification** - Prevents the end user from changing the device date and time.

## Kiosk

A kiosk device typically runs a specific app. Users are prevented from accessing any features or functions on the device outside of the kiosk app.

- **Kiosk mode** - Identifies the type of kiosk mode supported by the policy. Options include:

  - **Not Configured** (default) - The policy does not enable a kiosk mode. 
  - **Single app kiosk** - The profile enables the device to only run one app. When the user signs in, a specific app starts. This mode also restricts the user from opening new apps, or changing the running app.
  - **Multi-app kiosk** - The profile enables the device to run multiple apps. Only the apps you add are available to the user. The benefit of a multi-app kiosk, or fixed-purpose device, is to provide an easy-to-understand experience for individuals by only accessing apps they need. And, removing the apps they don’t need from their view. 
  
    When you add apps for a multi-app kiosk experience, you also add a start menu layout file. [Start menu layout file](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-file-for-intune) includes sample XML that can be used in Intune. 

#### Single app kiosks
Enter the following settings:

- **User account** - Enter the local (to the device) user account or the Azure AD account login associated with the kiosk app. For accounts joined to Azure AD domains, enter the account using the `domain\username@tenant.org` format. 

    For kiosks in public-facing environments with auto logon enabled, a user type with the least privilege (such as the local standard user account) should be used. To configure an Azure Active Directory (AD) account for kiosk mode, use the `AzureAD\user@contoso.com` format.

- **Application user model ID (AUMID) of app** - Enter the AUMID of the kiosk app. To learn more, see [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

## Reporting and Telemetry

- **Share usage data** - Select level of diagnostic data submission.
