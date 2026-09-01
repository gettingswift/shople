# Shople

A daily UK supermarket price-guessing game.

## Current snapshot

September 2026 only.

## Features

- Five deterministic questions per day
- Standard vs loyalty-price questions
- Explicit loyalty-card requirement (Tesco Clubcard, Nectar, Co-op Member Card, Lidl Plus, etc.)
- 5,000 points per question / 25,000 total
- Daily streaks and local personal statistics
- Shareable score links
- Retailer source link on every revealed answer
- Static deployment: GitHub → Vercel
- Standalone `data.js` so annual price updates do not require changing game logic

See `GITHUB-SETUP.md` for deployment instructions.


## Price location policy
Shople intentionally does not invent branch or regional prices. Each question uses the retailer/product price stored in the September 2026 snapshot. A location is not shown unless a future dataset contains a verifiable store-specific price. Loyalty questions explicitly name the required card (for example Tesco Clubcard, Sainsbury's Nectar, Co-op Member Card or Lidl Plus).
