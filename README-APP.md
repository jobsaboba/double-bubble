# Double Bubble Racing

The Holy Grail's banker's double, as a PWA.

**The rule:** in each race the Holy Grail ranks every runner by score. When the
top-ranked runner's score is **at least twice** the score of the second-ranked
runner, that top runner goes on Double Bubble. One pick per race, a few per day.

**The money:** £10 starting bank, every selection stakes **1% of the rolling
bank** at its race's off time (all bets in one race stake the same), win-only —
a WIN pays the published odds, a PLACE or LOSE costs the stake, non-runners are
refunded. Walked back to the start of the season (1 Jan 2026) from the Holy
Grail's published day files.

- Live app: https://jobsaboba.github.io/double-bubble/
- Data: `data/<date>.json`, plus `data/index.json` and `data/latest.json`

## Publish

Everything derives from the Holy Grail's files in `~/projects/holy-grail/data/`
(no network fetching). One command rebuilds, dirty-checks every day file,
commits and pushes:

    python3 ~/racing-scripts/double_bubble.py --publish

Runs at 06:25 every morning (cron, after the Grail's 06:00 publish) and again
on the half-hour settle tick from `results-refresh.sh`, so afternoon results
settle into the bank the same way as the other apps.

## App

Pure viewer — day tabs, bank card (bank · day P/L · W·P·L), race list with
score-×N chips, gold odds chips, money chips and win-green / place-gold /
lose-red badges. Installable on the phone (manifest + service worker, ⤓ button
when the browser offers it). Service worker cache: `dbapp-v1` — bump it and the
`APP_VER` whenever `index.html` changes.

## Local repo

    ~/projects/double-bubble   ← this repo (main → GitHub Pages)
    ~/racing-scripts/double_bubble.py   ← the engine

Commits use identity `jobsaboba <160133851+jobsaboba@users.noreply.github.com>`.
