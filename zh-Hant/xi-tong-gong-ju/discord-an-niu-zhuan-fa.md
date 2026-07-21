---
description: Discord 限定。把角色卡按鈕或要求擲骰按鈕的結果，轉發到指定頻道。
---

# Discord 按鈕轉發（.forward）

{% hint style="info" %}
僅限 Discord。可將 `.ch button`、`.char button`、`.re` 產生的按鈕結果，轉發到另一個頻道。
{% endhint %}

### 用途

跑團時角色卡按鈕常釘在私頻或準備頻道；用 `.forward` 可讓點擊結果同步出現在公開跑團頻道，不必複製貼上。

### 指令

| 指令 | 說明 |
| ---- | ---- |
| `.forward [Discord訊息連結]` | 將該則按鈕訊息的結果，轉發到**當前頻道** |
| `.forward show` | 顯示所有轉發設定 |
| `.forward delete [編號]` | 刪除指定編號的轉發設定 |

### 支援的按鈕類型

* `.ch button`（角色卡狀態）
* `.char button`（角色卡擲骰）
* `.re`（[要求擲骰／點擊](../trpg-gong-neng/yao-qiu-zhi-tou.md)）

### 使用流程（建議）

1. 在準備頻道產生按鈕，例如 `.ch button` 或 `.char button 角色名`
2. 對該則訊息按右鍵 → **複製訊息連結**
3. 到要顯示結果的跑團頻道，輸入：`.forward https://discord.com/channels/...`
4. 之後在原按鈕上點擊，結果會轉發到已設定的頻道

### 注意事項

* 只能轉發**自己的**角色卡按鈕
* 每個按鈕只能指定一個轉發頻道
* 轉發數量受 [VIP 等級](../kai-shi-shi-yong/kai-fa-zhi-yuan.md#vip-權益對照) 限制（一般約 4 個起，視等級提高）
* 轉發設定會永久保存，直到你刪除

### 相關頁面

* [角色卡](../trpg-gong-neng/kai-shi-jin-hang-trpg/jiao-se-ka.md)（含按鈕與 `.forward` 搭配）
* [要求擲骰](../trpg-gong-neng/yao-qiu-zhi-tou.md)
* [開發支援（VIP 對照）](../kai-shi-shi-yong/kai-fa-zhi-yuan.md#vip-權益對照)
