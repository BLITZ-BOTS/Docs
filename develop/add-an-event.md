---
description: Add an event to your plugin
---

# Add An Event

All events must be placed inside of the `/events` folder inside of your plugin. If it is not, bots with your plugin install will not load your event.

{% hint style="info" %}
Plugins are built on top of [<mark style="color:red;">discord.js</mark>](https://discord.js.org/), so many functions you are used to, can be used within blitz!
{% endhint %}



## Basic Ready Event

Create a new file called `ready.ts` inside of your events folder.

```typescript
import { Client } from "npm:discord.js";

export default {
  event: "ready",
  once: true,
  action: async (
    client: Client,
  ) => {
    console.log(`${client.user.username} is online!`)
    }
  };
```

This code adds a simple ready event to your plugin which will log in the console when the client has logged in.





## Adding Config Values

You can load values from the config you specify in the [<mark style="color:red;">config file of a plugin</mark>](../getting-started/customizing-plugins.md). These will help users modify your plugin to fit their needs.

```typescript
import { Client, Message } from "npm:discord.js";

export default {
  event: "messageCreate",
  once: true,
  action: async (
    client: Client,
    config: any
    message: Message,
    
  ) => {
     message.reply(`${config.message}`)
    }
  };
```

This will reply to any message with a custom message set within the config file.

For this to work, you will need to add the config option in the config file for your plugin.

```yaml
name: MyPlugin
description: Reply With A Custom Message
version: 1.0.0

config:
    message: This is a custom message!
```

Users can now configure your plugin to reply to a message with anything they want!



