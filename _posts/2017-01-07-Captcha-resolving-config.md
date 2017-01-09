---
author: samuraitruong
layout: post
title: "Captcha Resolving config"
date: 2017-01-07 20:30
comments: true
category: Config.json
tags:
- Captcha;Manual Captcha;Auto Captcha
---

No matter what you are bot or human, in some case Niantic will detect your activity as a suspicious activities then they will display a captcha to verify you are not a bot. Resolving captcha in bot very important because once captcha display, all activity need to stop until it resolved. If we keep the bot sending API call to server, They may ban us, so please follow below config to make sure that we are good to run bot 247

# Manual resolving config

We are using Chrome browser to display captcha then you solve captcha manualy, then bot will continue after you solve the captcha, after 120 - configurable time and you didn't solve captcha, bot will stop 
- Display message and exit if you are in single bot mode
- Send notification and change to next bot also block current bot for 15 mins if you in multi accounts mode

{% highlight json %}

 "CaptchaConfig": {
    "AllowManualCaptchaResolve": true,
    "ManualCaptchaTimeout": 120,
    "PlaySoundOnCaptcha": true,
    "DisplayOnTop": true
    ...........
  }
{% endhighlight %}

```diff
--NOTE: MANUAL CAPTCHA SOLVING REQUIRE CHROME BROWSER INSTALL ON YOUR MACHINE
```

# Auto resolving captcha with 2Captcha service

[2Captcha](http://2captcha.com) is the online service provide that workers with low price to resolve captcha for you, the cost quite good only 3$/1000 captcha resolved. 
- Go to 2captcha.com and register an account
- Deposit an small amount of money into your account
- Make sure Sandbox off (in developer menu)
- Copy API key and fill the config as below

{% highlight json %}

 "CaptchaConfig": {
    "AutoCaptchaRetries": 3,
    "TwoCaptchaAPIKey": "xxxxxxxxxxxxxxxxxx"
    "Enable2Captcha": true,
    ...........
  }
{% endhighlight %}

# Auto resolving captcha with SolutionCaptcha service
[Solution Captcha](https://www.captchasolutions.com/clients/login/) also provide same service as 2Captcha, You need register an account, order package of tokens then use them 

{% highlight json %}

 "CaptchaConfig": {
    "AutoCaptchaRetries": 3,
    "CaptchaSolutionAPIKey": "xxxxxxxxxxxxxxxxxxxxxxxxxxxx",
    "CaptchaSolutionsSecretKey": "xxxxxxxxxxx",
    ...........
  }
{% endhighlight %}


Sometimes, Auto captcha service is down or not stable, then bot will fallback to manual captcha before sending notification and stop, make sure you have notification setup actioned just in case bot not able to resolve automatically.


Happy botting .. :)
