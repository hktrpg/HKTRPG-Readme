---
description: Discord only. Forward results from character-sheet or request-roll buttons to another channel.
---

# Discord Button Forwarding (.forward)

{% hint style="info" %}
Discord only. Forward results from `.ch button`, `.char button`, or `.re` buttons to another channel.
{% endhint %}

### Why

Sheet buttons are often pinned in a prep channel. `.forward` sends click results to the public play channel without copy-paste.

### Commands

| Command | Description |
| ------- | ----------- |
| `.forward [Discord message link]` | Forward that button message’s results to the **current** channel |
| `.forward show` | List all forward rules |
| `.forward delete [index]` | Delete a rule by number |

### Supported button types

* `.ch button` (sheet state)
* `.char button` (sheet rolls)
* `.re` ([request roll / click](../trpg-gong-neng/yao-qiu-zhi-tou.md))

### Suggested flow

1. Create buttons in a prep channel: `.ch button` or `.char button name`
2. Right-click the message → **Copy Message Link**
3. In the play channel: `.forward https://discord.com/channels/...`
4. Clicks on the original buttons then appear in the forwarded channel

### Notes

* You can only forward **your own** sheet buttons
* Each button maps to one forward channel
* Limits scale with [VIP level](../getting-started/development-support.md#vip-benefits-overview) (about 4 at VIP 0)
* Rules persist until deleted

### Related

* [Character Sheets](../trpg-gong-neng/kai-shi-jin-hang-trpg/jiao-se-ka.md)
* [Request a Roll](../trpg-gong-neng/yao-qiu-zhi-tou.md)
* [Development Support (VIP)](../getting-started/development-support.md#vip-benefits-overview)
