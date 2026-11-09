# ProGM21 Formwork Estimator

Upload a plan (PDF) or a photo, choose what to estimate (wall, column, beam, tie beam, slab), and the page lists the Euroform items and computes the **rental** or **sale** price using the ProGM21 price list.

A single file, `index.html`, with no build step.

## Put it online with GitHub Pages
1. Create a new repository on GitHub (for example `progm21-estimator`).
2. Upload `index.html` and `README.md` (**Add file → Upload files**), then commit.
3. Go to **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then **Save**.
4. After a minute your site is at `https://YOUR-USERNAME.github.io/progm21-estimator/`.

## How to use
1. Paste your **Anthropic API key** (from console.anthropic.com) in the key box. It is saved only in your own browser.
2. Pick **Rental** or **Sale**, tick the elements, upload the PDF or photo.
3. Check the quantities in the table (you can edit them), then read the price.

Without a key you can still add items by hand and get the price.

## Security notes
- The key is used directly from the browser, so **anyone who has your key can spend your credit.** Only type it on your own device, and set a spending limit on the key.
- Do not put a key inside `index.html` before uploading it to GitHub.
- For a public site used by other people, use a small server (for example Cloudflare Workers or Netlify Functions) that holds the key.

## Updating prices
Open `index.html` and edit the two lists near the top of the script:
- `CAT`: `[id, material, size, base price, price per day, sale price new, sale price refurbished]`
- `ACC`: purchase-only items (flat ties, wedge pin, hooks) with VAT-inclusive prices

## How the price is computed (same as your Excel)
- Rental, 30 days = quantity × (base price + 30 × price per day)
- 2nd month = quantity × price per day × 30
- Flat ties, wedge pins and hooks are purchase only (price includes VAT, so it is divided by 1.12 for the VAT-exclusive subtotal)
- VAT = 12%
- Sale = quantity × sale price (VAT inclusive)

The estimate from the photo is a starting point. Always check quantities before sending a quotation.
