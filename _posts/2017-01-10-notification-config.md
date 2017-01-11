---
author: samuraitruong
layout: post
title: "Notification config"
date: 2017-01-07 0:30
comments: true
category: Config.json
tags:
- notification
---

Necrobot2 support notificaiton in some when there important event happen and required your attention, just as captcha not been resolved, account limit reached, account banned....


Please change below config in config.json to get Notificaiton work with your bot

{% highlight json %}


 "NotificationConfig": {
    "EnablePushBulletNotification": false, 
    "EnableEmailNotification": false,
    "PushBulletApiKey": "xxxx",
    "GmailUsername": "xxx",
    "GmailPassword": "@xxx$",
    "Recipients": ""
  }

  {% endhighlight %}

* *Recipients* : Put your email address you want to recieve notification
* *EnablePushBulletNotification* : Allow bot send push notification to your phone by using [Push Bullet] (https://www.pushbullet.com/) service
* *PushBulletApiKey* : the Push bullet API key you get from Pushbuttle.com , note free API key only has 500 push a month, after you use all those limit, you won't be able to recieve notificaiton until next month.
* *GmailUsername*  and *GmailPassword" : Set your personal email in, bot will use this credential to send email to your Recipients

Cheers
 



