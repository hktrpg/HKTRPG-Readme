---
description: 本指南描述一种简洁、便于人手编辑的交互故事文本格式（RUN_DESIGN）
---

# RUN\_DESIGN 文本格式指南

## RUN\_DESIGN 文本格式指南

本指南描述一种简洁、便于人手编辑的交互故事文本格式（RUN\_DESIGN）。同时支持可逆转换：JSON → RUN\_DESIGN → JSON，在支持的字段范围内不会有语义流失。

### 目标

* 简单、可读、利于版本控管的文本格式
* 能编译成 JSON 的故事结构
* 能将 JSON 无语义差异地导出回文本

### 文件编码

* UTF-8

### 空白与注解（Whitespace & Comments）

* 允许空白行。
* 以 `//` 开头的单行为注解，编译时会被忽略。请另开新行。

### 顶层元数据（Metadata）

* `[meta] title "<Title>"` 设置故事标题
* `[meta] author "<Author>"` 设置作者（必填；导入/更新时若缺少会被拒绝）
* `[intro] <text>` 追加一行故事导言（可重复多行），在剧本开始时会显示。

显示行为：

* 在 `.st list` 中：
  * 指定 alias 时，会完整显示该故事的导言（若有）。
  * 列出所有可启动剧本时，会在每列标题下显示导言第一行的预览（最多 80 字）。
* 在 `.st mylist` 中：
  * 每项剧本会显示导言第一行的预览（最多 80 字）。
* 在启动游戏后且玩家变量尚未完成设置时：
  * 角色设置提示前会先显示【简介】区块，内容为导言全文。

范例：

```
[meta] title "猫咪的一天"
[intro] 欢迎来到交互故事！
```

### 玩家变量（Player Variables）

* `[player_var] <key> "<prompt>" ["<placeholder>"]`
  * key：识别字，例如 `cat_name`
  * prompt：显示给玩家的提问
  * placeholder：可选的提示文本

范例：

```
[player_var] cat_name "1. 请输入你的猫咪名字：" "例如：橘子、Mochi、小黑"
[player_var] owner_name "2. 请输入主人的名字：" "小明、艾蜜莉、阿杰"
```

### 游戏属性（Game Stats）

* `[stat_def] <key> <min> <max> ["<label>"]`
* 初始化：未被明确设置时，首次开始时以 `min`\~`max` 随机整数初始化。
* 锁定：若该属性曾被内容内的 `[set]` 明确指定，之后将不再被随机初始化覆写。

范例：

```
[stat_def] Cuteness 1 10 "萌度 (Cuteness)"
[stat_def] Energy 1 10 "活力 (Energy)"
[stat_def] Mischief 1 10 "淘气度 (Mischief)"
```

### 变量（Variables）

* `[var_def] <key> <min> <max> ["<label>"]`

范例：

```
[var_def] rain 0 1 "下雨"
```

### 页面（Pages）

故事由多个页面组成。

* 定义页面标签（ID）：`[label] <id>`
  * **限制**：页面 ID 只能使用数字（如 `0`, `1`, `2`, `10` 等）
  * **开点页面**：`[label] 0` 为故事的起始页面，游戏开始时会自动加载此页面
  * 其他页面可使用任意数字作为 ID，建议使用连续数字以保持可读性
* 可选页面标题：`[title] <text>`
* 页面内容（不限行数）：
  * `[text] <content>`
  * `[text|if=<expr>] <content>` 条件显示
  * `[text|else] <content>` 与前一或多个连续的 `[text|if=...]` 形成条件链，只会显示第一个符合条件的项目；若皆不符合则显示 `else`。也支持于结局区块中使用。
  * `[text|ifs=<expr>] <content>` 独立条件显示：只要命中就显示，不会与上下邻近的 `[text|if=...]`/`[text|else]` 形成条件链。
  * `[text|speaker=<key>] <content>` 指定说话者
  * `[text|speaker=<key>,if=<expr>] <content>` 指定说话者且具条件
  * `[random] <percent>%` 仅影响「下一行」的 `[text]`（例如 30%），`percent` 为 0\~100 的整数。
  * `[set] <key>=<expr>` 在渲染时设置值：若 `key` 属于已定义的 `stat_def`，则写入 `stats`；否则写入 `variables`。`<expr>` 支持基本表达式（见下文）。
    * 任一属性一旦被 `[set]` 明确设置，之后将不再由随机初始化覆写。
  * 文本内可直接掷骰：`{xDy}` 会在显示时掷骰并以总和取代，例如 `{1D100}`、`{2d20}`、`{3d6}`。
* 结局标记：
  * `[ending]` 之后的 `[text]` 行视为结局文本，会使用第一个符合条件的结局
  * 支持条件链：可使用多行 `[text|if=...]` 后接一行 `[text|else]` 作为后备
  * 要求：一个有效的 RUN\_DESIGN 必须至少包含一个带有 `[ending]` 标记的页面；若未定义结局，上传/更新将被拒绝。
* 选项区块：
  * `[choice]` 开始定义选项列表
  * `-> <text> | <页面代号> [| if=<expr>] [| stat=a+1,b-2]`
    * `<页面代号>` 必须为数字页面 ID，或使用带字母尾码的变体（例如 `2a`、`2b`、`2c`）；或特殊值 `END`。
    * **新功能**：支持 `2a`, `2b`, `2c` 等格式，其中数字部分（如 `2`）为实际跳转的页面，字母部分（如 `a`, `b`, `c`）仅用于区分不同的加成或描述变体（实际跳转到 `2`）。
    * `<页面代号>` 为 `END` 时，接口会提供「`.st end`」按钮以结束游戏。
    * `stat=` 仅支持整数加减，并在成功前往该选项之目标页面时套用（例：`Cuteness+1,Energy-2`）。

#### 新功能：多选项同页面跳转

使用 `2a`, `2b`, `2c` 等格式可以让多个选项都跳转到同一个页面（如页面 `2`），但每个选项可以有不同的加成效果：

```
[choice]
-> 准备好大闹一场了！ | 2a | stat=Mischief+1
-> 先伸个懒腰，看看今天心情如何。 | 2b | stat=Cuteness+1
-> 今天也要充满活力！ | 2c | stat=Energy+1
```

当玩家使用 `.st goto 2a`、`.st goto 2b`、`.st goto 2c` 时：

* 都会跳转到页面 `2`
* 但会分别获得不同的加成：淘气度+1、萌度+1、活力+1

#### 表达式（Expressions）

* 条件以小型、类 JS 的子集合为语法，运行于 scope（`variables` + `stats` + `playerVariables`）
* 支持操作符：`&& || ! < <= > >= == === != !== + - * / % ()`
* 安全限制：不允许任何函数调用；不可访问 `globalThis`、`global`、`process`、`this`、`Function`、`constructor`、`require` 等识别字。
  * 范例：`if=Cuteness>=8 && Energy>3`
* 支持一元否定 `!expr`（可搭配括号以控制优先级）。
  * 范例：`if=(Strength>5) && !(Agility>5)`

**掷骰（Dice）**

* 在条件与赋值表达式中，可直接使用 `xDy` 字面量，会在运算前掷骰并以总和值替换，例如：
  * `if=2d20>25`
  * `[set] luck=3d6+2`
  * 允许的范围：`x` 1~~100、`y` 1~~10000；超出将被夹在此范围内。

**条件赋值（Conditional Set）**

* 支持在 `[set]` 上使用条件选项：`[set|if=<expr>] key=<expr>`。
* 结合掷骰，可实作常见的检定流程。

范例：

```
[stat_def] san 0 100 "SAN"
[set] san=70

[label] SAN_CHECK
[set] sancheck=1d100
[text] sancheck={sancheck}
[set|if=san<sancheck] san=san-1
[text|if=san<sancheck] 你扣了1san
[text|if=san>=sancheck] 你稳住了心神
```

#### 范例页面（Example Page）

```
[label] 0
[title] 角色创造
[text] 设置完成！现在，让我们来看看 {cat_name} 今天的状态...
[text] (系统会为你随机生成 1-10 的数值)
[text] - 萌度 (Cuteness): {Cuteness}
[text] - 活力 (Energy): {Energy}
[text] - 淘气度 (Mischief): {Mischief}
[text|ifs=Wit==1]确切属性值 -> Wit: 1
[text|ifs=Wit==2]确切属性值 -> Wit: 2
[text|ifs=Wit==3]确切属性值 -> Wit: 3
[text|ifs=Wit==4]确切属性值 -> Wit: 4
[text|if=Cuteness>Mischief+2] 他笑了笑，把它捡起来，说：「你这个小捣蛋鬼。」然后把我抱起来，亲了一下。我的恶作剧成功了！
[text|if=Cuteness<=Mischief+2 && Cuteness > 4] 他叹了口气说：「{cat_name}，不可以这样喔。」但他还是忍不住摸了摸我的头。看来这次被原谅了。
[text|if=Cuteness<=4] 他看起来有点生气，把我抱起来念了几句，今天没有点心了。
[text|if=Cleverness>=10] 他注意到我的聪明眼神，笑着说：「你是不是在计划什么？」并给了我额外奖励。
[text|else] 他只是摇摇头，收拾了一下。今天是普通的一天。
[choice]
-> 准备好了吗？ | 1
```

#### 结局页（Ending Page）

```
[label] 22
[title] 结局
[ending]
[text|if=Cuteness>8] 以卖萌获得原谅
[text|else] 温柔的无奈
[choice]
-> 回到开头 | 0
-> 结束游戏 | END
```

### 占位符（Placeholders）

* 在 `[text]` 内使用 `{key}` 会依序从 `playerVariables`、`stats`、`variables` 取值并套入（优先级如前，后者可覆盖前者）。
* 若找不到对应键，将保留原样（例如 `{unknown_key}` 会原样输出）。

#### 注：兼容性与限制补充

* 目前不支持以纯字符串作为页面 ID；请使用数字页面 ID（例如 `0`, `1`, `2`）。
* `[set]` 行允许在值的后方加上行尾 `//` 注解，导入时该注解会被忽略，不影响赋值内容。

### 往返转换（Round Trip）

* 导入文本（于 Discord 夹带文件）：发送 `.st import <alias> [title]` 并附上 `.txt`（RUN\_DESIGN）或 `.json` 文件
* 更新既有剧本：`.st update <alias> [title]` 并附上新文件
* 导出文本：`.st exportfile <alias>`（机器人将以私讯发送文本档）
* 验证可逆：`.st verify <alias>`

#### 范式（Normalization）

* 编译器会将紧邻的 `[random]` 与其后的第一行 `[text]` 合并解释为「几率显示」。
* 导出时，若页面是结局页，`[ending]` 会紧跟在该页 `[label]` 之下，以维持可逆性。

### 惯例（Conventions）

* **开点页面**：`[label] 0` 为故事的起始页面，游戏开始时会自动加载此页面。若需要可在编译后的 JSON 再行设置。
* **页面 ID 限制**：只能使用数字作为页面 ID。
* 说话者为可选；示例采用纯文本。
* 若需在内文中加入随机性，请于欲影响的 `[text]` 之前「紧贴」放置 `[random] <percent>%`（percent 为整数）。
* 若需在选项上改变属性值，使用 `stat=a+1,b-2`（仅支持整数加减）。
* 若需多个选项跳转到同一页面但有不同的加成效果，使用 `2a`, `2b`, `2c` 等格式。

### 最佳实务（Best Practices）

* 为可读性建议使用数字且连续的 ID
* 条件判断尽量简单并以已定义的键为基础
* 避免过长的行；可拆分成多个 `[text]`
* 确保每个结局页面都提供重新开始或结束的选项
* 善用 `2a`, `2b`, `2c` 格式来创建有不同加成的选项

### 限制（Limits）

* 最多页数：400
* 每段文本（每一行 `[text]`，包含结局文本）最长 500 字
* 至少需包含一个带有 `[ending]` 的页面
* 导入/更新之附件大小上限：约 1 MB
* 页面 ID 只能使用数字

### 更多范例（More Examples）

#### 说话者（Speakers）与条件链

```
[label] 5
[title] 对话示例
[text|speaker=cat] 喵～今天要做什么呢？
[text|if=Energy>=8] 我觉得精力充沛！
[text|if=Energy>=5 && Energy<8] 还行，可以动一动。
[text|else] 有点想睡觉……
[choice]
-> 出门巡视 | 6
-> 先小睡一下 | 7
```

说话者为可选字段，渲染时仅作为数据字段保存，不影响文本输出。

#### 随机显示（Random）

```
[label] 6
[title] 随机事件
[random] 30%
[text] 你意外捡到一根猫薄荷棒！
[text] 无论是否捡到，你继续前进。
```

`[random] <percent>%` 仅作用于其后第一行 `[text]`，编译器在导出时会保持可逆性。

#### 内嵌掷骰（Dice）与条件检定

```
[label] 8
[title] 掷骰检定
[set] roll=1d20
[text] 你的检定结果为：{roll}
[text|if=roll+Energy>=18] 大成功！
[text|else] 普通成功或失败。
```

在表达式中可使用 `xDy` 字面量；在文本中可用 `{xDy}` 直接内嵌掷骰，显示总和。

#### 条件赋值（Conditional Set）与字符串值

```
[label] 9
[title] 状态标记
[set|if=Energy>=8] mood="energetic"
[set|if=Energy<8] mood="lazy"
[text] 目前心情：{mood}
```

RHS 以引号包装时会被视为字符串常值；否则会尝试以表达式求值。

#### 多个选项同页面跳转（带加成）

```
[label] 10
[title] 开场选择
[choice]
-> 走力量路线 | 2a | stat=Power+1
-> 走敏捷路线 | 2b | stat=Agility+1
-> 走智力路线 | 2c | stat=Wit+1

[label] 2
[title] 共用页面
[text] 你来到了训练场。
```

玩家输入 `.st goto 2a/2b/2c` 皆会抵达页面 `2`，但各自套用不同的加成。

#### 独立条件显示（ifs）

```
[label] 11
[title] 属性揭示
[text|ifs=Wit==1] 你感到有点迟钝。
[text|ifs=Wit>=8] 你灵光一闪，找到了捷径。
[text] 无论如何，你继续前进。
```

使用 `ifs` 的 `[text]` 不会与相邻的 `if/else` 形成条件链，命中就显示，可同时出现多行。

#### 结局区块的条件链

```
[label] 99
[title] 结局
[ending]
[text] 旅程告一段落。
[text|if=Power>=8] 你以力量压倒众人，创建了威名。
[text|if=Agility>=8] 你以身法穿梭暗影，无迹可寻。
[text|else] 你学到了宝贵的一课，准备再出发。
[choice]
-> 重新开始 | 0
-> 结束 | END
```

结局的多行 `[text|if=...]` 与一行 `[text|else]` 形成条件链，仅显示第一个符合条件者；可在其上方书写无条件前言文本。

#### 占位符的优先级与嵌套

```
[label] 12
[title] 占位符
[set] title="勇者"
[set] who="{owner_name}"
[text] {who} 称呼你为「{title}」。
```

`{key}` 查找顺序为 `playerVariables` → `stats` → `variables`。字符串值内若再包含 `{...}`，会进行一次嵌套展开。
