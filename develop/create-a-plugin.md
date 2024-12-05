---
description: Create your first Blitz bot to install plugins onto.
---

# Create A Plugin

There are 2 methods to create a plugin, manually or using the[ <mark style="color:red;">Blitz CLI</mark>](https://jsr.io/@blitz-bots/cli)

## Blitz CLI

Using the blitz cli to create a bot is as simple as running one command!

```bash
deno run -A jsr:@blitz-bots/cli plugin
```

## Manually

If you prefer to manually create the plugin, it is also very simple!

Then, you need to edit the file structure to look like this:

```
├── /commands
├── /events
└── blitz.config.yaml
```

Next up, adding the bots code! Edit `blitz.config.yaml` to contain the metadata for your plugin

```typescript
name: MyPlugin
description: My totally cool plugin
version: 1.0.0
```

The code above allows your plugin to be registered to the blitz registry.

## Finally

Your plugin is now ready for you to add events and commands!
