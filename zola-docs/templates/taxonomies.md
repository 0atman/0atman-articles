+++
title = "Taxonomies"
weight = 40
+++

Zola will look up the following, taxon-specific files in the `templates` directory:

- `$TAXONOMY_NAME/single.html`
- `$TAXONOMY_NAME/list.html`

if they are not found, it will attempt to fall back on the following generic template files:
- `taxonomy_single.html`
- `taxonomy_list.html`

The taxonomy templates are required only if at least one taxonomy exists with `render` set to `true`.

First, `TaxonomyTerm` has the following fields:

```ts
name: String;
slug: String;
path: String;
permalink: String;
pages: Array<Page>;
page_count: Number;
```

and `TaxonomyConfig` has the following fields:

```ts
name: String,
paginate_by: Number?;
paginate_path: String?;
feed: Bool;
render: Bool;
```


### Taxonomy list (`list.html`)

This template is never paginated and therefore gets the following variables in all cases.

```ts
// The site config
config: Config;
// The data of the taxonomy, from the config
taxonomy: TaxonomyConfig;
// The current full permalink for that page
current_url: String;
// The current path for that page
current_path: String;
// All terms for that taxonomy
terms: Array<TaxonomyTerm>;
// The lang of the current page
lang: String;
```


### Single term (`single.html`)
```ts
// The site config
config: Config;
// The data of the taxonomy, from the config
taxonomy: TaxonomyConfig;
// The current full permalink for that page
current_url: String;
// The current path for that page
current_path: String;
// The current term being rendered
term: TaxonomyTerm;
// The lang of the current page
lang: String;
```

A paginated taxonomy term will also get a `paginator` variable; see the
[pagination page](@/documentation/templates/pagination.md) for more details.
