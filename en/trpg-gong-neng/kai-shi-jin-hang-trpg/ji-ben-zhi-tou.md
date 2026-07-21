---
description: Basic dice rolling in HKTRPG.
---

# Basic Rolling

{% hint style="info" %}
**Tip:** In most TRPG and board-game docs, dice are written as xDy — x dice with y sides each.\
Example: the bluffing game Liar’s Dice uses five six-sided dice, i.e. 5D6.
{% endhint %}

### xDy

Roll x dice with y sides each.\
Example: `1D100` rolls one hundred-sided die; the result is 1–100.

Example with flavor text: `1D100 攻撃！`\
Output: `1D100：攻撃！  38[38] = 38`

![](<../../.gitbook/assets/image (33) (1) (1).png>)\
As above, add a space after the dice expression to attach a message.

### Multiple Rolls

`.5 3D6` — roll 3d6 five times (up to 30 times)\
![](<../../.gitbook/assets/image (20).png>)



### Math

Supports parentheses, + − × ÷, and comparisons (>, <, >=, <=).

![](<../../.gitbook/assets/image (16).png>)

![](<../../.gitbook/assets/image (4) (1).png>)

### kh | kl | dh | dl

{% hint style="info" %}
Common in DND and PF.
{% endhint %}

k = keep, d = drop, h = highest, l = lowest\
Example: `3d6kh` — keep the highest one die\
![](<../../.gitbook/assets/image (29).png>)\
\
`3D6dl2` — drop the lowest two dice\
![](<../../.gitbook/assets/image (26) (1).png>)


