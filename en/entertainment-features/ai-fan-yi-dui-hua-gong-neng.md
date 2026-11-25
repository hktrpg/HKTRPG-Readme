---
description: Welcome to the AI assistant service. This feature integrates multiple large language models for AI chat and translation.
---

# AI Chat & Translation

### 🗣️ Conversation

You can chat with the AI by typing a command or **Reply**ing to a message.

| **Command** | **Audience** | **Model / Notes**                                                                                                                                                       |
| ---------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `.ai [message]` | All users     | <p>Default command</p><p><br></p><p>Randomly rotates among:</p><p><br></p><p>• Aurora Alpha</p><p><br></p><p>• Z.ai: GLM 4.5 Air</p><p><br></p><p>• Arcee AI: Trinity Large Preview</p> |

> 💡 Tip: You can also **Reply** to the message you want to discuss; the AI will read that context.

***

### 📝 Translation

The system specializes in converting text and files to **Traditional Chinese**.

| **Command**      | **Audience** | **Model / Notes**                                        |
| ----------- | -------- | -------------------------------------------------- |
| `.ait [content]` | All users     | <p>Default translation</p><p><br></p><p>Uses Aurora Alpha.</p> |

#### 📂 Supported File Formats and Limits

Upload a file with the translation command.

* Formats: `.txt`, `.pdf`, `.docx`, `.jpg`, `.png`, `.gif`
* Size limits:
  * PDF: `50MB`
  * DOCX: `25MB`
  * Images (OCR): `20MB`
  * TXT: `10MB`

***

### ⚠️ Limits and Permissions

| **User Tier** | **Text Limit** | **Model Access**            |
| -------- | -------- | ------------------- |
| Regular users     | 2,500 characters  | Basic models only (LOW Models) |
| VIP users   | Higher limit     | Mid-tier models unlocked              |

***

### 📌 Important Notes

Processing time

* Long translations: Content over 10,000 characters may take **more than 10 minutes**.
* Files: PDF/DOCX or image OCR take longer—please wait patiently.

System behavior

* Long replies: If the AI response exceeds 1,900 characters, it is sent as a `.txt` file.
