# Code Documentation (Player Class)
## Functions

### CreateExtendedPlayer()
- Parameters:
  - `playerId` (number): The player's ID.
  - `name` (string): The player's name.
  - `identifier` (string): The player's identifier.
  - `rank` (string): The player's rank or group.
  - `coords` (table): The player's coordinates.
  - `metadata` (table): Additional metadata associated with the player.

```md
The `CreateExtendedPlayer` function is responsible for creating an extended player object in the BLRP framework. It takes various parameters to initialize the player object and returns the created object.
```

The player object contains the following properties:

- `coords`: The player's coordinates.
- `rank`: The player's rank or group.
- `name`: The player's name.
- `identifier`: The player's identifier.
- `playerId`: The player's ID.
- `source`: The player's ID (same as playerId).
- `variables`: Additional variables associated with the player.
- `metadata`: Additional metadata associated with the player.
- `license`: The player's license identifier.
- `ghost`: A flag indicating if the player is a ghost (invisible) (optional, defaults to false).

The player object has the following methods:

- `triggerEvent(eventName, ...)`: Triggers a client event for the player with the given event name and additional arguments.
- `setCoords(coords)`: Sets the player's coordinates to the provided coordinates.
updateCoords()`: Continuously updates the player's coordinates based on their entity in the game.
- `getName()`: Returns the player's name.
- `setGhost(set)`: Sets the ghost flag for the player (true/false).
- `getGhost()`: Returns the ghost flag for the player.
- `getCoords(vector)`: Returns the player's coordinates as a vector3 or vector4 object based on the vector parameter.
- `kick(reason)`: Kicks the player from the server with the specified reason.
- `getIdentifier()`: Returns the player's identifier.
- `setGroup(newGroup)`: Sets the player's group or rank to the specified new group.
- `getGroup()`: Returns the player's group or rank.
- `set(k, v)`: Sets a custom variable with the provided key-value pair for the player.
- `get(k)`: Returns the value of the custom variable with the specified key for the player.
- `showNotification(msg)`: Shows a notification to the player.
- `showHelpNotification(msg, thisFrame, beep, duration)`: Shows a help notification to the player.
- `getMeta(index, subIndex)`: Retrieves metadata for the player. If index is provided, it returns the corresponding metadata. If subIndex is provided along with index, it returns the metadata value for the subIndex within the index.
- `setMeta(index, value, subValue)`: Sets metadata for the player. If subValue is provided, it sets the value for the subValue within the index. Otherwise, it sets the value for the entire index.
- `clearMeta(index)`: Clears the metadata for the player. If index is provided, it clears the corresponding metadata. If index is a table, it clears the metadata for each value within the table.

```md
The `CreateExtendedPlayer` function also allows for the registration of player function overrides. 
It checks if the `Config.PlayerFunctionOverride` variable is set and if the corresponding overrides exist in the `Core.PlayerFunctionOverrides` table. 
If found, it assigns the overridden functions to the player object.

The function concludes by returning the created player object.
```