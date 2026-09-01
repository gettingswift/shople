# Shople — GitHub + Vercel setup

This is a static Shople build. The easiest deployment is GitHub → Vercel.

## 1. Create the GitHub repository

1. Open GitHub and choose **New repository**.
2. Name it `shople`.
3. Create the repository.
4. Open the new repository and choose **Add file → Upload files**.
5. Upload these files from this folder:

```text
index.html
data.js
prices-2026-09.csv
README.md
GITHUB-SETUP.md
.gitignore
```

6. Click **Commit changes**.

Do not upload the ZIP file itself as the website.

## 2. Import into Vercel

1. Open Vercel.
2. Choose **Add New → Project**.
3. Select the `shople` GitHub repository.
4. Use these settings:

| Setting | Value |
|---|---|
| Framework Preset | Other |
| Root Directory | `./` |
| Build Command | Leave blank |
| Install Command | Leave blank |
| Output Directory | Leave blank |

5. Click **Deploy**.

Vercel will serve `index.html` directly.

## 3. Automatic updates

Once GitHub and Vercel are linked, each commit to the repository causes Vercel to redeploy the site.

For the annual September refresh, update `data.js` and the CSV, commit the changes, and Vercel will publish the new dataset.

## 4. Loyalty-price fields

A product can have both a standard price and a loyalty price. Keep these fields together:

```javascript
{
  price: 4.50,
  hasLoyaltyPrice: true,
  loyaltyPrice: 3.50,
  loyaltyCard: "Tesco Clubcard"
}
```

For a product with no loyalty price:

```javascript
{
  price: 2.49,
  hasLoyaltyPrice: false
}
```

The game will automatically decide whether today's question asks for the standard or loyalty price and will display the required card.

## 5. Share links

Shople generates a shareable URL using the browser URL itself. No database is required. A shared link contains the date and the score breakdown and opens the shared-score screen.

Example structure:

```text
https://your-site.vercel.app/?share=...
```

The share link is intentionally client-side and is not a server-side leaderboard.

## 6. Important limitation

The game uses browser `localStorage` for streaks, games played and personal statistics. Clearing browser storage or changing device/browser will reset those local stats.

## 7. Annual data refresh checklist

Before publishing a new annual snapshot:

1. Replace/update product prices in `data.js`.
2. Verify `snapshotDate` and `snapshotLabel`.
3. Keep the source URL and verification date for each product.
4. Check that loyalty prices still identify the exact card required.
5. Update the CSV export.
6. Commit to GitHub.
7. Check the Vercel deployment.


## Price location policy
Shople intentionally does not invent branch or regional prices. Each question uses the retailer/product price stored in the September 2026 snapshot. A location is not shown unless a future dataset contains a verifiable store-specific price. Loyalty questions explicitly name the required card (for example Tesco Clubcard, Sainsbury's Nectar, Co-op Member Card or Lidl Plus).
