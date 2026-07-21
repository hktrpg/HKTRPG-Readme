---
description: Pull reference text instantly during play.
---

# Database



`.db (add del show custom_keyword)`

* Keyword lookup database — type a keyword to show stored text.
* Example: `.db add 九大陣營 九大陣營包括守序善良 (...省略) 中立邪惡 混亂邪惡`
* Then `.db 九大陣營` outputs the full stored text.
* After `add`, the first token is the trigger keyword — Chinese, numbers, English, or emoji.



* `.db add (keyword) (content)` — add an entry
* `.db show` — list all keywords
* `.db del(number)` — delete by index
* `.db (keyword)` — show content
* Examples\
  `.db add COC COC是其中一系很受歡迎的TRPG系統，最新版本是7th`\
  `.db del 0` — delete the first keyword



### Two Modes

* `.db` — group version, shared in the server
* `.dbp` — public version, visible across HKTRPG
