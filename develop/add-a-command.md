---
description: Add a command to your plugin
---

# Add A Command

All commands must be placed inside of the `/commands` folder inside of your plugin. If it is not, bots with your plugin install will not load your command.

{% hint style="info" %}
Plugins are built on top of [<mark style="color:red;">discord.js</mark>](https://discord.js.org/), so many functions you are used to, can be used within blitz!
{% endhint %}



## Basic Ping Command

Create a new file called `ping.ts` inside of your commands folder.

```typescript
import { SlashCommandBuilder } from "npm:discord.js";

export default {
  data: new SlashCommandBuilder()
    .setName("ping")
    .setDescription("Pong!")
  action: async (client, interaction) => {
    await interaction.reply({ content: `Pong!` });
  }
};

```

This code adds a simple ping command to your plugin which will return "Pong!" when a member uses the `/ping` command.





## Adding Config Values

You can load values from the config you specify in the [<mark style="color:red;">config file of a plugin</mark>](../getting-started/customizing-plugins.md). These will help users modify your plugin to fit their needs.

```typescript
import { SlashCommandBuilder } from "npm:discord.js";

export default {
  data: new SlashCommandBuilder()
    .setName("greet")
    .setDescription("Greet someone")
  action: async (client, interaction, config) => {
    await interaction.reply({ content: `${config.greetMsg}` });
  }
};

```

This will reply with the custom welcome message when somebody used the `/greet` command.

For this to work, you will need to add the config option in the config file for your plugin.

```yaml
name: MyPlugin
description: Reply With A Custom Message
version: 1.0.0

config:
    greetMsg: 👋 Welcome to our server
```

Users can now configure your plugin to reply with anything they want!
