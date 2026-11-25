---
description: Dice faces are not always numbers — they can be symbols or text. This feature lets you define custom dice with your own faces.
---

# Custom Dice

Keyword-based random pick: once configured, matching input triggers a random choice.

{% hint style="info" %}
This feature was updated: `.rap` is now personal-only dice tables;\
server-wide `.rap` became `.ras`.\
`.ra` => random answer (group)\
`.rap` => random answer (personal)\
`.ras` => random answer (server)
{% endhint %}

### How to Use

Prepare die faces and a name for the die.

In a group, type `.ra add (die_name) (face1 face2 face3 face4 face5)`\
When added, roll with:

`.ra (die_name)`

### Command Reference

`.ra(p|s)(count) (add del show die_name)`

* `.ra add (die_name) (option1) (option2) (option3)` — add options\
     Repeating adds more options; total limit 2000 characters.

* `.ra show` — list all dice and index numbers
* `.ra show (die_name)` — show faces for one die
* `.ra del (die_name)` — delete a die
* `.ra(count, max 30) (die_name1/index) (die_name2)...(die_namen)` —\
     random pick without replacement

* `.rra(count, max 30) (die_name1/index)(die_name2)...(die_namen)` —\
     random pick with replacement

     Die names can be replaced by index numbers, e.g. index 5 → `.ra 5`

### Three Modes

* `.ra` — group version, shared in the server
* `.ras` — public version, visible across HKTRPG
* `.rap` — personal only
* Example: `.ras10 聖晶石召喚` — ten consecutive draws

### Template Codes

* Templates are supported; try `.ras newType` to preview.
* `{br}` — line break
* `{ran:100}` — random 1–100
* `{random:5-20}` — random 5–20
* `{server.member_count}` — member count in the current channel
* `{my.name}` — roller’s display name

Requires `.level` to be enabled:

* `{allgp.name}` — random name from all group members
* `{allgp.title}` — random title from the group
* `{my.RankingPer}` — current ranking percentile
* `{my.Ranking}` — roller’s current rank
* `{my.exp}` — roller’s experience
* `{my.title}` — roller’s title
* `{my.level}` — roller’s level
