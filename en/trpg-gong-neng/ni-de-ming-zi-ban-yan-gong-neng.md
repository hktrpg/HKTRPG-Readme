---
description: How to post messages on Discord with a fixed name and avatar for roleplay.
---

# Your Name (Roleplay Feature)

{% hint style="info" %}
On Discord, you can change your display name in a server at any time — but that change applies across the whole server. If you play text-based TRPG there, character names and avatars in past messages can get mixed up.

Note: you can only **append or edit content** on existing messages using [.edit (edit old messages)](../xi-tong-gong-ju/discord-xiu-gai-jiu-xun-xi.md).
{% endhint %}

`.myname` `.me` `.me1` `.me(name)` — *Discord only*

### TRPG Roleplay Posting

Set a character name and avatar, then type a command plus your line — the bot posts as that character.

Dice rolls are supported. Wrap roll commands in `[[]]`, e.g. `[[1d100]]`.

Note: this feature requires permission to manage webhooks and messages.

### Tutorial

#### 1. Set up a character

Type `.myname "name" character_image_url name_abbreviation (optional)`

Example: `.myname "泉心 造史"` [`https://images.pexels.com/photos/10013067/pexels-photo-10013067.jpeg`](https://images.pexels.com/photos/10013067/pexels-photo-10013067.jpeg) `造`

**Name** — the character name shown on posts. Use `"quotes"` if the name contains spaces, e.g. **"泉心 造史"**; otherwise quotes are optional.

**Image** — character icon URL. If the image fails, a default Discord icon is used.

You can upload images to Discord or imgur.com.

**Name abbreviation** — shortcut to invoke this character, e.g. `.me造 「來玩吧」`

#### 2. Delete a character

**`.myname delete index / abbreviation / "name"`**

After `delete`, provide the index, abbreviation, or full name.

#### 3. List characters

`.myname show`

#### 4. Post as a character

**`.me(index/abbreviation) message`**

Examples:

* **`.me1 泉心慢慢的走到他們旁邊，伺機行動`**
* ![](<../.gitbook/assets/image (13).png>)
* **`.me造 「我接受你的挑戰」`**

### Command Reference

* `.myname` — set up a character
* `.myname delete index / abbreviation` — delete a character
* `.myname show` — list characters
* `.me(index/abbreviation) message` — post as that character
* `.mehistory` — show past `.me` posts in this channel




