---
description: 这里介绍怎样在Google Docs 上进行掷骰
---

# Google Docs

![使用示范](<../../.gitbook/assets/google docs rolling.gif>)

## 准备方法

打开你需要掷骰的文档，在Tools -> Scripts Editor 中，\
把最下面代码取代进去。选择init

## 使用方法

有两种方式

1. 直接按Run，直接启动程序。
2. 按画面左边时钟符号Triggers，再按右下角Add Trigger，选择init，\
   然后按Save。以后每次重启Docs 画面时，就会自动掷骰。

## 代码

```
async function init() {
  do {
    var next = await replaceHKTRPG_Text();
  } while (next);

}

async function replaceHKTRPG_Text() {
  let body = DocumentApp.getActiveDocument().getBody();
  let target = body.findText("^(?im)/hk\\s+(.*)");
  if (!target) return;
  let text = target.getElement().asText().getText();
  let result = await HKTRPG_Api(text.replace(/\/hk\s+/i, ''))
  target.getElement().asText().setText('HKTRPG\n' + result.message);
  return true;
}


async function HKTRPG_Api(query = 'cc 80') {
  if (!query) return;
  var url = 'https://api.hktrpg.com/'
    + '?msg=' + encodeURIComponent(query);
  var response = UrlFetchApp.fetch(url, { 'muteHttpExceptions': true });
  var json = response.getContentText();
  var data = JSON.parse(json);
  return data;
}


```
