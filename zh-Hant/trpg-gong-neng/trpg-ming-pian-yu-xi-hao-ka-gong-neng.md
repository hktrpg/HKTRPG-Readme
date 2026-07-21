---
description: >-
  本文介紹兩個 TRPG 角色相關的網頁功能：TRPG
  角色卡與遊玩喜好卡。這兩項功能分別提供完整的編輯、匯出與備份功能，同時支援自訂樣式與色彩設置，讓使用者可以快速建立與分享個人化的角色卡與喜好資訊。
---

# TRPG 名片與喜好卡功能

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>範例君-TRPG 名片</p></figcaption></figure>

### 與 Bot 角色卡（`.char` / `.ch`）的關係

| | 網頁名片／喜好卡 | Bot 角色卡（`.char` / `.ch`） |
| --- | --- | --- |
| 用途 | 對外展示、美觀分享、玩家喜好說明 | 跑團擲骰、改 HP／SAN、快速技能檢定 |
| 入口 | [character.hktrpg.com](https://character.hktrpg.com/)、[player.hktrpg.com](https://player.hktrpg.com) | 聊天軟體指令；編輯庫 [card.hktrpg.com](https://card.hktrpg.com/) |
| 連動 | 獨立網頁工具 | 可與群組連動擲骰（見 [角色卡](kai-shi-jin-hang-trpg/jiao-se-ka.md)） |

兩者互補：Bot 卡負責開團運算；名片／喜好卡負責形象與溝通。

### `.admin account` 登入網頁版入口

若要使用 **Bot 連動的網頁角色卡管理庫**（[card.hktrpg.com](https://card.hktrpg.com/)）：

1. **私訊** HKTRPG（不要在群組輸入密碼）
2. 輸入：`.admin account 使用者名稱 密碼`
   * 使用者名稱：4–16 字，可中英文
   * 密碼：6–16 字，英文字母與 `!@#$%^&*`
3. 開啟 [card.hktrpg.com](https://card.hktrpg.com/) 登入後編輯 `.char` 角色卡

名片站（character / player）為獨立網頁工具，依該站介面註冊或編輯即可。

### 1. TRPG 角色卡名片

* **網址**：[https://character.hktrpg.com/](https://character.hktrpg.com/)
* **功能特色**：
  * 編輯角色基本資訊、屬性、技能、筆記及其他多項自訂資料
  * 使用 Chart.js 與 SortableJS 呈現動態圖表與拖曳排序功能
  * 提供匯出 PNG 與備份連結，方便分享與儲存角色資料

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption><p>範例君-TRPG喜好卡</p></figcaption></figure>

### 2. TRPG 遊玩喜好卡

* **網址**：[https://player.hktrpg.com](https://player.hktrpg.com)
* **功能特色**：
  * 展示玩家頭像、暱稱和其他基本資訊
  * 支援多重編輯模式，可自訂遊玩方式、跑團平台、關係扮演等設定
  * 提供即時預覽與匯出為 PNG 的功能，並帶有色彩自訂設定

### 匯出 PNG 後怎麼用（Discord / LINE）

1. 在名片或喜好卡頁面編輯完成 → 匯出／下載 **PNG**
2. **Discord**：把 PNG 拖到頻道，或貼到自我介紹／角色頻道；需要按鈕擲骰仍用 Bot 的 `.ch button`
3. **LINE**：在聊天室選擇相簿／圖片傳送該 PNG；群組簡介可另存後上傳（視 LINE 介面）
4. 建議檔名標上角色名，方便團員辨識

{% hint style="info" %}
PNG 不會自動變成 Bot 角色卡。要在群組用 `.ch` 擲骰，仍須建立 [Bot 角色卡](kai-shi-jin-hang-trpg/jiao-se-ka.md)。
{% endhint %}
