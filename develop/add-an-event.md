---
description: Add an event to your plugin
---

# Add An Event

All events must be placed inside of the `/events` folder inside of your plugin. If it is not, bots with your plugin install will not load your event.

Create a new file called `ready.ts` inside of your events folder.

```typescript
import { Client, Events } from "npm:discord.js";

export default {
  event: Events.Ready,
  once: true,
  action: async (
    client: Client,
  ) => {
    console.log(`${client.user.username} is online!`)
    }
  };
```

This code adds a simple ready event to your plugin which will log in the console when the client has logged in.

Plugins are built on top of [<mark style="color:red;">discord.js</mark>](https://discord.js.org/), so many functions you are used to, can be used within blitz!
