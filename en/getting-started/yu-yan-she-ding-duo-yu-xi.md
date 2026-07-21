---
description: HKTRPG lets you set the bot's reply language per group/server or per DM.
---

# Language Settings (Multilingual)

The default language is **Traditional Chinese (zh-tw)**.

{% hint style="info" %}
**Tip:** Changing the language only affects the bot's **reply text**. Roll command prefixes stay the same—`.cc`, `bothelp`, `/lang`, `.in`, and so on are unchanged.
{% endhint %}

### Supported Languages

| Code      | Language                      |
| --------- | ----------------------------- |
| `zh-tw`   | Traditional Chinese (default) |
| `zh-hans` | Simplified Chinese            |
| `en`      | English                       |

{% hint style="warning" %}
Use `zh-hans` for Simplified Chinese. **Do not** use `cn` or `zh-cn` (not supported).
{% endhint %}

### Command Reference

| Command                | Description                          |
| ---------------------- | ------------------------------------ |
| `.lang` or `.lang show` | Show the current language            |
| `.lang list`           | List supported languages             |
| `.lang help`           | Show help                            |
| `.lang zh-tw`          | Set to Traditional Chinese           |
| `.lang zh-hans`        | Set to Simplified Chinese            |
| `.lang en`             | Set to English                       |
| `/lang`                | Discord Slash version (same features) |

### Two Setting Scopes

Language settings come in two scopes that do not interfere with each other:

#### 1. Server / Group

* **Who can set it:** Requires **administrator** permissions in that group
* **Scope:** Bot replies everyone sees in this server/group
* **Does not affect:** Other servers, other groups, or anyone's DMs

Example (in a Discord server or group channel):

```
.lang en
.lang zh-hans
.lang zh-tw
```

Or use Slash:

```
/lang
```

#### 2. Direct Messages (DM)

* **Who can set it:** Anyone
* **Scope:** Replies in **your** DMs with HKTRPG only
* **Does not affect:** Reply language in any server/group

Example (DM HKTRPG directly):

```
.lang en
.lang zh-hans
.lang zh-tw
```

{% hint style="success" %}
Want Traditional Chinese in the group but English when you DM the bot for lookups? Set the group to `zh-tw` and your DM to `.lang en`.
{% endhint %}

### Step-by-Step Usage

#### Switch an entire Discord server to English

1. Confirm you have administrator permissions on that server
2. Enter in any channel:

```
.lang en
```

3. After that, help text, error messages, and most feature replies in this server will be in English
4. To switch back to Traditional Chinese:

```
.lang zh-tw
```

#### Change only your DM language

1. Open a DM with HKTRPG
2. Enter:

```
.lang zh-hans
```

3. Only your DMs will use Simplified Chinese; group language stays unchanged

#### Check the current language

```
.lang show
```

Or:

```
.lang
```

### FAQ

#### Q: I changed my DM language—why is the group still in Traditional Chinese?

That is expected. DM language and group language are stored separately.

#### Q: I entered `.lang en` in a group and got a permission error—why?

Group/server language requires **administrator** permissions. Regular members can only set their own language in **DMs**.

#### Q: Will the Discord client UI language change too?

No. `.lang` controls the language of **HKTRPG reply content**.\
The Discord client UI and Slash command name localization still follow Discord's own language settings.

#### Q: Will commands change to English versions (e.g. `.cc` becoming something else)?

No. Command prefixes and dice-system commands stay the same; only reply text changes.

#### Q: Does this work on Line / Telegram / WhatsApp?

Yes. Use `.lang` in the corresponding platform's group or DM (groups still require admin permissions to change group language).

#### Q: The setting doesn't seem to take effect?

Language settings require a database connection to persist. If the system cannot connect to the database temporarily, it will report that it cannot save; try again later.

### Quick Reference

| What you want to do              | Where to enter | Command         |
| -------------------------------- | -------------- | --------------- |
| English for the whole server     | Server channel | `.lang en`      |
| Simplified Chinese for the server | Server channel | `.lang zh-hans` |
| Restore Traditional Chinese on server | Server channel | `.lang zh-tw`   |
| English for my DMs only          | DM             | `.lang en`      |
| View current language            | Anywhere       | `.lang show`    |
| View supported list              | Anywhere       | `.lang list`    |

{% hint style="info" %}
You can also enter `.lang help` or `/lang` in chat for command help.
{% endhint %}
