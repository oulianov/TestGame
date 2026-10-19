TestGame-DynRPG
===============

Tests of EasyRPG Player's emulation of DynRPG 0.20 (RPG Maker 2003 1.08):

- the patches DynRPG applies to RPG_RT at start-up, from the IPS files of `DynPatches/`
  and the `[QuickPatches]` of `DynRPG.ini`;
- the plugins `EasyRPG.ini` lists in `[DynRPG] Plugins=`, which the Player runs without
  their DLLs.

It is TestGame-2003 with a test room on map 14 (`dynrpg`), where a new game starts. Each
person of the room tests one feature and says what to look at. Run EasyRPG Player with
`--no-patch` to see the same game without DynRPG.

| Person | Feature |
|---|---|
| top row, 1st | msg_commands: `@process_cmd` writes item, skill, state and title names into the next message |
| top row, 2nd | game_clock: play time in the main menu; ATBWaitOnly: the ATB mode is Wait after a new game |
| top row, 3rd | Direct Menu Patch: Open Menu opens Zack's status (variables 50 and 51) |
| top row, 4th | status window: quickpatches (no Class/Title labels), norow (no "Front"), ExpBug-in (EXP) |
| top row, 5th | ExpBug-in: 5000 EXP leave Zack at level 10 (RPG_RT's curve: level 78) |
| bottom row, 1st | KillSwitch: switch 50 OFF, the party dies on the map without a Game Over |
| bottom row, 2nd | KillSwitch: switch 50 ON, Game Over |
| bottom row, 3rd | battle: norow (no Row command), FixBattlerFlash (Albert, on auto battle, doesn't flash under the cursor) |
| bottom row, 4th | faster_atb_advanced: variable 10 sets the battle speed |
| bottom row, 5th | game_clock: play time in variables 24 to 27 |

Settings: `DynPatches/` has DMP, KillSwitch, norow and RPG_RT_FixBattlerFlash. `DynRPG.ini`
sets KillSwitch to switch 50, DMP to variable 50, faster_atb_advanced to variable 10,
game_clock to variables 21 to 30 and an EXP curve that doubles at each level.

Requirements: the RPG Maker 2003 RTP (the battles and menus use its graphics, which are not
included), and an EasyRPG Player that emulates these patches and plugins
(https://github.com/oulianov/Player, branch `dynrpg`).
