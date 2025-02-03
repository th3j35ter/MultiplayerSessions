# MultiplayerSessions Plugin

This plugin is designed to provide streamlined multiplayer functionality for Unreal Engine 5 projects. It integrates with the **OnlineSubsystem**, **OnlineSubsystemUtils**, and **OnlineSubsystemSteam** and allows for customizable multiplayer session setups.

---

## Requirements

Before using this plugin, ensure your project meets the following requirements:

1. **Build.cs File Setup:**
   Add the following modules to your project's `Build.cs` file:
   ```csharp
   PublicDependencyModuleNames.AddRange(new string[] {
       "OnlineSubsystem",
       "OnlineSubsystemUtils",
       "OnlineSubsystemSteam"
   });
   ```

2. **Plugins Setup:**
   Ensure the **OnlineSubsystem** and **OnlineSubsystemSteam** plugins are enabled in your project.

---

## Installation

1. Clone or download this plugin into your project’s `Plugins/` folder:
   ```bash
   git submodule add https://github.com/your-username/MultiplayerSessions.git Plugins/MultiplayerSessions
   ```

2. Add the plugin to your project by enabling it in the **Editor**:
   - Open Unreal Engine.
   - Go to `Edit > Plugins`.
   - Search for `MultiplayerSessions` and enable it.
   - Restart the Editor.

3. Ensure the **OnlineSubsystemSteam** is set up in your project:
   - Update `DefaultEngine.ini`:
     ```ini
     [OnlineSubsystem]
     DefaultPlatformService=Steam

     [OnlineSubsystemSteam]
     bEnabled=true
     SteamDevAppId=480
     ```
   - Replace `480` with your own Steam App ID if applicable.

---

## Usage

1. **Setup Your GameMode:**
   - Create a custom `BP_GameMode` in your project.
   - Set the desired **Pawn Class**, **Player Controller**, and **HUD**.

2. **Configure the Starting Map:**
   - Open the **Level Blueprint** for your starting map.
   - Add the following logic:
     - Create a `WBP_Menu` widget.
     - Call `MenuSetup` with the required parameters:
       - `Num Public Connections` (e.g., 4).
       - `Match Type` (e.g., "Deathmatch").
       - `Map File Path` (e.g., `/Game/Folder/Maps/MapName`).

3. **Launch Multiplayer Sessions:**
   - Use the in-game menu to host, find, and join multiplayer sessions.

---

## Notes

- This plugin requires the **Steam subsystem** to be functional. Make sure you have the Steam client running when testing multiplayer features.
- The map file path must be provided in the format `/Game/...` for the `MenuSetup` function to work correctly.

---

## Troubleshooting

1. **OnlineSubsystemSteam Not Working:**
   - Ensure `Steamworks` SDK is properly integrated into your project.
   - Confirm `SteamDevAppId` is set correctly in `DefaultEngine.ini`.

2. **Widget Does Not Appear:**
   - Verify the `WBP_Menu` widget is being created and added to the viewport in the **Level Blueprint**.

3. **Session Errors:**
   - Double-check the parameters passed to `MenuSetup`.
   - Ensure your firewall allows connections for the game.

---

## Contributing

Contributions are welcome! If you’d like to improve this plugin, please open an issue or submit a pull request to the GitHub repository.

---

## License

This plugin is distributed under the MIT License. See the `LICENSE` file for details.
