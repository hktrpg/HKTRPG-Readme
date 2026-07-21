# Discord Version Notes

### Why Slash Commands (/) Were Introduced

On August 31, Discord changed its [bot usage policy](https://support.discord.com/hc/en-us/articles/360040720412). Unless a bot has special approval, it may not read chat messages directly.\
That means typing `1D100` freely in chat will be phased out; bots in servers must be used via slash commands (/).

### Differences Between Slash Commands (/) and Regular Commands

Slash commands must start with **/** and follow specific input rules. They may include buttons or options for easier selection.\
To ease the transition, conversion follows these rules:

1. Commands without a prefix get a slash (/)
2. Commands with a leading period (.) become slash commands (/)
3. If commands conflict, more important features keep their names under the rules above; less important ones are renamed.
   1. Renaming principles
      1. Lengthen the name, e.g. `.me` becomes `/mee`
      2. Change to a different name

### Why My Server Added HKTRPG but Has No Slash Commands (/)

Usually this is because an old invite link was used. Click HKTRPG -> Profile -> Add to Server\
and add it to your server again. **You do not need to remove it first**—just add it again.\
Or use the [Discord invite link](https://discord.hktrpg.com).

<img src="../.gitbook/assets/image (21).png" alt="" data-size="original">

### Why Slash Commands (/) Are Not Fully Rolled Out Yet

Because ~~I’m lazy~~ there really are a lot of them—over a hundred commands in total.
