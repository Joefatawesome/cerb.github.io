---
title: Send room notifications to HipChat from a Cerb bot
permalink: /examples/hipchat/room-notifications
layout: integration
jumbotron:
  title: Send room notifications to HipChat from a Cerb bot
  tagline: ""
  breadcrumbs:
  -
    label: Examples &raquo; HipChat &raquo;
    url: /examples/hipchat/
---

## Introduction

This article will demonstrate how to send messages to HipChat from a Cerb bot.

When you create a custom integration in [HipChat](https://hipchat.com) you're given a unique URL with a built-in authentication token. This allows you to send messages to the specified room from a third-party application using a simple HTTP POST[^http-post].

Rather than using this URL directly in various actions within a Cerb bot, we're going to create a reusable behavior for sending a notification to HipChat that several other bots can use.  This protects the pre-authenticated HipChat URL, and it also improves maintainability since you make changes to the behavior in a single place.

## Add an integration in HipChat

First, we need to create a new custom integration in HipChat to generate the URL we'll use to send messages.

Log in to HipChat from a web browser.

Click **Integrations** in the top navigation.

Select a room and click **Build your own integration**:

<div class="cerb-screenshot">
<img src="/assets/images/integrations/hipchat/room-notifications/create-integration.png" class="screenshot">
</div>

Name it _Cerb_ and click the **Create** button:

<div class="cerb-screenshot">
<img src="/assets/images/integrations/hipchat/room-notifications/name-integration.png" class="screenshot">
</div>

You should see your POST URL:

<div class="cerb-screenshot">
<img src="/assets/images/integrations/hipchat/room-notifications/post-url.png" class="screenshot">
</div>

With the above URL we can use the HipChat room notification API[^hipchat-notify-api] to send messages from Cerb.  For instance, here's a new message in JSON[^json] format:

{% highlight json %}
{
    "color": "random",
    "message": "This is a new message.",
    "notify": false,
    "message_format": "text"
}
{% endhighlight %}

## Build the reusable bot behavior in Cerb

Now we'll create the behavior in Cerb that POSTs to this URL when a bot wants to send a message to the HipChat room.

Log in to Cerb as an administrator.

From **Search &raquo; Virtual Attendant**, click **(+)** in the top right of the worklist to add a new bot.

<div class="cerb-screenshot">
<img src="/assets/images/integrations/hipchat/room-notifications/cerb-new-bot.png" class="screenshot">
</div>

You can find the HipChat logo on their Twitter profile[^hipchat-twitter].

Optionally, you can also restrict **Events** to _Custom virtual attendant behavior_ and **Actions** to _Execute an HTTP request_.

Once finished, click the **Save Changes** button.

Click **HipChat Bot** in the worklist:

<div class="cerb-screenshot">
<img src="/assets/images/integrations/hipchat/room-notifications/cerb-bot-worklist.png" class="screenshot">
</div>

On the **Behaviors** tab, click the **Create Behavior** button:

<div class="cerb-screenshot">
<img src="/assets/images/integrations/hipchat/room-notifications/cerb-new-behavior.png" class="screenshot">
</div>

Select the **Import** tab and paste the following behavior:

{% gist cerb/b95c1f67df59049f6781eecef72c8a3d %}

Cerb will prompt you for the URL that HipChat generated for you in the first step above.  Paste it into the text box and click the **Continue** button:

<div class="cerb-screenshot">
<img src="/assets/images/integrations/hipchat/room-notifications/cerb-behavior-import.png" class="screenshot">
</div>

The new behavior has been automatically created for you:

<div class="cerb-screenshot">
<img src="/assets/images/integrations/hipchat/room-notifications/cerb-behavior.png" class="screenshot">
</div>

Now let's test the behavior to make sure it's working properly. Click on the **Custom virtual attendant behavior** node and select **Simulate Behavior** from the menu:

<div class="cerb-screenshot">
<img src="/assets/images/integrations/hipchat/room-notifications/cerb-behavior-sim-menu.png" class="screenshot">
</div>

In the simulator, type a test message and click the **Simulate** button:

<div class="cerb-screenshot">
<img src="/assets/images/integrations/hipchat/room-notifications/cerb-behavior-sim.png" class="screenshot">
</div>

You should see the new message in HipChat:

<div class="cerb-screenshot">
<img src="/assets/images/integrations/hipchat/room-notifications/hipchat-new-message.png" class="screenshot">
</div>

## Use the new behavior from any Cerb bot

In any bot behavior, you can now add a new **Run behavior** action and call this HipChat behavior:

<div class="cerb-screenshot">
<img src="/assets/images/integrations/hipchat/room-notifications/cerb-run-behavior.png" class="screenshot">
</div>

Your message can include any placeholders from that event.  For example, if you want to notify a room about new tickets, you can include the mask, subject, and the profile URL.

## References

[^json]: <https://en.wikipedia.org/wiki/JSON>
[^http-post]: <https://en.wikipedia.org/wiki/POST_(HTTP)>
[^hipchat-notify-api]: <https://www.hipchat.com/docs/apiv2/method/send_room_notification>
[^hipchat-twitter]: <https://twitter.com/hipchat>