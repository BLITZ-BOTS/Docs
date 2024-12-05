---
description: Add a command to your plugin
---

# Add A Command

All commands must be placed inside of the `/commands` folder inside of your plugin. If it is not, bots with your plugin install will not load your command.

Create a new file called `ping.ts` inside of your commands folder.

<pre class="language-typescript"><code class="lang-typescript">import { CommandInteraction } from 'discord.js';
<strong>export default {
</strong>     name: 'ping',
     description: 'Pong!',
     action: async (interaction: CommandInteraction) => {
         await interaction.reply(`Pong!`);
     },
};
</code></pre>

This code adds a simple ping command to your plugin which will return "Pong!" when a member uses the `/ping` command.

Plugins are built on top of [<mark style="color:red;">discord.js</mark>](https://discord.js.org/), so many functions you are used to, can be used within blitz!
