#  Guard tab 
The guard tab is the main an original tab in this mod. It auto protects every alive player when turned on. Ignore ghosts toggle and ignore impostors toggle should be kept turned on, bu i still gave it as a choice to turn them off instead of hard coding them into the code if you need to turn them off for whatever reason. Guard has 3 modes:
Safe mode: increases delay between each protect RPC being sent by 0.02s
Balanced mode(Recommended): increases delay between each protect RPC being sent by 0.01s
Extreme mode: The fastest but most unsafe mode. no extra delay, the mod runs at maximum possible speeds. In my experience, bans are very rare even with this mode. However, i would still recommend using the balanced mode
Refer to Chart sub tab to get detailed info about each of the modes

# # Drain tab
Automates the process of draining. Simply input the number of desired cycles, and the mod will handle the rest. Click stop drain to force stop the drain before cycles finish. The tab offers a sophiscated players list to make sure all the selected players are present in the lobby before starting the next cycle. To prevent softlocking the drain tab, selected players who are not in the lobby/went offline will still be visible in the list( Example: KRUSH [UNAVAILABLE] )
Auto return to lobby after each cycle does exactly what it says. Disable role intro disables the "Your role is ____" screen to get to make the drain cycles faster. Turning it off is not recommended, as it may break the drain process( i may or may not have forgotten to test drain without disable role intro). Send "Drained?" after cycles complete automates asking the players if they have drained or not. It has a small delay before sending to make sure all the players have rejoined the lobby after game ending

# # Anti-Nuke tab
This tab is espically made to stop people from destroying your glitched lobbies. Most of the features in Anti-Nuke are self explanatory, except one, which i will explain myself:
You proablby already know of the vent kick exploit. Its the most widely used and reliable way to destroy lobbies, because there is no mod to prevent it... Until now
Prevent vent kick exploit for all players works by immidiately removing the map upon starting the game. When the map is deleted, there is no way to use vent kick exploit as there is no VenitlationSystem spawned in, meaning every vent related exploit(kick players, teleport any player to vent, immortality etc) become useless
To make sure players do not get lost in the void, a lobby instance is spawned in to keep all the players close together and make the shields process easier 

# # Players tab
I intentoially limited the number of features in this tab to make it more Glitch Lobby-specific
The tab contains kick and ban options to kick any players from your lobby
The assign role feature assigns the selected player the chosen role the next game
Turn player to guardian angel immidiately turns the player into guardian angel regardless of their current role. Can be helpful for getting extra support from players with Auto Clickers
Teleport to vent feature is present to make sure the player does not ruin shields by running around the whole map. clicking teleport to vent immidiately telerpots the player to the selected room's vent

# # Lobby tab
The lobby tab has many features, so i wont explain every one of them. I will explain the less self-explanatory ones:
Allow all to chat mid game is a pretty unique feature to all even non modded alive players to chat with eachother mid game. Can be very useful to pass the time while the imposters spam kill them
Imposter amount assigns the next game the selected number of imposters next game. you can choose from 0-15 imposters. Useing this with disable game ending is recommended

# # Glitch tab
A useful QoL tab to improve your overall Glitch Loby experience. It has 3 sub tabs:
Codes: Contains all the glitch codes. The mod is directly hooked to te website, so all the codes in the mod are correct. It has a search option as well as a option to only see a selected region's glitch codes to look for the exact glitch code you like. The mod refreshes every 20s, however, you can also manually refresh by pressing the refresh button
Creation: Has a button to automatically create a glitch lobby. It is divided into two phases: Phase 1 and Phase 2. In phase 1, the mod creates a normal lobby in the offical region and leaves 1.5s later to arm the glitch lobby creation. In phase 2, The custom AUGL region is automatcially selected and a glitched lobby is created. The sub tab also contains a Tutorial section to explain how to get the custom server
Credits(NOT the entire mod's credits): Contains the credits for the help used in Glitch tab   


