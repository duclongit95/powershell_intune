---
# required metadata

title: Mobile device security policy settings 
description: Use Intune to configure a wide range of settings that you can deploy to managed devices in your organization.
keywords:
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ROBOTS: NOINDEX,NOFOLLOW

# optional metadata

#audience:
#ms.devlang:
ms.reviewer: heenamac
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-classic


---

# Mobile device security policy settings in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!IMPORTANT]
> Microsoft Intune now features separate configuration policies for each device platform. These policies contain the most up-to-date settings that you can use. You can continue to use the mobile device security policy, and any existing deployments will still work. However, you should plan to migrate to the new configuration policies as soon as possible because the mobile device security policy will be removed in the future.

You can use Intune mobile device security policies to configure a wide range of settings that you can deploy to managed devices in your organization. These settings are used to control the functionality and security of your devices.

You can create and deploy mobile device security policies for the following device types:

-   Windows RT 8.1 and enrolled Windows 8.1 devices

-   Windows RT

-   Windows Phone 8 and Windows Phone 8.1

-   iOS

-   Android and Samsung KNOX Standard

> [!NOTE]
> Some settings are not applicable to some devices. See the tables below for a full list of settings that you can configure.
> From October  2016, Microsoft Intune will deprecate support for Windows 8 Company Portal apps. Microsoft Intune will also deprecate support for the Windows Phone 8 and WinRT platforms. As a consequence, you will not be able to enroll or update any Windows Phone 8 or WinRT devices. You can continue to manage Windows Phone 8, WinRT  and Windows 8 devices that are already enrolled. Update Windows Phone 8 and Windows 8 devices to Windows 8.1 and Windows Phone 8.1, and use the corresponding Windows 8.1 and Windows Phone 8.1 Company Portal apps to continue distributing apps to these devices without disruptions.

## Security settings

|                                                                                                                                                                                        Setting name                                                                                                                                                                                         | Windows 8.1 and Windows RT 8.1 | Windows RT | Windows Phone 8 and Windows Phone 8.1 |       iOS       | Android and Samsung KNOX Standard |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------|------------|---------------------------------------|-----------------|-----------------------------------|
|                                                                                                                                                                <strong>Require a password to unlock mobile devices</strong>                                                                                                                                                                 |               No               |     No     |                  Yes                  |       Yes       |                Yes                |
|                                                                                                                 <strong>Required password type</strong><br /><br />This setting specifies the type of password that will be required, such as numeric only or alphanumeric.                                                                                                                 |              Yes               |    Yes     |                  Yes                  |       Yes       |                No                 |
| <strong>Required password type ??? Minimum number of character sets</strong><br /><br />There are four character sets: lowercase letters, uppercase letters, numbers, and symbols. This setting specifies how many different character sets must be included in the password. However, for iOS devices, this specifies the number of symbol characters that must be included in the password. |              Yes               |    Yes     |                  Yes                  |       Yes       |                No                 |
|                                                                                                                                                                          <strong>Minimum password length</strong>                                                                                                                                                                           |              Yes               |    Yes     |                  Yes                  |       Yes       |                Yes                |
|                                                                                                                                               <strong>Allow simple passwords</strong><br /><br />Simple passwords include ???0000??? and ???1234???.                                                                                                                                                |               No               |     No     |                  Yes                  |       Yes       |                No                 |
|                                                                                                                                                  <strong>Number of repeated sign-in failures to allow before the device is wiped</strong>                                                                                                                                                   |              Yes               |    Yes     |                  Yes                  |       Yes       |                Yes                |
|                                                                                                                                                         <strong>Minutes of inactivity before screen turns off</strong><sup>1</sup>                                                                                                                                                          |              Yes               |    Yes     |                  Yes                  |       Yes       |                Yes                |
|                                                                                                                                                                         <strong>Password expiration (days)</strong>                                                                                                                                                                         |              Yes               |    Yes     |                  Yes                  |       Yes       |                Yes                |
|                                                                                                                                                                         <strong>Remember password history</strong>                                                                                                                                                                          |              Yes               |    Yes     |                  Yes                  |       Yes       |                Yes                |
|                                                                                                                                              <strong>Remember password history</strong> ??? <strong>Prevent reuse of previous passwords</strong>                                                                                                                                              |              Yes               |    Yes     |                  Yes                  |       Yes       |                Yes                |
|                                                                                                                                                                              <strong>Password quality</strong>                                                                                                                                                                              |               No               |     No     |                  No                   |       No        |                Yes                |
|                                                                                                                                                                       <strong>Allow picture password and PIN</strong>                                                                                                                                                                       |              Yes               |    Yes     |                  No                   |       No        |                No                 |
|                                                                                                                                                             <strong>Minutes of inactivity before password is required</strong>                                                                                                                                                              |               No               |     No     |                  No                   |       Yes       |                No                 |
|                                                                                                                                                                          <strong>Allow fingerprint unlock</strong>                                                                                                                                                                          |               No               |     No     |                  No                   | iOS 7 and later |                No                 |

<sup>1</sup>For iOS devices, when you configure the settings **Minutes of inactivity before screen turns off** and **Minutes of inactivity before password is required**, they are applied in sequence. For example, if you set the value for both settings to **5** minutes, the screen will turn off automatically after 5 minutes, and the device will be locked after an additional 5 minutes. However, if the user turns off the screen manually, the second setting is immediately applied. In the same example, after the user turns off the screen, the device will lock 5 minutes later.

When you deploy a password length policy to devices that run Windows RT, users will be forced to reset their password???even if their current password complies with the policy requirements.

## Encryption settings

|                                                                                                                                     Setting name                                                                                                                                     | Windows 8.1 and Windows RT 8.1 | Windows RT |              Windows Phone 8 and Windows Phone 8.1              | iOS | Android and Samsung KNOX Standard |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------|------------|-----------------------------------------------------------------|-----|-----------------------------------|
| <strong>Require encryption on mobile device</strong><sup>1</sup><br /><br />For Windows Phone 8 devices, you must set this to <strong>Yes</strong>.<br /><br />To enable encryption on iOS devices, enable the setting <strong>Require a password to unlock mobile devices</strong>. |              Yes               |     No     |                               Yes                               | No  |                Yes                |
|                                                                    <strong>Require encryption on storage cards</strong><br /><br />This setting applies to devices that are managed by Exchange ActiveSync also.                                                                     |              n/a               |    n/a     | n/a <br />Apps and associated data are automatically encrypted. | n/a |                Yes                |

<sup>1</sup>Here is additional information for devices that run Windows 8.1:

-   To enforce encryption on devices that run Windows 8.1, you must install the [December 2014 MDM client update for Windows](http://support.microsoft.com/kb/3013816) on each device.

-   If you enable this setting for Windows 8.1 devices, all users of the device must have a Microsoft account.

-   For encryption to work, the device must meet the Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) hardware certification requirements.

-   When you enforce encryption on a device, the recovery key is only accessible from the user's Microsoft account, which is accessed from their OneDrive account. You cannot recover this key on behalf of a user.

## Malware settings

|Setting name|Windows 8.1 and Windows RT 8.1|Windows RT|Windows Phone 8 and Windows Phone 8.1|iOS|Android and Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Require network firewall**|Yes|No|No|No|No|
|**Enable SmartScreen**|Yes|No|No|No|No|

## System settings

|Setting name|Windows 8.1 and Windows RT 8.1|Windows RT|Windows Phone 8 and Windows Phone 8.1|iOS|Android and Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Require automatic updates**|Yes|No|No|No|No|
|**Require automatic updates ??? Minimum classification of updates to install automatically**<br /><br />Choose the classification of updates that will be installed automatically:<br /><br />- **Important**. Installs all updates that are classified as important.<br /><br />- **Recommended**. Installs all updates that are classified as important or recommended.|Yes|No|No|No|No|
|**Allow screen capture**|No|No|Windows Phone 8.1 only|Yes|Yes (Samsung KNOX Standard only)|
|**Allow control center in lock screen**|No|No|No|iOS 7 and later|No|
|**Allow notification view in lock screen**|No|No|No|iOS 7 and later|No|
|**Allow today view in lock screen**|No|No|No|iOS 7 and later|No|
|**User Account Control**|Yes|No|No|No|No|
|**Allow diagnostic data submission**|Yes|No|Windows Phone 8.1 only|Yes|Yes (Samsung KNOX Standard only)|
|**Allow untrusted TLS certificates**|No|No|No|Yes|No|
|**Allow personal wallet software while locked**|No|No|No|Yes|No|
|**Allow factory reset**|No|No|No|No|Yes (Samsung KNOX Standard only)|


## Cloud settings ??? documents and data

|Setting name|Windows 8.1 and Windows RT 8.1|Windows RT|Windows Phone 8 and Windows Phone 8.1|iOS|Android and Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Allow backup to iCloud**|No|No|No|Yes|No|
|**Allow document sync to iCloud**|No|No|No|Yes|No|
|**Allow Photo Stream sync to iCloud**|No|No|No|Yes|No|
|**Require encrypted backup**|No|No|No|Yes|No|
|**Work Folders URL**<br /><br />This setting sets the URL of the work folder to allow documents to be synchronized across devices.|Yes|No|No|No|No|
|**Allow Google backup**|No|No|No|No|Yes (Samsung KNOX Standard only)|

## Cloud settings ??? accounts and synchronization

|Setting name|Windows 8.1 and Windows RT 8.1|Windows RT|Windows Phone 8 and Windows Phone 8.1|iOS|Android and Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Allow Microsoft account**|No|No|Windows Phone 8.1 only|No|No|
|**Allow Google account auto sync**|No|No|No|No|Yes (Samsung KNOX Standard only)|

## Email settings

|Setting name|Windows 8.1 and Windows RT 8.1|Windows RT|Windows Phone 8 and Windows Phone 8.1|iOS|Android and Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Allow users to download email attachments**<sup>1</sup>|n/a|n/a|n/a|n/a|n/a|
|**Email synchronization period** <br /><br />This setting applies to devices that are managed by Exchange ActiveSync also.|n/a|n/a|n/a|n/a|n/a|
|**Allow mobile devices that don???t fully support these settings to synchronize with Exchange (Exchange ActiveSync)** <br /><br />This setting applies to devices that are managed by Exchange ActiveSync also.|n/a|n/a|n/a|n/a|n/a|
|**Make Microsoft account optional in Windows Mail application**|Yes|No|No|No|No|
|**Allow custom email accounts**|No|No|Windows Phone 8.1 only|No|No|

## Application settings - browser

|Setting name|Windows 8.1 and Windows RT 8.1|Windows RT|Windows Phone 8 and Windows Phone 8.1|iOS|Android and Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Allow web browser**|No|No|Windows Phone 8.1 only|Yes|Yes (Samsung KNOX Standard only)|
|**Allow autofill**|Yes|No|No|Yes|Yes (Samsung KNOX Standard only)|
|**Allow pop-up blocker**|Yes|No|No|Yes|Yes (Samsung KNOX Standard only)|
|**Allow cookies**|No|No|No|Yes|Yes (Samsung KNOX Standard only)|
|**Allow plug-ins**|Yes|No|No|No|No|
|**Allow active scripting**|Yes|No|No|Yes|Yes (Samsung KNOX Standard only)|
|**Allow fraud warning**|Yes|No|No|Yes|No|
|**Allow intranet site for single word entry**<br /><br />(This setting allows the use of a single word to direct Internet Explorer to a website???for example, ???Bing???.)|Yes|No|No|No|No|
|**Allow automatic detection of intranet network**|Yes|No|No|No|No|
|**Security level for Internet**|Yes|No|No|No|No|
|**Security level for intranet**|Yes|No|No|No|No|
|**Security level for trusted sites**|Yes|No|No|No|No|
|**Security level for restricted sites**|Yes|No|No|No|No|
|**Send Do Not Track header**|Yes|No|No|No|No|
|**Allow Enterprise Mode menu access**|Yes|No|No|No|No|
|**Enterprise Mode site list location**|Yes|No|No|No|No|

## Application settings - apps

|Setting name|Windows 8.1 and Windows RT 8.1|Windows RT|Windows Phone 8 and Windows Phone 8.1|iOS|Android and Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Allow application store**|No|No|Windows Phone 8.1 only|Yes|Yes (Samsung KNOX Standard only)|
|**Require a password to access application store**|No|No|No|Yes|No|
|**Allow in-app purchases**|No|No|No|Yes|No|
|**Allow managed documents in other unmanaged apps**|No|No|No|iOS 7 and later|No|
|**Allow unmanaged documents in other managed apps**|No|No|No|iOS 7 and later|No|
|**Allow video conferencing**|No|No|No|Yes|No|
|**Allow adult content in media store**|No|No|No|Yes|No|
|**Allow app installation**|No|No|No|iOS 6 and later|No|

## Application settings - gaming

|Setting name|Windows 8.1 and Windows RT 8.1|Windows RT|Windows Phone 8 and Windows Phone 8.1|iOS|Android and Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Allow Game Center friends**|No|No|No|Yes|No|
|**Allow multiplayer gaming**|No|No|No|Yes|No|

## Device capabilities settings - hardware

|Setting name|Windows 8.1 and Windows RT 8.1|Windows RT|Windows Phone 8 and Windows Phone 8.1|iOS|Android and Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Allow camera**|No|No|Windows Phone 8.1 only|Yes|Yes|
|**Allow removable storage**|No|No|Yes|No|Yes (Samsung KNOX Standard only)|
|**Allow Wi-Fi**|No|No|Windows Phone 8.1 only|No|Yes (Samsung KNOX Standard only)|
|**Allow Wi-Fi tethering**|No|No|Windows Phone 8.1 only|No|Yes (Samsung KNOX Standard only)|
|**Allow automatic connection to free Wi-Fi hotspots**|No|No|Windows Phone 8.1 only|No|No|
|**Allow Wi-Fi hotspot reporting**<br /><br />This setting sends information about Wi-Fi connections to help discover nearby connections.|No|No|Windows Phone 8.1 only|No|No|
|**Allow geolocation**<br /><br />This setting allows the device to utilize location information.|No|No|Windows Phone 8.1 only|No|Yes (Samsung KNOX Standard only)|
|**Allow NFC**<br /><br />This setting allows operations that use near-field communication.|No|No|Windows Phone 8.1 only|No|Yes (Samsung KNOX Standard only)|
|**Allow Bluetooth**|No|No|Windows Phone 8.1 only|No|Yes (Samsung KNOX Standard only)|
|**Allow power off**<br>If this setting is disabled, the setting **Number of repeated sign in failures to allow before the device is wiped** for Samsung KNOX Standard devices does not function.|No|No|No|No|Yes (Samsung KNOX Standard only)|

## Device capabilities settings - cellular

|Setting name|Windows 8.1 and Windows RT 8.1|Windows RT|Windows Phone 8 and Windows Phone 8.1|iOS|Android and Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Allow voice roaming**|No|No|No|Yes|Yes (Samsung KNOX Standard only)|
|**Allow data roaming**|Yes|No|No|Yes|Yes (Samsung KNOX Standard only)|
|**Allow automatic synchronization while roaming**|No|No|No|Yes|No|
|**Allow SMS/MMS messaging**|No|No|No|No|Yes (Samsung KNOX Standard only)|

## Device capabilities settings - features

|Setting name|Windows 8.1 and Windows RT 8.1|Windows RT|Windows Phone 8 and Windows Phone 8.1|iOS|Android and Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Allow voice assistant**|No|No|No|Yes|Yes (Samsung KNOX Standard only)|
|**Allow voice assistant while device is locked**|No|No|No|Yes|No|
|**Allow voice dialing**|No|No|No|Yes|Yes (Samsung KNOX Standard only)|
|**Allow copy and paste**|No|No|Windows Phone 8.1 only|No|Yes (Samsung KNOX Standard only)|
|**Allow clipboard share between applications**|No|No|No|No|Yes (Samsung KNOX Standard only)|
|**Allow YouTube**|No|No|No|No|Yes (Samsung KNOX Standard only)|

### See also
[Manage settings and features on your devices with Microsoft Intune policies](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
