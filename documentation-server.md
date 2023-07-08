# Code Documentation (Server Side)

This document provides an overview of the functions and events in the BLRP Framework.

## Functions

### BLRP.Trace()
- Parameters:
  - `msg` (string): The message to be traced.

```markdown
The `BLRP.Trace` function is responsible for printing a trace message to the console if the `EnableDebug` flag in the `Config` table is set to `true`.
```

### BLRP.RegisterCommand()
- Parameters:
  - `name` (string or table): The name of the command or a table of command names.
  - `group` (string or table): The group or groups associated with the command.
  - `cb` (function): The callback function to be executed when the command is triggered.
  - `allowConsole` (boolean): Flag indicating whether the command is allowed to be executed from the console.
  - `suggestion` (table): Optional table providing suggestions for command parameters.

```markdown
The `BLRP.RegisterCommand` function is used to register a command in the BLRP framework. It allows the execution of a callback function when the command is triggered by a player. The function supports registering multiple commands at once by providing a table of command names.
```

### Core.SavePlayer()
- Parameters:
  - `blrPlayer` (table): The player object to be saved.
  - `cb` (function): Optional callback function to be executed after saving the player.

```markdown
The `Core.SavePlayer` function is responsible for saving player data to the database. It takes a player object (`blrPlayer`) and a callback function (`cb`) as parameters. The function encodes the player's accounts, coordinates, and metadata into JSON format and updates the corresponding database record. After the save operation, it triggers the event `blrp:playerSaved` and executes the optional callback function.
```

### Core.SavePlayers()
- Parameters:
  - `cb` (function): Optional callback function to be executed after saving all players.

```markdown
The `Core.SavePlayers` function is used to save data for all players in the BLRP framework to the database. It takes an optional callback function (`cb`) as a parameter. The function iterates over all players and collects their account data, coordinates, and metadata. It then updates the corresponding records in the database. After saving all players, it prints a log message indicating the number of players saved and the execution time, and executes the optional callback function.
```

### BLRP.GetPlayers
```md
The `BLRP.GetPlayers` variable holds a reference to the `GetPlayers` function. This function is typically provided by the game framework or an external library and allows retrieving a list of all connected players.
```

### BLRP.GetExtPlayers()
- Parameters:
  - `key` (string): The key to match against player attributes.
  - `val` (any): The value to match against the provided key.

```md
The `BLRP.GetExtPlayers` function is responsible for retrieving a list of players based on a specified key-value pair. It takes a key and a value as parameters and returns an array of players that match the provided criteria. If no key-value pair is provided, it returns all players.
```

### BLRP.GetPlayerFromId()
- Parameters:
  - `source` (number): The player's source identifier.

```md
The `BLRP.GetPlayerFromId` function retrieves a player object from the `BLRP.Players` table based on the provided player source identifier (`source`).
```

### BLRP.GetPlayerFromIdentifier()
- Parameters:
  - `identifier` (string): The player's identifier.

```md
The `BLRP.GetPlayerFromIdentifier` function retrieves a player object from the `Core.playersByIdentifier` table based on the provided player identifier (`identifier`).
```

### BLRP.GetIdentifier()
- Parameters:
  - playerId (number): The player's ID.

```md
The `BLRP.GetIdentifier` function retrieves the player's identifier based on the provided player ID (`playerId`). It searches through the player's identifiers and returns the one that starts with `'license:'`.
```

### BLRP.GetVehicleType()
- Parameters:
  - `model` (string or number): The model name or hash of the vehicle.
  - `player` (number): The player's ID.
  - `cb` (function): The callback function to be executed with the vehicle type.

```md
The `BLRP.GetVehicleType` function is responsible for retrieving the type of a vehicle based on its model. It takes the model name or hash as the first parameter (`model`), the player ID as the second parameter (`player`), and a callback function (`cb`) to be executed with the vehicle type as the third parameter. The function first checks if the vehicle type is already known based on the provided model. If not, it triggers a client callback (`blrp:GetVehicleType`) to request the vehicle type from the player's client. Once the client responds with the vehicle type, it caches the information and invokes the callback function.
```

### BLRP.DiscordLog()
- Parameters:
  - `name` (string): The name of the Discord webhook.
  - `title` (string): The title of the log entry.
  - `color` (string): The color of the log entry.
  - `message` (string): The log message.

```md
The `BLRP.DiscordLog` function is responsible for sending a log entry to a Discord webhook. It takes the name of the webhook (`name`), the title of the log entry (`title`), the color of the log entry (`color`), and the log message (`message`) as parameters. It constructs an embed object with the provided information and sends it as a POST request to the webhook URL.
```

### BLRP.DiscordLogFields()
- Parameters:
  - `name` (string): The name of the Discord webhook.
  - `title` (string): The title of the log entry.
  - `color` (string): The color of the log entry.
  - `fields` (table): The fields to include in the log entry.

```md
The `BLRP.DiscordLogFields` function is similar to `BLRP.DiscordLog`, but it allows specifying additional fields for the log entry. It takes the name of the webhook (`name`), the title of the log entry (`title`), the color of the log entry (`color`), and a table of fields (`fields`) as parameters. It constructs an embed object with the provided information and fields and sends it as a POST request to the webhook URL.
```

### BLRP.RegisterPlayerFunctionOverrides()
- Parameters:
  - `index` (any): The index or key to identify the player function overrides.
  - `overrides` (table): The table of player function overrides.

```md
The `BLRP.RegisterPlayerFunctionOverrides` function is responsible for registering player function overrides. It takes an index or key (`index`) and a table of player function overrides (`overrides`) as parameters. It stores the overrides in the `Core.PlayerFunctionOverrides` table using the provided index.
```

### BLRP.SetPlayerFunctionOverride()
- Parameters:
  - `index` (any): The index or key of the player function overrides to set.

```md
The `BLRP.SetPlayerFunctionOverride` function sets the player function overrides based on the provided index (`index`). It retrieves the stored player function overrides from the `Core.PlayerFunctionOverrides` table using the provided index and assigns it to the `Config.PlayerFunctionOverride` variable. This allows the framework to use the specified player function overrides when necessary.
```

### Core.IsPlayerAdmin()
- Parameters:
  - `playerId` (number): The player's ID.

```md
The `Core.IsPlayerAdmin` function checks if a player is considered an admin. It first checks if the player has the "command" ace permission or if the server is in LAN mode. If either condition is met, it returns `true`. Otherwise, it retrieves the player object from the `BLRP.Players` table based on the provided player ID (`playerId`) and checks if the player's group is set to "admin". If the player is an admin, it returns `true`. Otherwise, it returns `false`.
```

## Event Handlers

### 'blrp:onPlayerJoined'

```
This event handler is triggered when a player joins the server. It checks if the player is already present in the BLRP.Players table. If not, it calls the onPlayerJoined function to handle the player's joining process.
```

### 'playerConnecting'
```md
This event handler is triggered when a player is connecting to the server. It defers the connection process and performs the following checks:

- Checks the OneSync state and returns an error message if it's not set to "infinity".
- Checks if the database connection is established and returns an error message if not.
- Checks if the player's identifier is available and returns an error message if it's already active in-game.
- If all checks pass, the connection is allowed to proceed
```

### 'chatMessage'
```
This event handler is triggered when a chat message is sent by a player. If the message starts with '/', indicating a command, and the player is not the console (playerId > 0), it cancels the chat message event and shows an error notification to the player.
```

### 'playerDropped'
```
This event handler is triggered when a player disconnects from the server. It retrieves the player's BLRP object from the BLRP.Players table, triggers the 'blrp:playerDropped' event, removes the player's data from the Core.playersByIdentifier table, saves the player's data, and removes the player's object from the BLRP.Players table.
```

### 'blrp:playerLogout'
```
This event handler is triggered when a player logs out. It performs similar actions to the 'playerDropped' event handler but also triggers the 'blrp:onPlayerLogout' client event.
```