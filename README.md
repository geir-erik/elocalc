# EloCalc

A tiny SwiftUI chess Elo calculator. Multiplatform — runs on **iPhone/iPad (iOS 16+)** and **Mac (macOS 13 Ventura+)** from a single target. (The rating graph uses Swift Charts, which requires iOS 16 / macOS 13.)

## Fields
- **White ELO**, **Black ELO** — current ratings
- **White Result** — dropdown: `1` (white wins), `0.5` (draw), `0` (white loses)
- **K-factor** — rating volatility (common values: 10, 20, 40)
- **New ELO White / New ELO Black** — calculated automatically as you type

## Run it
Open `EloCalc.xcodeproj` in **Xcode**, pick a destination in the toolbar dropdown
(**My Mac**, or an **iPhone simulator** / your connected iPhone), then press ⌘R.

> Note: this machine only has the Command Line Tools installed, not full Xcode,
> so the app can't be built from here — open it in Xcode on a Mac to run.

## The math
Expected score for a player: `E = 1 / (1 + 10^((opponentRating − rating) / 400))`
New rating: `R' = R + K · (score − E)`
Black's score is `1 − whiteResult`. See `EloCalc/ContentView.swift` (`enum Elo`).
