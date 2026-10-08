# ห้างทองเยาวราชคลองหาด — gold price website

A single-page Thai website that shows live gold prices for the shop. It works on computers and on phones held upright or sideways.

## What's in the folder

| File | What it is |
|---|---|
| `index.html` | The whole website (design, prices, chart, calculator, slideshow) |
| `shop-prices.json` | The shop's own prices, used only when you switch them on |
| `logo-lions.webp`, `logo-full.webp`, `favicon.png` | Shop logo for the header, footer and browser tab icon |
| `promo-services.jpg`, `promo-buy-old-gold.jpg` | Slideshow pictures. To add or swap one, upload the image and list its file name in `slides` inside `CONFIG` |
| `README.md` | This guide |

## Where the prices come from

| What | Source | Refresh |
|---|---|---|
| Gold bar and jewelry buy/sell (สมาคมค้าทองคำ) | Thai Gold API, `api.chnwt.dev` — free, no key, community-run, reads goldtraders.or.th | every 60 s |
| World gold price (spot) and USD/THB | XAUS, `xaus.com` — free, no key | every 30 s |
| Chart (24 hours to 5 years) | XAUS intraday and daily history | every 5 min / 6 h |

Both sources are free and need no account. Neither is official, so they can occasionally lag or go down. When that happens the page keeps showing the last prices it received, marks them as offline, and retries on its own.

## Put it online (free)

The page has to be served from a web address. Opening `index.html` straight from your computer will not load `shop-prices.json`.

**Option A — GitHub Pages (recommended, lets staff edit prices from a phone)**
1. Create a free account at github.com and make a new public repository, for example `khlonghat-gold`.
2. Upload the three files (Add file → Upload files → Commit).
3. Settings → Pages → Source: "Deploy from a branch", Branch: `main`, folder `/ (root)` → Save.
4. After about a minute the site is at `https://<your-username>.github.io/khlonghat-gold/`.
5. To use your own domain (e.g. `www.khlonghatgold.com`), add it under Settings → Pages → Custom domain.

**Option B — Netlify Drop (quickest)**
1. Go to app.netlify.com/drop and drag the whole folder onto the page.
2. You get a link straight away. Create a free account to keep it permanently.
3. To change anything later, drag the updated folder again.

## Using the shop's own prices

By default the site shows the สมาคมค้าทองคำ prices. To show the shop's prices instead, edit `shop-prices.json`:

```json
{
  "ใช้ราคาหน้าร้าน": true,
  "ทองคำแท่ง_รับซื้อ": 65750,
  "ทองคำแท่ง_ขายออก": 65950,
  "ทองรูปพรรณ_รับซื้อ": 64400,
  "ทองรูปพรรณ_ขายออก": 66750,
  "หมายเหตุ": "ราคาพิเศษเฉพาะวันนี้",
  "อัปเดตเมื่อ": "8 ต.ค. 2569 14:59 น."
}
```

- `true` = show shop prices (the badge changes to "ราคาหน้าร้าน"); `false` = back to association prices.
- Leave a price out to keep the association price for just that one.
- `หมายเหตุ` shows as a notice on the price board; leave it `""` to hide it.
- On GitHub: open `shop-prices.json` → pencil icon → edit → Commit. Visitors see the change within about 1–2 minutes.

## Changing shop details

At the top of the `<script>` in `index.html`, the `CONFIG` block holds the shop name, tagline, phone number, opening hours, closed days and the slideshow text. Edit the values between the quotes and save.
