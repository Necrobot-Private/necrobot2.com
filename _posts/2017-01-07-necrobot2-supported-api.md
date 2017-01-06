---
author: samuraitruong
layout: post
title: "Necrobot2 supported API version"
date: 2017-01-07 10:30
comments: true
category: auth.json
tags:
- auth, hash server, hash key
---

Since 0.49 API forced to update, PogoDev and RE won't release public API any more, It mean that we won't have a latest API to run bot, However, Pogodev & Pokefamer came with paid solution to access their service which using lastest api version to hashing data before send back to Niantic.

*What API available in necrobot2
Necrobot allow you choose Legacy API 0.45 or Using PF hash server, the only thing you need do do is update APIconfig section in auth.json as below

{% highlight json%}  

 "APIConfig": {
    "UsePogoDevAPI": true,
    "AuthAPIKey": "PUT YOUR API KEY HERE",
    "UseLegacyAPI": false,
    "DiplayHashServerLog": true
  }

{% endhighlight %} 

Bot require you select 1 option to run. 

# Should I use Legacy version?

Quick anwser is no, because old API easy to be tracked by Niantic and flag your account, most likely that you account will be ban in their ban wave.  If you running bot with Old API, bot will display an warning message when starting and pause in 15 sec for you have a chance your mind and close it before it make any call to server.


# Where I can buy Hash API

Necrobot doesn't provide service for API key, you have to buy it from Pokefamer, please read below
[API Hashing Service by PokeFarmer](https://talk.pogodev.org/d/51-api-hashing-service-by-pokefarmer,"API Hashing Service by PokeFarmer")
Sometime you will get the key by email very fast after checkout, however, most case will require few hours before you get email from them.

# What is RPM and what should I buy

RPM is request per Minute that bot make to server. depend on your config and delay as well as your network perfomance, RPM from our bot will varied, Normaly, One bot instance will ue about 40 RPM, It mean that with the minumun key 150 RPM you able to run 3 bots. Also, if you want to see how many request that your bot config use, you can turn Verbose log on

{% highlight json%}  
"DiplayHashServerLog": true json

{% endhighlight %} 

Note: auth.json not auto reload when you change, any change in this file require you restart bot.


Happy botting .. :)
 