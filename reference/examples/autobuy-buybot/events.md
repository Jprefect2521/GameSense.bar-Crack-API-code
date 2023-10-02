# Events

**Examples:**

```lua
client.set_event_callback("paint", function()
	renderer.text(15, 15, 255, 255, 255, 255, nil, 0, "hello world")
end)
```

#### paint\_ui

Fired every time the game renders a frame, even if you're in the menu. Can be used to draw to the screen using the render functions

#### run\_command

Fired every time the game runs a command (usually 64 times a second, equal to tickrate) while you're alive. This is the best event for processing data that only changes when the game receives an update from the server, like information about other players.

| Key                 | Description                                   |
| ------------------- | --------------------------------------------- |
| **chokedcommands**  | Amount of commands that the client has choked |
| **command\_number** | Current command number                        |

#### setup\_command

Fired every time the game prepares a move command that's sent to the server. This is ran before cheat features like antiaim and can be used to modify user input (view angles, pressed keys, movement) how it's seen by the cheat. For example, setting `in_use = 1` will disable antiaim the same way pressing use key ingame does. This is the preferred method of setting user input and should be used instead of `client.exec` whenever possible

| Key                     | Description                                                              |
| ----------------------- | ------------------------------------------------------------------------ |
| **chokedcommands**      | Amount of commands that the client has choked                            |
| **command\_number**     | Current command number                                                   |
| **pitch**               | Pitch view angle                                                         |
| **yaw**                 | Yaw view angle                                                           |
| **forwardmove**         | Forward / backward speed (-450 to 450)                                   |
| **sidemove**            | Left / right speed (-450 to 450)                                         |
| **move\_yaw**           | Yaw angle that's used for movement. If not set, view yaw is used         |
| **allow\_send\_packet** | Set to false to make the cheat choke the current command (when possible) |
| **in\_attack**          | IN\_ATTACK Button                                                        |
| **in\_jump**            | IN\_JUMP Button                                                          |
| **in\_duck**            | IN\_DUCK Button                                                          |
| **in\_forward**         | IN\_FORWARD Button                                                       |
| **in\_back**            | IN\_BACK Button                                                          |
| **in\_use**             | IN\_USE Button                                                           |
| **in\_cancel**          | IN\_CANCEL Button                                                        |
| **in\_left**            | IN\_LEFT Button                                                          |
| **in\_right**           | IN\_RIGHT Button                                                         |
| **in\_moveleft**        | IN\_MOVELEFT Button                                                      |
| **in\_moveright**       | IN\_MOVERIGHT Button                                                     |
| **in\_attack2**         | IN\_ATTACK2 Button                                                       |
| **in\_run**             | IN\_RUN Button                                                           |
| **in\_reload**          | IN\_RELOAD Button                                                        |
| **in\_alt1**            | IN\_ALT1 Button                                                          |
| **in\_alt2**            | IN\_ALT2 Button                                                          |
| **in\_score**           | IN\_SCORE Button                                                         |
| **in\_speed**           | IN\_SPEED Button                                                         |
| **in\_walk**            | IN\_WALK Button                                                          |
| **in\_zoom**            | IN\_ZOOM Button                                                          |
| **in\_weapon1**         | IN\_WEAPON1 Button                                                       |
| **in\_weapon2**         | IN\_WEAPON2 Button                                                       |
| **in\_bullrush**        | IN\_BULLRUSH Button                                                      |
| **in\_grenade1**        | IN\_GRENADE1 Button                                                      |
| **in\_grenade2**        | IN\_GRENADE2 Button                                                      |
| **in\_attack3**         | IN\_ATTACK3 Button                                                       |
| **weaponselect**        |                                                                          |
| **weaponsubtype**       |                                                                          |

#### override\_view

Lets you override the camera position and angles

| Key       | Description       |
| --------- | ----------------- |
| **x**     | Camera X position |
| **y**     | Camera Y position |
| **z**     | Camera Z position |
| **pitch** | Pitch view angle  |
| **yaw**   | Yaw view angle    |
| **fov**   | Field of view     |

#### console\_input

Fired every time the user types something in the game console and presses enter. Return true from the event handler to make the game not process the input

|   | Property           |
| - | ------------------ |
| 1 | console input text |

**Examples:**

```lua
client.set_event_callback("console_input", function(text)
	client.log("entered: '", text, "'")
end)
```

#### output

This event lets you override the text drawn in the top left. There can only be one callback for this event. This event callback is invoked from print, client.log, client.color\_log, "Missed due to spread" message, etc.

{% hint style="warning" %}
Make sure to unset your callback when you don't need it. Otherwise you will break the built-in output and other scripts using this event.
{% endhint %}

| Key      | Description              |
| -------- | ------------------------ |
| **text** | Drawn text               |
| **r**    | Drawn color: Red 0-255   |
| **g**    | Drawn color: Green 0-255 |
| **b**    | Drawn color: Blue 0-255  |
| **a**    | Alpha 0-255              |

#### indicator

This event lets you lets you override how indicators are drawn. There can only be one callback for this event. This event callback is invoked from renderer.indicator and indicators like "DT".

{% hint style="warning" %}
Make sure to unset your callback when you don't need it. Otherwise you will break the built-in indicators and other scripts using this event.
{% endhint %}

| Key      | Description              |
| -------- | ------------------------ |
| **text** | Drawn text               |
| **r**    | Drawn color: Red 0-255   |
| **g**    | Drawn color: Green 0-255 |
| **b**    | Drawn color: Blue 0-255  |
| **a**    | Alpha 0-255              |

#### player\_chat

Fired when a player sends a message to chat

| Key          | Description                                    |
| ------------ | ---------------------------------------------- |
| **teamonly** | true if the message was sent to team chat      |
| **entity**   | Entity index of the player sending the message |
| **name**     | Name of the player sending the message         |
| **text**     | Chat message text                              |

#### string\_cmd

Fired before a string command (chat messages, weapon inspecting, buy commands) is sent to the server.

|   | Property       |
| - | -------------- |
| 1 | string command |

#### net\_update\_start

Fired before the game processes entity updates from the server. (`FrameStageNotify FRAME_NET_UPDATE_START`) Be careful when using this event to modify entity data, some things have to be restored manually as not even a full update will update them

#### net\_update\_end

Fired after an entity update packet is received from the server. (`FrameStageNotify FRAME_NET_UPDATE_END`)

#### predict\_command

Fired when the game prediction is ran

{% hint style="info" %}
This event is called a lot of times per second, avoid doing any heavy processing in it.
{% endhint %}

| Key                 | Description                             |
| ------------------- | --------------------------------------- |
| **command\_number** | Command number of the predicted command |

#### pre\_render

Fired before a frame is rendered

#### post\_render

Fired after a frame is rendered

#### aim\_fire

Fired when the rage aimbot shoots at a player

| Key                | Description                                                                                   |
| ------------------ | --------------------------------------------------------------------------------------------- |
| **id**             | Shot ID, this can be used to find the corresponding aim\_hit / aim\_miss event                |
| **target**         | Target player entindex                                                                        |
| **hit\_chance**    | Chance the shot will hit, depends on spread                                                   |
| **hitgroup**       | Targeted hit group, this is not the same thing as a hitbox                                    |
| **damage**         | Predicted damage the shot will do                                                             |
| **backtrack**      | Amount of ticks the player was backtracked                                                    |
| **boosted**        | True if accuracy boost was used to increase the accuracy of the shot                          |
| **high\_priority** | True if the shot was at a high priority record, like on shot backtrack                        |
| **interpolated**   | Player was interpolated                                                                       |
| **extrapolated**   | Player was extrapolated                                                                       |
| **teleported**     | Target player was teleporting (breaking lag compensation)                                     |
| **tick**           | Tick the shot was fired at. This can be used to draw the hitboxes using client.draw\_hitboxes |
| **x**              | X world coordinate of the aim point                                                           |
| **y**              | X world coordinate of the aim point                                                           |
| **z**              | Z world coordinate of the aim point                                                           |

**Examples:**

```lua
local function time_to_ticks(t)
	return floor(0.5 + (t / globals.tickinterval()))
end

local hitgroup_names = {'generic', 'head', 'chest', 'stomach', 'left arm', 'right arm', 'left leg', 'right leg', 'neck', '?', 'gear'}

local function aim_fire(e)
	local flags = {
		e.teleported and 'T' or '',
		e.interpolated and 'I' or '',
		e.extrapolated and 'E' or '',
		e.boosted and 'B' or '',
		e.high_priority and 'H' or ''
	}
	local group = hitgroup_names[e.hitgroup + 1] or '?'
	print(string.format('Fired at %s (%s) for %d dmg (chance=%d%%, bt=%2d, flags=%s)', entity.get_player_name(e.target), group, e.damage, math.floor(e.hit_chance + 0.5), time_to_ticks(e.backtrack), table.concat(flags)))
end
client.set_event_callback('aim_fire', aim_fire)
```

#### aim\_hit

Fired when the rage aimbot hit a shot at a player

| Key             | Description                                                    |
| --------------- | -------------------------------------------------------------- |
| **id**          | Shot ID, the corresponding aim\_fire event has the same ID     |
| **target**      | Target player entindex                                         |
| **hit\_chance** | Actual hit chance the shot had                                 |
| **hitgroup**    | Hit group that was hit. This is not the same thing as a hitbox |
| **damage**      | Actual damage the shot did                                     |

**Examples:**

```lua
local hitgroup_names = {'generic', 'head', 'chest', 'stomach', 'left arm', 'right arm', 'left leg', 'right leg', 'neck', '?', 'gear'}

local function aim_hit(e)
	local group = hitgroup_names[e.hitgroup + 1] or '?'
	print(string.format('Hit %s in the %s for %d damage (%d health remaining)', entity.get_player_name(e.target), group, e.damage, entity.get_prop(e.target, 'm_iHealth')))
end
client.set_event_callback('aim_hit', aim_hit)
```

#### aim\_miss

Fired when the rage aimbot missed a shot at a player

| Key             | Description                                                                                               |
| --------------- | --------------------------------------------------------------------------------------------------------- |
| **id**          | Shot ID, the corresponding aim\_fire event has the same ID                                                |
| **target**      | Target player entindex                                                                                    |
| **hit\_chance** | Actual hit chance the shot had                                                                            |
| **hitgroup**    | Hit group that was missed. This is not the same thing as a hitbox                                         |
| **reason**      | Reason the shot was missed. This can be 'spread', 'prediction error', 'death' or '?' (unknown / resolver) |

**Examples:**

```lua
local hitgroup_names = {'generic', 'head', 'chest', 'stomach', 'left arm', 'right arm', 'left leg', 'right leg', 'neck', '?', 'gear'}

local function aim_miss(e)
	local group = hitgroup_names[e.hitgroup + 1] or '?'
	print(string.format('Missed %s (%s) due to %s', entity.get_player_name(e.target), group, e.reason))
end
client.set_event_callback('aim_miss', aim_miss)
```

#### pre\_config\_load

Fired before a config will be loaded

#### post\_config\_load

Fired after a config has been loaded

#### pre\_config\_save

Fired before a config will be saved

#### post\_config\_save

Fired after a config has been saved
