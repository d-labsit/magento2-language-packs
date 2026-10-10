# Magento 2 storefront language packs: el, sq, bg, nl, mk

Translations of everything a customer sees around the products in a Magento 2 shop, for
**Greek (el_GR), Albanian (sq_AL), Bulgarian (bg_BG), Dutch (nl_NL) and Macedonian (mk_MK)**:
login and registration, customer account (dashboard, addresses, orders, wishlist, newsletter,
reviews), cart, checkout, search, the 404 page and form validation / error messages.

Covers Magento core storefront modules, **Hyvä** (default theme) and the **Luma** checkout,
about 3,600 phrases per language. Admin (backend) phrases are not included.

Why: Albanian has no Magento language pack at all, the Macedonian community pack is mostly
untranslated, and the Greek community pack is partly English and uses English Title Case
("Δημιουργία Λογαριασμού"). These packs use the normal capitalisation of each language.

## Install

```sh
composer config repositories.dlabsit-language-packs vcs https://github.com/dlabsit/magento2-language-packs
composer require dlabsit/magento2-language-packs
bin/magento setup:upgrade
bin/magento setup:static-content:deploy el_GR sq_AL bg_BG nl_NL mk_MK   # production mode
bin/magento cache:flush
```

Then set **Stores > Configuration > General > Locale Options > Locale** per store view.

Without Composer: copy a language directory (e.g. `sq_al/`) to `app/i18n/Dlabsit/sq_al/`.

## Load order

Magento loads module CSVs, then language packs (lowest `sort_order` first), then the theme CSV.
These packs have `sort_order` 10, so they override packs with the default 0 (such as the
Mageplaza packs). A module's own CSV for the same phrase is overridden too; your theme's
`i18n/<locale>.csv` always wins, so put your own wording there.

## Quality

Machine-translated with Claude and proofread line by line by a second pass (wrong words, mixed-in
Russian/Serbian, meaning errors, placeholders `%1` / `{{var}}` / HTML checked). Dutch uses the
informal *je*, the others the polite form. They run on a live shop, but have not been reviewed
by native speakers: corrections are welcome as a pull request.

## License

MIT, see [LICENSE](LICENSE). Made by [Dlabs IT](https://dlabs.nl).
