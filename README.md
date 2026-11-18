
## Guard

The original protection system now has two protection methods:

 **Classic** repeatedly sends protection to every selected player. Its **Normal** mode is the most direct option. Classic **Smart** keeps the repeated protection behavior, but adapts the interval to the number of selected players currently needing protection instead of always using the total selected player count to allow maximum protect speeds
 
 **Smarter** only sends protection to players whose live guardian shield is missing. **Normal** uses the selected speed mode, while **Smartest** also adapts the interval to the number of players currently needing protection( fastest 

The speed tables are independent for Safe, Balanced, and Extreme. The interval increases as more players need protection, reducing the chance that you go past the rate limit ceiling

 The Chart sub tab shows the active speed mode's table and explains the expected rate

### Guard speed tables

The values below are the delay between protection cycles. A lower delay means faster protection, but also increases the chance of hitting the protection RPC rate limit. The tables use the number of players currently needing protection. If more than 14 players are selected, then the mod uses the 14 player limit( because who the hell spam protecting more than 14 players anyway)

**Safe mode**

| Players | Minimum delay |
| ---: | ---: |
| 1 | 0.04s |
| 2 | 0.06s |
| 3 | 0.08s |
| 4 | 0.10s |
| 5 | 0.12s |
| 6 | 0.14s |
| 7 | 0.17s |
| 8 | 0.18s |
| 9 | 0.21s |
| 10 | 0.26s |
| 11 | 0.28s |
| 12 | 0.31s |
| 13 | 0.32s |
| 14 | 0.36s |

**Balanced mode (Recommended)**

| Players | Minimum delay |
| ---: | ---: |
| 1 | 0.03s |
| 2 | 0.05s |
| 3 | 0.07s |
| 4 | 0.09s |
| 5 | 0.11s |
| 6 | 0.13s |
| 7 | 0.16s |
| 8 | 0.17s |
| 9 | 0.20s |
| 10 | 0.25s |
| 11 | 0.27s |
| 12 | 0.30s |
| 13 | 0.31s |
| 14 | 0.35s |

**Extreme mode**

| Players | Minimum delay |
| ---: | ---: |
| 1 | 0.02s |
| 2 | 0.04s |
| 3 | 0.06s |
| 4 | 0.08s |
| 5 | 0.10s |
| 6 | 0.12s |
| 7 | 0.15s |
| 8 | 0.16s |
| 9 | 0.19s |
| 10 | 0.24s |
| 11 | 0.26s |
| 12 | 0.29s |
| 13 | 0.30s |
| 14 | 0.34s |

Extreme is the fastest option and has minimum delays. Balanced is recommended for normal use, while Safe gives the largest delay and the lowest rate limit risk( 0% risk if youre not doing any other RPC related action).

Note: Smart mode works best when the user is the one spam killing the protected players, because your client must observe the shield state changing before it can send another protection. But when another player is doing the spam killing, smart mode does not receive the protection needing player's current shield status in time and hence, the player gets killed. This happens due to network latency

## Auto Run

Auto Run coordinates the existing Guard and Drain settings instead of maintaining a second copy of every setting. It can stop by a requested number of complete cycles(Kill round+Drain round) or by a timer. (A timer finishing during a game or drain does not interrupt that active cycle, the current process is allowed to finish first)

Auto Run can optionally begin the drain portion after the protection timer, repeat the complete process, and notify the lobby when it stops automatically.

## Drain

The main Drain tab automates repeated game start, end game after 30secs and return cycles. It waits for selected players to be present before starting the next cycle and keeps unavailable selected players visible in the list( to prevent softlocking the tab).

Drain has two modes:

 **Classic** uses a manually entered number of cycles.
 **Smart** uses /XP reports from selected players to calculate how many drain rounds each player needs, then runs until the highest required number of drain rounds is complete(This mode is experimental, let me know if you encounter any bugs).

## AFK Grind

AFK Grind automates the farming, but alone and at much faster rates. It is separated into 4 phases:

1. **Lobby creation** moves from the menu or current room into a AFK grind lobby.
2. **Test round** verifies that the selected lobby method can start, end, and return correctly.
3. **Grind** runs the selected protection and local automation method.
4. **Drain**  Ends the game after the configured drain duration(Minimum is 30 seconds), then returns to the lobby.

AFK Grind supports Round and Timer stopping modes. Rounds mode stops AFK grind after the configured number of rounds and timer mode ends it after the configured timer.

AFK Grind has two methods:

 **Method 1(Classic)** uses the classic protection and kill method and its own protection and kill rate settings. **Smart** mode adjusts protections RPCs to the speed of killing. This also helps slighlty increase the maximum kills/s due to smarter use of protection RPCs. 
 **Method 2** uses the faster packet based method and is overall less complicated than method 1(Recommened).

### AFK Grind recovery

AFK Grind has several recovery methods running in the background so one bad lobby or one bad game does not mess up the whole process:

**Lobby creation recovery** retries the selected lobby creation strategy when the first attempt gets stuck or fails. If the strategy cannot finish within its deadline,AFK grind leaves the room, returns to the main menu, and starts the lobby creation phase again.

**Test-round recovery** watches the test round separately from the normal grind. If the test round never starts, never returns, or cannot prove that the selected method works, the process starts again from Phase 1.

**Disconnect/kick recovery** watches for an unexpected disconnect, kick, rate limit kick, or any other unintentional kicks. When triggered, it creates a new lobby and restarts the entire AFK Grind process from Phase 1

**Crash recovery** uses the crash watchdog to detect when the game stops responding or closes unexpectedly. A fresh game instance is started and AFK Grind resumes from Phase 1 after the new game has loaded.

**Stale process recovery** handles cases where the game is still open but the AFK process is no longer making progress/is stuck on a unfixable problem. It leaves the lobby, creates a fresh lobby, and retries.

**Method recovery** can switch between the Client sided GL and AUGL lobby methods when automatic method switching is enabled. If neither method can make a usable lobby, AFK Grind goes on standby on AUGL method and waits for a new code to appear in the glitch tab before starting the process

## Anti-Nuke

This tab is espically made to stop people from destroying your glitched lobbies. Most of the features in Anti-Nuke are self explanatory, except one, which i will explain myself:

You probably already know of the vent kick exploit. Its the most widely used and reliable way to destroy lobbies, because there is no mod to prevent it directly. Guardian mod is the same, it does not have some sort of method to protect other players fromthis exploit, but what this mod does have is the ability to remove the root of the exploit: VentlationSystem.

**Prevent vent kick exploit for all players** works by immidiately removing the map upon starting the game. When the map is deleted, there is no way to use vent kick exploit as there is no VentilationSystem spawned in, meaning every vent related exploit(kick players, teleport any player to vent, immortality etc) becomes useless.

To make sure players do not get lost in the void, a lobby instance is spawned. This also keeps all the players close together and makes the shields process easier.

Note: Allow all to chat mid game will not work with this feature turned on

## Players

 Kick and ban.
 
 Set player role for the next game.
 
 Turn a player into Guardian Angel.
 
 Teleport a player to any vent
 
 Select which player's ghost chat is shown.
 
 Player specific mid game chat

## Lobby

 Allowing all players to chat mid-game or ending a meeting immediately after calling it
 Custom impostor count for the next game.
 Auto kick players above a configured lobby player count limit. The player is informed with a chat only the can see, then is kicked after 2 secs.
 
(Self explinatory features in this tab have been skipped)

## Glitch

The Glitch tab reads AUGL's codes and refreshes every 20 secs(if i remember correctly). It contains 3 sub tabs:

 **Codes** (Self explinatory)
 **Creation** automates GL creation. It has 2 phases: Phase 1 arms the process by creating a normal official region lobby and leaving it 1.5secs later. Phase 2 selects the AUGL codes region and creates a glitch lobby.(Phase 1 is skipped when the session has already been armed by creating or joining a lobby)
 **Credits** Contains credits for AUGL

## Misc

Misc contains client side and convenience features that do not belong to a specific tab

**Show ghost chat to all** works by relaying all ghost chats through your client to all other client. There is a limit of 6 relay chats per second to prevent you from getting kicked. Example: KRUSH(Cyan) said: Ghost chat relay test

**Allow all to chat mid game** allow all players in the game to chat with eachother mid game. Useful for passing the time as a crewmate during shields. This works by calling a meeting, and ending it immidiately, which bugs out the game and the chat button does not dissapear.

**Give all players camera(lobby only)** gives every player in the lobby the influencer camera without turning them into a ghost. This feature works only if a player has not played a game/round in this session. for example, if player 1 played a game in this session but player 2 did not, using Give camera to all will appear to have made every player into a influencer on player 1's screen whereas on player 2's screen, everyone would be alive and have the influencer camera. A player must restart the game if they have played a round in this session in order to see the camera while being alive.(Very gimmicky feature, may get removed in the next update)

**Show custom XP** and **Show custom level** change what XP and level is shown on the level/XP end screen after the Victory/defeat end screen. Client sided only, do not affect your actual level or XP.

**Show custom beans** works in a similar manner, but for beans instead

**Turn on new GUI** switches the legacy GUI to the new GUI( couldnt think of actual name, so lets just call it new GUI). The red scheme is inspired from [REDACTED] menu.( name redacted because its a shitty menu that proabably also has a virus)


(Self explinatory features in this tab have been skipped)

## Credits

 Some general QoL features taken and inspired from: Sicko menu
 
 Map and lobby spawn/despawn feature and some anti nuke protections taken from: Hydra menu
 
 Skip role intro taken from: Elysium menu
 
 Some anti stale methods for AFK grind refrenced from: Sky menu
