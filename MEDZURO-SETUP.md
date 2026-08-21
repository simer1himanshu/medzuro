# Medzuro Retail — Admin setup

Theme code is in place, but three things must be configured in Shopify Admin
before the storefront renders fully. None of this can live in theme files.

## 1. Product metafields (spec §8)

Settings → Custom data → Products → Add definition. Namespace **`medzuro`**.

| Key | Type | Name |
|---|---|---|
| `benefits` | Rich text | Benefits |
| `ingredients` | Rich text | Ingredients |
| `directions` | Rich text | Directions for use |
| `warnings` | Rich text | Warnings |
| `nutrition` | Multi-line text | Nutrition table |
| `serving` | Single line text | Serving size |

`nutrition` is one row per line, pipe separated — `Nutrient | Amount | %DV`:

```
Vitamin C | 500 mg | 555%
Zinc | 15 mg | 136%
Magnesium | 100 mg | 24%
```

Empty fields are skipped, so partially filled products still render cleanly.

Then in the theme editor: Product page → Add block → **Product facts (Medzuro)**.

## 2. Product tags (spec §6, §9)

Badges are tag-driven and renamed in Theme settings → Product grid → Labels.
Defaults ship as:

| Tag | Badge |
|---|---|
| `Best Seller` | slot 1 |
| `New Arrival` | slot 2 |
| `Premium` | slot 3 |
| `Limited Stock` | slot 4 |
| `Authorized Seller` | slot 5 |
| `Eurofins Tested` | slot 6 |
| `Made in India` | slot 7 |
| `coming-soon` | Coming Soon — also replaces Sold Out and shows Notify Me |

Slot 8 is intentionally blank and free for future use. The tag must match the
badge text exactly.

## 3. Theme settings

- **Medzuro → Authorized seller** — title, subtitle, icon, colours (§3)
- **Medzuro → Cart reassurance** — delivery note, secure-checkout note, trust image (§12)
- **Medzuro → Structured data** — support phone/email, organization description (§26)

## Still outstanding

| Spec | Needs |
|---|---|
| §13 | Pickup locations in Admin; nearest-store/map UI needs an app |
| §14 | **Decision required** — deposits/pay-at-store need Shopify Plus or the reservation-product fallback |
| §17 | Notification app (email/SMS/WhatsApp) |
| §18, §19 | Courier API + warehouse label printing — separate integration phase |
| §20, §21 | Loyalty and subscription apps |
| §23 | Review app (verified purchase, photos, votes) |
| §25 | GA4, Search Console, Meta Pixel + CAPI, Merchant Center |

## 4. Collections and pages to create (spec §7, §22)

Collections cannot be created from theme code. The homepage category grid and
the main navigation link to these handles — until they exist in Admin, those
links 404 and the grid renders without images.

| Handle | Title | Source |
|---|---|---|
| `holyoak` | HolyOak | §3 — the launch range, linked from the nav and hero |
| `vitamins-minerals` | Vitamins & Minerals | §1 "vitamins, minerals" |
| `herbal-formulations` | Herbal Formulations | §1 "herbal formulations" |
| `sports-nutrition` | Sports Nutrition | §1 "sports nutrition" |
| `daily-wellness` | Daily Wellness | §1 "wellness products" |

Give each collection an image — the grid uses it automatically.

**These four category names are inferred, not specified.** The docx mentions
"category" only twice (§7 "Shop by Category", §22 "Category Search") and never
defines a taxonomy. They were derived from the §1 product scope. Confirm them
with the client before products are loaded, since category structure drives
navigation, search and collection URLs, and is costly to change later.

Note also §6: launch is 15 HolyOak products. Four categories across 15 SKUs may
leave some near-empty — consider fewer categories until the range grows.

Pages linked from the navigation: `/pages/about`, `/pages/contact`, and the
blog at `/blogs/news`. Footer menus expect link lists with the handles
`customer-service` and `information`.
