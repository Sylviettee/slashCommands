# DEPRECATED, USE [SPAR'S INSTEAD](https://github.com/GitSparTV/discordia-slash/)

# Slash Commands

Add the functionality of [slash commands](https://discord.com/developers/docs/interactions/slash-commands) in discordia 2.x!

## Example

```lua
local discordia = require 'discordia'

---@type slashCommands
local slashCommands = require 'slashCommands'

local SlashCommand = slashCommands.SlashCommand
local enums = slashCommands.enums

local client = discordia.Client()

---@type SlashCommand
local command = SlashCommand(client, 'ban', 'Ban a user')
   :argument('user', 'The user to ban', enums.argumentType.user)
   :argument('reason', 'The reason to ban the user', enums.argumentType.string)

command:execute(function(ctx)
   local args = ctx.arguments

   args.user:ban(args.reason)

   ctx:reply('Banned ' .. args.user.username .. ' for ' .. args.reason)
end)

client:once('ready', function()
   command:commit() -- Pass in a guild id to add commands to a specific guild
end)

client:run("Bot TOKEN")
```

Note: `command:commit()` **must** be ran in a coroutine, everything else doesn't need to be within a coroutine.

## Installation

You can install via lit.

```sh
lit install SovietKitsune/slashCommands
```

## TODO

* [ ] - Add functionality for subcommands
* [x] - Fix bugs
