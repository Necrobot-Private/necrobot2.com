---
author: samuraitruong
layout: post
title: "Telegram configuration "
date: 2017-01-11 0:30
comments: true
category: Config.json
tags:
- notification,Telegram
---

Telegram is a bot service that allow you control your bot when you are not on PC, Telegram also good to use to recieve notificaiton from BOT such as Captcha, Account reach limit, see Notificaiton config for more detail. Please follow step to config your bot work with Telegram

# Create an Teleram bot
You have to register an account and create an a bot with BotFather, then He will give you API key to config in config.json. Telegram can be install by app on your phone or access via web from [https://web.telegram.org](web.telegram.org). 

Use the /newbot command to create a new bot. The BotFather will ask you for a name and username, then generate an authorization token for your new bot.

The name of your bot is displayed in contact details and elsewhere.

The Username is a short name, to be used in mentions and telegram.me links. Usernames are 5-32 characters long and are case insensitive, but may only include Latin characters, numbers, and underscores. Your bot's username must end in ‘bot’, e.g. ‘tetris_bot’ or ‘TetrisBot’.

The token is a string along the lines of 110201543:AAHdqTcvCH1vGWJxfSeofSAs0K5PALDsaw that is required to authorize the bot and send requests to the Bot API.

Read more about telegram at - [https://core.telegram.org/bots](https://core.telegram.org/bots)

#Setup Necrobot work with telegram

Pretty simple because there only few paramter you need to setup, please look for config below in config.json

{% highlight json %}


  "TelegramConfig": {
    "UseTelegramAPI": true,
    "TelegramAPIKey": "COPY API KEY THAT BOT FATHER GIVE YOU",
    "TelegramPassword": ""
  }

  {% endhighlight %}


#Test your bot
After you make that config change, you need to restart BOT, if you see the message on screen tell that you successful connect with your Telegram BOT, then you are settled. If you don't see message or get error, just need to verify that you enter correct API key, make sure no trail space after or before KEY, and make sure *UseTelegramAPI* is set to TRUE

You need access telegram from web or from your phone, after your NECROBOT start, type anything if he reply with the menu includes all options you have then the NecroBOT and Telegram bot working .

If you have multiple Necrobot instance, you may need to create multiple telegram bot  but you also able to use 1 API key for all config.json. in that case when you type 1 command, all NECROBOT will anwser you, that is super good in case you want to snipe because all your bot recieve your command.

``` dif ++NOTE: Snipe command is /Snipe PokemonName,Lat,Long   

```

Happy botting :)


Cheers
 



