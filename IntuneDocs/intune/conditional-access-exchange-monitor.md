---
# required metadata

title: Monitor Exchange conditional access in Microsoft Intune
titlesuffix:
description: Monitor conditional access compliance for on-premises Exchange and Exchange Online through the Intune Azure portal.
keywords:
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Monitor conditional access compliance for on-premises Exchange and Exchange Online in Intune

Beginning with Intune 1704 release, admins can see reporting information related to Exchange ActiveSync device records that are synchronized with Intune through either the on-premises Exchange Connector or the Intune service-to-service connector (Exchange Online connector). The conditional access compliance reporting provides a summary of devices with different synchronization states:

-   **Allow**

-   **Block**

-   **Quarantine**

## To monitor conditional access compliance

1.  Go to the [Azure portal](https://portal.azure.com/), and sign in with your Intune credentials.

2.  After you've successfully signed in, you see the **Azure Dashboard**.

3.  Choose **All services** from the left menu, then type **Intune** in the text box filter.

4.  Choose **Intune**, you see the **Intune Dashboard**.

5.  Choose **Conditional access**, then choose **Overview**.

6.  Choose one of the three areas (**Allowed**, **Blocked**, or **Quarantine**) on the chart to view your conditional access compliance reporting.

    ![Image of the Conditional Access Dashboard](./media/CA-reporting-intune-1.png)

Once you choose one of three areas, you can see more details about devices being allowed, blocked, or quarantined.

You can also drill down in specific devices to see more details. For example, the device chosen on the following image is blocked. Intune gives you the option of removing corporate data from the conditional access compliance report pane.

![Image of Conditional access device detail reporting](./media/CA-reporting-intune-3.png)

At the device details pane, you can see more information:

-   **Overview:** You can see device properties like: OS version, device model, ownership, serial number, device manufacturer, phone number, and last time the device checked in.

-   **Properties:** You can set the device ownership (Personal or Corporate).

-   **Hardware:** It provides the information you see on the Overview, and also storage details (total space and free space), system enclosure, network details, network service, and more conditional access blocking details.

-   **Discovered Apps:** It shows all applications installed at your device. You can also export the list of installed apps to .CSV format.

-   **Compliance:** It shows all device compliance policy details.

-   **Device Configuration:** It shows all device configuration details.

-   **Exchange Access:** Here you can learn more about the device state after applying conditional access policies.
