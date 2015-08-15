---
layout: post
title:  "Week 3 - Communications with Messaging Platforms"
date:   2015-08-15 23:30:42
categories: week-3 api
---

After the conversation with friends last week, it is clear that a bespoke messaging system for Project Gather wouldn't work well at launch. In order to get people into the platform and be loyal users Project Gather has to be able to jump into their communication platform of choice well so they could use Project Gather seamlessly as a form of first test. A bespoke messaging system for Project Gather might still be necessary, but a system capable of tapping into user's messaging platform of choice should prove to be more powerful.

In order for that to happen, analysis must be made on the messaging platforms. For Project Gather to be able to tap into them, they should have a way to let external apps use the features in the messaging platform. These are called Application Programming Interfaces (API) and they let other apps to communicate to them only with commands allowed. These APIs vary according to the messaging systems implementation, and some even don't have APIs at all for reasons. Tapping onto these APIs take up a long time to test because every API is different and might not have the necessary permissions and interfaces, like sending messages on behalf of Project Gather or the user to the people involved in the process of organizing the event.

With that in mind, I set off to find the APIs of the popular messaging platforms around the world. Here's the list.

## WhatsApp  
WhatsApp has been very clear about giving API access to developers, and the answer is **no**, not at the moment. The reason behind it is that the team at WhatsApp only wants communication between users and not allow communication from other media like bots, automated messages or any other form of messages that aren't from real users.

## LINE
LINE [has an API](https://developers.line.me/), **yes**. The API is also very diverse from SDKs for mobile devices — Android and iOS, a JavaScript SDK, and a REST API. They allow for a multitude of data able to be fetched from, but that's mostly it. The amount of APIs related towards sending data in is scarce, with the only messages allowed to be sent via the APIs are link messages pointing towards a certain website or app.

That API allows for messages to be sent on behalf of the user pointing to Project Gather's URL related to the action the user takes on that specific event being organized, so it is still very possible for integration with LINE. If a text-only message needs to be sent, LINE has a URL dedicated towards it that the user can go to in order to prepare a text message to be sent. That means the user has to open a URL over on their browser though.

## KakaoTalk
KakaoTalk is a strong competitor with LINE, and unsurprisingly, **yes**, they [have an API](https://developers.kakao.com/features/kakao#카카오-링크) and what they offer is similar to LINE. It has Android and iOS SDKs as well as a JavaScript one and a REST API too, and they only allow link messages just as LINE does as well via a service they call the Kakao Story. They also have the URL to prepare a text message for the user to be sent too.

The API documentation is written in Korean, which is expected as the API represents other services Kakao has and they are heavily used in Korea for other forms of features such as payments and calling taxis. Google Translate seems to work well with it, which is a relief.

## WeChat
WeChat's presence in China is as strong, if not stronger than KakaoTalk's presence in Korea. **Yes**, it [has an API](http://dev.wechat.com/), but the APIs for other features only available in China is excluded from the documentation, it seems.

Nevertheless, the API is in English and it allows developers to send messages on behalf of the user only. But, the messages are not limited to link messages as what LINE and KakaoTalk does. You can send text, links, video and even music with it. The only drawback is that the API is only available as an SDK for Android and iOS, and considering that Project Gather is going to be released on the web at launch first with interactions with the messaging systems only depending on URLs, WeChat seems only available to work with after launch as an additional future in the long run.

## Telegram
Telegram's [API](https://core.telegram.org/api) approach is different than the rest of the messaging platforms. Unlike the others approach of dominating a certain part of the world, Telegram is very diverse even though rarely I find users using it. But, Telegram is very developer-friendly with it being open-sourced and all, so **yes**, it wouldn't be a surprise if it has an API.

The difference is that the API they have are intended to be used to make custom Telegram clients and apps. But they have what they call as the [Bot API](https://core.telegram.org/bots). Essentially this allows developers to send messages on behalf of the system, and this is the best API concept to be used for Project Gather. They use IRC-like commands (/command) for interactions and the developer uses REST API requests over HTTPS. **Very, very great!**

However they have one flaw though, as found in the documentations.

![They're bad at doing dishes.]({{site.baseurl}}/images/{{page.title | slugify}}/bots.png)

## Path Talk
This messaging system hasn't taken off, but the social media counterpart, Path, is very popular in Indonesia. But sadly, they have **no** APIs for the messaging system — only the social media APIs.

## Slack
Slack needs a mention on this list. It's a very great team communication platform and I've been loving Slack after using it recently.

**Yes**, Slack [has an API](https://api.slack.com/) and the great features Slack provides are heavily influenced by their offering of APIs. The API they provide allows for the same feature Telegram provides — bots. So there is no need for explanations as the system will work the same when implemented on both Slack or Telegram.

## BlackBerry Messenger
Another messaging system that is popular mostly in Indonesia. Sadly, **no** APIs that can be used on the web or Android and iOS. The APIs they have can only be used on BlackBerry devices only.

## Google Hangouts
Google Hangouts is a peculiar one since it is essentially a video calling platform at the start, but now people use it for messaging as well. **Yes**, it has an API, but for the chat counterpart it doesn't. The API of Google Hangouts allows for apps to take advantage over the video calls, which also opens up a possibility of Project Gather to be used on Google Hangouts or other video calling platforms as well.

That's quite long, but that is all of the messaging platforms that I've checked over the week.

Analyzing all these platforms give ideas about how communication should be for Project Gather between these messaging apps. Bots that represent the system is the first choice plan of implementation, with link messages to a URL specified by Project Gather that points to the event information hosted as the fallback plan of implementation. There is also a possibility that if these methods are impossible for the chosen messaging platform, the user organizing the event can be given a text with the information needed to copy and paste to the messaging platform chats.

But for now, with Project Gather being a startup work, I need a platform to be chosen by the end of this week. That way I can prioritize implementation over the chosen platform and experiment with it to see if it's viable or not. Telegram or Slack seem to be the obvious choice of implementation since there are bot APIs, but considering that they are not that popular it might not worth doing as the first platform of choice. LINE and WeChat seem like more of a better choice when it comes to reaching as much users as possible.

But we'll see. Hopefully I can come up with a decision next week.
