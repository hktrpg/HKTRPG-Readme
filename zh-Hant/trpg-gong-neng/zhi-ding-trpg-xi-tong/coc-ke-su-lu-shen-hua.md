---
description: 這裡介紹如何使用HKTRPG進行COC擲骰
---

# CoC克蘇魯神話

`cc` `cc(n)1~2` `ccb` `ccrt` `ccsu` `.dp` `.cc7build` `.cc6build` `.cc7bg` `.sc` `.chase`

{% hint style="info" %}
[CoC7ed規則書介紹](https://www.patreon.com/posts/67705000)
{% endhint %}

### 擲骰檢定

* CoC6版擲骰： `ccb 80` 技能小於等於80
* CoC7版擲骰： `cc 80` 技能小於等於80\
  ![](<../../.gitbook/assets/image (43).png>)
* CoC7版獎勵骰： cc(1\~2) `cc1 80` 一粒獎勵骰
* CoC7版懲罰骰： ccn(1\~2) `ccn2 80` 兩粒懲罰骰
* CoC7版聯合檢定：cc (x,y) (z,a) `cc 80,60 鬥毆,魅惑` \
  支援獎勵懲罰骰，如：`cc１ 80,60 鬥毆,魅惑`
* CoC7版SanCheck ： `.sc (SAN值) (成功)/(失敗)`\
  ![](<../../.gitbook/assets/image (28).png>)
*   CoC7 手動成長或增長檢定

    ![](<../../.gitbook/assets/image (32).png>)\
    可以一次輸入多個技能<br>

    `.dp` 或 `成長檢定` 或 `幕間成長 (技能%) (名稱)` \
    `.DP 50 騎乘 60 鬥毆 50 60` \
    `.DP 50 60 50` \
    `成長檢定 65 頭槌 45 劍術`  \
    `幕間成長 40 單車`

### COC資料

`coc7版 神話組織 隨機產生： 啓動語 .cccc` \
`coc7版 神話資料 隨機產生： 啓動語 .ccdr` \
`coc7版 施法推骰後果： 啓動語 .ccpc`\
![](<../../.gitbook/assets/image (7).png>)

![](<../../.gitbook/assets/image (9).png>)

### 瘋狂結果

* coc7版 即時型瘋狂： 啓動語 `ccrt`
* coc7版 總結型瘋狂： 啓動語 `ccsu`

### `創造角色`

* coc6版創角： 啓動語 `.cc6build`
* coc7版創角： 啓動語 `.cc7build (歲數7-79)`
* coc7版隨機創角 ： 啓動語 `.cc7build random`
* coc7版自由分配點數創角 ： 啓動語 `.cc7build .xyz (歲數7-89)`

如`.cc7build .752` \
就會擲出\
`7次 3d6 * 5`\
`5次 (2d6+6) * 5` \
`2次 3d6 * 5`

可只輸入`.`  不輸入xyz\
預設值為 .53 即`5次 3d6 * 5` 和`3次 (2d6+6) * 5`&#x20;

![](<../../.gitbook/assets/image (45).png>)

* coc pulp版創角 ： 啓動語 `.ccpulpbuild`
* coc7版角色背景隨機生成： 啓動語 `.cc7bg`

### 成長檢定紀錄功能

![](<../../.gitbook/assets/image (34) (1).png>)

開啓後將會紀錄你使用CC功能投擲成功和大成功大失敗的技能， 然後可以呼叫出來進行自動成長。

* `.dp start` ： 開啓紀錄功能
* `.dp stop` ： 停止紀錄功能
* `.dp show` ： 顯示擲骰紀錄
* `.dp auto` ： 進行自動成長並清除擲骰紀錄
* `.dp clear` ： 清除擲骰紀錄
* `.dp clearall` ： 清除擲骰紀錄包括大成功大失敗

### coc7版追逐戰產生器:&#x20;

指令 `.chase`&#x20;

{% hint style="info" %}
追逐戰功能使用了可選規則及我對規則書之獨斷理解， 並不一定完全符合規則書內容，請自行衡量使用，建議使用前詳細閱讀規則書第七章追逐
{% endhint %}

![](<../../.gitbook/assets/image (40).png>)

