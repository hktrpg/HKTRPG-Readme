---
description: 經驗值升級的附屬功能，可以另外增加經驗值或是得到特效。
---

# 事件功能

![](<../../.gitbook/assets/image (31).png>)

`.event (add delete show) .evt (random/事件名稱)`

經由新增的事件，會得到一些狀態或增加減少經驗值，並可以賺取額外經驗值。

### 使用教學

`.event add` 詳情看下面說明 - 新增事件 \
`.event delete (事件名稱)` - 刪除事件 \
`.event show` - 顯示你新增的所有事件, 及賺取了的EXP \
`.event show (事件名稱)` - 顯示你新增的指定事件詳情 \
`.event useExp` - 在群組中使用, 將會得到你賺取的EXP\
`.evt random` - 進入隨機的事件, 消耗5EN \
`.evt (系列名稱)` - 進入指定的系列事件, 消耗10EN \
`.evt (事件名稱)` - 進入指定的事件, 消耗15EN

### 規則

EN上限 = 20+LV 每10分鐘回複1點EN

#### 得知事件名稱的方法

別人告知 或 經隨機事件知道名字 設計事件的好處 能夠吸收對方消耗的en和經驗值 作為自己賺取到的經驗值

### 新增事件的格式範例

`.event add` \
`name:Haha chain:開心系列` \
`exp:SAN`\
`0:你今天的運氣真好;你是個好人;我愛你` \
`-1:你中招了;你不好運要-SAN了` \
`1:你吃了好味的糖，加SAN`

#### name ->&#x20;

事件標題&#x20;

#### chain->&#x20;

系列名稱，別人可以指定該系列來進行抽選&#x20;

#### exp ->&#x20;

(可選)經驗值的名稱, 例如改成SAN, 會變成「你損失了X點SAN」&#x20;

#### 0:你今天的運氣真好;你是個好人;我愛你&#x20;

\-> (事件類型):(事件的描述);(事件的描述2);.....(事件的描述N)&#x20;

#### 事件的描述->

會從描述1,2,N中隨機選取其中一個

#### 事件類型 ->&#x20;

&#x20; 0\. 沒有事發生

1. 直接增加X點經驗
2. 未來X次裡會得到 X 倍經驗值
3. 贈送群組所有人1點經驗
4. 贈送作者已賺取到的經驗給玩家
5. 從整個CHANNEL 的X人吸收X點經驗 -1. 直接減少X點經驗 -2. 停止得到經驗(X次) -3. 被事件開發者吸收X點經驗 -4. 分發X經驗給整個CHANNEL中的X人 -5. 每次發言減少X經驗(X次內)



#### 限制

A. 一個事件中，正面選項要比負面選項多 \
B. 一個事件中，可以有3+(ROUNDDOWN 設計者LV/10) 項選項 \
C. 一個事件中，不可以全部正面效果 \
D. 一個事件可用的總EN 為(10+LV)，負面事件消耗X點EN
