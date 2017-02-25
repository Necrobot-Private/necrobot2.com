---
author: RoskamiesX
layout: post
title: "Human-like configuration"
date: 2017-02-25 14:41
comments: true
category: Config.json
tags:
- Delay,Human,Config
---

Sometimes when you are botting, you wan't to play safe and make your bot to act like a real client. There is few things to watch out in the config.json in order to make your bot more safer. I will list them and describe them below.


How does your player move? Movement is defined in LocationConfig-section. Note here that do you act like you are on foot, bicycle or a car? Avarage human walks 5 km/h, bicycler should go from 10-40 km/h and car can go up to 180 km/h. Please note that in order to hatch eggs, you should se speed under 12 km/h.

So for example, if you wish your bot to move like walking human, set config to this:
{% highlight json %}

  "LocationConfig": {
	...
    "WalkingSpeedInKilometerPerHour": 5.0,
    "UseWalkingSpeedVariant": true,
    "WalkingSpeedVariant": 1.0,
	...
  },

{% endhighlight json %}

Then there is actions you can make and delays for them (to seem like a real client). There is new added feature to make your pokemoncatching a real client-like. These are things that you should understand:
* Inside PokemonConfig section: DelayBetweenPokemonCatch. This is delay when you have caught the pokemon and start to capture a new one.
* Whole PlayerConfig section: these delays are applied to actions your bot can do. It menas that if you set "DelayBetweenPlayerActions": 1000, bot can interact with the world once every second.
* New HumanlikeDelays section: These delays can be activated to make a catching a pokemon more realistic. Delays are applied based on what phase is your catch going (Throwing ball, Waiting catch animation etc.) You need to put "UseHumanlikeDelays": true, if you wish to use these and PokemonConfig:DelayBetweenPokemonCatch to 0

So this is example how to make bot more humanlike (this might slower your xp/h but will make you more harder to be banned):

{% highlight json %}

  "PokemonConfig": {
    ...
    "DelayBetweenPokemonCatch": 0,
	...
  },
  
  ...
  
  "PlayerConfig": {
    "DelayBetweenPlayerActions": 2000,
    "EvolveActionDelay": 25000,
    "TransferActionDelay": 2500,
    "RecycleActionDelay": 2500,
    "RenamePokemonActionDelay": 2500,
    "UseNearActionRandom": true,
    "RandomizeSettingsByPercent": 5,
    "AutoFinishTutorial": false
  },
  
  ...
  
  "HumanlikeDelays": {
    "UseHumanlikeDelays": true,
    "CatchSuccessDelay": 13000,
    "CatchErrorDelay": 1000,
    "CatchEscapeDelay": 3500,
    "CatchFleeDelay": 2000,
    "CatchMissedDelay": 1500,
    "BeforeCatchDelay": 1500
  }  

{% endhighlight json %}
Notice that these values has been clocked from real client thus you should not lower these from defaults if you wish to act like a real client. If you use HumanlikeDelays, you can lower DelayBetweenPokemonCatch to 0 as humanlike will handle it and lower your DelayBetweenPlayerActions to about 2 secondish.
If you lower default HumanlikeDelays, you can boost your xp/h, but is can be detectable by Niantic as the real client cannot make CatchSuccess under 13 seconds in any way.

Feel free to drop issue with HumanlikeDelays subject in github, or ping me in discord if i'm online :)