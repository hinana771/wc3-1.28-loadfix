# w3load + w3perf

Faster map loading and fewer fight freezes for **Warcraft III 1.28.5**.

|                                 | Before                                                    | After                        |
| ------------------------------- | --------------------------------------------------------- | ---------------------------- |
| Map load (TWRPG)                | ~40 s                                                     | **7–9 s**                    |
| Second load in the same session | ~70 s                                                     | **~9 s** (no restart needed) |
| Big fights                      | freezes when abilities/sounds are used for the first time | smooth                       |

> Works only with **1.28.5.7680**. On any other version both mods switch themselves off and the game runs normally.

## What they do

- **w3load.mix** makes map loading much faster, and stops later loads in the same session from getting slower.
- **w3perf.mix** removes the freezes in big fights. w3load also relies on its fixes: with w3load alone a load takes about 17 s instead of 7–9 s. **Use both.**

Neither mod changes gameplay, the map, or anything sent to other players. They only make the game's own slow work faster on your PC, so you can play with people who don't have them, with no desyncs. Graphics settings are not touched.

## Install

1. Download the zip from [Releases](../../releases).
2. Copy these 4 files into your Warcraft III folder (the one with `war3.exe` and `Game.dll`):
   
   ```
   w3load.mix
   w3load.ini
   w3perf.mix
   w3perf.ini
   ```
3. Start the game. The game loads `.mix` files from its folder by itself.

Keep the `.ini` files: `w3load.ini` turns on one of the speedups, and without it loading is slower.

## Uninstall

Delete the 4 files, and the `.log` files if you like.

## Settings

The defaults are the tested ones. Change them only if something goes wrong. `1` = on, `0` = off.

**w3load.ini** `[w3load]`

| Key          | Default |                                                                                              |
| ------------ | ------- | -------------------------------------------------------------------------------------------- |
| `Enabled`    | 1       | `0` turns the whole mod off                                                                  |
| `LoadingFps` | 15      | how often the loading screen is redrawn (lower = slightly faster load, choppier loading bar) |
| `ScanFast`   | 1       | fast map data lookup, the biggest single speedup                                             |
| `ScanCheck`  | 0       | testing only: double-checks ScanFast against the game                                        |

**w3perf.ini** `[w3perf]`

| Key                                 | Default |                                                                                                                              |
| ----------------------------------- | ------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `RowMemo`, `FilterMemo`, `FindMemo` | 1       | the fight-freeze fixes                                                                                                       |
| `VerifyEvery`                       | 64      | every 64th remembered answer is checked against the game; any difference switches the fix off and is written to `w3perf.log` |
| `FileCache`                         | 1       | remembers missing sound/model files so fights don't ask the disk again and again                                             |

The main speedups regularly check their own answers against the game's while running. If anything ever differs, they fall back to the game's normal code.
