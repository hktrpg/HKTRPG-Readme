---
description: Tracks group participation with a level (LV) system—similar in concept to MEE6.
---

# Experience & Leveling

![](<../../.gitbook/assets/image (76).png>)

`.level (show config LevelUpWord RankWord)`

Enable this to earn experience from chatting in a channel and compare levels with people worldwide.

Experience increases with messages; level up and rank within the server.

When you reach the required experience, a notification tells you that you leveled up.

### Tutorial

Disabled by default. Enter `.level config 11` to enable.

`11` means you get a notification on level up.\
`10` means no notification.\
`00` turns the feature off.

### Default Response

* “XXXX 《title》, your Cthulhu Mythos knowledge is now X points!
* You rank X out of XX people! XX%!
* Investigation experience is XX points.”

### Command List

Enter `.level LevelUpWord (content)` to customize the level-up message in this group\
Enter `.level RankWord (content)` to customize the rank query response in this group\
Enter `.level TitleWord -(LV) (content)` to set titles applied at or above that level\
Start from `-0`; you can set multiple at once, e.g. `.level TitleWord -0 Child -5 Apprentice -10 Warrior`\
Enter `.level RankWord/LevelUpWord/TitleWord del` to restore defaults\
Enter `.level RankWord/LevelUpWord/TitleWord show` to show current settings\
Enter `.level show` to check your level\
Enter `.level showMe (number)` to show this group’s leaderboard (default top 5)\
Enter `.level showMeTheworld (number)` to show global leaderboard (default top 6)\
Enter `.level showMeAtTheworld` to check your global rank

### Placeholders for Level-Up and RankWord&#x20;

`{user.name}` — Name\
`{user.level}` — Level\
`{user.title}` — Title \
`{user.exp}` — Experience \
`{user.Ranking}` — Current rank \
`{user.RankingPer}` — Rank percentile \
`{server.member_count}` — Total members in the channel
