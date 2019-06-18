---
title: "Run Dynamics 365 for Marketing with a portal or portal-free (Dynamics 365 for Marketing) | Microsoft Docs "
description: "How to decide whether to install Dynamics 365 for Marketing with or without a Dynamics 365 portal"
keywords: 
ms.date: 06/13/2019
ms.service: dynamics-365-marketing
ms.custom: 
  - dyn365-marketing
ms.topic: article
applies_to: 
  - Dynamics 365 for Customer Engagement (online)
  - Dynamics 365 for Customer Engagement Version 9.x
ms.assetid: b908216e-f09b-4f12-a78c-658ba3cc3e48
author: kamaybac
ms.author: kamaybac
manager: shellyha
ms.reviewer:
topic-status: Drafting
search.audienceType: 
  - admin
  - customizer
  - enduser
search.app: 
  - D365CE
  - D365Mktg
---

# Decide whether to install Dynamics 365 for Marketing with or without a Dynamics 365 portal

Read this topic to learn how you can run interactive marketing features for Dynamics 365 for Marketing by using an integrated Dynamics 365 portal or by using your own website or CMS system.

## How portal integration affects Marketing features

Dynamics 365 for Marketing provides several features that enable contacts to interact directly with the system. These are:

- **Landing pages**, which provide forms that contacts can use to register for mailing lists, free downloads, webinars, or other perks
- **Subscription centers**, which enable contacts to manage their mailing list subscriptions and personal information
- **Forwarding pages**, which enable contacts to forward marketing emails they have received from you (while preserving accurate tracking info)
- **The event website**, which enables contacts to read about and register for your events

Each of these features requires one or more webpages that are available publicly on the internet. Each page must furthermore be able to fetch information from Dynamics 365 for Marketing and also be able to submit data back to it. There are two ways to accomplish this:

- **Use Dynamics 365 portals**: This option is based on a Dynamics 365 add-on product that runs directly on the same tenant as your Dynamics 365 for Marketing instance. It enables  you to go live with Marketing without needing to manage or modify your own website. 
- **Use your own website or CMS system**: This option requires that you have your own website where you can host pages, add scripts, and embed forms from Dynamics 365 for Marketing. You can use this option in parallel with a Dynamics 365 portal if you wish.

The following table compares how each of the public-facing interactive features works when you implement it using a Dynamics 365 portal or your own website.

|   | **With Dynamics 365 portals** | **Without Dynamics 365 portals** |
| --- | --- | --- |
| Landing pages | Design and publish landing pages using the [graphical page designer](create-deploy-marketing-pages.md) in Dynamics 365 for Marketing. The pages run directly on the portal. | Design and publish landing pages on your own website or CMS system.<br><br>Enable forms by adding a Dynamics 365 for Marketing [form-capture script](embed-forms.md#form-capture) or by [embedding a marketing form](embed-forms.md#embed-form) created using the graphical form designer in Dynamics 365 for Marketing.<br><br>Include a [website-tracking script](register-engagement.md#monitor-visitors) generated by Dynamics 365 for Marketing on all landing pages to enable page visits and submissions to be tracked, and to enable customer-journey triggers to react to landing-page interactions. |
| Subscription centers | Design and publish subscription centers using the [graphical page designer](create-deploy-marketing-pages.md) in Dynamics 365 for Marketing. The pages run directly on the portal. | Design and publish subscription centers for your own website or CMS system using techniques similar to those for creating landing pages. [Prefilling must be enabled](embed-forms.md#form-prefil) for subscription center forms.<br><br>To satisfy the legal requirement, a [default subscription center](set-up-subscription-center.md#default-center) is published on the service fabric used by your Dynamics 365 for Marketing instance. This allows you to run email marketing campaigns even without a portal or external website. You can customize this page using the [graphical page designer](create-deploy-marketing-pages.md) in Dynamics 365 for Marketing.<br><br>Include a [website-tracking script](register-engagement.md#monitor-visitors) generated by Dynamics 365 for Marketing on all subscription-center pages to enable page visits and submissions to be tracked, and to enable customer-journey triggers to react to landing-page interactions.  |
| Forward-to-a-friend pages | Design and publish forwarding pages using the [graphical page designer](create-deploy-marketing-pages.md) in Dynamics 365 for Marketing.  The pages run directly on the portal. | Not supported. |
| Event website | The then-current version of the [event website](set-up-event-portal.md) is published automatically on the portal when you install Dynamics 365 for Marketing.<br><br>To update or customize the site, [download the latest version](developer/event-management-web-application.md) as an Angular project, customize it as needed using your preferred development tools, and then [publish the result on the portal](developer/portal-hosted.md). | [Download the current version](developer/event-management-web-application.md) of the [event website](set-up-event-portal.md) as an Angular project, customize it using your preferred development tools, and then [publish the result on your own website](developer/self-hosted.md). |

## Choose whether to use a portal when setting up a new Marketing instance

Each time you install Dynamics 365 for Marketing, you must choose whether or not to integrate it with a portal. 

To use a portal, you must have a separate Dynamics 365 portals license for each Dynamics 365 for Marketing instance that uses portal features. A free portals license is provided with Dynamics 365 for Marketing, but you can only have [one free portal per tenant](setup-troubleshooting.md#why-portal), so you must purchase additional portals licenses if you want to use a portal with more than one Dynamics 365 instance on your tenant. 

If you choose the non-portals option, then you'll be able to complete the Marketing setup even without an unconfigured portal available.

You can use portal features in parallel with website/CMS features provided you have a portal. You could, for example, start by using a portal for all interactive features and then slowly transition to an external website until you're ready to remove the portal entirely.

## Remove portal integration from an existing Marketing instance

You can choose to remove portal integration from a Dynamics 365 for Marketing instance at any time. If you choose to do so, the following will occur:

- Your portal license will be released and can then be reused with another Marketing instance, or another Customer Engagement app.
- All of the existing portal content and settings will be permanently deleted.
- All existing marketing pages in Dynamics 365 for Marketing will still be configured to be published on the now removed portal, so they will cease to function. However, their design and content will still be stored in Dynamics 365 for Marketing. If you re-add a portal, the pages will be reconfigured to use the new portal and you'll be able to publish them there.
- The event website will be removed. All events will still provide a link to the old website, so that link will no longer function. If you install the event website on your own server, it will work correctly right away (you won't have to update your event records), but if you want the links in your event records to open the new site, you must edit each record manually.

Before removing the portal, you should recreate your landing pages and subscription centers on your external website as needed, and design your customer journeys, [content settings](dynamic-email-content.md#content-settings), and email messages to link to them there. If you're using event management, then you should also install the event management website on your external server. When you've confirmed that everything is working as expected on your external site, you can remove the portal from your Marketing installation.

To remove portal integration from an existing Marketing instance:

1. [Launch the Marketing setup wizard](re-run-setup.md) for the instance you want to modify. You should be able to see that the **Use Dynamics 365 Portals** option is currently selected.

    ![Setup wizard for an existing instance with portal integration](media/fre-re-run.png "Setup wizard for an existing instance with portal integration")

1. From the **Other actions** panel, choose **Configure your portal**.

1. The portal admin site opens. Select **Portal actions** from the side navigator.

    ![Setup wizard for an existing instance with portal integration](media/portal-reset.png "Setup wizard for an existing instance with portal integration")

1. Select **Reset portal** and follow the instructions on your screen to reset the portal. [!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [Reset a portal](../portals/reset-portal.md).

    > [!WARNING]
    > When you reset the portal, all of the existing portal content and settings will be permanently deleted.

> [!NOTE]
> If you initially installed Marketing with portal integration enabled, then you did not receive a [default subscription center](set-up-subscription-center.md#default-center) (which otherwise would be running on the service fabric of your Marketing instance). You still won't have one after you remove the portal integration, and you can't manually create pages that run on the service fabric. You must therefore create at least one subscription center on your external website and configure your [content settings](dynamic-email-content.md#content-settings) to link to it before your remove the portal.

## Add portal integration to an existing Marketing instance

You can choose to add (or re-add) a portal to a Marketing instance at any time. When you do this, the following will occur:

- All of your external marketing pages and external event website will continue to function.
- If you initially installed Marketing with portal integration disabled, then you should have a default [default subscription center](set-up-subscription-center.md#default-center) (which runs on the service fabric of your Marketing instance). It will continue to be available even after you add the portal.
- If you have any portal-based marketing page designs left over in your system from a previous portals integration, these will be reconfigured to use the new portal automatically.

To add a portal to an existing Marketing installation that doesn't have one:

1. Make sure you have an unconfigured portal available on your tenant. Purchase a new one if necessary.

1. [Launch the Marketing setup wizard](re-run-setup.md) for the instance  you want to modify. You should be able to see that the **Use own webserver** option is currently selected.

    ![Setup wizard for an existing instance without portal integration](media/fre-add-portal-1.png "Setup wizard for an existing instance without portal integration")

1. Select **Use Dynamics 365 Portals**. The **Portal setup** dialog opens and shows some information about what to expect.

    ![Portal setup notice](media/fre-add-portal-2.png "Portal setup notice")

1. Select **OK** to continue. You go back to the setup wizard, which now shows the **Use Dynamics 365 Portals option** selected.

    ![Setup wizard with the portals option selected](media/fre-add-portal-3.png "Setup wizard with the portals option selected")

1. In the field now provided under the **Use Dynamics 365 Portals** option, enter a prefix for your portal URL in the field provided. Your contacts and customers can see the URL when they open a portal, so you should choose a subdomain name that they will recognize, such as your organization's name.

1. Select **Set up portal** to start setting up your portal. The process may take some time. You can track its progress by leaving the page open in your browser, but installation will continue uninterrupted if you choose to close your browser.

### See also

[Purchase and set up Dynamics 365 for Marketing](purchase-setup.md)  
[Create interactive features with or without portals](portals.md)  
[When do I need a portal license, and how can I get one?](setup-troubleshooting.md#why-portal)  
[Integrate with landing pages published on an external website](embed-forms.md)  
[Set up subscription lists and subscription centers](set-up-subscription-center.md)  
[Set up the event website](set-up-event-portal.md)  
[Build and host a custom event website](developer/event-management-web-application.md)