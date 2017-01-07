---
author: samuraitruong
layout: post
title: "Necrobot2 - Manual Snipe config"
date: 2017-01-07 10:30
comments: true
category: Config.json
tags:
- snipe, manual, socketdata
---

Necrobot version > 1.0.0.30 support manual snipe , which is suite for everyone who don't want to setup auto snipe.

# How manual snipe work

Your bot is running , you will visit website [snipe.necrobot2.com]('http://snipe.necrobot2.com') and looking for good pokemon, if you want bot cach him just click on him, that's all. but before the magical happen, you need to do a very simple setup as below

Generate your unique ID, BOT & mypogosnipers.com will use this UUID to make a handshake, You can using 1 UUID share with all other instance of bot running (which is great , you click one and all your bot will catch him, nice isn't ). You can also share your UUID with your friend and snipe to gether , that is double cool

# So, how UUID look like?
UUID is a unique string you can use your personal email, phone, whatever string you think it is unique and only you know. I recommend to generate 1 UUID from here  

https://www.guidgen.com/

OR 
https://www.uuidgenerator.net/

OR https://www.guidgenerator.com/online-guid-generator.aspx

Next step, you need to have a version of bot > 1.0.0.30 to have the new awesome feature. Setup bot with the UUID you generated above in config.json as below

# Change config for support manual snipe

{% highlight json%}
"DataSharingConfig": {
    "EnableSyncData": true,
    "AutoSnipe": true,
    "DataServiceIdentification": "ca32d7dc-4443-4602-a568-2aa5887c8ba8 - this is the id you generate step 1",
    "DataRecieverURL": "ws://necrosocket.herokuapp.com/socket.io/?EIO=3&transport=websocket"
  },

{% endhighlight %}

This manual snipe mode even works with autosnipe so that you can leave autosnipe TRUE or FALSE doesn't matter. But you need turn on data sync EnableSyncData (set it to TRUE)

Step 3: Go to mypogosnipers.com, then go to setting change sniper mode to use build in sniper and use the UUID you generate and set in the data service Identification, save setting and you are all good

[Imgur](http://i.imgur.com/PAHeaHd.png)
![](http://i.imgur.com/PAHeaHd.png)

Step 4 : Click on any pokemon to verify that is work, you will see a notification message when you click on pokemon and the console message in bot.
![Imgur](http://i.imgur.com/ik3AyGh.png)

Step 5: Hunting as many as pokemon you want


Happy botting .. :)
 