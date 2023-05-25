---
description: TRPG有時可能需要定時發訊，例如提醒跑團或是倒數交咭日子。
---

# 定時發訊功能

![](<../.gitbook/assets/image (35) (1).png>)

定時功能擁有兩種模式\
`.at .cron mins hours delete show`

### 【at】 指定一個時間，然後只發佈一次

輸入`.at 20220604 1900` **(年月日 時間)**\
`.at 5mins` (五分鐘後)\
`.at 5hours` (五小時後)\
就會在指定時間發佈指定一個信息

#### 支援擲骰

使用`[[]]`包著指令就可\
範例\
`.at 5hours`\
`[[CC 60]]`\
`[[立FLAG]]`

### 【cron】 每天或隔天一個指定時間可以發佈一個信息(24小時制)

#### 格式

必須輸入一個24小時制的時間，如**`2300`**，然後可以用`-`\
加上像數字`1`,`2`,`3`表示相隔多少天，\
或`mon` `tue` `wed` `thur` `friday` `sat` `sun`\
來表示逢星期幾發佈

#### 範例

`on 0831` \
`每天八時三十一分嚎叫吧!`

`.cron 0721`\
`每天七時二十一分擲`\
`[[CC 80 幸運]]`

`.cron 1921-2`\
`我將會每隔兩天的晚上7時21分發一次訊息`

`.cron 1921-wed-mon`\
`我將會每個星期一和三發一次訊息`

### 以自定的名字和圖片發訊(Patreoner專用)

在時間後加上name 和link 就可以像.meX 功能，使用自定的身份來定時發訊

![](<../.gitbook/assets/image (19).png>)\
**範例**

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
* `.cron / .at show` 可以顯示已新增的定時訊息
* `.cron / .at delete (序號)` 可以刪除指定的定時訊息
* 如 `.at delete 1` 請使用`.at show` 查詢序號
