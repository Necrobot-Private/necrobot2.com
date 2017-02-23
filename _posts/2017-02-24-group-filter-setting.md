---
author: samuraitruong
layout: post
title: "Group filter settings"
date: 2017-02-22 0:30
comments: true
category: Config.json
tags:
- Snipe,Upgrade,Config
---

If you are familiar with necrobot setting/filter/config system you will see if very powerful and flexiable. however, for newbie , most of them strugge with the huge json file. The new requirement had been implmenet to clean up and make setting shorter and easier to read and config. What what I call group filter setting.

As you all know that you can put 720 different filter for control your bot but it seem overkill because most we should partition pokemons to a group. this change allow you do that

You will see the new key config add to your filter look like below (SnipeFilter)
{% highlight json %}

 "Snorlax": {
      "SnipeIV": 95,
      "Moves": [],
      "Operator": "and",
      "VerifiedOnly": false,
      "Priority": 1,
      "AutoSnipeCandy": 2000,
      "Level": 30,
      "AllowMultiAccountSnipe": false,
      "AffectToPokemons": ["lapras","dragonite"]
    },

{% endhighlight json %}

Above example I grouped Lax, Lap, and Nite to same config before I have to make 3 separate config if I want to overwrite the global config setting. If you want to keep moves, you have to put all moves set of 3 type in the moves setting

Of course, the invidiual filter still work, and priority is the single filter over group filter.

This change was apply for 
* Snipe filter
* Upgrade Filter
* Transfer Filter
* Favorite filter


(Will add support for bot switch and human walk snipe later )

I also would say something about how AutoSnipeCandy work, this feature allow you collect candy for specific pokemon. with the setting above , I tell bot to get 2000 candies for those pokemon. Bot will ignore all setting about Level, Move, IV to get enought 2000 candies, after it collected 2000 candies, bot only snipe level 30 and IV 95+ , (Move set  if you set in)


