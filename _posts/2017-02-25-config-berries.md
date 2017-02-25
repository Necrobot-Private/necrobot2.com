---
author: samuraitruong
layout: post
title: "Berries config"
date: 2017-02-22 0:30
comments: true
category: Config.json
tags:
- Berries, Catching
---

Two new berries type has been added into the game awhile ago, of course our bot have support for it very quickly just a day or so after release. However, I would writing a quick guide to explian how the config work

## How berries work?
Please check the post here [https://www.cnet.com/au/how-to/how-to-use-the-new-berries-in-pokemon-go/](https://www.cnet.com/au/how-to/how-to-use-the-new-berries-in-pokemon-go/) for learn about usage of new berries type

## How berries config with necro?

We introduced config section "UseItemFilters" which allow us to separate control when to use berries, 

{% highlight json %}

ItemUseFilters": {
    "ItemNanabBerry": {
      "UseItemMinIV": 50,
      "UseItemMinLevel": 20,
      "UseItemMinCP": 500,
      "Operator": "and",
      "CatchProbability": 0.3,
      "Pokemons": [
        "abra",
        "dragonite",
        "venusaur",
        "blastoise",
        "charizard"
      ],
      "MaxItemsUsePerPokemon": 20,
      "UseIfExceedBagRecycleFilter": true
    },
    "ItemRazzBerry": {
      "UseItemMinIV": 90,
      "UseItemMinLevel": 0,
      "UseItemMinCP": 1500,
      "Operator": "and",
      "CatchProbability": 0.5,
      "Pokemons": [],
      "MaxItemsUsePerPokemon": 20,
      "UseIfExceedBagRecycleFilter": true
    },
    "ItemPinapBerry": {
      "UseItemMinIV": 0,
      "UseItemMinLevel": 0,
      "UseItemMinCP": 0,
      "Operator": "or",
      "CatchProbability": 1.0,
      "Pokemons": [
        "lapras",
        "larvitar",
        "snorlax",
        "chansey",
        "dratini",
        "porygon",
        "porygon2",
        "sunkern"
      ],
      "MaxItemsUsePerPokemon": 10,
      "UseIfExceedBagRecycleFilter": true
    }

{% endhighlight %}

- *UseItemMinIV* : Define min IV to use this type of berries
- *UseItemMinLevel* : Define min level to use this type berries, if you don't want to check you can set it to level 0, make sure you use "and" logic
- *UseItemMinCP* : Same with above, this to define the CP of pokemon to use
- *Operator*: The logic check between all setting parameter .
- *CatchProbability*: The catch chance of the pokemon
- *Pokemons* : List of pokemon you want to use this type of berry. leave it null or empty "[]" it will apply to all pokemon.
- *UseIfExceedBagRecycleFilter*: Regardless the condition, if number of berry is greater than the recycel setting this this berry time. bot will use it.


## How to priority berries

The list will priority by order, in the example above, Nanab is first priority then Razz and finially is Pinnab. If 1 pokemon matching with multiple berries, only 1 berry will be use and that is the first berry met with condition from top to bottom. 


## Tips to config
Make sure you understand the usage by read the above post. For example, use Pinnab berry for the pokemon you want to have candy like Larvitar, Chansey, Porygon. make sure you don't waste berry, only use when they are easy to catch so low level, low CP 

