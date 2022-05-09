---
description: 這裡介紹一個在Discord上固定名字和頭像的發訊方式。
---

# 你的名字(扮演功能)

{% hint style="info" %}
在Discord之中，你在群組中的名字可以隨時改變，但問題是這種改變是追溯整個群組的，導致如果你有使用文字跑團，角色的名字圖片將會被打亂。

請注意，這種方式只可以以[.edit (修改舊訊息功能)](../xi-tong-gong-ju/discord-xiu-gai-jiu-xun-xi.md) 來**追加修改內容**。
{% endhint %}

`.myname` `.me` `.me1` `.me(名字)` \*Discord限定功能

### TRPG扮演發言功能

你可以設定一個角色的名字及頭像，

然後你只要輸入指令和說話，就會幫你使用該角色發言。

支援擲骰，請使用`[[]]`來包著擲骰指令 如`[[1d100]]`

注意: 此功能需求編輯Webhook及訊息功能，請確定授權

[![示範](https://camo.githubusercontent.com/9bdcdb52ced2f592682c1e44d91da5195212b917dd37813ad3d3a2d250c9a791/68747470733a2f2f692e696d6775722e636f6d2f56537a4f3038552e706e67)](https://camo.githubusercontent.com/9bdcdb52ced2f592682c1e44d91da5195212b917dd37813ad3d3a2d250c9a791/68747470733a2f2f692e696d6775722e636f6d2f56537a4f3038552e706e67)

### 使用教學

#### 1.設定角色

輸入 `.myname "名字" 角色圖片網址 名字縮寫(非必要)`

例子 `.myname "泉心 造史"` [`https://images.pexels.com/photos/10013067/pexels-photo-10013067.jpeg`](https://images.pexels.com/photos/10013067/pexels-photo-10013067.jpeg) `造`

_**名字**_是角色名字，會作為角色顯示的名字，但如果該名字有空格就需要用開`引號"`包著

如**"泉心 造史"** 不然可以省去`"`

_**圖片**_則是角色圖示，如果圖片出錯會變成最簡單的Discord圖示

圖片可以直接上傳到DISCORD或IMGUR.COM上

_**名字縮寫**_是 是用來方便你啓動它

例如_`.me造 「來玩吧」`_

#### 2.刪除角色

_**`.myname delete 序號 / 名字縮寫 / "名字"`**_

刪除方式是delete 後面接上序號或名字縮寫或名字

#### 3.顯示角色

`.myname show`

#### 4.使用角色

**`.me(序號/名字縮寫) 訊息`**

如

* **`.me1 泉心慢慢的走到他們旁邊，伺機行動`**
* **``**![](<../.gitbook/assets/image (13).png>)**``**
* **`.me造 「我接受你的挑戰」`**

### 功能一覧

* `.myname` - 設定角色
* `.myname delete 序號 / 名字縮寫` - 刪除角色
* `.myname show` - 顯示角色列表
* `.me(序號/名字縮寫) 訊息` - 使用角色發言





