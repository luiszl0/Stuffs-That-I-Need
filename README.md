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

User-facing storefront copy should use Shopify's translation filter:

```liquid
{{ 'home.products.title' | t }}
```

When adding or changing translated copy, keep the key structure consistent across the relevant files in `locales/`. The current default storefront strings are maintained in [`locales/en.default.json`](./locales/en.default.json); `locales/pt-BR.json` provides the Brazilian Portuguese locale. Preserve interpolation placeholders such as `{{ terms }}` and `{{ count }}` exactly in translated values.

## Shopify theme resources

- [Theme architecture](https://shopify.dev/docs/storefronts/themes/architecture)
- [Liquid](https://shopify.dev/docs/api/liquid)
- [Shopify CLI](https://shopify.dev/docs/api/shopify-cli)
- [Theme Check](https://shopify.dev/docs/storefronts/themes/tools/theme-check)
