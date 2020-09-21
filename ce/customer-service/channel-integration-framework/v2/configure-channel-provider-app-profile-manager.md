---
title: "Preview: Configure channel provider using app profile manager in Channel Integration Framework (CIF) version 2.0| Microsoft Docs"
description: "Learn how to configure a channel provider using the app profile manager."
author: susikka
ms.author: susikka
manager: shujoshi
ms.date: 09/07/2020
ms.topic: article
ms.service: 
  - dynamics-365-customerservice
ms.custom: 
  - "dyn365-a11y"
  - "dyn365-developer"
---

# Preview: Configure channel provider using app profile manager

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

> [!IMPORTANT]
>
> - This feature is a preview, which means that it is made available to you before general availability so you can test and evaluate the preview and provide feedback to Microsoft.
> - This preview may employ reduced or different privacy, security, or compliance commitments than a commercial version. As such, this preview is not meant to be used with any "live" or production Customer Data, Personal Data, or other data that is subject to heightened compliance requirements. Any use of "live" data is at your sole risk and it is your sole responsibility to notify your end users that they should not include sensitive information with their use of the Preview.
> - This preview, and any support Microsoft may elect to provide, is provided "as-is," "with all faults," "as available," and without warranty. This preview is subject to the [Preview Terms](../../../legal/supp-dynamics365-preview.md).

The app profile manager is an out-of-the-box solution that lets you create targeted app experiences for agents and supervisors. More information: [App profile manager](../../../app-profile-manager/overview.md).

Channel Integration Framework version 2.0 is for multi-session applications such as Omnichannel for Customer Service and Customer Service workspace. Given below are the steps to configure a new channel provider using the app profile manager. To configure a third-party voice channel provider with the multi-session application, perform the following steps.

1. Log in to your Power Apps portal.

2. Under the available apps, select the ellipsis towards the right of **Omnichannel for Customer Service** or **Customer service workspace (preview)**.

3. Select **App profile manager**.

4. Select **App profiles** from the site map and then, select your app profile.

5. Select the **Channels** tab.

  > ![Select app profiles](../media/channel-app-profile-manager.PNG "Select app profiles")

6. Select **Add channel providers** and then, select **Create a new channel provider in Unified Interface**. The **New Channel Provider** page opens in a new tab.

  > ![Create new channel provider](../media/create-new-channel-provider-app-profile-manager.PNG "Create new channel provider")

7. Fill in all the required details to configure a new channel provider.

| Field | Description |
|-------|-------|
|Name|Name of the channel provider.|
|Unique Name|A unique identifier in the <*prefix*>_<*name*> format. <br>**IMPORTANT:** The following are required for the unique name:<ul><li> The prefix can only be alphanumeric and its length must be between 3 to 8 characters.</li><li>An underscore must be there between the prefix and name</li></ul>|
|Label|The label is displayed as the title on the widget.|
|Channel URL|The URL of the provider to host in the widget. See the JavaScript APIs on how to develop communication widget with Dynamics 365 Channel Integration Framework.|
|Enable Outbound Communication|Selecting a phone number in the Dynamics 365 Unified Interface page, the widget initiates the call or outbound communication.|
|Channel Order|The order precedence of the channel providers. That is, the priority to display the channel for the agents and unified Interface Apps.|
|API Version|The version of the Channel Integration Framework APIs.|
|Trusted Domain| An additional domain if the initial landing URL and the final domain from which the communication widget is hosted are different. Add the domain (URL) to access the Channel Integration Framework APIs. |
|Custom Parameter|This takes a text blob as input and `Microsoft.CIFramework.getEnvironment` will return this as value of key `customParams`.|
|Enable Analytics|Select `Yes` if you wish to enable analytics for your channel provider.|

  > ![Configure channel provider](../media/channel-provider-app-profile.png "Configure channel provider")

  > [!NOTE]
  > The `API Version` field is set to `2` when you navigate from the app profile manager.

8. After you have configured the channel provider, go back to the app profile manager and add the newly created channel provider to the app profile.
  
## See also

[App profile manager](../../../app-profile-manager/overview.md)<br />
[Enable outbound communication (ClickToAct)](enable-outbound-communication-clicktoact.md)<br />
[Microsoft.CIFramework.getEnvironment](../v2/reference/microsoft-ciframework/getEnvironment.md)