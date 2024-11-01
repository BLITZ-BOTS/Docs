# BLITZ WIP Tracker

## Plugin File Structure

```
/PLUGIN_NAME
│
├── manifest.json              # Contains metadata and permissions for the plugin.
├── config.json                # Holds customizable settings for the plugin.
│
├── commands                   # Directory for command scripts.
│   └── ping.js                # Example script for the 'ping' command.
│
├── events                     # Directory for event handler scripts.
│   └── message.js             # Example handler for message events.
│
└── slash_commands             # Directory for slash command scripts.
    └── hello.js               # Example script for the '/hello' command.
```

## Overview of Each Component

### 1. `manifest.json`

* **Purpose**: Contains essential metadata about the plugin.
* **Key Attributes**:
  * `name`: The name of the plugin.
  * `description`: A brief overview of its functionality.
  * `version`: Current version of the plugin.
  * `author`: Name of the author or organization.
  * `repo`: Link to the source code repository.

### 2. `config.json`

* **Purpose**: Defines customizable settings for your plugin.
* **Common Settings**:
  * API keys
  * Toggle options
  * Default parameters

### 3. `commands/`

* **Purpose**: Houses individual command scripts.
* **Structure**: Each script is responsible for the functionality of a single command.
* **Example**:
  * `ping.js`: Responds to the 'ping' command with a 'pong' reply.

### 4. `events/`

* **Purpose**: Contains event handler scripts that respond to specific events.
* **Structure**: Each script handles one type of event.
* **Example**:
  * `message.js`: Processes incoming messages and triggers actions based on their content.

### 5. `slash_commands/`

* **Purpose**: Dedicated to scripts that implement slash commands.
* **Structure**: Each script defines the behavior of a specific slash command.
* **Example**:
  * `hello.js`: Sends a greeting when the `/hello` command is invoked.

## Example Manifest File

```json
{
  "name": "MyPlugin",                            // Name of the plugin
  "description": "A brief description of what the plugin does.", // Description of functionality
  "version": "1.0.0",                           // Current version of the plugin
  "author": "Your Name",                        // Author or organization name
  "repo": "https://github.com/yourusername/MyPlugin", // URL to the source code repository
  "folders": {
    "events": "events/",                        // Path to the events directory
    "commands": "commands/",                    // Path to the commands directory
    "slash_commands": "slash_commands/"         // Path to the slash commands directory
  }
}
```

## Plugin Registry

### Upload

A route for users to submit a folder containing their plugin code with all files and directories as outlined in the Plugin File Structure.

**Endpoint**: `POST /reg/upload`\
**Request Body**: The request must include the plugin folder as form data. Here’s an example of how to structure the request using `multipart/form-data`:

```plaintext
{
  "folder": "<plugin_folder>"   // The folder containing all plugin files (e.g., manifest.json, config.json, commands/, events/, slash_commands/)
}
```

### Delete

A route allowing users to delete their submitted plugins from the registry.

**Endpoint**: `DELETE /reg/delete`\
**Request Body**: The request must specify the name of the plugin to be deleted.

```json
{
  "plugin_name": "MyPlugin"    // The name of the plugin to be deleted
}
```

### Update

A route for users to update their plugin in the registry with a new version specified in `manifest.json`.

**Endpoint**: `PUT /reg/update`\
**Request Body**: The request must include the name of the plugin and the updated plugin folder as form data.

```plaintext
{
  "plugin_name": "MyPlugin",   // The name of the plugin to be updated
  "folder": "<plugin_folder>"   // The folder containing the updated plugin files (e.g., updated manifest.json, config.json, commands/, events/, slash_commands/)
}
```
