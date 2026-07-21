---
description: 这里介绍如何使用HKTRPG进行COC掷骰
---

# CoC克苏鲁神话

`cc` `cc(n)1~2` `ccb` `ccrt` `ccsu` `.dp` `.cc7build` `.cc6build` `.cc7bg` `.sc` `.chase`

{% hint style="info" %}
[CoC7ed规则书介绍](https://www.patreon.com/posts/67705000)
{% endhint %}

### 掷骰检定

* CoC6版掷骰： `ccb 80` 技能小于等于80
* CoC7版掷骰： `cc 80` 技能小于等于80\
  ![](<../../.gitbook/assets/image (43).png>)
* CoC7版奖励骰： cc(1\~2) `cc1 80` 一粒奖励骰
* CoC7版惩罚骰： ccn(1\~2) `ccn2 80` 两粒惩罚骰
* CoC7版联合检定：cc (x,y) (z,a) `cc 80,60 斗殴,魅惑` \
  支持奖励惩罚骰，如：`cc１ 80,60 斗殴,魅惑`
* CoC7版SanCheck ： `.sc (SAN值) (成功)/(失败)`\
  ![](<../../.gitbook/assets/image (28).png>)
*   CoC7 手动成长或增长检定

    ![](<../../.gitbook/assets/image (32).png>)\
    可以一次输入多个技能<br>

    `.dp` 或 `成长检定` 或 `幕间成长 (技能%) (名称)` \
    `.DP 50 骑乘 60 斗殴 50 60` \
    `.DP 50 60 50` \
    `成长检定 65 头槌 45 剑术`  \
    `幕间成长 40 单车`

### COC数据

`coc7版 神话组织 随机产生： 启动语 .cccc` \
`coc7版 神话数据 随机产生： 启动语 .ccdr` \
`coc7版 施法推骰后果： 启动语 .ccpc`\
![](<../../.gitbook/assets/image (7).png>)

![](<../../.gitbook/assets/image (9).png>)

### 疯狂结果

* coc7版 即时型疯狂： 启动语 `ccrt`
* coc7版 总结型疯狂： 启动语 `ccsu`

### `创造角色`

* coc6版创角： 启动语 `.cc6build`
* coc7版创角： 启动语 `.cc7build (岁数7-79)`
* coc7版随机创角 ： 启动语 `.cc7build random`
* coc7版自由分配点数创角 ： 启动语 `.cc7build .xyz (岁数7-89)`

如`.cc7build .752` \
就会掷出\
`7次 3d6 * 5`\
`5次 (2d6+6) * 5` \
`2次 3d6 * 5`

可只输入`.`  不输入xyz\
默认值为 .53 即`5次 3d6 * 5` 和`3次 (2d6+6) * 5`&#x20;

![](<../../.gitbook/assets/image (45).png>)

* coc pulp版创角 ： 启动语 `.ccpulpbuild`
* coc7版角色背景随机生成： 启动语 `.cc7bg`

### 成长检定纪录功能

![](<../../.gitbook/assets/image (34) (1).png>)

开启后将会纪录你使用CC功能投掷成功和大成功大失败的技能， 然后可以调用出来进行自动成长。

* `.dp start` ： 开启纪录功能
* `.dp stop` ： 停止纪录功能
* `.dp show` ： 显示掷骰纪录
* `.dp auto` ： 进行自动成长并清除掷骰纪录
* `.dp clear` ： 清除掷骰纪录
* `.dp clearall` ： 清除掷骰纪录包括大成功大失败

### coc7版追逐战产生器:&#x20;

指令 `.chase`&#x20;

{% hint style="info" %}
追逐战功能使用了可选规则及我对规则书之独断理解， 并不一定完全符合规则书内容，请自行衡量使用，建议使用前详细阅读规则书第七章追逐
{% endhint %}

![](<../../.gitbook/assets/image (40).png>)

