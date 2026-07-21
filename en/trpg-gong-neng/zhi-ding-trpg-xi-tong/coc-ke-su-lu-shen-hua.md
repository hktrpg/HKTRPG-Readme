---
description: How to roll Call of Cthulhu with HKTRPG.
---

# CoC (Call of Cthulhu)

`cc` `cc(n)1~2` `ccb` `ccrt` `ccsu` `.dp` `.cc7build` `.cc6build` `.cc7bg` `.sc` `.chase`

{% hint style="info" %}
[CoC 7th Edition rulebook overview](https://www.patreon.com/posts/67705000)
{% endhint %}

### Skill Checks

* CoC 6th edition: `ccb 80` — skill ≤ 80
* CoC 7th edition: `cc 80` — skill ≤ 80\
  ![](<../../.gitbook/assets/image (43).png>)
* CoC 7th bonus dice: `cc(1~2)` e.g. `cc1 80` — one bonus die
* CoC 7th penalty dice: `ccn(1~2)` e.g. `ccn2 80` — two penalty dice
* CoC 7th combined check: `cc (x,y) (z,a)` e.g. `cc 80,60 鬥毆,魅惑`\
  Bonus/penalty supported, e.g. `cc１ 80,60 鬥毆,魅惑`
* CoC 7th Sanity check: `.sc (SAN value) (success)/(failure)`\
  ![](<../../.gitbook/assets/image (28).png>)
*   CoC 7th manual improvement or growth rolls

    ![](<../../.gitbook/assets/image (32).png>)\
    Multiple skills in one command<br>

    `.dp` or `成長檢定` or `幕間成長 (skill%) (name)` \
    `.DP 50 騎乘 60 鬥毆 50 60` \
    `.DP 50 60 50` \
    `成長檢定 65 頭槌 45 劍術`  \
    `幕間成長 40 單車`

### CoC Reference Tables

`CoC 7th mythos organizations (random): .cccc` \
`CoC 7th mythos tomes (random): .ccdr` \
`CoC 7th spell push consequences: .ccpc`\
![](<../../.gitbook/assets/image (7).png>)

![](<../../.gitbook/assets/image (9).png>)

### Insanity Results

* CoC 7th short-term madness: `ccrt`
* CoC 7th long-term madness: `ccsu`

### Character Creation

* CoC 6th edition: `.cc6build`
* CoC 7th edition: `.cc7build (age 7–79)`
* CoC 7th random character: `.cc7build random`
* CoC 7th point-buy: `.cc7build .xyz (age 7–89)`

Example `.cc7build .752` rolls:\
`7× 3d6 * 5`\
`5× (2d6+6) * 5` \
`2× 3d6 * 5`

You can use `.` alone without xyz;\
default is `.53` → `5× 3d6 * 5` and `3× (2d6+6) * 5`

![](<../../.gitbook/assets/image (45).png>)

* CoC Pulp: `.ccpulpbuild`
* CoC 7th random background: `.cc7bg`

### Improvement Roll Log

![](<../../.gitbook/assets/image (34) (1).png>)

When enabled, logs successful rolls (and crits/fumbles) from `cc` commands for automatic improvement.

* `.dp start` — start logging
* `.dp stop` — stop logging
* `.dp show` — show log
* `.dp auto` — auto-improve and clear log
* `.dp clear` — clear log
* `.dp clearall` — clear log including crits/fumbles

### CoC 7th Chase Generator

Command: `.chase`

{% hint style="info" %}
The chase tool uses optional rules and the author’s reading of the rulebook — it may not match Chapter 7 exactly. Read the chase rules before relying on it.
{% endhint %}

![](<../../.gitbook/assets/image (40).png>)

