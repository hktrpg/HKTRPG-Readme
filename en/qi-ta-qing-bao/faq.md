---
description: Behind-the-scenes development stories
---

# FAQ

### Origins of HKTRPG

On 30 Nov 2016, someone published the [Machine Duck Beast open-source project](https://docs.google.com/document/d/1dYnJqF2_QTp90ld4YXj6X8kgxvjUoHrB4E2seqlDlAk/edit).

**Duck Beast**’s commands were basically the same as the TRPG platform **Frozen Tofu**. At the time, Frozen Tofu was more or less the only Japanese-style TRPG platform, so everyone built on top of it.\
But I thought the CoC command `CC<=80` was too annoying—LINE is mainly used on phones, and `<=` is basically anti-human—so I wanted to write my own.\
I mainly referenced [BcDice](https://docs.bcdice.org/) and LINE anti-raid bots. The first feature I added was probably **`運勢` (fortune)**, mimicking those anti-raid bots.

### Who Is the Developer?

My name is Sad. My English name was too long, so everyone called me by the first letter, and it became Sad.\
I’m not a programmer by profession and my job has nothing to do with coding, but I kept going out of curiosity.

### Why Is HKTRPG So Unstable?

Because I never formally learned JS. I did one year of C# in class, but I never got solid programming training.\
So when writing this, I mostly learned by Googling as I went.\
That means I miss a lot of common knowledge and there are many bugs…\
If I had learned about classes back then, maybe it wouldn’t be this bad. I wish I could go back ten years…

### What Was the Goal of HKTRPG?

I’m lazy. If I have to repeat something, I hate it.\
So HKTRPG and the things I build are mainly so I can be lazy—avoid repetitive work and save time.\
Also to learn new things—it’s a small hobby.\
Finally, I love playing TRPG, so anything that lets me run games faster and save time makes me happy XD<br>

### Why Did HKTRPG Gain So Many Features?

After that, HKTRPG mostly refined existing features and added random stuff BcDice had.\
The second truly original feature was probably someone on Bahamut asking,\
**“Can the bot TAG the person who typed the command?”**—and that seems to be when custom features really started.

### Why Is There Patreon?

The first time I used Patreon was to buy TRPG maps online. I didn’t understand how Patreon worked—I just knew that after paying I had to keep reading posts to download images.\
Anyway, the first real reason: after the Discord version launched for a while, user count suddenly jumped.\
Discord emailed me warning that usage had increased, that I needed Spawn to run, and that I had to register HKTRPG with real-name verification to keep going.\
At that moment I wondered if something was wrong—that was supposed to happen only at around a thousand servers. I wrote a check and found, huh, over a thousand groups already…?\
Then came excitement and a pile of paperwork. HKTRPG was hosted on free Heroku; the dashboard kept showing insufficient RAM, so HKTRPG moved to a paid server. With ten to twenty new groups every day, Patreon became an idea.

<img src="../.gitbook/assets/image (49).png" alt="" data-size="original">\
\#2022/02/09 As Discord usage grew, server RAM, CPU, and SSD stayed maxed out. Don’t ask me why…\
\
Patreon is financial support and moral support—“there really are supporters,” “someone really finds this useful”—which made me invest more in HKTRPG and tackle many challenges. The `.ra` draw feature took me forever reading docs to implement; looking back, the code is ugly and unreasonable, but it was my first step.\
So why Patreon? Roughly “server costs went up” and “I wanted support.”

### How Do I Give Feedback on This Documentation?

Click **Edit on GitHub** on the right to open issues, or use a pull request to update content directly.<br>
