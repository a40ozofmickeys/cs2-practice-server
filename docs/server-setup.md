# AMP server deployment

## 1. Back up and stop

1. Create an AMP backup or make copies of the current files listed below.
2. Stop the CS2 instance completely before replacing configuration files.

Back up at least:

- `game/csgo/gamemodes_server.txt`
- `game/csgo/cfg/server.cfg`
- `game/csgo/cfg/1v1.cfg`, if later customized
- `game/csgo/addons/counterstrikesharp/configs/plugins/GameModeManager/GameModeManager.json`

## 2. Deploy repository files

Copy the contents of:

```text
deploy/game/csgo/
```

into the AMP instance's:

```text
game/csgo/
```

Preserve the directory structure and merge folders rather than replacing the
entire `addons` or `cfg` directory.

This deployment does not install or remove Metamod, CounterStrikeSharp,
GameModeManager, CleanerCS2, Custom Votes, MenuManagerAPI, or PlayerSettings.

## 3. AMP launch parameters

Keep AMP's normal executable and networking parameters. For map startup, use
one unambiguous Workshop startup command:

```text
+game_type 0 +game_mode 0 +mapgroup mg_prefire +host_workshop_map 3289507717
```

Remove any stock startup map such as:

```text
+map de_mirage
```

Do not store the real GSLT in this repository. Enter it in AMP's protected
field or protected command-line parameter.

For the first validation run, omit `+sv_pure 2`, `+sv_cheats 0`, and
`+sv_workshop_allow_other_maps 0`. Add restrictions back only after Prefire and
1v1 map changes work reliably.

## 4. First startup checks

Start the instance and confirm the console shows:

1. Metamod and CounterStrikeSharp loading.
2. GameModeManager reaching `LOADED` rather than remaining at `LOADING`.
3. Workshop item `3289507717` loading as `prefire_inferno`.
4. The server executing a map-specific configuration under `cfg/maps/`.
5. Prefire spawn groups loading and bots appearing at the intended positions.

Useful console commands:

```text
css_plugins list
css_plugins reload GameModeManager
status
mapgroup
```

## 5. Functional test

1. Join Inferno Prefire and complete at least one route.
2. Confirm bots use intended locations and behavior.
3. Use GameModeManager to switch to the 1v1 mode.
4. Confirm `aim_redline_fp` loads and `1v1.cfg` executes.
5. Switch back to Prefire and confirm the selected Prefire map initializes.
6. Test `!rtv`, nominations, and end-of-map voting with enough players to meet
   the configured minimum.

## Known limitation

The supplied extracted files did not include dedicated-server launcher/AI
folders for Vertigo, Anubis, or Train. Those maps remain in `mg_prefire`, but
should be tested individually before being offered in public voting.
