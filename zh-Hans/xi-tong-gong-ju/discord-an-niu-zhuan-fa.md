---
description: Discord 限定。把角色卡按钮或要求掷骰按钮的结果，转发到指定频道。
---

# Discord 按钮转发（.forward）

{% hint style="info" %}
仅限 Discord。可将 `.ch button`、`.char button`、`.re` 产生的按钮结果，转发到另一个频道。
{% endhint %}

### 用途

跑团时角色卡按钮常钉在私频或准备频道；用 `.forward` 可让点击结果同步出现在公开跑团频道，不必复制粘贴。

### 指令

| 指令 | 说明 |
| ---- | ---- |
| `.forward [Discord消息链接]` | 将该则按钮消息的结果，转发到**当前频道** |
| `.forward show` | 显示所有转发设置 |
| `.forward delete [编号]` | 删除指定编号的转发设置 |

### 支持的按钮类型

* `.ch button`（角色卡状态）
* `.char button`（角色卡掷骰）
* `.re`（[要求掷骰／点击](../trpg-gong-neng/yao-qiu-zhi-tou.md)）

### 使用流程（建议）

1. 在准备频道产生按钮，例如 `.ch button` 或 `.char button 角色名`
2. 对该则消息按右键 → **复制消息链接**
3. 到要显示结果的跑团频道，输入：`.forward https://discord.com/channels/...`
4. 之后在原按钮上点击，结果会转发到已设置的频道

### 注意事项

* 只能转发**自己的**角色卡按钮
* 每个按钮只能指定一个转发频道
* 转发数量受 [VIP 等级](../kai-shi-shi-yong/kai-fa-zhi-yuan.md#vip-权益对照) 限制（一般约 4 个起，视等级提高）
* 转发设置会永久保存，直到你删除

### 相关页面

* [角色卡](../trpg-gong-neng/kai-shi-jin-hang-trpg/jiao-se-ka.md)（含按钮与 `.forward` 搭配）
* [要求掷骰](../trpg-gong-neng/yao-qiu-zhi-tou.md)
* [开发支持（VIP 对照）](../kai-shi-shi-yong/kai-fa-zhi-yuan.md#vip-权益对照)
