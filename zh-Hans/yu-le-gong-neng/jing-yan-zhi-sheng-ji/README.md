---
description: 用来纪录群组参与度的功能，加入LV概念，嘛，就是MEE6的概念。
---

# 经验值升级

![](<../../.gitbook/assets/image (3) (1) (1).png>)

`.level (show config LevelUpWord RankWord)`

想在频道中说话可以得到经验，请开启这个功能!还可以和世界各地的人比较LV

按发言次数增加经验，提升等级，实现服务器内排名等欢乐功能

当经验达到要求，就会弹出通知，提示你已提升等级。

### 使用教学

默认并不开启，需要输入`.level config 11` 启动功能

数字11代表等级升级时会进行通知\
10代表不会通知\
00的话代表关闭功能

### 默认回应

* 是「 XXXX 《称号》， 你的克苏鲁神话知识现在是 X点！
* 现在排名是XX人中的第XX名！XX%！
* 调查经验是XX点。」

### 功能一覧

输入`.level LevelUpWord (内容)` 修改在这群组升级时弹出的升级语\
输入`.level RankWord (内容)` 修改在这群组查找等级时的回应\
输入`.level TitleWord -(LV) (内容)`，修改称号，大于等级即会套用\
建议由-0开始，可一次输入多个，如 `.level TitleWord -0 幼童 -5 学徒 -10 武士`\
输入`.level RankWord/LevelUpWord/TitleWord del` 即使用默认字句\
输入`.level RankWord/LevelUpWord/TitleWord show` 即显示现在设置 \
输入`.level show` 可以查找你现在的等级 \
输入`.level showMe (数字)` 可以查找这群组排名 默认头5名 \
输入`.level showMeTheworld (数字)` 可以查找世界排名 默认头6名 \
输入`.level showMeAtTheworld` 可以查找自己的世界排名

### 升级语及RankWord可使用不同代码&#x20;

`{user.name}` 名字\
`{user.level}` 等级\
`{user.title}` 称号 \
`{user.exp}` 经验值 \
`{user.Ranking}` 现在排名 \
`{user.RankingPer}` 现在排名百分比 \
`{server.member_count}` 现在频道中总人数
