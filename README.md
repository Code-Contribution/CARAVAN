# Caravan v1.0.0 - Resident Runtime Test 2A

Memory-stability test for the Wand Company Pip-Boy 3000 (firmware 1.1.6).

## What changed

- Engine loads once per Caravan play session.
- Renderer loads once per Caravan play session.
- Game Audio loads once per Caravan play session.
- At Results, only the current match data (decks, hands, caravans, directions) is released.
- Rematch rebuilds match data using the already-loaded Engine/Renderer/Audio modules.
- No Renderer or Game Audio eval/load happens on Rematch.
- Play/Discard use the previously tested short WAV playback with explicit stop/unload timers.
- `SOLD` now requires actually beating the opposing caravan; equal totals such as 26 vs 26 remain tied.
- Real matches now randomize among the 14 Fallout: New Vegas Caravan players.
- Results offers `Rematch`, `Challenge New Opponent`, and `Back`; Rematch keeps the same opponent while Challenge New Opponent performs an in-place resident match reset with a different opponent.

## Diagnostic log

`CARAVAN.LOG` uses short lifecycle markers with free Espruino blocks:

- `CV G# READY F#### T####` - match fully loaded and playable; T is total Espruino variable blocks
- `CV G# RESULT ... F#### T####` - match finished
- `CV G# DATAFREE F#### T####` - match data released; resident modules remain
- `CV G# REMATCH F#### T####` - rematch rebuild is starting
- next `CV G# READY F#### T####` - next match is ready

The game number increments only after a match becomes ready.


Music asset: "Lazy Day - Tired" (16 kHz mono IMA ADPCM, 1024-byte blocks).
