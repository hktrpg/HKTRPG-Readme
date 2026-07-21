---
description: When TRPG combat starts, initiative order is usually needed. This page shows how to build an initiative tracker quickly.
---

# Initiative Tracker

{% hint style="info" %}
Systems like DND and Infinite Horror reroll 1D20+initiative each fight, so this feature supports rerolling and saving your roll formula without retyping it.
{% endhint %}

![](<../../.gitbook/assets/image (44).png>)

### How to Use

#### Add a combatant

`.in (roll or number) (name)`

(roll or number) is required — e.g. `1D20+3` or a fixed value like `5`.

(name) is optional. If omitted, your chat display name is used.

Repeat `.in (roll or number) (different name)` to add multiple combatants.

#### Show initiative

`init` — show initiative, highest first

`.initn` — show initiative, lowest first

#### Reroll initiative

`.in reroll`

Many systems reroll initiative each encounter;\
this reruns the stored formulas on the tracker.

#### Other

* `.in -3+6*3/2.1` — supports arithmetic
* `.in remove (name)` — remove a combatant
* `.in clear` — clear the whole tracker

### Command Reference

`.in (remove clear reroll help)` `.init`

* `.in (roll or number) (name)`
* `.in 1d20+3 (name)`
* `.in 1d3` (uses your chat name if name is omitted)
* `.in 80` — set initiative to a fixed value
* `.in -3+6*3/2.1` — arithmetic
* `.in remove (name)` — remove a combatant
* `.in reroll` — reroll formulas on the tracker
* `.in clear` — clear the tracker
* `.init` — show initiative, highest first
* `.initn` — show initiative, lowest first
