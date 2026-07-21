---
description: Sometimes roll results should be hidden or sent only to specific people. This page shows how.
---

# Secret Rolls

### DR — DM roll result to yourself

Prefix the command with `dr` to receive the result in a private message.

Examples: `dr 3d6`, `dr cc 80`

![](<../../.gitbook/assets/image (19) (1).png>)

### DDR / DDDR — DM result to specific people

Send roll results privately to the GM or chosen recipients.

`ddr` — DM the result to registered group GMs and yourself.

`dddr` — DM only registered group GMs.

#### Register as GM

Type `.drgm addgm` yourself.

Others can then use `ddr` or `dddr` with a command to DM that GM.

Example: `ddr cc 80 鬥毆` — DMs the GM and you.

Example: `dddr cc 80 鬥毆` — DMs only the GM.

#### Alias

To use a display alias: `.drgm addgm (alias)`

Output uses the alias instead of your name.

#### Command Reference

* `.drgm show` — list all GMs
* `.drgm del(number)` or `all` — remove GM(s)
* `dr (command)` — DM yourself
* `ddr (command)` — DM GMs and yourself
* `dddr (command)` — DM GMs only
