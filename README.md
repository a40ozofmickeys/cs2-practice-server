# Bay Area CS2 Practice Server

Git-ready configuration for a CubeCoders AMP CS2 server using Metamod,
CounterStrikeSharp, and GameModeManager.

## Included now

- Minimal `gamemodes_server.txt` containing only `mg_prefire` and `mg_1v1`.
- GameModeManager configuration containing only Prefire and 1v1.
- Inferno Prefire (`3289507717`) as the default Prefire map.
- Minimal global `server.cfg`.
- Baseline `1v1.cfg` for `aim_redline_fp`.
- Map-name wrapper configs for the six Prefire maps whose extracted configs were supplied.
- Original extracted third-party files preserved under `vendor/lmtlss/`.

## Deploy

Copy the contents of `deploy/game/csgo/` into the server's `game/csgo/`
directory, preserving paths. Back up the existing files first.

Recommended AMP map-related arguments:

```text
+mapgroup mg_prefire +host_workshop_map 3289507717
```

Do not also specify a stock `+map de_mirage` argument.

## Important asset note

The supplied AI files cannot safely be flattened into one global `ai/azy`
directory: Mirage's `config.kv3` differs from the other supplied maps. The
Workshop VPK should remain the source of map-specific AI and script assets.
The repository therefore preserves the extracted copies under `vendor/` for
inspection and future update tooling but does not deploy them globally.

## Missing extracted map configs

No extracted cfg/AI folders were supplied for:

- `prefire_vertigo`
- `prefire_anubis`
- `prefire_train`

They remain in `mg_prefire`, but no wrapper or extracted launcher cfg is
included yet. Add their extracted files before expecting identical dedicated-
server behavior on those maps.

## CleanerCS2

CleanerCS2 is intentionally not configured here. It can remain installed to
reduce excess console output; this repository does not replace or modify it.
