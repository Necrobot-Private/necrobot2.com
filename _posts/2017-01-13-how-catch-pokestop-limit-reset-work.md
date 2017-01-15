---
author: samuraitruong
layout: post
title: "How the limit reset works?"
date: 2017-01-11 0:30
comments: true
category: Announcement
tags:
- GUI
---

Reset limit is awesome feature that control number of pokestop or pokemon cauht winthin the limit to avoid softban affected on your account. 

# What are limits?

Niantic apply some limit on your statistic to detect your account is BOT not a human that you should know
- 1000 pokemon caught limit in 24 hours
- 2000 pokestop visit/looted in 24 hours

If total of pokemon caught or pokestop looted in pass 24 hours over that values, you will triggered softban on your account and take a flag for higher ban risk

# How to avoid it?
Necrobot has implement the kill switch will allow you never over the limit. it will turn on by default in branch new bot setup, however, it will able to turn of by you in config.json

- Catch limit

{% highlight json %}

	 "PokemonConfig": {
	    "UseCatchLimit": true,
	    "CatchPokemonLimit": 998,
	    "CatchPokemonLimitMinutes": 1470
	    ............
	}

{% endhighlight %}

* *CatchPokemonLimit* :Number of pokemon you allow bot catch in duration setup in CatchPokemonLimitMinutes
	* *CatchPokemonLimitMinutes* : Duration 1470 minute ~ 24h

- Pokestop limit

{% highlight json %}

 "PokeStopConfig": {
    "UsePokeStopLimit": true,
    "PokeStopLimit": 1700,
    "PokeStopLimitMinutes": 1470
  }

{% endhighlight %}

```NOTE : When you turn on these option, BOT will output the message count everytime it catch pokemon or spin pokestop.```

# How bot works
Bot will store all data about catch pokemon and pokestop in a local database file name sessiondb in your account folder (under config folder). Everytime before catch pokemon or spin pokestop, bot will remove all data which older than 24 hours then count number of item in still there, if number of remaining item >= limit, Bot will cancel action and stop or keep going depend on your config

It mean that the reset happen in every minutes let see this example

- I start bot and catch 150 pokemon in 1 hours, I go to to take a nap for 30 min 
- Assume that in first 30 min I catch 100 pkm
- After wake up, I open bot and catch will still 150 because those data < 24h


another example:

I keep that bot running for 12h and it hit the limit 998, OK I stop bot

1 hour later, I open bot , remember in first hours my bot caught 150 pkm, then now the limit been reseted to 998-150. with that amount I can keep bot running until total number item >= 998

That is Pro-rata data cycle, not mean if you start bot from 7AM, then you have to wait util 7AM next day to reset it back to 0.

# Can I delete sessiondb

Yes, you can but bot won't understand historical data, then limit will reset back to 0 and you may be softban if catch over limit, 

# Can I view raw data

Yes, data is liteDB you can use any LiteDB tool to view it - [https://github.com/falahati/LiteDBViewer](https://github.com/falahati/LiteDBViewer)

The raw data is just a timestamp. you need to make sure that the last 1 is 24 hours ago - copy the value and come to [http://tickstodatetime.com](http://tickstodatetime.com/) and see what is the time for that value

Pleaes do not manually delete sessiondb, or remove data in that table it will cause softban to your account




