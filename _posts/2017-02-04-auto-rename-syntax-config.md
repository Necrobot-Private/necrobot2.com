---
author: samuraitruong
layout: post
title: "Auto rename config guide"
date: 2017-02-4 0:30
comments: true
category: Config.json
tags:
- Auth, Multi Account
---

Necrobot support you config to rename the pokemon in your inventory to help easier manage them on the official app by look in their name since non of useful information show like Level, IV.

You can turn on rename feature by  below config 

{% highlight json %}

  "PokemonConfig": {
    "RenamePokemon": true,
    "RenameOnlyAboveIv": false,
    "RenameTemplate": "{IV}_{Name}_LV{Level}",
   }
{% endhighlight json %}

If you turn *RenameOnlyAboveIv* to true, then bot only rename those pokemon has IV > KeepMinIV value. this is just check for global transfer minIV. I will make change to check for transfer filter, make sure that bot only rename those pokemon we decided to keep

RenameTemplate support 4 tokens below

1. {IV} => will replace by pokemon IV, 0 decimal place
2. {Level} => Pokemon Level
3. {CP} => Pokemon CP
4. {Name} => Pokemon Name

The limit of pokemon name is 12 characters lengh, so please make sure you don't put  to many thing in the template, if the lengh is longer then 12 character, it will be trimmged back to 12 character. 

You also can add more free characters into your pattern 

```{Name}_LV{LV}_{IV}```

cheers
