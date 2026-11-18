# tiny-chess — a 4 KB chess engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/rizko-d/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/rizko-d/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4,096 bytes of Python: alpha-beta with quiescence search,
transposition table, null-move pruning, late move reductions and check
extensions, under a fixed 100,000-node budget per move. Deterministic: no
clock, no randomness, no model calls.

`main.py` (3,333 bytes) is the kit's `makefun compress` packing of the
readable source: 0x88 board, MVV-LVA + killer/history ordering, incremental
material + piece-square eval with bishop pair and tempo. It also avoids
threefold repetition while the position is drawish or better (contempt).

Practice trials against the house gauntlet (kit env + scorer): trial-0 Elo
1654 (4W/2D/0L), trial-1 Elo 1364 (2W/3D/1L), trial-2 Elo 1654 (4W/2D/0L)
— mean 1557, above the 1154 final floor and the ~1365 sunfish baseline.
Trial-0 replayed twice gives byte-identical games. Repo total 5,415 bytes.

## Run it

Set `MAKEFUN_ENV_URL` to the trial env, then `python3 main.py`.
