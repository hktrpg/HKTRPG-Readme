---
description: TRPG有时可能需要定时发讯，例如提醒跑团或是倒数交咭日子。
---

# 定时发讯功能

![](<../.gitbook/assets/image (35) (1).png>)

定时功能拥有两种模式\
`.at .cron mins hours delete show`

### 【at】 指定一个时间，然后只发布一次

输入`.at 20220604 1900` **(年月日 时间)**\
`.at 5mins` (五分钟后)\
`.at 5hours` (五小时后)\
就会在指定时间发布指定一个信息

#### 支持掷骰

使用`[[]]`包着指令就可\
范例\
`.at 5hours`\
`[[CC 60]]`\
`[[立FLAG]]`

### 【cron】 每天或隔天一个指定时间可以发布一个信息(24小时制)

#### 格式

必须输入一个24小时制的时间，&#x5982;**`2300`**，然后可以用`-`\
加上像数字`1`,`2`,`3`表示相隔多少天，\
或`mon` `tue` `wed` `thur` `friday` `sat` `sun`\
来表示逢星期几发布

#### 范例

`on 0831` \
`每天八时三十一分嚎叫吧!`

`.cron 0721`\
`每天七时二十一分掷`\
`[[CC 80 幸运]]`

`.cron 1921-2`\
`我将会每隔两天的晚上7时21分发一次消息`

`.cron 1921-wed-mon`\
`我将会每个星期一和三发一次消息`

### 以自定的名字和图片发讯(Patreoner专用)

在时间后加上name 和link 就可以像.meX 功能，使用自定的身份来定时发讯

![](<../.gitbook/assets/image (19).png>)\
**范例**

`.cron 2258` \
`name=Sad` \
`link=`[`https://user-images.githubusercontent.com/23254376/113255717-bd47a300-92fa-11eb-90f2-7ebd00cd372f.png`](https://user-images.githubusercontent.com/23254376/113255717-bd47a300-92fa-11eb-90f2-7ebd00cd372f.png) \
`第一行` \
`[[2d3 第二行]]` \
`hello world 文末`

`.at 1mins` \
`name=Sad` \
`link=`[`https://user-images.githubusercontent.com/23254376/113255717-bd47a300-92fa-11eb-90f2-7ebd00cd372f.png`](https://user-images.githubusercontent.com/23254376/113255717-bd47a300-92fa-11eb-90f2-7ebd00cd372f.png) \
`第一行` \
`[[2d3 第二行]]` \
`hello world 文末`

### 功能一覧

* `.cron / .at` 增加信息
* `.cron / .at show` 可以显示已添加的定时消息
* `.cron / .at delete (序号)` 可以删除指定的定时消息
* 如 `.at delete 1` 请使用`.at show` 查找序号
