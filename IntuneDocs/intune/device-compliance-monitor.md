---
# required metadata

title: Monitor device compliance
titlesuffix: "Microsoft Intune"
description: Learn how to monitor device compliance."
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: muhosabe
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---
# Monitor device compliance in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

You can view the summary of the status of your **compliance profiles** in the **Overview** blade.
You can interactively click through the charts to drill down into the details. If you have multiple compliance profiles configured, you can view the policy status on the policy blade under **Manage** > **Reports**.

##  Device compliance

The summarized view of the device compliance report lists aggregated information about the number of devices that are reporting in one of the following states:

- **Compliant**: The device has recently been evaluated and complies with the compliance profile settings you specified.
- **Noncompliant**: The device has been evaluated and determined as noncompliant.  If there was a grace period specified in the profile, the grace period has expired putting the device in a noncompliant status.
- **Grace period**: Device has been evaluated and determined as noncompliant. However, the grace period still applies before the device is marked as noncompliant.

You can drill down on each section to see more details on the individual devices and users.

## Setting compliance

The setting compliance report provides the details for each compliance setting such as:

- Number of devices that are noncompliant with the setting.
- The platform that the setting is applied to.

You can drill down on each of the setting to see more information about the profiles on which these settings have been enabled, and the value of the setting.
