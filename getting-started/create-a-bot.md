---
description: Create your first Blitz bot to install plugins onto.
---

# Create A Bot

There are 2 methods to create a bot, manually or using the[ <mark style="color:red;">Blitz CLI</mark>](https://jsr.io/@blitz-bots/cli)

## Blitz CLI

Using the blitz cli to create a bot is as simple as running one command!

```bash
blitz bot
```

## Manually

If you prefer to manually create the bot, it is also very simple!

Firstly, you need to initialize a new [<mark style="color:red;">deno</mark>](https://deno.com) project.

Then, you need to edit the file structure to look like this:

```
├── deno.json
├── bot.ts
├── .env
└── /plugins
```

Next up, adding the bots code! Edit `bot.ts` to look like this:

```typescript
import { Bot } from "@blitz-bots/bot";

const token = Deno.env.get("DISCORD_TOKEN");

if (!token) {
    console.error("DISCORD_TOKEN is not defined in the environment variables.");
    Deno.exit(1);
}

const bot = new Bot(token);

try {
    await bot.start();
} catch (error) {
    console.error("Failed to start the bot:", error);
}
```

The code above uses the `Bot` class from the [<mark style="color:red;">@blitz-bots/bot</mark>](https://jsr.io/@blitz-bots/bot) package. It then provides with the bot which is set in the environment variables, and then tries to start the bot.

We will now set the bots token in the .env file so we can access the client.

{% hint style="info" %}
You can skip this step if you run the `blitz bot` command with the `-t` flag
{% endhint %}



Head over to `.env` and add `DISCORD_TOKEN="".`

Your file should look like this:

```editorconfig
DISCORD_TOKEN=""
```

Now, get your token from the[ <mark style="color:red;">Discord Developer Portal</mark>](https://discord.com/developers/applications/) and add it in between the quotation marks (`""`)



## Finally

Your bot is now ready to load plugins through the `/plugins` folder!
