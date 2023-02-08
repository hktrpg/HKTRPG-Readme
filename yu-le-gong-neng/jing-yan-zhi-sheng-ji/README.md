---
description: 用來紀錄群組參與度的功能，加入LV概念，嘛，就是MEE6的概念。
---

# 經驗值升級

![](<../../.gitbook/assets/image (3) (1).png>)

`.level (show config LevelUpWord RankWord)`

想在頻道中說話可以得到經驗，請開啓這個功能!還可以和世界各地的人比較LV

按發言次數增加經驗，提升等級，實現服務器內排名等歡樂功能

當經驗達到要求，就會彈出通知，提示你已提升等級。

### 使用教學

預設並不開啓，需要輸入`.level config 11` 啓動功能

數字11代表等級升級時會進行通知\
10代表不會通知\
00的話代表關閉功能

### 預設回應

* 是「 XXXX 《稱號》， 你的克蘇魯神話知識現在是 X點！
* 現在排名是XX人中的第XX名！XX%！
* 調查經驗是XX點。」

### 功能一覧

輸入`.level LevelUpWord (內容)` 修改在這群組升級時彈出的升級語\
輸入`.level RankWord (內容)` 修改在這群組查詢等級時的回應\
輸入`.level TitleWord -(LV) (內容)`，修改稱號，大於等級即會套用\
建議由-0開始，可一次輸入多個，如 `.level TitleWord -0 幼童 -5 學徒 -10 武士`\
輸入`.level RankWord/LevelUpWord/TitleWord del` 即使用預設字句\
輸入`.level RankWord/LevelUpWord/TitleWord show` 即顯示現在設定 \
輸入`.level show` 可以查詢你現在的等級 \
輸入`.level showMe (數字)` 可以查詢這群組排名 預設頭5名 \
輸入`.level showMeTheworld (數字)` 可以查詢世界排名 預設頭6名 \
輸入`.level showMeAtTheworld` 可以查詢自己的世界排名

### 升級語及RankWord可使用不同代碼&#x20;

`{user.name}` 名字\
`{user.level}` 等級\
`{user.title}` 稱號 \
`{user.exp}` 經驗值 \
`{user.Ranking}` 現在排名 \
`{user.RankingPer}` 現在排名百分比 \
`{server.member_count}` 現在頻道中總人數
