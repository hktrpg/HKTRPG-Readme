---
description: >-
  StoryTeller
  是一个交互故事系统，允许用户添加自己的剧本、管理和游玩他人文本冒险游戏。系统支持多种平台（Discord、Line、Telegram、WhatsApp），并希望以丰富的功能来创造沉浸式的交互体验。你可以用它来设计抉择丛书式游戏或知识测验等等。
---

# StoryTeller 交互故事系统

{% hint style="info" %}
## 制作这个功能的目的，是因为小时候玩的抉择丛书，明明它好像一本小说，却可以让自己选择行动。长大后还是念念不忘，希望有一天自己也可以再玩到这种类型的游戏。
{% endhint %}

## 快速开始

#### 基本指令

```bash
# 启动剧本
.st start <alias|title> [alone|all|poll
 x]  
 
 # 查看可玩剧本清单
.st list     

# 游戏控制
.st pause                                   # 暂停目前进行中的剧本
.st continue [runId]                        # 继续暂停中的剧本
.st end                                     # 结束目前剧本
```

#### 游戏进行

```bash
.st goto <page>                             # 跳至指定页面/选项
.st set <var> <value>                       # 设置变量
```

### 详细功能说明

#### 1. 剧本管理

**添加和更新剧本**

**Discord 专用功能：**

```bash
# 以附件方式上传及下载
.st import <alias> [title]                  # 上传文件以添加剧本
.st update <alias> [title]                  # 上传文件以覆盖既有剧本
.st export <alias>                      # 将剧本以私讯发送文本档
```

**支持的文件格式：**

* `.json` - 完整的 StoryTeller 格式
* `.txt` - RUN\_DESIGN 语法格式

**剧本管理指令**

```bash
.st my [alias]                              # 查看自己添加之剧本统计
.st mylist                                  # 显示自己所有添加之剧本清单
.st list <alias>                            # 显示该剧本简介与可用信息
.st delete <alias>                          # 删除自己拥有的剧本
.st verify <alias>                          # 检查剧本内容格式是否正确
```

#### 2. 权限管理

```bash
.st allow <alias> AUTHOR                    # 仅作者本人可在任何地方启动（默认）
.st allow <alias>                           # 在本群组/频道允许启动
.st allow <alias> <groupId...>              # 允许指定之群组/频道启动（可多个）
.st allow <alias> all                       # 任何人皆可启动（公开）
```

#### 3. 游戏设置

```bash
.st edit alone|all|poll x                   # 发起者可切换参与权限
```

**参与权限选项：**

* `alone` - 仅发起者可交互
* `all` - 任何人可参与
* `poll x` - 激活 Discord 投票 x 分钟（默认 3，仅 Discord）

#### 4. 状态查看

```bash
.st game                                    # 显示目前运行与暂停中的游戏
.st debug                                   # 显示详细的调试信息
```

### RUN\_DESIGN 语法

StoryTeller 支持 RUN\_DESIGN 语法，这是一种简洁的文本格式来定义交互故事。

#### 基本语法结构

```txt
[meta] title "故事标题"
[intro] 故事简介内容

[player_var] name "请输入角色名称" "范例：小明"
[stat_def] hp 1 20 "生命值"
[var_def] gold 0 1000 "金币"

[label] 0
[title] 开始页面
[text] 欢迎来到这个故事世界！
[text|if=hp>10] 你的生命值看起来不错。
[set] gold=100
[random] 50%
[text] 你发现了一些宝藏！

[choice]
-> 继续前进 | 1
-> 休息一下 | 2 | if=hp<5
-> 结束游戏 | END

[label] 1
[title] 第二页
[text] 你继续前进了...
[ending]
[text] 恭喜你完成了故事！
```

#### 语法元素说明

**元数据**

* `[meta] title "标题"` - 设置故事标题

**简介**

* `[intro] 内容` - 设置故事简介

**玩家变量**

* `[player_var] key "提示文本" "默认值"` - 定义玩家需要设置的变量

**统计值定义**

* `[stat_def] key min max "标签"` - 定义游戏统计值（如生命值、攻击力等）

**变量定义**

* `[var_def] key min max "标签"` - 定义游戏变量

**页面结构**

* `[label] id` - 定义页面 ID
* `[title] 标题` - 设置页面标题
* `[text] 内容` - 显示文本内容
* `[text|if=条件] 内容` - 条件性文本
* `[text|speaker=角色] 内容` - 指定说话角色

**变量操作**

* `[set] key=value` - 设置变量值
* `[set|if=条件] key=value` - 条件性设置变量

**随机事件**

* `[random] 百分比%` - 设置随机触发几率

**选项**

* `[choice]` - 开始定义选项
* `-> 选项文本 | 目标页面 | if=条件 | stat=统计变化`

**结局**

* `[ending]` - 标记为结局页面

### 变量系统

#### 变量类型

1. **玩家变量** (`playerVariables`)
   * 由玩家设置的角色相关信息
   * 例如：角色名称、职业等
2. **统计值** (`stats`)
   * 游戏中的数值属性
   * 例如：生命值、攻击力、防御力等
3. **游戏变量** (`variables`)
   * 故事进行中的状态变量
   * 例如：金币数量、任务进度等

#### 变量操作

```bash
.st set name 小花          # 设置角色名称
.st set hp 12             # 设置生命值
.st set gold 500          # 设置金币数量
```

#### 条件表达式

支持多种条件判断：

```txt
[text|if=hp>10] 你的生命值很高
[text|if=gold>=100] 你有足够的金币
[text|if=name=="小明"] 你好，小明！
[text|if=hp>5 && gold>50] 你的状态不错
```

#### 骰子系统

支持骰子表达式：

```txt
[text] 你投出了 {2d6} 点伤害
[text] 你的攻击力是 {1d20+5}
```

### 平台特定功能

#### Discord 专用功能

1.  **投票系统**

    ```bash
    .st start story poll 5    # 激活 5 分钟投票
    .st edit poll 3          # 切换为 3 分钟投票
    ```
2. **文件上传**
   * 支持拖拽上传 `.json` 或 `.txt` 文件
   * 自动解析和验证文件格式
3. **私讯功能**
   * 可将剧本以私讯方式发送给用户

#### 跨平台兼容性

* **Line/Telegram/WhatsApp**: 支持基本功能，不支持投票和文件上传
* **Discord**: 支持所有功能，包括投票、文件上传等

### 限制和规则

#### 文件大小限制

* 最大上传文件：1MB
* 最大页数：400 页
* 每段文本最大长度：500 字

#### 用户限制

根据 VIP 等级有不同的限制：

| VIP 等级 | 剧本数量限制 | 同时进行游戏数 |
| ------ | ------ | ------- |
| 0      | 3      | 3       |
| 1      | 10     | 10      |
| 2+     | 100    | 100     |

#### 权限系统

1. **AUTHOR\_ONLY**: 仅作者可启动
2. **GROUP\_ONLY**: 仅指定群组可启动
3. **ANYONE**: 任何人可启动

### 最佳实践

#### 添加剧本

1. **规划故事结构**
   * 先设计主要情节和分支
   * 确定结局数量和多样性
2. **变量设计**
   * 合理设计统计值范围
   * 提供有意义的玩家变量
3. **测试和验证**
   * 使用 `.st verify` 检查格式
   * 测试所有分支和结局

#### 游戏进行

1. **角色设置**
   * 鼓励玩家设置丰富的角色信息
   * 根据角色信息提供个性化内容
2. **进度管理**
   * 适时使用暂停功能
   * 记录重要的游戏状态
3. **社群交互**
   * 在 Discord 中使用投票功能增加参与感
   * 鼓励玩家分享游戏体验

### 故障排除

#### 常见问题

1. **找不到剧本**
   * 检查 alias 是否正确
   * 确认权限设置
2. **无法启动游戏**
   * 检查是否已达同时进行游戏数限制
   * 确认剧本格式是否正确
3. **变量设置失败**
   * 检查变量名称是否正确
   * 确认数值范围是否合理

#### 调试工具

```bash
.st debug    # 显示详细的游戏状态信息
```

### 范例剧本

#### 简单冒险故事

```txt
[meta] title "森林冒险"
[intro] 你是一个勇敢的冒险者，正在探索神秘的森林。

[player_var] name "请输入你的角色名称" "范例：亚瑟"
[stat_def] hp 10 20 "生命值"
[stat_def] strength 1 10 "力量"

[label] 0
[title] 森林入口
[text] 欢迎，{name}！你来到了神秘的森林入口。
[text] 你的生命值：{hp}，力量：{strength}
[choice]
-> 进入森林 | 1
-> 先休息一下 | 2 | if=hp<15
-> 离开 | END

[label] 1
[title] 森林深处
[text] 你进入了森林深处，发现了一个古老的遗迹。
[random] 30%
[text] 突然，一只野兽出现了！
[set] hp=hp-5
[choice]
-> 战斗 | 3 | if=strength>5
-> 逃跑 | 4
-> 投降 | END

[label] 2
[title] 休息
[text] 你决定先休息一下，恢复了一些体力。
[set] hp=hp+5
[choice]
-> 现在进入森林 | 1
-> 继续休息 | 2

[label] 3
[title] 战斗胜利
[text] 你勇敢地击败了野兽！
[set] strength=strength+1
[ending]
[text] 恭喜你完成了冒险！

[label] 4
[title] 逃跑
[text] 你选择了逃跑，虽然安全但错过了宝藏。
[ending]
[text] 你安全离开了森林，但没有获得任何奖励。
```

这个范例展示了 StoryTeller 的基本功能，包括变量设置、条件判断、随机事件和多重结局。

### 更新日志

#### 最新功能

* 支持 RUN\_DESIGN 语法
* Discord 投票系统
* 跨平台暂停/继续功能
* 增强的角色统计系统
* 改进的权限管理

#### 已知限制

* 投票功能仅限 Discord
* 文件上传仅限 Discord
* 某些高端功能需要 VIP 等级

***

StoryTeller 系统持续更新中，请关注最新版本的功能和改进。
