---
# required metadata

title: VPN connections 
description: Use VPN profiles to deploy VPN settings to users and devices in your organization.
keywords:
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 05/15/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73
ROBOTS: NOINDEX,NOFOLLOW

# optional metadata

#audience:
#ms.devlang:
ms.reviewer: karanda
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-classic

---

# VPN connections in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Virtual private networks (VPNs) give your users secure remote access to your company network. Devices use a *VPN connection profile* to initiate a connection with the VPN server. Use *VPN profiles* in Microsoft Intune to deploy VPN settings to users and devices in your organization, so they can easily and securely connect to the network.

For example, assume that you want to provision all iOS devices with the settings required to connect to a file share on the corporate network. You create a VPN profile that contains the settings necessary to connect to the corporate network, and then you deploy this profile to all users who have iOS devices. The users will see the VPN connection in the list of available networks and can connect with minimal effort.

You can configure the following device types by using VPN profiles:

* Devices that run Android 4 and later
* Android for Work devices
* Devices that run iOS 8.0 and later
* Devices that run Mac OS X 10.9 and later
* Enrolled devices that run Windows 8.1 and later
* Devices that run Windows Phone 8.1 and later
* Devices that run Windows 10 desktop and mobile

The VPN profile configuration options differ depending on the device type that you select.

## VPN connection types

Intune supports creating VPN profiles that use the following connection types:


Connection type |iOS and Mac OS X  |Android and Android for Work|Windows 8.1|Windows RT 8.1|Windows Phone 8.1|Windows 10 desktop and mobile |
----------------|------------------|-------|-----------|----------|--------------|-----------------|----------------------|
Cisco AnyConnect|Yes |Yes   |No    |No  |No    | Yes (OMA-URI, mobile only)|     
Cisco (IPsec)|Yes |Yes   |No  |No  |No | No|
Citrix|Yes |Yes (Android only)   |No  |No  |No | No|
Pulse Secure|Yes  |Yes |Yes   |Yes  |Yes| Yes|        
F5 Edge Client|Yes |Yes |Yes |Yes  |   Yes |  Yes|   
SonicWall Mobile Connect|Yes |Yes |Yes |Yes |Yes |Yes|         
CheckPoint Mobile VPN|Yes |Yes |Yes |Yes|Yes|Yes|
Microsoft SSL (SSTP)|No |No |No |No|No|VPNv1 OMA-URI*|
Microsoft Automatic|No |No |No |No|Yes (OMA-URI)|Yes|
IKEv2|iOS custom profile|No |No |No|Yes (OMA-URI)|Yes|
PPTP|iOS custom profile|No |No |No|No|Yes|
L2TP|iOS custom profile|No |No |No|Yes (OMA-URI)|Yes|

\* Without additional settings that are otherwise available for Windows 10.

> [!IMPORTANT]
> Before you can use VPN profiles deployed to a device, you must install the applicable VPN app for the profile. You can use the information in the [Deploy apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md) topic to help you deploy the applicable app by using Intune.  

 Learn how to  create custom VPN profiles by using URI settings in [Custom configurations for VPN profiles](create-custom-vpn-profiles.md).     

## Methods of securing VPN profiles

VPN profiles can use a number of different connection types and protocols from different manufacturers. These connections are typically secured through one of two methods.

### Certificates

When you create the VPN profile, you choose a SCEP or PFX certificate profile that you previously created in Intune. This is known as the identity certificate. It's used to authenticate against a trusted certificate profile (or *root certificate*) that you created to establish that the user???s device is allowed to connect. The trusted certificate is deployed to the computer that authenticates the VPN connection, typically, the VPN server.

For more information about how to create and use certificate profiles in Intune, see [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md).

### User name and password

The user authenticates to the VPN server by providing a user name and password.

## Create a VPN profile

1. In the [Microsoft Intune administration console](https://manage.microsoft.com), choose **Policy** > **Add Policy**.
2. Select a template for the new policy by expanding the relevant device type, and then choose the VPN profile for that device:
	* **VPN Profile (Android 4 and later)**
	* **VPN Profile (Android for Work)**
	* **VPN Profile (iOS 8.0 and later)**
	* **VPN Profile (Mac OS X 10.9 and later)**
	* **VPN Profile (Windows 8.1 and later)**
	* **VPN Profile (Windows Phone 8.1 and later)**
	* **VPN Profile (Windows 10 Desktop and Mobile and later)**

   You can create and deploy only a custom VPN profile policy. Recommended settings are not available.

> [!Note]
> A VPN profile for Android for Work devices will enable a VPN connection only for apps that are installed on the device's work profile.
>
> Some VPN connection types support per-app VPN for Android for Work devices, and for enabling per-app VPN on apps distributed through Intune.  

3. Use the following table to help you configure the VPN profile settings:

|                                                    Setting name                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                  More information                                                                                                                                                                                                                                                                                                                                                                                                                   |
|---------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                <strong>Name</strong>                                                |                                                                                                                                                                                                                                                                                                                                                                               Enter a unique name for the VPN profile to help you identify it in the Intune console.                                                                                                                                                                                                                                                                                                                                                                                |
|                                            <strong>Description</strong>                                             |                                                                                                                                                                                                                                                                                                                                                             Provide a description that gives an overview of the VPN profile and other relevant information that helps you to locate it.                                                                                                                                                                                                                                                                                                                                                             |
|                              <strong>VPN connection name (displayed to users)</strong>                              |                                                                                                                                                                                                                                                                                                                                                         Specify a name for the VPN profile. This is the name that users will see in the list of available VPN connections on their devices.                                                                                                                                                                                                                                                                                                                                                         |
|                                          <strong>Connection type</strong>                                           |                                                                                                                                                                                                                                                     Select one of the following connection types to use in the VPN profile: <strong>Cisco AnyConnect</strong> (not available for Windows 8.1 or Windows Phone 8.1), <strong>Pulse Secure</strong>, <strong>Citrix</strong>, <strong>F5 Edge Client</strong>, <strong>SonicWall Mobile Connect</strong>, <strong>CheckPoint Mobile VPN</strong>.                                                                                                                                                                                                                                                     |
|                                       <strong>VPN server description</strong>                                       |                                                                                                                                                                                                                                                                               Specify a description for the VPN server that devices will connect to. Example: <strong>Contoso VPN Server</strong>. When the connection type is <strong>F5 Edge Client</strong>, use the <strong>Server list</strong> field to specify a list of server descriptions and IP addresses.                                                                                                                                                                                                                                                                               |
|                                     <strong>Server IP address or FQDN</strong>                                      |                                                                                                                                                                                                                                                 Provide the IP address or fully qualified domain name of the VPN server that devices will connect to. Examples: <strong>192.168.1.1</strong>, <strong>vpn.contoso.com</strong>.  When the connection type is <strong>F5 Edge Client</strong>, use the <strong>Server list</strong> field to specify a list of server descriptions and IP addresses.                                                                                                                                                                                                                                                 |
|                                            <strong>Server list</strong>                                             |                                                                                                                                                                                                                                                                                           Choose <strong>Add</strong> to add a new VPN server to use for the VPN connection. You can also specify which server will be the default server for the connection. This option is displayed only when the connection type is <strong>F5 Edge Client</strong>.                                                                                                                                                                                                                                                                                            |
|                        <strong>Send all network traffic through the VPN connection</strong>                         |                                                                                                                                                                                                                                If you select this option, all network traffic is sent through the VPN connection. If you do not select this option, the client will dynamically negotiate the routes for split tunneling upon connecting to the third-party VPN server. Only connections to the company network are sent over a VPN tunnel. VPN tunneling is not used when you connect to resources on the Internet.                                                                                                                                                                                                                                |
|                                       <strong>Authentication method</strong>                                        |                                                                                                                                                                                                                                                         Select the authentication method that the VPN connection uses: <strong>Certificates</strong> or <strong>Username and Password</strong>. (<strong>Username and Password</strong> is not available when the connection type is Cisco AnyConnect.) The <strong>Authentication method</strong> option is not available for Windows 8.1.                                                                                                                                                                                                                                                         |
|                            <strong>Remember the user credentials at each logon</strong>                             |                                                                                                                                                                                                                                                                                                                                          Select this option to ensure that the user credentials are remembered so that the user does not have to enter credentials each time a connection is established.                                                                                                                                                                                                                                                                                                                                           |
|            <strong>Select a client certificate for client authentication (Identity Certificate)</strong>            |                                                                                                                                                                                                                     Select the client SCEP certificate that you previously created and that will be used to authenticate the VPN connection. For more information about how to use certificate profiles in Intune, see [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md). This option is displayed only when the authentication method is <strong>Certificates</strong>.                                                                                                                                                                                                                      |
|                                                <strong>Role</strong>                                                |                                                                                                                                                                                                                                                                          Specify the name of the user role that has access to this connection. A user role defines personal settings and options, and it enables or disables certain access features. This option is displayed only when the connection type is <strong>Pulse Secure</strong> or <strong>Citrix</strong>.                                                                                                                                                                                                                                                                           |
|                                               <strong>Realm</strong>                                                |                                                                                                                                                                                                                                                                   Specify the name of the authentication realm that you want to use. An authentication realm is a grouping of authentication resources that the Pulse Secure or Citrix connection type uses. This option is displayed only when the connection type is <strong>Pulse Secure</strong> or <strong>Citrix</strong>.                                                                                                                                                                                                                                                                    |
|                                       <strong>Login group or domain</strong>                                        |                                                                                                                                                                                                                                                                                                                                   Specify the name of the login group or domain that you want to connect to. This option is displayed only when the connection type is <strong>SonicWall Mobile Connect</strong>.                                                                                                                                                                                                                                                                                                                                   |
|                                            <strong>Fingerprint</strong>                                             |                                                                                                                 Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn???t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses <strong>trust</strong> to connect.) This option is displayed only when the connection type is <strong>CheckPoint Mobile VPN</strong>.                                                                                                                 |
|                                            <strong>Per App VPN</strong>                                             |                                                                                                                                                                                                                                                         Select this option if you want to associate this VPN connection with an iOS or Mac OS X app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you deploy the software. For more information, see [Deploy apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md).                                                                                                                                                                                                                                                         |
|                                           <strong>On-demand VPN</strong>                                            |                                                                                                                                                                                                                                                                                                                                    You can set up on-demand VPN for iOS 8.0 and later devices. Instructions for setting this up are provided in [On-demand VPN for iOS devices](#on-demand-vpn-for-ios-devices).                                                                                                                                                                                                                                                                                                                                    |
|    <strong>Automatically detect proxy settings</strong> (iOS, Mac OS X, Windows 8.1, and Windows Phone 8.1 only)    |                                                                                                                                                                                                                                                                                                                    If your VPN server requires a proxy server for the connection, specify whether you want devices to automatically detect the connection settings. For more information, see your Windows Server documentation.                                                                                                                                                                                                                                                                                                                    |
|    <strong>Use automatic configuration script</strong> (iOS, Mac OS X, Windows 8.1, and Windows Phone 8.1 only)     |                                                                                                                                                                                                                                                                                If your VPN server requires a proxy server for the connection, specify whether you want to use an automatic configuration script to define the settings, and then specify a URL to the file that contains the settings. For more information, see your Windows Server documentation.                                                                                                                                                                                                                                                                                 |
|             <strong>Use proxy server</strong> (iOS, Mac OS X, Windows 8.1, and Windows Phone 8.1 only)              |                                                                                                                                                                                                                                                                                                                  If your VPN server requires a proxy server for the connection, select this option, and then specify the address and port number of the proxy server. For more information, see your Windows Server documentation.                                                                                                                                                                                                                                                                                                                  |
| <strong>Bypass proxy settings for local addresses</strong> (iOS, Mac OS X, Windows 8.1, and Windows Phone 8.1 only) |                                                                                                                                                                                                                                                                                                           If your VPN server requires a proxy server for the connection, select this option if you do not want to use the proxy server for local addresses that you specify. For more information, see your Windows Server documentation.                                                                                                                                                                                                                                                                                                           |
|                <strong>Custom XML</strong> (Windows 8.1 and later, and Windows Phone 8.1 and later)                 | Specify custom XML commands that configure the VPN connection. Example for <strong>Pulse Secure</strong>: &lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. Example for <strong>CheckPoint Mobile VPN</strong>: &lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true"  debug="3" /&gt;. Example for <strong>SonicWall Mobile Connect</strong>: &lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. Example for <strong>F5 Edge Client</strong>: &lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;. Refer to each manufacturer's VPN documentation for more information about how to write custom XML commands. |
|                          <strong>DNS Suffix search list</strong> (Windows Phone 8.1 only)                           |                                                                                                                                                                                        Specify one DNS suffix on each line. Each DNS suffix that you specify will be searched when connecting to a website by using a short name. For example, specify the DNS suffixes <strong>domain1.contoso.com</strong> and <strong>domain2.contoso.com</strong>, visit the URL <strong><http://mywebsite></strong>, and the URLs <strong><http://mywebsite.domain1.contoso.com></strong> and <strong><http://mywebsite.domain2.contoso.com></strong> will be searched.                                                                                                                                                                                        |
|            <strong>Bypass VPN when connected to company Wi-Fi network</strong> (Windows Phone 8.1 only)             |                                                                                                                                                                                                                                                                                                                                                          Select this option to specify that the VPN connection will not be used when the device is connected to the company Wi-Fi network.                                                                                                                                                                                                                                                                                                                                                          |
|              <strong>Bypass VPN when connected to home Wi-Fi network</strong> (Windows Phone 8.1 only)              |                                                                                                                                                                                                                                                                                                                                                            Select this option to specify that the VPN connection will not be used when the device is connected to a home Wi-Fi network.                                                                                                                                                                                                                                                                                                                                                             |

The following additional settings are available for Windows 10 desktop and mobile devices.


|              Setting name              |                                                                                                                                                                     More information                                                                                                                                                                     |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>Network traffic rules</strong> | Select which protocols, and which local and remote port and address ranges, will be enabled for the VPN connection. If you do not create a network traffic rule, all protocols, ports, and address ranges are enabled. After you create a rule, the VPN connection will use only the protocols, ports, and address ranges that you specify in that rule. |
|        <strong>Routes</strong>         |                                                                                                                                                     Select which routes will use the VPN connection.                                                                                                                                                     |
|      <strong>DNS servers</strong>      |                                                                                                                                Select which DNS servers the VPN connection will use after the connection is established.                                                                                                                                 |
|    <strong>Associated apps</strong>    |                                                           Provide a list of apps that will automatically use the VPN connection. The type of app will determine the app identifier. For a universal app, provide the package family name. For a desktop app, provide the file path of the app.                                                           |

> [!IMPORTANT]
> We recommend that you secure all lists of apps that you compile for use in configuration of per-app VPN. If an unauthorized user modifies your list and you import it into the per-app VPN app list, you will potentially authorize VPN access to apps that should not have access. One way you can secure app lists is by using an access control list (ACL).

Here's an example of when you might use settings for corporate boundaries. If you want to enable VPN only for Remote Desktop, create a network traffic rule that allows traffic for protocol 27 on external port 3996. No other traffic will use the VPN.

Defining routes in corporate boundaries is useful when your VPN connection type does not allow you to define how traffic is handled in split tunneling. In that case, use **Routes** to list the routes that will use the VPN.

You can restrict VPN usage for Windows 10 devices to specific apps by creating a custom OMA-URI setting.

The new policy appears in the **Configuration Policies** node of the **Policy** workspace.

### On-demand VPN for iOS devices
You can configure on-demand VPN for iOS 8.0 and later devices.

> [!NOTE]
>  
> You cannot use per-app VPN and on-demand VPN in the same policy.

1. On the policy configuration page, find **On-demand rules for this VPN connection**. The columns are labeled **Match**, the condition that the rules check for, and **Action**, the action that the policy will trigger when the condition is matched.
2. Choose **Add** to create a rule. There are two types of matches that you can set up in the rule. You can only configure one of these types per rule.
   - **SSIDs** - which refer to wireless networks.
   - **DNS search domains** - You can use full-qualified domain names such as *team. corp.contoso.com*, or use domains such as *contoso.com*, which is the equivalent of using * *.contoso.com*.
3. Optional :provide a URL string probe, which is a URL that the rule uses as a test. If the device on which this profile is installed is able to access this URL without redirection, the VPN will be established and the device will connect to the target URL. The user will not see the URL string probe site. An example of a URL string probe is the address of an auditing Web server that checks device compliance before connecting the VPN. Another possibility is that the URL tests the ability of the VPN to connect to a site, before connecting the device to the target URL through the VPN.
4. Choose one of these actions:
   - **Connect**
   - **Evaluate connection**, which has three settings
	  a. **Domain action**  - choose **Connect if needed** or **Never connect**
	  b. **Comma-separated list of domains** - you configure this only if you choose a **Domain action** of **Connect if needed**
      c. **Required URL string probe** - an HTTP or HTTPS (preferred) URL, such as *https://vpntestprobe.contoso.com*. The rule will check to see if there's a response from this address. If not, and the **Domain action** is **Connect if needed**, the VPN will be triggered.
      
     > [!TIP]
     >
     >An example of when you might use this action is when some sites on your corporate network require a direct or VPN corporate network connection, but others do not. If you list in **Comma-separated list of DNS search domains** *corp.contoso.com*, you can choose **Connect if needed** and then list specific sites within that network that may require VPN, such as *sharepoint.corp.contoso.com*. The rule will then check if *vpntestprobe.contoso.com* can be reached. If it can't, the VPN will be triggered for the sharepoint site.
   - **Ignore** - this causes no change in the VPN connectivity. If the VPN is connected, leave it connected, if it's not connected, don't connect it. For example, you may have a rule that connects the VPN for all of your internal corporate web sites, but want to make one of those internal sites accessible only when the device is actually connected to the corporate network. In that case, you would create an ignore rule for that one site.
   - **Disconnect** - disconnect devices from the VPN when the conditions are matched. For example, you could list your corporate wireless networks in the **SSIDs** field, and create a rule that disconnects devices from the VPN when they connect to one of those networks.

Domain-specific rules are evaluated before all-domain rules.


## Deploy the policy

1.  In the **Policy** workspace, select the policy that you want to deploy, and then choose **Manage Deployment**.

2.  In the **Manage Deployment** dialog box:

    -   To deploy the policy, select one or more groups to which you want to deploy the policy, and then choose **Add** &gt; **OK**.

    -   To close the dialog box without deploying it, choose **Cancel**.


After successful deployment, users will see the VPN connection name that you specified in the list of VPN connections on their devices.

A status summary and alerts on the **Overview** page of the **Policy** workspace identify issues with the policy that require your attention. Additionally, a status summary appears in the Dashboard workspace.
