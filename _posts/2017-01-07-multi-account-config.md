---
author: samuraitruong
layout: post
title: "How to config multiple account"
date: 2017-01-07 1:30
comments: true
category: auth.json
tags:
- config, multi account;switches
---

If you have high EXP/H bot config then bot will reach to 24h limti very soon, with out Multi account config bot will pause or exit after hit that limit. Multiple account was design to keep bot run 247 and level up as many as account per bot since we can run limited instance on same IP address.

Just few thing need to config to bring this feature to work, please follow below step

## Allow bot multiple mode and add bot
You need to do this in auth.config as below

{%highlight json%}
"AllowMultipleBot": false, =>  turn it to true
  "Bots": [
    {
      "AuthType": "ptc",
      "GoogleUsername": null,
      "GooglePassword": null,
      "PtcUsername": "xxxxx",
      "PtcPassword": "123456"
    },
    {
      "AuthType": "ptc",
      "GoogleUsername": null,
      "GooglePassword": null,
      "PtcUsername": "yyyyy",
      "PtcPassword": "123456"
    }
]
{% endhighlight%}
```Note: Auth.json change require bot restart```

Next steps, you need to config to tell your bot when need to change account, by default the config quite good already, but you can customize them as you wish. The need to be done in config.json

## Config the logic for bot switches
{%highlight json%}
 "MultipleBotConfig": {
    "RuntimeSwitch": 25,
    "OnRarePokemon": true,
    "MinIVToSwitch": 99.0,
    "EXPSwitch": 50000,
    "PokestopSwitch": 3000,
    "PokemonSwitch": 3000,
    "PokemonPerHourSwitch": 100,
    "StartFromDefaultLocation": true,
    "PokestopSoftbanCount": 10,
    "DisplayList": true,
    "SelectAccountOnStartUp": true,
    "CatchFleeCount": 5,
    "SwitchOnCatchLimit": true,
    "SwitchOnPokestopLimit": true
  },

{% endhighlight%}

* **EXPSwitch** : When bot colect this amount of EXP, bot will trigger switch to change to next account. 
* **RuntimeSwitch** : After bot ran for x minutes, bot will trigger switch to change to next account. 
* **OnRarePokemon** : Bot will trigger switches after caught or encountered good pokemon that you define in MinIVToSwitch or in the filter below
{%highlight json%}
"BotSwitchPokemonFilters": {
    "Dragonite": {
      "IV": 10, switch when catch or encountered dragonite > 10% iV
      "RemainTimes": 60, //not use
      "Operator": "or",
      "LV": 0, nto implemented, place holder only
      "Moves": [] //not implemented, place holder only
    },
    "Hitmonchan": {
      "IV": 10,
      "RemainTimes": 60,
      "Operator": "or",
      "LV": 0,
      "Moves": []
    } 
{% endhighlight%}

```Note: Per pokemon config will overwrite global value of MinIVToSwitch```


Happy botting .. :)
