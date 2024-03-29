---
description: 有很多時候，擲骰的結果需要隱藏或只分享給指定人仕，這裡會示範怎樣做
---

# 暗骰

### DR  把擲骰結果私訊給自己

在指令前輸入 `dr` 結果會私訊你

如`dr 3d6`

`dr cc 80`

![](<../../.gitbook/assets/image (19) (1).png>)

### DDR DDDR 把結果私訊給指定的人

這功能讓你可以把擲骰結果私訊給GM或指定的人

`ddr` 私訊結果給已設定成群組GM的人及自己

`dddr` 可以私訊已設定的群組GM

#### 登記成GM

#### 自行輸入`.drgm addgm`

然後別人DDR 或DDDR (指令)即可以私訊給這位GM

例如輸入 `ddr cc 80 鬥毆`

就會把結果私訊GM及自己

例如輸入 `dddr cc 80 鬥毆`

就會把結果只私訊GM

#### 化名

如果想化名一下，輸入.drgm addgm (化名)&#x20;

輸出時會以化名代替

#### 功能一覧

* 輸入`.drgm show` 顯示所有GM
* 輸入`.drgm del(編號)`或all 即可刪除
* 輸入`dr (指令)` 私訊自己
* 輸入`ddr (指令)` 私訊GM及自己
* 輸入`dddr(指令)` 私訊GM
