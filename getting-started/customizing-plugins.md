---
description: Learn how to customize a plugin to make it your own
---

# Customizing Plugins

Some plugins may have values which you can customize.

Plugins will store their config in the `blitz.config.yaml` file.

Not all plugins will contain config values, you will know if you are able to add config by checking the plugins blitz.config.yaml file.

## <mark style="color:red;">Plugin Without Config</mark>

```yaml
name: MyPlugin
description: My plugin with no config
version: 1.0.0
```



## <mark style="color:green;">Plugin With Config</mark>

```yaml
name: MyPlugin
description: My plugin with config
version: 1.0.0

config:
    message: Hello World
    reaction: 👋
    count: 1
```



Config is passed into both commands end events within a plugin.

### Event Action

```typescript
action: async (client, config, args..,) => {}
```

### Command Action

```typescript
action: async (client, args.., config) => {}
```



In both examples, args is dynamcally passed into the action;

For an event this could be things such as, a message object, a reaction object, ect.

For a command this is usually interaction, as the bots register commands as slash commands.



