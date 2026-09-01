# Shople

A static daily UK supermarket price-guessing game.

## Run it

Open `index.html` in a modern browser, or serve the folder with any static web server:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Current September 2026 dataset

The game uses a fixed September 2026 food-price snapshot with:

- 176 product records
- 9 retailers: Aldi, ASDA, Co-op, Iceland, Lidl, Morrisons, Sainsbury's, Tesco and Waitrose
- 20 UK gameplay locations
- 61 records with both standard and loyalty-card prices
- Loyalty-card pricing explicitly labelled as Tesco Clubcard, Nectar, Co-op Member Card or Lidl Plus

The location is part of the game question. Unless the source is store-specific, it should not be interpreted as proof that the displayed price came from a particular branch.

## Pricing schema

Each product uses:

- `price` — standard price
- `hasLoyaltyPrice` — whether a separate loyalty price is available
- `loyaltyPrice` — loyalty-card price when available
- `loyaltyCard` — exact card/app name
- `priceType` — `standard` or `standard_and_loyalty`
- `snapshotDate` / `verified` — date of the price snapshot/check
- `source` — source page for the captured price

For products with both prices, the daily game deterministically chooses either the standard price or the loyalty price. The question tells the player which one to use.

## Annual updates

For the next annual refresh, update `data.js` and `prices-2026-09.csv` with the new snapshot. Keep the same field structure so the game logic does not need to change.

Do not invent historical prices. Store only prices you have sourced and dated.

## Pricing note

Retailer online prices, promotions, eligibility and stock can change. Some loyalty prices require the retailer's membership/account/app. Lidl records in this snapshot were sourced from late-August 2026 pages immediately before the September launch and are labelled with their source check date.
