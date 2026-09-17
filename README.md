# Caravan v1.0.0

A playable recreation of **Caravan from Fallout: New Vegas** for **The Wand Company Pip-Boy 3000**, built specifically for firmware **1.1.6** and its memory-constrained Espruino runtime.

## Features

* Player-vs-CPU Caravan gameplay.
* Randomized 54-card decks.
* Number cards, Aces, Jacks, Queens, Kings, and Jokers.
* Three caravans per player.
* Betting and ante selection.
* Ascending and descending caravan rules.
* Same-suit override behavior.
* 21–26 selling range.
* Correct tie handling.
* Two-of-three caravan win detection.
* Randomized Fallout: New Vegas opponents.
* Guided Demo / Tutorial.
* Rematches.
* Challenge New Opponent.
* Animated bottle-cap win/loss results.
* Configurable game sound effects and background music.
* Persistent audio volume settings.
* Low-memory lifecycle logging.

## Resident Runtime Architecture

Caravan uses a low-memory resident-runtime design intended to improve stability across consecutive matches.

The following systems load once for the current Caravan play session:

* Game Engine
* Renderer
* Game Audio

When a match ends, only match-specific data is released, including:

* Decks
* Hands
* Caravan cards
* Direction state
* Current match state

Selecting **Rematch** rebuilds only the match data while keeping the Engine, Renderer, and Game Audio resident.

This avoids repeatedly evaluating and loading the largest gameplay modules between matches.

## Opponents

Real matches randomly select from 14 Fallout: New Vegas Caravan players:

* Cliff Briscoe
* Dale Barton
* Ambassador Dennis Crocker
* Isaac
* Private Jake Erwin
* Johnson Nash
* Jules
* Keith
* Lacey
* Little Buster
* Quartermaster Mayes
* No-bark Noonan
* Ringo
* Jed Masterson

**Rematch** keeps the current opponent.

**Challenge New Opponent** performs an in-place match reset and selects a different opponent.

## Gameplay Rules

Caravan supports number cards and the major face-card mechanics from Fallout: New Vegas.

### Jack

Removes the targeted numeric card and its attached face cards.

### Queen

Reverses the caravan's current direction and changes its effective suit.

### King

Doubles the value of the targeted numeric card. Additional Kings multiply the value again.

### Joker

When played on an Ace, removes other numeric cards of that Ace's suit from both boards.

When played on a 2–10, removes other numeric cards of that rank from both boards.

### SOLD / Ties

A caravan must be within the valid selling range and actually beat the opposing caravan to count as **SOLD**.

Equal totals remain tied.

## Audio

Caravan includes:

* Playing Card sound - Sound Effect by Alex from Pixabay
* Discard sound - Sound Effect by Alex from Pixabay
* Bottle Cap result audio - Sound already in the Pip-Boy 3000
* Background music

Music:

* Lazy Day - Tired - Music by Geoff Harvey from Pixabay

## THANKYOU

Holotape Image by Goji! He put work into the art cover thumbnail for the Caravan Game and it's awesome!
