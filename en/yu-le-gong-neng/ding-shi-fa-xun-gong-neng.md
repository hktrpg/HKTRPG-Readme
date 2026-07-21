---
description: TRPG groups sometimes need scheduled messages—for example session reminders or countdowns to submission deadlines.
---

# Scheduled Messages

![](<../.gitbook/assets/image (50).png>)

The scheduler has two modes:\
`.at .cron mins hours delete show`

### 【at】 Send once at a specified time

Enter `.at 20220604 1900` **(YYYYMMDD HHMM)**\
`.at 5mins` (in 5 minutes)\
`.at 5hours` (in 5 hours)\
to post a message at the specified time.

#### Dice Support

Wrap commands in `[[]]`.\
Example:\
`.at 5hours`\
`[[CC 60]]`\
`[[立FLAG]]`

### 【cron】 Post daily or on a schedule at a set time (24-hour clock)

#### Format

Enter a 24-hour time such as **`2300`**, then optionally use `-`\
followed by a number like `1`, `2`, `3` for interval in days,\
or `mon` `tue` `wed` `thur` `friday` `sat` `sun`\
for specific weekdays.

#### Examples

`on 0831` \
`Howl every day at 8:31!`

`.cron 0721`\
`Roll every day at 7:21`\
`[[CC 80 幸運]]`

`.cron 1921-2`\
`I will post every two days at 7:21 PM`

`.cron 1921-wed-mon`\
`I will post every Monday and Wednesday at 7:21 PM`

### Custom Name and Avatar for Scheduled Messages (Patreon Only)

Add `name` and `link` after the time to post as a custom identity, like `.meX`.

![](<../.gitbook/assets/image (43).png>)\
**Example**

`.cron 2258` \
`name=Sad` \
`link=`[`https://user-images.githubusercontent.com/23254376/113255717-bd47a300-92fa-11eb-90f2-7ebd00cd372f.png`](https://user-images.githubusercontent.com/23254376/113255717-bd47a300-92fa-11eb-90f2-7ebd00cd372f.png) \
`First line` \
`[[2d3 Second line]]` \
`hello world footer`

`.at 1mins` \
`name=Sad` \
`link=`[`https://user-images.githubusercontent.com/23254376/113255717-bd47a300-92fa-11eb-90f2-7ebd00cd372f.png`](https://user-images.githubusercontent.com/23254376/113255717-bd47a300-92fa-11eb-90f2-7ebd00cd372f.png) \
`First line` \
`[[2d3 Second line]]` \
`hello world footer`

### Command List

* `.cron / .at` — Add a scheduled message
* `.cron / .at show` — List scheduled messages
* `.cron / .at delete (number)` — Delete a scheduled message
* e.g. `.at delete 1` — Use `.at show` to find the number
