# Discord Channel Chat Log Export

![](<../.gitbook/assets/image (51).png>)

`.discord html` exports a chat log with analysis features (temporarily unavailable)

`.discord txt` exports a plain-text chat log

`.discord txt -withouttime` exports a text file without timestamps. This is useful if you want to turn session logs into novel material without manually removing timestamps.

Both you and the bot need permission to read channel message history. The log will be sent to you via DM.

#### **Note**

You need permission to manage the channel or administrator permissions to use this feature.\
The HTML version is AES-encrypted; the TXT version is a plain file. Because processing happens on the server, do not use this if you are concerned about personal data leakage.
