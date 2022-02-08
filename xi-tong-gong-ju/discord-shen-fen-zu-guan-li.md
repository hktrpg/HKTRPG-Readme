---
description: Discord 在群組中以「分類」來對不同頻道進行管理，但大型群組的頻道數量往往極多，造成很長的頻道列表。
---

# Discord身分組管理

{% hint style="info" %}
身份組管理 預計增加 可以用指定的訊息來管理 \
現在由HKTRPG增加信息，不能再修改內容，有點麻煩
{% endhint %}

讓對指定訊息的Reaction Emoji(如😀😃😄)進行點擊的用家**分配指定的身分組別**

* 注意: 此功能需求HKTRPG擁有【編輯身分組】及【增加Reaction】的權限，請確定授權。
* 另外，使用者需要【伺服器管理者】權限。

![](https://camo.githubusercontent.com/64127e839e299470afdba2e56a364ecbed6351a1e72b24b247caeae377c7d777/68747470733a2f2f692e696d6775722e636f6d2f6b755a4841336d2e676966)

### 使用教學

首先去**User Setting**=>**Advanced**=>開啓**Developer Mode**

再去**Server Setting**=>**Roles**=>**新增**或**設定**希望分配的**身分組**

然後對該身分組按右鍵並按**COPY ID**，把該**ID**記下來

*   最後按以下格式來輸入指令

    `.roleReact add`

    `身份組ID Emoji`

    `[[message]]`

    `需要發佈的訊息`
*   **範例**

    `.roleReact add`

    `232312882291231263 🎨`

    `123123478897792323 😁`

    `[[message]]`

    `按🎨可得身分組-畫家`

    `按😁可得身分組-大笑`

### 功能一覧

* `.roleReact add` 新增指定信息
* `.roleReact show` 顯示現有的指定訊息的資料
* `.roleReact delete 序號` 刪除後該信息將不會再派發移除身分組

\
