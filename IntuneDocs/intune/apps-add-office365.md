---
# required metadata

title: Install Office 365 apps to devices using Microsoft Intune
titlesuffix: 
description: Learn how you can use Microsoft Intune to make it easier to install Office 365 apps on Windows 10 devices.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: aiwang
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Assign Office 365 apps to Windows 10 devices with Microsoft Intune

This app type makes it easy for you to assign Office 365 apps to devices you manage that run Windows 10. You can also install apps for the Microsoft Project Online desktop client and Microsoft Visio Pro for Office 365, if you own licenses for them. The apps that you want are displayed as a single entry in the list of apps on the Intune console.


## Before you start

>[!IMPORTANT]
>This method of installing Office is supported only if no other versions of Microsoft Office are installed on the device.

- Devices to which you deploy these apps must be running the Windows 10 Creators Update or later.
- Intune supports adding Office apps from the Office 365 suite only.
- If any Office apps are open when Intune installs the app suite, the installation might fail, and users might lose data from unsaved files.
- This installation method is not supported on Windows 10 S, Windows Home, Windows Team, Windows Holographic, or Windows Holographic for Business devices.
- Intune does not support installing Office 365 desktop apps from the Microsoft Store (known as Office Centennial apps) on a device to which you have already deployed Office 365 apps with Intune. If you install this configuration, it might cause data loss or corruption.
- Multiple required or available app assignments are not additive. A later app assignment will overwrite pre-existing installed app assignments. For example, if the first set of Office apps contains Word, and the later one does not, Word will be uninstalled. This condition does not apply to any Visio or Project applications.


## Get started

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **All Services** > **Intune**. Intune is located in the **Monitoring + Management** section.
3. In the **Intune** pane, select **Mobile apps**.
4. In the **Mobile apps** workload pane, under **Manage**, select **Apps**.
5. Select **Add**.
6. In the **Add apps** pane, in the **App type** list, under **Office 365 Office**, select **Windows 10**.

You can now configure the app suite.

## Configure the app suite

Select the Office apps that you want to assign to devices.

1. In the **Add App** pane, select **Configure App Suite**.
2. In the **Configure App Suite** pane, select the standard Office apps that you want to assign to devices.  
    Additionally, you can install apps for the Microsoft Project Online desktop client and Microsoft Visio Pro for Office 365, if you own licenses for them.
3. Select **OK**.

>[!IMPORTANT]
> After you've created the app suite, you cannot edit its properties. To configure different properties, delete the app suite and create a new one.

## Configure app information

In this step, you provide information about the app suite. This information helps you to identify the app suite in Intune, and it helps users to find the app suite in the company portal.

1. In the **Add App** pane, select **App Suite Information**.
2. In the **App Suite Information** pane, do the following:
	- **Suite Name**: Enter the name of the app suite as it is displayed in the company portal. Make sure that all suite names that you use are unique. If the same app suite name exists twice, only one of the apps is displayed to users in the company portal.
	- **Suite Description**: Enter a description for the app suite. For example, you could list the apps you've selected to include.
	- **Publisher**: Enter the name of the publisher of the app.
	- **Category**: Optionally, select one or more of the built-in app categories or a category that you created. This setting makes it easier for users to find the app suite when they browse the company portal.
	- **Display this as a featured app in the Company Portal**: Select this option to display the app suite prominently on the main page of the company portal when users browse for apps.
	- **Information URL**: Optionally, enter the URL of a website that contains information about this app. The URL is displayed to users in the company portal.
	- **Privacy URL**: Optionally, enter the URL of a website that contains privacy information for this app. The URL is displayed to users in the company portal.
	- **Developer**: Optionally, enter the name of the app developer.
	- **Owner**: Optionally, enter a name for the owner of this app, for example, *HR department*.
	- **Notes**: Enter any notes that you want to associate with this app.
	- **Logo**: Upload an icon that is displayed with the app when users browse the company portal.
3. Select **OK**.

## Configure app settings

In this step, configure installation options for the app suite. The settings apply to all apps that you added to the suite.

1. In the **Add App** pane, select **App Suite Settings**.
2. In the **App Suite Settings** pane, do the following:
	- **Office version**: Choose whether you want to assign the 32-bit or 64-bit version of Office. You can install the 32-bit version on both 32-bit and 64-bit devices, but you can install the 64-bit version on 64-bit devices only.
	- **Update Channel**: Choose how Office is updated on devices. For information about the various update channels, see [Overview of update channels for Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Choose from:
		- **Monthly**
		- **Monthly (Targeted)**
		- **Semi-Annual**
		- **Semi-Annual (Targeted)**
	- **Automatically accept the app end user license agreement**: Select this option if you don't require end users to accept the license agreement. Intune then automatically accepts the agreement.
	- **Use shared computer activation**: Select this option when multiple users share a computer. For more information, see Overview of shared computer activation for Office 365.
	- **Languages**: Office is automatically installed in any supported languages that are installed with Windows on the end-user's device. Select this option if you want to install additional languages with the app suite.

>[!IMPORTANT]
> After you've created the app suite, you cannot edit its properties. To configure different properties, delete the app suite and create a new one.

## Finish up

When you're done, in the **Add App** pane, select **Add**. The app you've created is displayed in the apps list.

## Errors during installation of the app suite

The following tables list common error codes you might encounter and their meaning.

### Status for Office CSP

||||
|-|-|-|
|Status|Phase|Description|
|1460 (ERROR_TIMEOUT)|Download|Failed to download the Office Deployment Tool|	 
|13 (ERROR_INVALID_DATA)|-|Cannot verify the signature of the downloaded Office Deployment Tool|
|Error code from CertVerifyCertificateChainPolicy|-|Failed certification check for the downloaded Office Deployment Tool|	 
|997|WIP|Installing|
|0|After installation|Installation succeeded|	 
|1603 (ERROR_INSTALL_FAILURE)|-|Failed any prerequisite check, such as:<ul><li>SxS (Tried to install when 2016 MSI is installed)</li><li>Version mismatch</li><li>Others</li></ul>|	 
|0x8000ffff (E_UNEXPECTED)|-|Tried to uninstall when there is no Click-to-run Office on the machine|	 
|17002|-|Failed to complete the scenario (install). Possible reasons:<ul><li>Installation canceled by user</li><li>Installation canceled by another installation</li><li>Out of disk space during installation</li><li>Unknown language ID</li></ul>|
|17004|-|Unknown SKUs|	 


### Office Deployment Tool error codes

|||||
|-|-|-|-|
|Scenario|Return code|UI|Note|
|Uninstall effort when there is no active Click-to-run installation|-2147418113, 0x8000ffff or 2147549183|Error Code: 30088-1008<br>Error Code: 30125-1011 (404)|Office Deployment Tool|
|Install when there is MSI version installed|1603|-|Office Deployment Tool|
|Installation canceled by user, or by another installation|17002|-|Click-to-run|
|Try to install 64-bit on a device that has 32-bit installed.|1603|-|Office Deployment Tool return code|
|Try to install an unknown SKU (not a legitimate use case for Office CSP since we should only pass in valid SKUs)|17004|-|Click-to-run|
|Lack of space|17002|-|Click-to-run|
|The click-to-run client failed to start (unexpected)|17000|-|Click-to-run|
|The click-to-run client failed to queue scenario (unexpected)|17001|-|Click-to-run|

## Next steps

- To assign the apps to the groups you choose, see [Assign apps to groups](/intune-azure/manage-apps/deploy-apps).
