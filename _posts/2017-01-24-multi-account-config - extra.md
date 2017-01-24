Easy instructions to set Necrobot to run multiple accounts one after each other

1. In auth.json, set login credentials to your 1st account
<% highlight json %>
  "AuthConfig": {
    "AuthType": "ptc",
    "GoogleUsername": null,
    "GooglePassword": null,
    "PtcUsername": "1st_account_name",
    "PtcPassword": "1st_account_pass"
   }
<% endhighlight json %>
2. Near bottom of auth.json set your other accounts
<% highlight json %>

  "AllowMultipleBot": true,
  "Bots": [
    {
      "AuthType": "google",
      "GoogleUsername": "2nd_account@gmail.com",
      "GooglePassword": "2nd_account_pass"
      "PtcUsername": null,
      "PtcPassword": null
    },
    {
      "AuthType": "ptc",
      "GoogleUsername": null,
      "GooglePassword": null,
      "PtcUsername": "3rd_account_name",
      "PtcPassword": "3rd_account_pass"
    }
  ]
<% endhighlight json %>
3. In config.json, tweak the Multi Bot settings as desired
  <% highlight json %>
  "MultipleBotConfig": {
    "RuntimeSwitch": 55,
    "OnLimitPauseTimes": 15,
    "OnRarePokemon": true,
    "MinIVToSwitch": 101.0,
    "EXPSwitch": 25000,
    "PokestopSwitch": 500,
    "PokemonSwitch": 200,
    "PokemonPerHourSwitch": 100,
    "StartFromDefaultLocation": true,
    "PokestopSoftbanCount": 5,
    "DisplayList": true,
    "SelectAccountOnStartUp": false,
    "CatchFleeCount": 5,
    "SwitchOnCatchLimit": true,
    "SwitchOnPokestopLimit": true
  }
  <% endhighlight json %>
