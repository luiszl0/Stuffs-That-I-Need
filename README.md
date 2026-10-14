# Stuff That I Need

A Shopify Online Store theme for **Stuff That I Need**, a store for curious finds, useful everyday items, and playful gifts. The storefront uses a minimalist visual style with warm neutral colors, responsive product imagery, and reusable sections that can be managed in the Shopify theme editor.

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

- **Homepage:** a responsive split hero, featured products, and a brand-story section.
- **Product discovery:** collection pages use responsive product cards with product imagery, prices, sale and sold-out states, and Shopify pagination. Search results support products, pages, and articles.
- **Product pages:** product information and purchase actions use Shopify product and variant data.
- **Cart:** the cart uses Shopify's native cart form and data, including quantity updates, item removal, discounts, cart attributes, and the native checkout action.
- **Theme editor:** homepage sections expose settings for copy, product collections, and images.
- **Responsive layout:** grids and imagery adapt to desktop, tablet, and mobile widths.
- **Navigation:** the header always shows Início, Catálogo, Contato, and Play. Catálogo uses Shopify's all-products collection.

Product and collection content is managed in Shopify Admin. The theme renders store data; it does not create or publish products.

## Theme structure

```text
.
├── assets/       # Global critical styles and static theme assets
├── blocks/       # Reusable theme blocks
├── config/       # Theme settings and editor data
├── layout/       # Document shell and section groups
├── locales/      # Brazilian Portuguese storefront and theme-editor strings
├── sections/     # Homepage, catalog, product, cart, and content sections
├── snippets/     # Shared Liquid fragments
└── templates/    # JSON and Liquid page compositions
```

Templates determine which sections render on each page. Sections contain their own styles and Shopify schema settings, so merchants can arrange and configure the storefront in the theme editor without editing Liquid.

## Language

The theme ships Brazilian Portuguese only. Storefront strings and theme-editor labels are in `locales/pt-BR.default.json` and `locales/pt-BR.default.schema.json`. The header has no language selector or configurable menu; Portuguese (Brazil) should remain the default language in Shopify Admin.

Create a Shopify page with the handle `contato` for the Contato link. The page template automatically displays a contact form on that page. The Play link targets the collection with handle `play`.

## Shopify theme resources

- [Theme architecture](https://shopify.dev/docs/storefronts/themes/architecture)
- [Liquid](https://shopify.dev/docs/api/liquid)
- [Shopify CLI](https://shopify.dev/docs/api/shopify-cli)
- [Theme Check](https://shopify.dev/docs/storefronts/themes/tools/theme-check)
