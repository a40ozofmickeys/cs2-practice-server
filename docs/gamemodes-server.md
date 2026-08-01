# gamemodes_server.txt design

The rewritten file registers only two map groups under Classic Casual because
GameModeManager is the higher-level mode selector.

- `mg_prefire`: nine lmtlss Prefire Workshop maps.
- `mg_1v1`: `aim_redline_fp`.

Anti-Peek Spray is deliberately excluded because it is a separate trainer, not
a Prefire route map.

The duplicate `mg_1v1` definitions from the original file were removed.
