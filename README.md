# Stuffs That I Need

A Shopify Online Store theme for **Stuffs That I Need**, a store for curious finds, useful everyday items, and playful gifts. The storefront uses a minimalist visual style with warm neutral colors, responsive product imagery, and reusable sections that can be managed in the Shopify theme editor.

## Development

### Requirements

- [Shopify CLI](https://shopify.dev/docs/api/shopify-cli)
- A Shopify development store or theme preview access

### Run a local theme preview

From the theme directory, authenticate with Shopify if needed and start the development preview:

```sh
shopify theme dev
```

Shopify CLI prints the local preview URL after the theme is connected to a store. Changes to theme files are synchronized to the preview while the command is running.

### Check the theme

Run Shopify Theme Check before submitting theme changes:

```sh
shopify theme check
```

## Storefront features

- **Homepage:** a responsive split hero, featured products, and category discovery cards.
- **Product discovery:** collection pages use responsive product cards with product imagery, prices, sale and sold-out states, and Shopify pagination. Search results support products, pages, and articles.
- **Product pages:** product information and purchase actions use Shopify product and variant data.
- **Cart:** the cart uses Shopify's native cart form and data, including quantity updates, item removal, discounts, cart attributes, and the native checkout action.
- **Theme editor:** homepage sections and category cards expose settings for copy, collections, destinations, and images.
- **Responsive layout:** grids and imagery adapt to desktop, tablet, and mobile widths.

Product and collection content is managed in Shopify Admin. The theme renders store data; it does not create or publish products.

## Theme structure

```text
.
├── assets/       # Global critical styles and static theme assets
├── blocks/       # Reusable theme blocks
├── config/       # Theme settings and editor data
├── layout/       # Document shell and section groups
├── locales/      # Storefront and theme-editor translations
├── sections/     # Homepage, catalog, product, cart, and content sections
├── snippets/     # Shared Liquid fragments
└── templates/    # JSON and Liquid page compositions
```

Templates determine which sections render on each page. Sections contain their own styles and Shopify schema settings, so merchants can arrange and configure the storefront in the theme editor without editing Liquid.

## Localization

Theme translations live in `locales/` and are split into two kinds of files:

- [`en.default.json`](./locales/en.default.json) contains storefront strings for the theme's default locale.
- [`pt-BR.json`](./locales/pt-BR.json) contains storefront strings for Brazilian Portuguese.
- [`en.default.schema.json`](./locales/en.default.schema.json) contains labels shown in the theme editor, such as section names, setting labels, and option names.

Storefront locale keys are organized by feature and purpose. For example, cart strings use `cart.*`, product discovery uses `home.products.*`, and catalog strings use `collections.*`. Keep keys descriptive and reuse an existing key when the meaning is the same.

### Add or change storefront copy

1. Add the key under the appropriate namespace in the default storefront locale file.
2. Add the same key and nesting to every supported storefront locale, including `pt-BR.json`.
3. Reference the key in Liquid with Shopify's `t` filter instead of hard-coding user-facing copy:

```liquid
{{ 'home.products.title' | t }}
```

For dynamic text, use named interpolation parameters and keep placeholder names identical in every locale:

```json
{
  "search": {
    "page_title": "Busca por {{ terms }}"
  }
}
```

```liquid
{{ 'search.page_title' | t: terms: search.terms }}
```

Keep plural forms consistent too. The cart uses `item_count_one` and `item_count_other`, with `count` passed to the plural form. Do not translate, rename, or remove placeholders such as `{{ terms }}`, `{{ count }}`, or `{{ product }}`.

### Translate theme editor labels

Theme editor text belongs in a schema locale file rather than a storefront locale file. Reference it in a section or block schema with a `t:` key:

```json
{
  "name": "t:general.collection"
}
```

Then add the matching nested key to `locales/en.default.schema.json`:

```json
{
  "general": {
    "collection": "Collection"
  }
}
```

### Validate locale changes

Run Theme Check after editing locale files. It checks theme files and reports missing or inconsistent translations:

```sh
shopify theme check
```

Shopify's language editor can update locale files, so review generated changes before committing. Also verify that the `*.default.json` filename matches the store's configured default language. In this repository, `en.default.json` currently contains mostly Portuguese storefront copy; confirm the intended default language before renaming the file or changing the store's language settings.

## Shopify theme resources

- [Theme architecture](https://shopify.dev/docs/storefronts/themes/architecture)
- [Liquid](https://shopify.dev/docs/api/liquid)
- [Shopify CLI](https://shopify.dev/docs/api/shopify-cli)
- [Theme Check](https://shopify.dev/docs/storefronts/themes/tools/theme-check)
