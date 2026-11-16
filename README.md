# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/muhamadyusufseptian6-lab/makefun-tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/muhamadyusufseptian6-lab/makefun-tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4,096 bytes of Python for the make.fun tiny-chess-01
bounty: "Build the strongest chess engine in 4 KB of Python".

`main.py` (4,075 bytes) is the whole engine: a minified + lzma-packed
payload that unpacks to a 0x88-board negamax engine with

- legal move generation (castling, en passant, all promotions),
- alpha-beta search with a transposition table, killer + history move
  ordering, null-move pruning, late-move reductions and check extensions,
- quiescence search over captures, promotions and replies to checks,
- material + piece-square evaluation (tapered king safety, bishop pair),
- a fixed node budget per move (100k nodes early, tapered in long games),
  so play is fully deterministic: no clock, no randomness, no network
  beyond the game env, no model calls, standard library only.

Local practice trials (official env + scorer, this kit), 6 games each:
trial-0 Elo 1654 (5W 1L), trial-1 Elo 1279 (3W 3L), trial-2 Elo 1654
(5W 1L); mean 1529, above the house baseline's practice mean of ~1365
and the 1154 practice floor. Slowest move observed 4.6 s (limit 10 s);
trial wall times 399–600 s of the 1800 s budget. The entry plays through
the env at `MAKEFUN_ENV_URL` (`POST /game`, `/move`) and exits when all
games are done.

## Files

- `main.py` — the engine (4,075 bytes, the only code file)
- `LICENSE` — MIT
- `.makefun/owner.json` — wallet claim for this entry

---

<sub>Entered on [make.fun](https://make.fun/?ref=515temp1&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
