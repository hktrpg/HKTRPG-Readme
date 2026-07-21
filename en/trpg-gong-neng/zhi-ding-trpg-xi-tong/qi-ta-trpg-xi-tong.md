---
description: Dice commands for additional TRPG systems.
---

# Other TRPG Systems

{% hint style="info" %}
From 2022/05/11, some legacy BcDice-style command prefixes were removed and replaced by BcDice (`.bc`).\
Examples replaced: 【朱の孤塔】【迷宮王國】【忍神】, etc.
{% endhint %}

Details always win via `command help` (e.g. `.4df help`).

### Fate — `.4df`

Four Fate dice: + / − / blank. For Fate / Fudge-style play.

* `.4df` — roll four Fate dice
* `.4df3` or `.4df+3` — result +3
* `.4df-4` or `.4dfm4` — result −4

### World of Darkness — `.xwd`

8–10 succeed; 10s may reroll (reroll threshold adjustable).

* `.3wd8` — 3×D10, succeed on 8+
* `.15wd9+2` — 15 dice, succeed on 9+, +2 successes
* Optional description text after the command

### Witch Hunting Night — `.wn`

Roll xD6; default success on ≧4; sin value and modifiers supported.

* `.wn 3` — three D6
* `.wn 5D4+3` — five D6, succeed on ≧5, then +3
* `.wn 3DD6+2` — net successes (double-D) then +2

`@` variants: see `.wn help`.

### Cat Onmyoji — `.kc`

“Eighteen” style: find pairs, sum remaining dice, compare to target.

* `.kc 4D10 15`
* `.kc D8 12`
* `.kc 5D12 18`

### Other

* Details omitted — type prefix + `help`, e.g. `.al help`
* Sword World — `.sw`
* Double Cross — `.dx`
* Shinobigami — `.kk`
* Many JP systems: [BcDice](bcdice-ri-xi-zhi-tou-fang-fa.md) `.bc`
