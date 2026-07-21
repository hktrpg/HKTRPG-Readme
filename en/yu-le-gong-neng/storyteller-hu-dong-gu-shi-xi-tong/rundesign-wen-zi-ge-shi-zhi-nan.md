---
description: This guide describes a concise, hand-editable interactive story text format (RUN_DESIGN).
---

# RUN\_DESIGN Text Format Guide

## RUN\_DESIGN Text Format Guide

This guide describes a concise, hand-editable interactive story text format (RUN\_DESIGN). It supports reversible conversion: JSON → RUN\_DESIGN → JSON with no semantic loss within supported fields.

### Goals

* Simple, readable text format suited to version control
* Compiles into a JSON story structure
* Exports JSON back to text without semantic differences

### File Encoding

* UTF-8

### Whitespace & Comments

* Blank lines are allowed.
* Lines starting with `//` are single-line comments and are ignored at compile time. Put them on their own line.

### Top-Level Metadata

* `[meta] title "<Title>"` — Set story title
* `[meta] author "<Author>"` — Set author (required; import/update rejected if missing)
* `[intro] <text>` — Append one line of introduction (repeatable). Shown when the script starts.

Display behavior:

* In `.st list`:
  * With a specific alias, shows the full introduction (if any).
  * When listing all playable scripts, shows a preview of the first intro line (max 80 characters) under each title.
* In `.st mylist`:
  * Each script shows a preview of the first intro line (max 80 characters).
* After starting a game, before player variables are set:
  * A 【Introduction】 block with the full intro is shown before character setup prompts.

Example:

```
[meta] title "A Cat's Day"
[intro] Welcome to the interactive story!
```

### Player Variables

* `[player_var] <key> "<prompt>" ["<placeholder>"]`
  * key: identifier, e.g. `cat_name`
  * prompt: question shown to the player
  * placeholder: optional hint text

Example:

```
[player_var] cat_name "1. Enter your cat's name:" "e.g. Orange, Mochi, Blackie"
[player_var] owner_name "2. Enter the owner's name:" "Alex, Emily, Jay"
```

### Game Stats

* `[stat_def] <key> <min> <max> ["<label>"]`
* Initialization: if not explicitly set, a random integer from `min` to `max` is chosen at first start.
* Lock: once set by `[set]` in content, random initialization no longer overwrites that stat.

Example:

```
[stat_def] Cuteness 1 10 "Cuteness"
[stat_def] Energy 1 10 "Energy"
[stat_def] Mischief 1 10 "Mischief"
```

### Variables

* `[var_def] <key> <min> <max> ["<label>"]`

Example:

```
[var_def] rain 0 1 "Raining"
```

### Pages

A story is made of multiple pages.

* Define page label (ID): `[label] <id>`
  * **Limit**: Page IDs must be numeric only (e.g. `0`, `1`, `2`, `10`)
  * **Starting page**: `[label] 0` is the entry page, loaded automatically at game start
  * Other pages may use any numeric ID; consecutive numbers improve readability
* Optional page title: `[title] <text>`
* Page content (unlimited lines):
  * `[text] <content>`
  * `[text|if=<expr>] <content>` — Conditional display
  * `[text|else] <content>` — Forms a chain with preceding `[text|if=...]` lines; only the first match shows; if none match, `else` shows. Also works in ending blocks.
  * `[text|ifs=<expr>] <content>` — Independent conditional display: shows whenever true; does not chain with nearby `[text|if=...]` / `[text|else]`.
  * `[text|speaker=<key>] <content>` — Specify speaker
  * `[text|speaker=<key>,if=<expr>] <content>` — Speaker with condition
  * `[random] <percent>%` — Affects only the **next** `[text]` line (e.g. 30%); `percent` is an integer 0–100.
  * `[set] <key>=<expr>` — Sets value at render time: if `key` is a defined `stat_def`, writes to `stats`; otherwise to `variables`. `<expr>` supports basic expressions (see below).
    * Once a stat is set by `[set]`, random initialization no longer overwrites it.
  * Inline dice in text: `{xDy}` rolls at display time and is replaced by the total, e.g. `{1D100}`, `{2d20}`, `{3d6}`.
* Ending marker:
  * `[text]` lines after `[ending]` are ending text; the first matching condition is used
  * Supports condition chains: multiple `[text|if=...]` followed by one `[text|else]` fallback
  * Requirement: a valid RUN\_DESIGN must include at least one page with `[ending]`; upload/update is rejected without an ending.
* Choice block:
  * `[choice]` — Start defining choices
  * `-> <text> | <page id> [| if=<expr>] [| stat=a+1,b-2]`
    * `<page id>` must be numeric, or a letter-suffixed variant (e.g. `2a`, `2b`, `2c`); or special value `END`.
    * **Feature**: `2a`, `2b`, `2c` etc.—the number (e.g. `2`) is the actual target page; the letter (e.g. `a`, `b`, `c`) distinguishes bonus or description variants (all jump to `2`).
    * When `<page id>` is `END`, the UI offers a “`.st end`” button to finish the game.
    * `stat=` supports integer add/subtract only, applied when successfully moving to that choice’s target (e.g. `Cuteness+1,Energy-2`).

#### Feature: Multiple Choices to the Same Page

Using `2a`, `2b`, `2c` lets several choices jump to the same page (e.g. page `2`) with different bonuses:

```
[choice]
-> Ready to cause chaos! | 2a | stat=Mischief+1
-> Stretch and see how I feel today. | 2b | stat=Cuteness+1
-> Full energy today! | 2c | stat=Energy+1
```

When the player uses `.st goto 2a`, `.st goto 2b`, or `.st goto 2c`:

* All jump to page `2`
* But apply different bonuses: Mischief+1, Cuteness+1, Energy+1

#### Expressions

* Conditions use a small JS-like subset evaluated in scope (`variables` + `stats` + `playerVariables`)
* Operators: `&& || ! < <= > >= == === != !== + - * / % ()`
* Safety: no function calls; no access to `globalThis`, `global`, `process`, `this`, `Function`, `constructor`, `require`, etc.
  * Example: `if=Cuteness>=8 && Energy>3`
* Unary negation `!expr` is supported (use parentheses for precedence).
  * Example: `if=(Strength>5) && !(Agility>5)`

**Dice**

* In conditions and assignments, use `xDy` literals; they roll before evaluation and are replaced by the total, e.g.:
  * `if=2d20>25`
  * `[set] luck=3d6+2`
  * Allowed range: `x` 1–100, `y` 1–10000; out-of-range values are clamped.

**Conditional Set**

* `[set]` supports conditions: `[set|if=<expr>] key=<expr>`.
* Combined with dice, this supports common check flows.

Example:

```
[stat_def] san 0 100 "SAN"
[set] san=70

[label] SAN_CHECK
[set] sancheck=1d100
[text] sancheck={sancheck}
[set|if=san<sancheck] san=san-1
[text|if=san<sancheck] You lose 1 SAN
[text|if=san>=sancheck] You keep your composure
```

#### Example Page

```
[label] 0
[title] Character Creation
[text] Setup complete! Let's see how {cat_name} is doing today...
[text] (The system randomly generates values from 1–10)
[text] - Cuteness: {Cuteness}
[text] - Energy: {Energy}
[text] - Mischief: {Mischief}
[text|ifs=Wit==1] Exact stat -> Wit: 1
[text|ifs=Wit==2] Exact stat -> Wit: 2
[text|ifs=Wit==3] Exact stat -> Wit: 3
[text|ifs=Wit==4] Exact stat -> Wit: 4
[text|if=Cuteness>Mischief+2] They smile, pick it up, and say, "You little troublemaker." Then they hug and kiss me. My prank worked!
[text|if=Cuteness<=Mischief+2 && Cuteness > 4] They sigh and say, "{cat_name}, you can't do that." But they still pet my head. Forgiven this time.
[text|if=Cuteness<=4] They look a bit angry, scold me while holding me—no treats today.
[text|if=Cleverness>=10] They notice my clever eyes and laugh, "Planning something?" and give me an extra reward.
[text|else] They just shake their head and tidy up. An ordinary day.
[choice]
-> Ready? | 1
```

#### Ending Page

```
[label] 22
[title] Ending
[ending]
[text|if=Cuteness>8] Forgiven by being cute
[text|else] Gentle resignation
[choice]
-> Back to start | 0
-> End game | END
```

### Placeholders

* In `[text]`, `{key}` is resolved from `playerVariables`, then `stats`, then `variables` (later sources can override earlier).
* If no key is found, the placeholder is left as-is (e.g. `{unknown_key}` outputs literally).

#### Compatibility Notes

* Plain-string page IDs are not supported; use numeric IDs (e.g. `0`, `1`, `2`).
* `[set]` lines may have trailing `//` comments after the value; import ignores them without affecting the assignment.

### Round Trip

* Import text (Discord attachment): send `.st import <alias> [title]` with a `.txt` (RUN\_DESIGN) or `.json` file
* Update existing script: `.st update <alias> [title]` with a new file
* Export text: `.st exportfile <alias>` (bot sends the text file via DM)
* Verify reversibility: `.st verify <alias>`

#### Normalization

* The compiler treats adjacent `[random]` and the following first `[text]` as “probability display.”
* On export, if a page is an ending page, `[ending]` follows `[label]` on that page to preserve reversibility.

### Conventions

* **Starting page**: `[label] 0` is loaded at game start. You may adjust in compiled JSON if needed.
* **Page ID limit**: numeric IDs only.
* Speakers are optional; examples use plain text.
* For randomness in body text, place `[random] <percent>%` immediately before the `[text]` it should affect (`percent` is an integer).
* To change stats on a choice, use `stat=a+1,b-2` (integer add/subtract only).
* For multiple choices to one page with different bonuses, use `2a`, `2b`, `2c`.

### Best Practices

* Use numeric, preferably consecutive IDs for readability
* Keep conditions simple and based on defined keys
* Avoid very long lines; split into multiple `[text]` lines
* Ensure each ending page offers restart or end options
* Use `2a`, `2b`, `2c` for choices with different bonuses to the same page

### Limits

* Max pages: 400
* Max length per `[text]` line (including ending text): 500 characters
* At least one page with `[ending]` is required
* Max attachment size on import/update: about 1 MB
* Page IDs must be numeric

### More Examples

#### Speakers and Condition Chains

```
[label] 5
[title] Dialogue Example
[text|speaker=cat] Meow—what should we do today?
[text|if=Energy>=8] I feel full of energy!
[text|if=Energy>=5 && Energy<8] Not bad—I can move around.
[text|else] Kind of sleepy...
[choice]
-> Go patrol | 6
-> Nap first | 7
```

Speakers are optional; at render time they are stored as metadata and do not change text output.

#### Random Display

```
[label] 6
[title] Random Event
[random] 30%
[text] You accidentally find a catnip stick!
[text] Whether or not you found it, you move on.
```

`[random] <percent>%` applies only to the next `[text]` line; the compiler preserves reversibility on export.

#### Inline Dice and Conditional Checks

```
[label] 8
[title] Dice Check
[set] roll=1d20
[text] Your check result: {roll}
[text|if=roll+Energy>=18] Critical success!
[text|else] Normal success or failure.
```

Use `xDy` in expressions; use `{xDy}` in text for inline rolls showing the total.

#### Conditional Set and String Values

```
[label] 9
[title] Status Flag
[set|if=Energy>=8] mood="energetic"
[set|if=Energy<8] mood="lazy"
[text] Current mood: {mood}
```

Quoted RHS values are string constants; otherwise the RHS is evaluated as an expression.

#### Multiple Choices to Same Page (With Bonuses)

```
[label] 10
[title] Opening Choice
[choice]
-> Strength path | 2a | stat=Power+1
-> Agility path | 2b | stat=Agility+1
-> Wit path | 2c | stat=Wit+1

[label] 2
[title] Shared Page
[text] You arrive at the training ground.
```

`.st goto 2a/2b/2c` all reach page `2` with different bonuses.

#### Independent Conditional Display (ifs)

```
[label] 11
[title] Stat Reveal
[text|ifs=Wit==1] You feel a bit slow.
[text|ifs=Wit>=8] Inspiration strikes—you find a shortcut.
[text] Either way, you continue.
```

`[text|ifs=...]` does not chain with adjacent `if/else`; each matching line can appear; multiple lines may show at once.

#### Ending Block Condition Chain

```
[label] 99
[title] Ending
[ending]
[text] The journey pauses here.
[text|if=Power>=8] You overpower everyone and build a reputation.
[text|if=Agility>=8] You slip through shadows unseen.
[text|else] You learned a valuable lesson and prepare to set out again.
[choice]
-> Restart | 0
-> End | END
```

Multiple `[text|if=...]` plus one `[text|else]` in an ending form a chain; only the first match shows; unconditional lines may appear above as preamble.

#### Placeholder Priority and Nesting

```
[label] 12
[title] Placeholders
[set] title="Hero"
[set] who="{owner_name}"
[text] {who} calls you "{title}".
```

`{key}` lookup order: `playerVariables` → `stats` → `variables`. If a string value contains `{...}`, one level of nested expansion is performed.
