# Code Documentation (Client Side)

This document provides an overview of the functions and events in the BLRP Framework.

## Events
### blrp:requestModel
Event triggered when a model is requested.

**Parameters:**
- `model` (string): The model that is requested.

**Functionality:**
This event is triggered when a model is Requested. It can be used to handle model requests and perform any related actions or logic.

---

### blrp:playerLoaded
Event Triggered when a player is loaded.

**Parameters:**
- `blrPlayer` (table): The player data.
- `isNew` (boolean): Flag indicating whether the player is a new player.

**Functionality:**
This event is triggered when a player is loaded. It provides the player data and whether the player is a new player. It can be used to perform any necessary actions or logic when a player is loaded.

---

### blrp:onPlayerJoined
Event triggered when a player joins the server.

**Parameters:**
- None

**Functionality:**
This event is triggered when a player joins the server. It can be used to perform any necessary actions or initialization tasks when a player joins.


# Variables

- `BLRP`: A table representing the main BLRP module.
- `Core`: A table representing the Core module.
- `BLRP.PlayerData`: A table representing player data.
- `BLRP.PlayerLoaded`: A boolean indicating whether the player is loaded.
- `Core.Input`: A table representing input commands.
### BLRP.Game
- `BLRP.Game.Utils`: A table containing utility functions for the Game module.

### BLRP.Scaleform
- `BLRP.Scaleform.Utils`: A table containing utility functions for the Scaleform module.

### BLRP.Streaming
- No additional information provided.

## Functions

### getObject()
- Returns: table

Exports a table named `BLRP` as an object.

```
The getObject function allows other parts of the code or external scripts to access the BLRP table by returning it. This can be useful for providing access to specific functionality or data within the BLRP table to other parts of the codebase or external scripts.

By exporting the BLRP table, it can be accessed and used by other parts of the code or scripts that import or require the exported object.

Please note that the purpose and usage of the BLRP table within the code snippet are not provided, and additional context or information may be required to fully understand its functionality and how it is used within the codebase.
```

### BLRP.IsPlayerLoaded()
- Returns: boolean

Checks if the player is loaded.

### BLRP.GetPlayerData()
- Returns: table

Gets the player data.

### BLRP.HashString()
Parameters:

- `str` (string): The input string.
- Returns: string

Hashes the input string and returns the hashed value as a string.

### BLRP.RegisterInput()
- Parameters:
    - `command_name` (string): The name of the command.
    - `label` (string): The label for the key mapping.
    - `input_group` (string): The input group for the key mapping.
    - `key` (number): The key code for the key mapping.
    - `on_press` (function): The function to execute when the command is pressed.
    - `on_release` (function): The function to execute when the command is released (optional).

Registers an input command and key mapping.

### BLRP.Game.GetVehicles()
- Returns: table

Gets the list of vehicles in the game.

### BLRP.SetPlayerData()
- Parameters:
    - `key` (string): The key to set in the player data.
    - `val` (any): The value to assign to the key.
    - Sets the specified key with the provided value in the player data.

### BLRP.Game.GetPlayers()
- Parameters:
    - `onlyOtherPlayers` (boolean): Flag indicating whether to include only other players.
    - `returnKeyValue` (boolean): Flag indicating whether to return the player-ped key-value pairs.
    - `returnPeds` (boolean): Flag indicating whether to return only peds.
- Returns: table

Gets the list of players in the game.

### BLRP.Game.GetPlayersInArea()
- Parameters:
  - `coords` (vector3): The center coordinates of the area.
  - `maxDistance` (number): The maximum distance from the center coordinates.
- Returns: table

Gets the list of players within the specified area.

### BLRP.Game.GetVehiclesInArea()
- Parameters:
  - `coords` (vector3): The center coordinates of the area.
  - `maxDistance` (number): The maximum distance from the center coordinates.
- Returns: table

Gets the list of vehicles within the specified area.

### BLRP.Game.IsSpawnPointClear()
- Parameters:
  - `coords` (vector3): The coordinates to check for spawn point clearance.
  - `maxDistance` (number): The maximum distance to check.
- Returns: boolean

Checks if the specified coordinates are clear for spawning a vehicle.

### BLRP.Game.GetClosestEntity()
- Parameters:
  - `entities` (table): The entities to search for the closest one.
  - `isPlayerEntities` (boolean): Flag indicating whether the entities are player entities.
  - `coords` (vector3): The reference coordinates.
  - `modelFilter` (table): The model filter for selecting specific entities (optional).
- Returns: entity, distance

Gets the closest entity from the provided list based on the reference coordinates.

### BLRP.Game.GetVehiclesInDirection()
- Returns: entity, coords

Gets the vehicle in the direction the player is facing.

### BLRP.Game.GetVehicleProperties()
- Parameters:
  - `vehicle` (vehicle): The vehicle to get the properties of.
- Returns: table

Gets the properties of the specified vehicle.

### BLRP.Game.SetVehicleProperties()
- Parameters:
  - `vehicle` (vehicle): The vehicle to set the properties for.
  - `props` (table): The properties to set for the vehicle.

Sets the properties of the specified vehicle using the provided properties table.

### BLRP.Game.Utils.DrawText3D()
- Parameters:
  - `coords` (vector3): The coordinates to draw the text.
  - `text` (string): The text to draw.
  - `size` (number): The size of the text (optional).
  - `font` (number): The font style of the text (optional).
Draws 3D text at the specified coordinates.

### BLRP.GetVehicleType()
- Parameters:
  - `model` (string or number): The model name or hash value of the vehicle.
- Returns: string

Gets the type of the specified vehicle based on the model name or hash value.

