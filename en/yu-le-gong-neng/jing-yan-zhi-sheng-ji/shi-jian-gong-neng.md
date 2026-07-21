---
description: A companion feature to experience leveling—you can add events that grant effects or change experience.
---

# Event System

![](<../../.gitbook/assets/image (14).png>)

`.event (add delete show) .evt (random/event name)`

Events you create can apply status effects or add/subtract experience, and you can earn bonus experience from them.

### Tutorial

`.event add` — Add an event (see format below)\
`.event delete (event name)` — Delete an event\
`.event show` — Show all events you created and EXP earned\
`.event show (event name)` — Show details for a specific event\
`.event useExp` — Use in a group to claim earned EXP\
`.evt random` — Enter a random event; costs 5 EN\
`.evt (series name)` — Enter a series event; costs 10 EN\
`.evt (event name)` — Enter a specific event; costs 15 EN

### Rules

EN cap = 20 + LV. Regenerates 1 EN every 10 minutes.

#### How to Learn Event Names

Someone tells you, or you discover names through random events. Designing events lets you absorb EN and experience others spend as your own earned experience.

### Event Creation Format Example

`.event add` \
`name:Haha chain:開心系列` \
`exp:SAN`\
`0:你今天的運氣真好;你是個好人;我愛你` \
`-1:你中招了;你不好運要-SAN了` \
`1:你吃了好味的糖，加SAN`

#### name ->&#x20;

Event title&#x20;

#### chain->&#x20;

Series name; others can target that series for random draws&#x20;

#### exp ->&#x20;

(Optional) Name for experience, e.g. SAN shows “You lost X SAN”&#x20;

#### 0:你今天的運氣真好;你是個好人;我愛你&#x20;

-> (event type):(description);(description 2);.....(description N)&#x20;

#### Description ->

One description is picked at random from 1, 2, … N

#### Event Types ->&#x20;

&#x20; 0\. Nothing happens

1. Gain X experience directly
2. For the next X times, gain X times experience
3. Give everyone in the group 1 experience
4. Give the player experience the author has earned
5. Absorb X experience from X people in the channel -1. Lose X experience directly -2. Stop gaining experience (X times) -3. Lose X experience to the event author -4. Distribute X experience to X people in the channel -5. Lose X experience per message (for X messages)

***

#### Limits

A. In one event, positive options must outnumber negative ones \
B. One event can have 3 + ROUNDDOWN(creator LV / 10) options \
C. An event cannot be all positive effects \
D. Total EN available for one event is (10 + LV); negative events consume X EN
