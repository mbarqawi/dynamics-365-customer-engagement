---
title: "Asynchronous channel support"
description: "Adaptive card, emojis, and other support in asynchronous channels in Omnichannel for Customer Service."
author: platkat 
ms.author: ktaylor
manager: shujoshi
ms.date: 08/06/2020
ms.service: 
  - "dynamics-365-customerservice"
ms.topic: article
---

# Asynchronous channel support

[!INCLUDE[cc-use-with-omnichannel](../../includes/cc-use-with-omnichannel.md)]

## Card support

| Channel              | Adaptive card | Hero card | Receipt card | Thumbnail card | Signin card | Audio card |
|----------------------|---------------|-----------|--------------|----------------|-------------|------------|
| Microsoft Teams      | ✔             | ✔         | ✔            | ✔              | ✔           | ❌          | 
| Facebook             | ⚠🔶           | ✔         | ✔            | ✔              | ✔           | 🌐         | 
| LINE                 | ⚠🔶           | ✔         | ✔            | ✔              | ✔           | 🌐         | 
| Custom (Telegram)    | ⚠🔶           | ✔         | ✔            | ✔              | ✔           | 🌐         | 
| Custom (Direct Line) | ✔             | ✔         | ✔            | ✔              | ✔           | ✔          | 

> [!Note]
> The Direct Line channel supports all the above mentioned cards, but it's up to the client to implement them.<br />
> Video card support can be achieved by adding the video URL in the adaptive card. 

✔: Supported - Card is supported fully with the exception that some channels only support a subset of Card Actions and/or may limit the number of actions allowed on each card. Varies by channel.

⚠: Partial support - Card may not be displayed at all if it contains inputs and/or buttons. Varies by channel.

❌: No support

🔶: Card is converted to image

🌐: Card is converted to unformatted text - Links may not be clickable, images may not display, and/or media may not be playable. Varies by channel.

These categories are intentionally broad and do not fully explain how every card feature is supported in each channel due to the many possible combinations of cards, features, and channels. Please use this table as a base reference, but test each of your cards in the desired channel(s).

For more information, refer to these external sources:
  - [Sending and Receiving Media with WhatsApp Messaging on Twilio](https://support.twilio.com/hc/articles/360017961894-Sending-and-Receiving-Media-with-WhatsApp-Messaging-on-Twilio-Beta-)
  - [Upload media, Twitter developer documentation](https://developer.twitter.com/docs/media/upload-media/uploading-media/media-best-practices)

## Suggested actions support

Suggested action is supported fully with the exception that some channels may limit the number of actions allowed. The number of actions supported varies by channel.

| Channel            | Suggested actions support       |
|--------------------|---------------------------------|
| Microsoft Teams    | No                              |
| Facebook           | Yes                             |
| LINE               | Yes                             |
| Custom messaging (Telegram) | Yes                    |
| Custom messaging (Direct Line) | Yes                 |

## File attachment support
You can file attachments on the **General settings** tab of a channel so that customers and agents can send files as attachments. Attachments that customers send to agents are referred to as inbound attachments, and attachments that agents send to customers are referred to as outbound attachments. For more information about file attachments, see [Enable file attachments](enable-file-attachments.md).

| Channel              | Inbound attachments                        | Outbound attachments                  |
|----------------------|--------------------------------------------|---------------------------------------|
| Microsoft Teams      | Image, Audio, Video, Documents, Gif, Emoji | Image, Audio, Video, Documents, Gif   |
| Facebook             | Image, Audio, Video, Documents, Gif, Emoji | Image, Audio, Video, Document, Gif    |
| LINE                 | Image, Audio, Video, Gif                   | Image, Audio, Video, Documents, Gif   |
| Custom (Telegram)    | Image, Audio, Video, Documents, Gif, Emoji | Image, Audio, Video, Documents, Gif   |
| Custom (Direct Line) | All types except blocked types in org      | All types except blocked types in org |
| Twitter              | Image, Video, Gif, Emoji                   | Image, Video, Gif                     |
| WeChat               | Image, Audio, Video                        | Image, Audio, Video                   |
| WhatsApp             | Image, Audio, Video, PDF                   | Image, Audio, Video, PDF              |

> [!Note]
> - For Microsoft Teams, when a customer sends an emoji from Teams client, the agent will receive a .png image. When an agent sents a .gif image outbound, the customer will receive a .png image. 
> - The Direct Line channel supports the above attachment types, but it is up to the client to implement them.
> - For LINE inbound and outbound, when sending a .gif image, the recipient will receive a .jpg image.

## Emoji support 

| Channel            | Emoji behavior                                                      |
|--------------------|---------------------------------------------------------------------|
| Facebook           | Yes. Emoji in text, like “😀”                                       |
| Twitter            | Yes. Emoji in text, like “😀”                                       |
| Microsoft Teams    | Yes. Emoji in .PNG image                                            |
| WeChat             | Yes. When an emoji is sent, the recipient sees characters, like :-) |
| LINE               | Yes. When an emoji is sent, the recipient sees a sticker.           |
| WhatsApp           | Not supported.                                                      |
| Custom messaging (Telegram) | Yes. Emoji in text, like “😀”                              |
| Custom messaging (Direct Line) | Yes. Emoji in text, like “😀”                           |

> [!Note]
> The Direct Line channel supports emojis, but it's up to the client to implement them.

## Sticker support

| Channel            | Sticker behavior                                                    |
|--------------------|---------------------------------------------------------------------|
| Facebook           | Yes, as .png image                                                  |
| Twitter            | Not supported.                                                      |
| Microsoft Teams    | Not supported.                    |
| WeChat             | Not supported. Recipient sees "Unsupported message" text.           |
| LINE               | Not supported. Recipient sees "Sticker" text.                       |
| WhatsApp           | Not supported.                                                      |
| Custom messaging (Telegram) | Not supported.                                             |
| Custom messaging (Direct Line) | Yes, as sticker image                                   |

> [!Note]
> The Direct Line channel supports stickers, but it's up to the client to implement them.

### See also

[Overview of channels](channels.md) <br />
[Bring your own custom messaging channel: Direct Line bot](../developer/how-to/bring-your-own-channel.md) <br />
[Configure custom messaging channel](configure-custom-channel.md) 
[Enable file attachments](enable-file-attachments.md)