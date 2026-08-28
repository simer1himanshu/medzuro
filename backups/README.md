# Backups

Snapshots of live-theme state that exists only on the store, kept here so it
survives in git.

## index.live.json

`templates/index.json` as pulled from the live theme `medzuro/main`
(#142677082211) on 2026-08-28.

This is the 10-section homepage built in the theme editor:

    hero_banner (slideshow) -> shop_by_category (medzuro-categories)
    -> holyoak_collection (product-slider) -> why_medzuro (medzuro-features)
    -> counters (medzuro-counters) -> reviews (medzuro-testimonials)
    -> product_grid (medzuro-products) -> blog -> newsletter -> faq

It differs from the repo's `templates/index.json`, which is a single
`medzuro-reference-home` section. The store's version has never been
overwritten because the first sync rejected the repo copy, and no later
commit touched the file.

To make the repo version live, change `templates/index.json` so the sync
re-uploads it. To keep this one, copy this file over `templates/index.json`.

## index.reference-home.json

`templates/index.json` for the single-section `medzuro-reference-home`
homepage, with the 25 blocks the refactored section needs. Copy it over
`templates/index.json` to make that homepage live.
