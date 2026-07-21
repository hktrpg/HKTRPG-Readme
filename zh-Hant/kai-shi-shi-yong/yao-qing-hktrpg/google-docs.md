---
description: 這裡介紹怎樣在Google Docs 上進行擲骰
---

# Google Docs

![使用示範](<../../.gitbook/assets/google docs rolling.gif>)

## 準備方法

打開你需要擲骰的文件，在Tools -> Scripts Editor 中，\
把最下面代碼取代進去。選擇init

## 使用方法

有兩種方式

1. 直接按Run，直接啓動程式。
2. 按畫面左邊時鐘符號Triggers，再按右下角Add Trigger，選擇init，\
   然後按Save。以後每次重啓Docs 畫面時，就會自動擲骰。

## 代碼

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
