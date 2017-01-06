---
author: samuraitruong
layout: post
title: "How to config auto sniper with necrobot2"
date: 2017-01-07 8:30
comments: true
category: Config.json
tags:
- Snipe,AutoSnipe
---

Auto snipe is an interesting feature that necrobot ship with release but not turn on it by default. You need to turn it on to use, please follow below steps to get it up and running.

Search for "DataSharingConfig" in the config.json file or DataSharingConfig in excel tab if you run bot with excel config

EnableSyncData = true AutoSnipe = true

like this


{% highlight json%} 
"DataSharingConfig": {
    "EnableSyncData": true,
    "AutoSnipe": true,
    "DataRecieverURL": "ws://necrosocket.herokuapp.com/socket.io/?EIO=3&transport=websocket"
  },

{% endhighlight %}

You can set autosnipe IV filter at SnipeConfig section. this config will tell the bot that you want auto snipe to catch all pokemon has IV >= config value


{% highlight json%} 

"SnipeConfig": {
    "UseSnipeLocationServer": false,
    "SnipeLocationServer": "localhost",
    "SnipeLocationServerPort": 16969,
    "GetSniperInfoFromPokezz": false,
    "GetOnlyVerifiedSniperInfoFromPokezz": false,
    "GetSniperInfoFromPokeSnipers": false,
    "GetSniperInfoFromPokeWatchers": false,
    "GetSniperInfoFromSkiplagged": false,
    "MinPokeballsToSnipe": 20,
    "MinPokeballsWhileSnipe": 0,
    "MinDelayBetweenSnipes": 60000,
    "SnipingScanOffset": 0.005,
    "SnipeAtPokestops": true,
    "SnipeIgnoreUnknownIv": false,
    "UseTransferIvForSnipe": false,
    "SnipePokemonNotInPokedex": false,
    "UseSnipeLimit": true,
    "SnipeRestSeconds": 600,
    "SnipeCountLimit": 39,
    "ActivateMSniper": false,
    "MinIVForAutoSnipe": 97 ===> new config here. don't make it too low because bot will snipe all the time and ball run out fast
  },

{% endhighlight %}

You also able to overwrite this minIV by  setup invidiual pokemon snipe filter. For example, you want to snipe all dratini for candy, or snipe Pidgey for evolve

{% highlight json%} 
"SnipePokemonFilter": {
    "Lapras": {
      "SnipeIV": 0,
      "Moves": []
    },
    "Dragonite": {
      "EnableSnipe": false, dont mind about this flag , added to support excel config
      "SnipeIV": 0,
      "Moves": []
    },
    "Dratini": {
      "SnipeIV": 0,
      "Moves": []
    },
    "Pidgey": {
      "SnipeIV": 0,
      "Moves": []
    }
  }
{% endhighlight %}


By default bot will snipe all pokemon IV>=97% and snolax, dragonite, lapras, dratini. However, auto snipe set to off by default to use it you have to turn it on as above.


# My BOT sniper too much?
After you turn on autosnipe, bot likely to catch lot of high snipe pokemon by IV, to avoid and configure bot to autosnipe the pokemon you want, please see the config below for you reference

*Method 1*. Set AutoSnipeMinIV to 101 - Then bot won't autosnipe any pokemon, you need to overwrite pokemon individual snipe filter . For example, Only want to snipe any Lapras and 100%IV Dragonite and exclude all others pokemon, below is my config

{% highlight json%} 
"MinIVForAutoSnipe": 101,
{% endhighlight %}

{% highlight json%} 
 "Lapras": {
      "SnipeIV": 0,
      "Moves": [],
      "Operator": "or",
      "VerifiedOnly": false
    },
    "Dragonite": {
      "SnipeIV": 100,
      "Moves": [],
      "Operator": "or",
      "VerifiedOnly": true
    }
{% endhighlight %}

*Method 2* : Autosnipe all pokemon then exclude those pokemon you don't want snipe, see config below . In this case I want to snipe all 100% pokemon and except some crabby pokemon like zubat, pidgey.

Please note that this config only work from 1.0.0.47

{% highlight json %} 
"MinIVForAutoSnipe": 100,
{% endhighlight %}

Then in snipe individual filter

{% highlight json%} 
"Pidgey":  
      "SnipeIV": 101,
      "Moves": [],
      "Operator": "or",
      "VerifiedOnly": false
    },
    "Zubat": {
      "SnipeIV": 101,
      "Moves": [],
      "Operator": "or",
      "VerifiedOnly": true
    }
    {% endhighlight %}
Note: snipe.necrobot2.com recently update with crowndedsource then some data are faked, but in most case they are work.



Happy Bottin
Then in snipe individual filter

{% highlight json%} 
"Pidgey":  
      "SnipeIV": 101,
      "Moves": [],
      "Operator": "or",
      "VerifiedOnly": false
    },
    "Zubat": {
      "SnipeIV": 101,
      "Moves": [],
      "Operator": "or",
      "VerifiedOnly": true
    }
    {% endhighlight %}
Note: snipe.necrobot2.com recently update with crowndedsource then some data are faked, but in most case they are work.

 .. :)
 Then in snipe individual filter

{% highlight json%} 
"Pidgey":  
      "SnipeIV": 101,
      "Moves": [],
      "Operator": "or",
      "VerifiedOnly": false
    },
    "Zubat": {
      "SnipeIV": 101,
      "Moves": [],
      "Operator": "or",
      "VerifiedOnly": true
    }
    {% endhighlight %}
Note: snipe.necrobot2.com recently update with crowndedsource then some data are faked, but in most case they are work.


