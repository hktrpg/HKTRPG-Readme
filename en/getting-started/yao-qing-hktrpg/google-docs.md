---
description: How to roll dice in Google Docs
---

# Google Docs

![Usage demo](<../../.gitbook/assets/google docs rolling.gif>)

## Setup

Open the document where you want to roll, go to Tools → Scripts Editor,\
replace the code at the bottom with the script below, then select `init`.

## Usage

There are two ways to run it:

1. Click Run to start the script directly.
2. Click the clock icon (Triggers) on the left, then Add Trigger at the bottom right, choose `init`,\
   and click Save. After that, rolls run automatically whenever you reopen the Doc.

## Code

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
