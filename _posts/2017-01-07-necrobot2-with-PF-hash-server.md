---
author: samuraitruong
layout: post
title: "Runing Necrobot2 with PF Hash service API"
date: 2017-01-07 8:30
comments: true
category: auth.json
tags:
- Auth, Hash,Starter Config
---

Necrobot 2 release 1.0.0.34 and above now support to running with Pokefamer hash API

What is Pokefamer hash API? - please read here [https://talk.pogodev.org/d/51-api-hashing-service-by-pokefarmer](https://talk.pogodev.org/d/51-api-hashing-service-by-pokefarmer)

Basically, API no longer open source and free, to use latest API you have to using Pokefamer service, Just need to buy a key from them and use it with Necrobot

What is RPM? RPM is request per minute, that is how many request that key allow your bot to make in a minutes, the lowest package is 5$ = 150 RPM that enough for 3+ instance of bot running at the same time.

How to buy it? Please by it from Pokefamer they provide link above

How to configure to use it?

If you are brand new user, at the very first time you run the bot, the form will display as you to choose API method you want to use.

Select Pogodev API option, then enter your API key that you got from email after purchase it

Necrobot also support legacy api - 0.45. use it at your own risk (this is free )

If you are existing necro user, you need to edit auth.json to add your key, look for the config below in you json.config
{% highlight json%}
  "APIConfig": {
    "UsePogoDevAPI": true,
    "AuthAPIKey": "xxxxxxxxxxxxxx",
    "UseLegacyAPI": false
  },```
{% endhighlight json%}
Change it with your key then start bot

[Read More  -Necrobot2 supported API version ](/auth.json/2017/01/07/necrobot2-supported-api/)


Happy botting
