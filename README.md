# Kaefibot-Interactive

Use with <https://woweepaw.itch.io/kaefibot> *(formerly known as #StreamManager)*
Coded with :blue_heart: by [WoweePaw](https://twitch.tv/WoweePaw)

## How to Install/Use

- Head to `%appdata% > KaefGAMES > StreamManager > Interactive` and place the `.json` files in there.
- Start your KaefiBOT or (if already running) use Command `/actions reload` to reload the File for current Game/load for current Game
- Switch to a supported Game e.g. `Dead by Daylight` s.o.
- Profit!

## Nice but what is this about?

These are `.json` based files for KaefiBOT, a Chatbot for Twitch.tv which enables Interactive features like "press Shift for 5 Seconds" in a Game a file exists for.
The files also now support OSC-Parameters since KaefiBOT `InDev_2a862bf-16-01-2025` (not yet released to the Public as of 25.01.2025 but soon:tm:)

You can Download the latest Dev from [our Discord](https://discord.gg/woweepaw)!

**Some Files are a bit older then the rest. __No worries__, KaefiBOT WILL update them to the newest standard. I haven't had them used for a while, that's all...*

## Pull requests?

Sure thing. If you've created a fun file for a Game, not already existing, push it into the PR's :3

## File Explanation

```jsonc
{
  "TempChannelPointsID": "", // Never touch, it will get created and removed if your Twitch Channel supports Channelpoints
  "ChannelPointsCosts": 500, // Change to your liking (the costs for this Redemption)
  "ChannelPointsDescription": "Ducken oder Rutschen", // This is what the Redemption has in their Description
  "Command": "🎮 SneakyPaw", // For the ones without Channelpoint Redemption and also used as the Name for the Channelpoint Redemption
  "KeyCooldown": 0, // How long (in Seconds) until it can get used again
  "KeySelectMode": 0, // 0 = List; 1 = Random
  "KeysToPress": [
    {
      "Name": "DIK_LCONTROL", // Never touch. KaefiBOT will set this! (unless you build the file on your own... then touch and name it to your liking)
      "Key": 29, // DirectX Input Key ID (German & English Keyboard are supported)
      "InputType": 1, // 0 = Mouse; 1 = Keyboard
      "HoldTime": 0 // How long should this Key getting pressed e.g. Left Control for 0 Seconds
    }
  ],
  "OSC": [
    {
      "Name": "/avatar/parameters/twitch", // Parameter/Name of Path the OSC has to send stuff to
      "DefaultValue": 0, // Default value e.g. 0 for disabled
      "Value": 8, // Value to set the parameter e.g. twitch to
      "HoldTime": 1 // How long should this parameter be set before resetting to default value
    }
  ],
  "Sound": "C:\\Users\\WoweePaw\\Music\\KaefiBOT-Sounds\\tv-total.mp3", // Path to a soundfile on your Computer (backspace needs to get escaped properly)
  "Message": "/me Ducken, Rutschen... Deal with it!" // Message the Chatbot will send on this Redemption/Command
}
```
