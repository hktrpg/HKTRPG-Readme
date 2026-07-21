---
description: >-
  StoryTeller is an interactive story system that lets users add their own scripts, manage them, and play
  text adventures by others. It supports Discord, Line, Telegram, and WhatsApp, with rich features for
  immersive interactive experiences. Use it for choose-your-own-adventure games, quizzes, and more.
---

# StoryTeller Interactive Story System

{% hint style="info" %}
## This feature exists because of the choose-your-own-adventure books I played as a kid—they read like novels, yet let you decide what to do. I never forgot them and always hoped to play that kind of game again someday.
{% endhint %}

## Quick Start

#### Basic Commands

```bash
# Start a script
.st start <alias|title> [alone|all|poll
 x]  
 
 # List playable scripts
.st list     

# Game control
.st pause                                   # Pause the current script
.st continue [runId]                        # Resume a paused script
.st end                                     # End the current script
```

#### During Play

```bash
.st goto <page>                             # Jump to a page/option
.st set <var> <value>                       # Set a variable
```

### Detailed Features

#### 1. Script Management

**Add and Update Scripts**

**Discord-only:**

```bash
# Upload and download as attachments
.st import <alias> [title]                  # Upload a file to add a script
.st update <alias> [title]                  # Upload a file to overwrite an existing script
.st export <alias>                      # Send the script as a text file via DM
```

**Supported Formats:**

* `.json` — Full StoryTeller format
* `.txt` — RUN\_DESIGN syntax format

**Script Management Commands**

```bash
.st my [alias]                              # View stats for scripts you added
.st mylist                                  # List all scripts you added
.st list <alias>                            # Show that script’s summary and info
.st delete <alias>                          # Delete a script you own
.st verify <alias>                          # Check whether the script format is valid
```

#### 2. Permission Management

```bash
.st allow <alias> AUTHOR                    # Only the author can start anywhere (default)
.st allow <alias>                           # Allow starting in this group/channel
.st allow <alias> <groupId...>              # Allow specific groups/channels (multiple)
.st allow <alias> all                       # Anyone can start (public)
```

#### 3. Game Settings

```bash
.st edit alone|all|poll x                   # Host can switch participation mode
```

**Participation Options:**

* `alone` — Only the host can interact
* `all` — Anyone can participate
* `poll x` — Enable Discord poll for x minutes (default 3; Discord only)

#### 4. Status View

```bash
.st game                                    # Show running and paused games
.st debug                                   # Show detailed debug info
```

### RUN\_DESIGN Syntax

StoryTeller supports RUN\_DESIGN—a concise text format for interactive stories.

#### Basic Structure

```txt
[meta] title "Story Title"
[intro] Story introduction

[player_var] name "Enter character name" "Example: Alex"
[stat_def] hp 1 20 "HP"
[var_def] gold 0 1000 "Gold"

[label] 0
[title] Start Page
[text] Welcome to this world!
[text|if=hp>10] Your HP looks good.
[set] gold=100
[random] 50%
[text] You found some treasure!

[choice]
-> Continue | 1
-> Rest | 2 | if=hp<5
-> End game | END

[label] 1
[title] Page Two
[text] You press on...
[ending]
[text] Congratulations—you finished the story!
```

#### Syntax Elements

**Metadata**

* `[meta] title "Title"` — Set the story title

**Introduction**

* `[intro] content` — Set the story introduction

**Player Variables**

* `[player_var] key "prompt" "default"` — Define variables the player must set

**Stat Definitions**

* `[stat_def] key min max "label"` — Define game stats (HP, attack, etc.)

**Variable Definitions**

* `[var_def] key min max "label"` — Define game variables

**Page Structure**

* `[label] id` — Define page ID
* `[title] title` — Set page title
* `[text] content` — Display text
* `[text|if=condition] content` — Conditional text
* `[text|speaker=character] content` — Specify speaker

**Variable Operations**

* `[set] key=value` — Set a variable
* `[set|if=condition] key=value` — Conditional set

**Random Events**

* `[random] percent%` — Set trigger probability

**Choices**

* `[choice]` — Start defining choices
* `-> choice text | target page | if=condition | stat=stat changes`

**Endings**

* `[ending]` — Mark an ending page

### Variable System

#### Variable Types

1. **Player Variables** (`playerVariables`)
   * Character info set by the player
   * e.g. name, class
2. **Stats** (`stats`)
   * Numeric attributes in the game
   * e.g. HP, attack, defense
3. **Game Variables** (`variables`)
   * State during the story
   * e.g. gold, quest progress

#### Variable Operations

```bash
.st set name 小花          # Set character name
.st set hp 12             # Set HP
.st set gold 500          # Set gold
```

#### Conditional Expressions

Supports many condition forms:

```txt
[text|if=hp>10] Your HP is high
[text|if=gold>=100] You have enough gold
[text|if=name=="Alex"] Hello, Alex!
[text|if=hp>5 && gold>50] You're in good shape
```

#### Dice System

Supports dice expressions:

```txt
[text] You rolled {2d6} damage
[text] Your attack is {1d20+5}
```

### Platform-Specific Features

#### Discord Only

1.  **Poll System**

    ```bash
    .st start story poll 5    # Enable 5-minute poll
    .st edit poll 3          # Switch to 3-minute poll
    ```
2. **File Upload**
   * Drag-and-drop `.json` or `.txt`
   * Automatic parse and validation
3. **DM**
   * Scripts can be sent to users via DM

#### Cross-Platform Compatibility

* **Line/Telegram/WhatsApp**: Basic features; no polls or file upload
* **Discord**: All features including polls and file upload

### Limits and Rules

#### File Size Limits

* Max upload: 1MB
* Max pages: 400
* Max text per segment: 500 characters

#### User Limits

Limits vary by VIP tier:

| VIP Tier | Script Limit | Concurrent Games |
| ------ | ------ | ------- |
| 0      | 3      | 3       |
| 1      | 10     | 10      |
| 2+     | 100    | 100     |

#### Permission System

1. **AUTHOR\_ONLY**: Only author can start
2. **GROUP\_ONLY**: Only specified groups can start
3. **ANYONE**: Anyone can start

### Best Practices

#### Creating Scripts

1. **Plan Structure**
   * Design main plot and branches first
   * Decide number and variety of endings
2. **Variable Design**
   * Set sensible stat ranges
   * Provide meaningful player variables
3. **Test and Validate**
   * Use `.st verify` to check format
   * Test all branches and endings

#### Running Games

1. **Character Setup**
   * Encourage rich character info
   * Personalize content from character data
2. **Progress Management**
   * Use pause when needed
   * Record important game state
3. **Community**
   * Use Discord polls for engagement
   * Encourage players to share experiences

### Troubleshooting

#### Common Issues

1. **Script Not Found**
   * Check alias spelling
   * Confirm permission settings
2. **Cannot Start Game**
   * Check concurrent game limit
   * Confirm script format
3. **Variable Set Failed**
   * Check variable name
   * Confirm value is in range

#### Debug Tools

```bash
.st debug    # Show detailed game state
```

### Example Script

#### Simple Adventure

```txt
[meta] title "Forest Adventure"
[intro] You are a brave adventurer exploring a mysterious forest.

[player_var] name "Enter your character name" "Example: Arthur"
[stat_def] hp 10 20 "HP"
[stat_def] strength 1 10 "Strength"

[label] 0
[title] Forest Entrance
[text] Welcome, {name}! You reach the entrance of the mysterious forest.
[text] Your HP: {hp}, Strength: {strength}
[choice]
-> Enter the forest | 1
-> Rest first | 2 | if=hp<15
-> Leave | END

[label] 1
[title] Deep Forest
[text] You go deeper and find an ancient ruin.
[random] 30%
[text] Suddenly, a beast appears!
[set] hp=hp-5
[choice]
-> Fight | 3 | if=strength>5
-> Flee | 4
-> Surrender | END

[label] 2
[title] Rest
[text] You rest and recover some stamina.
[set] hp=hp+5
[choice]
-> Enter the forest now | 1
-> Rest more | 2

[label] 3
[title] Victory
[text] You bravely defeat the beast!
[set] strength=strength+1
[ending]
[text] Congratulations—you completed the adventure!

[label] 4
[title] Escape
[text] You flee safely but miss the treasure.
[ending]
[text] You leave the forest safely but gain no reward.
```

This example shows basic StoryTeller features: variables, conditions, random events, and multiple endings.

### Changelog

#### Recent Features

* RUN\_DESIGN syntax support
* Discord poll system
* Cross-platform pause/continue
* Enhanced character stats
* Improved permission management

#### Known Limitations

* Polls: Discord only
* File upload: Discord only
* Some advanced features require VIP tier

***

StoryTeller is actively updated—watch for new features and improvements.
