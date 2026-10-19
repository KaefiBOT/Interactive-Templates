# Kaefibot-Interactive

Use with <https://woweepaw.itch.io/kaefibot> *(formerly known as #StreamManager)*
Coded with :blue_heart: by [WoweePaw](https://twitch.tv/WoweePaw)

## How to Install/Use

- Easiest way: open the KaefiBOT settings, go to `Interactive > Actions` and hit `Templates`. KaefiBOT downloads all files from here, files you already have stay untouched.
- Or by hand: head to `%appdata% > KaefGAMES > StreamManager > Interactive` and place the `.json` files in there.
- Start your KaefiBOT or (if already running) use Command `/actions reload` to reload the File for current Game/load for current Game
- Switch to a supported Game e.g. `Dead by Daylight` s.o.
- Profit!

## Nice but what is this about?

These are `.json` based files for KaefiBOT, a Chatbot for Twitch.tv which enables Interactive features like "press Shift for 5 Seconds" in a Game a file exists for.
Besides keys and mouse buttons the files support OSC-Parameters (e.g. for VRChat), Screen-Effects, Sounds, Bits and Channelpoints with text input.

You can Download the latest Dev from [our Discord](https://discord.gg/woweepaw)!

**Heads up:** If a game runs as admin, Windows blocks the key presses from KaefiBOT. Run KaefiBOT as admin too for these games.

You don't have to write the files by hand! KaefiBOT has an editor for them in `Interactive > Actions`, the explanation below is for the curious ones (and for PR's).

## Pull requests?

Sure thing. If you've created a fun file for a Game, not already existing, push it into the PR's :3
Please leave out paths to your own sound files, nobody else has them :D

## File Explanation

The file itself:

```jsonc
{
  "$schema": "../Schemas/application-interactive.schema.json", // Lets editors like VS Code check the file, KaefiBOT sets this
  "Name": "", // Name of the file shown in KaefiBOT
  "Description": "", // Short description
  "CreatedBy": "", // That's you!
  "Game": "", // Optional: Twitch category the file belongs to. Without it the file name is the game
  "InteractiveKeys": [ /* the actions, see below */ ]
}
```

One action in `InteractiveKeys`. Everything except `Command`, `Message` and either `KeysToPress`, `OSC` or `InputOptions` is optional, missing fields use the default value:

```jsonc
{
  "TempChannelPointsID": "", // Never touch, it will get created and removed if your Twitch Channel supports Channelpoints
  "ChannelBitsRequired": 0, // Bits needed to trigger this action (0 = no bits)
  "ChannelPointsCosts": 500, // Change to your liking (the costs for this Redemption)
  "ChannelPointsDescription": "Ducken oder Rutschen", // This is what the Redemption has in their Description
  "ChannelPointsColor": "#9146FF", // Background color of the Redemption (empty = KaefiBOT's default color)
  "ChannelPointsSkipQueue": true, // Redemptions skip the request queue (default: true)
  "ChannelPointsCooldown": 0, // Cooldown of the Redemption in Seconds (0 = the general cooldown of the actions)
  "ChannelPointsMaxPerStream": 0, // Max. Redemptions per stream (0 = unlimited)
  "ChannelPointsMaxPerUser": 0, // Max. Redemptions per viewer and stream (0 = unlimited)
  "Command": "🎮 SneakyPaw", // For the ones without Channelpoint Redemption and also used as the Name for the Channelpoint Redemption
  "KeyCooldown": 0, // How long (in Seconds) until it can get used again
  "KeySelectMode": 0, // 0 = all keys in order; 1 = one random key
  "KeysToPress": [
    {
      "Name": "DIK_LCONTROL", // Name of the key, KaefiBOT shows it in the action list (DIK_... for keys, MOUSE_... for the mouse)
      "Key": 29, // DirectX Input Key ID (German & English Keyboard are supported)
      "InputType": 1, // 0 = Mouse; 1 = Keyboard
      "HoldTime": 0 // How long should this Key getting pressed e.g. Left Control for 0 Seconds
    }
  ],
  "OSC": [
    {
      "Name": "/avatar/parameters/twitch", // Parameter/Name of Path the OSC has to send stuff to. "#DELAY#" just waits for HoldTime Seconds
      "DefaultValue": "0", // Default value e.g. 0 for disabled
      "Value": "8", // Value to set the parameter e.g. twitch to
      "HoldTime": 1.0 // How long should this parameter be set before resetting to default value
    }
  ],
  "ScreenEffect": 0, // 0 = None; 1 = Fake BSOD; 2 = Blackout; 3 = Invert; 4 = Rotate; 5 = Shake; 6 = Glitch
  "ScreenEffectDuration": 5, // How long the Screen-Effect lasts in Seconds
  "Sound": "C:\\Users\\WoweePaw\\Music\\KaefiBOT-Sounds\\tv-total.mp3", // Path to a soundfile on your Computer (backslashes need to get escaped properly)
  "Message": "/me Ducken, Rutschen... Deal with it!" // Message the Chatbot will send on this Redemption/Command
}
```

Channelpoints with text input: viewers type a text when redeeming and the text picks one of the options (small typos are fine). If nothing matches, the viewer gets the points back. Chat commands and bits use the first option:

```jsonc
{
  "Command": "🎮 Emote",
  "UserInput": true, // Turns on the text input. The Redemption never skips the request queue then
  "InputOptions": [
    {
      "Keyword": "dance, tanzen", // Text that picks this option
      "KeysToPress": [ { "Name": "DIK_1", "Key": 2, "InputType": 1, "HoldTime": 0.0 } ], // Same fields as in the action: KeySelectMode, KeysToPress, OSC, ScreenEffect, ScreenEffectDuration, Sound, Message
      "Message": "Let's dance!"
    }
  ],
  "Message": ""
}
```
