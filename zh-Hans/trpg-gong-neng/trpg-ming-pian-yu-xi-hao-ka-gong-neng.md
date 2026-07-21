---
description: >-
  本文介绍两个 TRPG 角色相关的网页功能：TRPG
  角色卡与游玩喜好卡。这两项功能分别提供完整的编辑、导出与备份功能，同时支持自定义样式与色彩设置，让用户可以快速创建与分享个人化的角色卡与喜好信息。
---

# TRPG 名片与喜好卡功能

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>范例君-TRPG 名片</p></figcaption></figure>

### 与 Bot 角色卡（`.char` / `.ch`）的关系

| | 网页名片／喜好卡 | Bot 角色卡（`.char` / `.ch`） |
| --- | --- | --- |
| 用途 | 对外展示、美观分享、玩家喜好说明 | 跑团掷骰、改 HP／SAN、快速技能检定 |
| 入口 | [character.hktrpg.com](https://character.hktrpg.com/)、[player.hktrpg.com](https://player.hktrpg.com) | 聊天软件指令；编辑库 [card.hktrpg.com](https://card.hktrpg.com/) |
| 连动 | 独立网页工具 | 可与群组连动掷骰（见 [角色卡](kai-shi-jin-hang-trpg/jiao-se-ka.md)） |

两者互补：Bot 卡负责开团运算；名片／喜好卡负责形象与沟通。

### `.admin account` 登录网页版入口

若要使用 **Bot 连动的网页角色卡管理库**（[card.hktrpg.com](https://card.hktrpg.com/)）：

1. **私讯** HKTRPG（不要在群组输入密码）
2. 输入：`.admin account 用户名 密码`
   * 用户名：4–16 字，可中英文
   * 密码：6–16 字，英文字母与 `!@#$%^&*`
3. 打开 [card.hktrpg.com](https://card.hktrpg.com/) 登录后编辑 `.char` 角色卡

名片站（character / player）为独立网页工具，依该站界面注册或编辑即可。

### 1. TRPG 角色卡名片

* **网址**：[https://character.hktrpg.com/](https://character.hktrpg.com/)
* **功能特色**：
  * 编辑角色基本信息、属性、技能、笔记及其他多项自定义数据
  * 使用 Chart.js 与 SortableJS 呈现动态图表与拖曳排序功能
  * 提供导出 PNG 与备份链接，方便分享与保存角色数据

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption><p>范例君-TRPG喜好卡</p></figcaption></figure>

### 2. TRPG 游玩喜好卡

* **网址**：[https://player.hktrpg.com](https://player.hktrpg.com)
* **功能特色**：
  * 展示玩家头像、昵称和其他基本信息
  * 支持多重编辑模式，可自定义游玩方式、跑团平台、关系扮演等设置
  * 提供即时预览与导出为 PNG 的功能，并带有色彩自定义设置

### 导出 PNG 后怎么用（Discord / LINE）

1. 在名片或喜好卡页面编辑完成 → 导出／下载 **PNG**
2. **Discord**：把 PNG 拖到频道，或贴到自我介绍／角色频道；需要按钮掷骰仍用 Bot 的 `.ch button`
3. **LINE**：在聊天室选择相册／图片传送该 PNG；群组简介可另存后上传（视 LINE 界面）
4. 建议文件名标上角色名，方便团员辨识

{% hint style="info" %}
PNG 不会自动变成 Bot 角色卡。要在群组用 `.ch` 掷骰，仍须建立 [Bot 角色卡](kai-shi-jin-hang-trpg/jiao-se-ka.md)。
{% endhint %}
