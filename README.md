# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/uyekt23/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/uyekt23/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

An original chess engine in 4,096 bytes of Python. `main.py` is a single
lzma-compressed payload: it unpacks and execs a 0x88 negamax engine with
alpha-beta search, a transposition table, quiescence search (captures and
promotions; positions with the side to move in check are searched one ply
deeper instead), MVV-LVA move ordering, and a tapered piece-square-table
evaluation maintained incrementally on make/unmake. It searches a fixed
budget of 120,000 nodes per move — no clock, no randomness — so every
trial replays identically. Full rules: castling, en passant, promotions,
repetition and fifty-move draws scored inside the search.

Local verification: perft from the start position to depth 4 is 197,281,
and a 13,701-position differential test against python-chess found zero
move-generation mismatches. In its local practice trial against the kit
gauntlet (house engines rated 855–1,596) this exact program scored
5.0/6 — a practice Elo of about 1,654, above the house baseline's
practice mean of about 1,365. The slowest move measured took 3.4
seconds, far inside the 10-second limit.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 main.py
```
