---
author: samuraitruong
layout: post
title: "Basic transfer config"
date: 2017-01-07 8:30
comments: true
category: Config.json
tags:
- Transfer,Starter Config
---

Thought, Transfer is the most issue I saw on discord that people as question, complain, worries, and angry about. I would ask you read this basic transfer config before run the bot to avoid any accident transfer your bag

# Weak Transfer Pokemon

Weak transfer pokemon is the mode that you tell bot to transfer all the pokemon that you don't want to keep as you think they are weak for you. It mean  that all pokemon not in 'PokemonsNotToTransfer'.

To avoid any accident, please careful when turn this option on because you may not add your pokemon to the list then they will be transfered with no way to get back. Default config only include few popular rare pokemon, it not include all rare pokemon so make sure you are setting up that list carefully.

{% highlight json %} 
"PokemonsNotToTransfer": [
    "venusaur",
    "charizard",
    "blastoise",
    "muk",
    "chansey",
    "gyarados",
    "articuno",
    "zapdos",
    "moltres",
    "mewtwo",
    "mew"
  ]
{% endhighlight %}

To turn on Weak Transfer mode,you only need to set them to true

{% highlight json%} 
 "PokemonConfig": {
    ............
    "TransferWeakPokemon": true,
    ........
  }
{% endhighlight %}

# Transfer duplication mode
This is the powerful transfer mode with fully control on what pokemons you want to keep , I will have separate guide for advance using this mode, in this page I only give some basic config how to use this feature

- Turn on this mode

{% highlight json%} 
 "PokemonConfig": {
    ............
    ""TransferDuplicatePokemon": true   // Turn on Duplicate pokemon transfer
    "KeepMinCp": 2500,                  // Transfer all pokemon < 2500cp
    "KeepMinIvPercentage": 100.0,       //Transfer all pokemon < 100% IV
    "KeepMinLvl": 35,
    "KeepMinOperator": "or",            //The logic check to combile with CP & IV
    "UseKeepMinLvl": false,             //Use level transfer 
    "PrioritizeIvOverCp": true,         //Tell bot that IV or CP is important to select pokemon to keep
    "KeepMinDuplicatePokemon": 1,       //Number of duplication pokemon you want to keep
  }
{% endhighlight %}

Lets discuss about these parametters, they are global config apply for every pokemon in your bad, if you not overwrite by individual config. Even keep pokemon condition not meet but bot stil keep  number of pokemon <= KeepMinDuplicatePokemon. for example you setup as above , but you only has 1 Snorlax 50% IV, that snorlax still being kept in your bag, but if you have another snorlax 80%IV, the 50 % IV will be transfer and bot keep the 80% one (Note IV or CP depend on PrioritizeIvOverCp) 

```Note: Transfer duplication only transfer the pokemon NOT in the list PokemonsNotToTransfer```

# How I specific transfer setting for specific pokemon

Okay, above is global config which will apply for every pokemon, But you have some pokemon that you never has 100% IV but you want to keep 5 of them for example Dragonite, you want to keep all dragonite > 80%IV, then in this case you need overwrite global setting by invidiual transfer as below

{% highlight json%} 


 "PokemonsTransferFilter": {
    "Dragonite": {
      "KeepMinCp": 3500,
      "KeepMinIvPercentage": 100.0,
      "KeepMinLvl": 30,
      "UseKeepMinLvl": false,
      "KeepMinOperator": "or", // important logic or in here to keep more pokemon you want
      "KeepMinDuplicatePokemon": 1,
      "Moves": [],
      "DeprecatedMoves": null,
      "MovesOperator": "and",
      "CatchOnlyPokemonMeetTransferCriteria": false
    }

.....................
{% endhighlight json%} 

Of invidual pokemon, you can specify moves you don't want too, since if 100% IV but they have crab move, we don't want to keep 

# What is transfer on capture

Like you play pokemon go official, everytime you catch pokemon the info screen appear and the transfer option there, you can tap on that to transfer pokemon. So turn that to On, it mean you want bot do do like this.

{% highlight json%} 

 "PokemonConfig": {
   "TransferDuplicatePokemonOnCapture": true,
  }
.....................
{% endhighlight json%} 


Are you sure it work? why I turn it on and my pokemon still not transfer, I thought it broken?,.... whatever come to your mind,hold it off for a sec and read the Bulk transfer section below

# Bulk Transfer mode

Bulk transfer is the mode that you tell the bot to transfer multiple pokemon at once instead  one by one. The benefit of that is save number of request and improve the perfomance of the bot a lot. Bulk transfer only apply for max 100 batch, so if you have more than 100 pkm to transfer, bot will perfomance multiple time to transfer all of them. so, what config parametter you need to change, see below

{% highlight json%} 

 "PokemonConfig": {
  .......
    "UseBulkTransferPokemon": true, //enable this function, default is true
    "BulkTransferStogareBuffer": 3,
    "BulkTransferSize": 100
  .......
  }
{% endhighlight json%} 
* **BulkTransferStogareBuffer** : That is the buffer for your bag, for example, your bag is 250, buffer = 3 mean that everytime you bad full to 250-3, bulk transfer will happen

* **BulkTransferSize** : As mentioned above, max 100 is number of pokemon in each transfer , you can set it to 20, so everytime you have 20 pokemon meet with transfer filter , the bulk transfer will happen.

```Note: Bulk transfer mode change the rule to select pokemon for transfer, it just do batch instead of single, so nothing impact on transfer such as wrong logic when turn it on```

If you setup your transfer properly then your bag never full . I will post advance config for transfer to completely avoid bag full later.



# Some message in console related to transfer
